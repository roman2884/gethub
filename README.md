#include <iostream>
#include <vector>
#include <cmath>

using namespace std;

vector<double> linear_regression(vector<double> x, vector<double> y) {
    int n = x.size();
    
    double sum_x = 0, sum_y = 0, sum_xy = 0, sum_x_squared = 0;
    
    for (int i = 0; i < n; i++) {
        sum_x += x[i];
        sum_y += y[i];
        sum_xy += x[i] * y[i];
        sum_x_squared += x[i] * x[i];
    }
    
    double slope = (n * sum_xy - sum_x * sum_y) / (n * sum_x_squared - sum_x * sum_x);
    double intercept = (sum_y - slope * sum_x) / n;
    
    vector<double> result = {slope, intercept};
    
    return result;
}

int main() {
    vector<double> x = {1, 2, 3, 4, 5};
    vector<double> y = {2, 3, 4, 5, 6};
    
    vector<double> result = linear_regression(x, y);
    
    cout << "Slope: " << result[0] << endl;
    cout << "Intercept: " << result[1] << endl;
    
    return 0;
}
