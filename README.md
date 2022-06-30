# Math-
new repo
#include <iostream>
#include <cmath>
#include <fstream>
#include <iomanip>

double f(double x);
double LeftRiemannSum(double a, double b, unsigned int n);
double RightRiemannSum(double a, double b, unsigned int n);
double MidPointRiemannSum(double a, double b, unsigned int n);

int main()
{
	std::ofstream File("data.csv");

	File << "n,L_n,R_n,M_n\n";
	for (unsigned int i = 20; i <= 10000; i += 20)
	{
		File << i << std::setprecision(11) << ',' 
			<< LeftRiemannSum(0, 2, i) << ',' 
			<< RightRiemannSum(0, 2, i) << ',' 
			<< MidPointRiemannSum(0, 2, i) << '\n';
	}
	std::cout << "Finished Writting...";
	std::cin.get();
	return 0;
}

double f(double x)
{
	return std::pow(x, 3) + 1;
}

double LeftRiemannSum(double a, double b, unsigned int n)
{
	double dx = (b - a) / n;
	double sum = 0.0;
	double x = a;
	for (unsigned int i = 1; i <= n; i++)
	{
		sum += f(x) * dx;
		x += dx;
	}
	return sum;

}

double RightRiemannSum(double a, double b, unsigned int n)
{
	double dx = (b - a) / n;
	double sum = 0.0;
	double x = a;
	for (unsigned int i = 1; i <= n; i++)
	{
		x += dx;
		sum += f(x) * dx;
	}
	return sum;

}

double MidPointRiemannSum(double a, double b, unsigned int n)
{
	double dx = (b - a) / n;
	double sum = 0.0;
	double x = a + 0.5*dx;
	for (unsigned int i = 1; i <= n; i++)
	{
		sum += f(x) * dx;
		x += dx;
	}
	return sum;
}
