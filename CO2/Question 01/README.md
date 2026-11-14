// Precedence, Associativity and the Discount Bug 
// PROGRAM CODE Q1 
#include <stdio.h> 
 
int main(void) 
{ 
    double bills[3][3] = { 
        {1000.0, 1.0, 1.0},   /* price, quantity, senior citizen? */ 
        {200.0,  3.0, 1.0}, 
        {500.0,  2.0, 0.0} 
    }; 
 
    for (int i = 0; i < 3; i++) { 
        double price = bills[i][0]; 
        double qty = bills[i][1]; 
        int senior = (int)bills[i][2]; 
 
        double gross = price * qty; 
        double discount = senior ? gross * 0.15 : 0.0; 
        double taxable = gross - discount; 
        double tax = taxable * 0.05; 
        double total = taxable + tax; 
        double net = total > 1000.0 ? total - 50.0 : total; 
 
        printf("Bill %d: gross=%.2f discount=%.2f tax=%.2f total=%.2f net=%.2f\n", 
               i + 1, gross, discount, tax, total, net); 
    } 
 
    /* Correctly sequence the counter increment. */ 
    int count = 0; 
    count = count + 1; 
    printf("Count = %d\n", count); 
    return 0; 
}
