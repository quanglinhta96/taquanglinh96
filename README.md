#include<bits/stdc++.h>
using namespace std;
#define ll long long

/*ll Factorial(int N){
    if (N == 0) return 1;
    return N * Factorial(N - 1);
}*/

int main(){
	ios_base::sync_with_stdio(0); cin.tie(0);
    int C = 0;
    int N; cin >> N;
    for (int i = 0; i < N; ++i){
        int X; cin >> X;
        if (X == 2) C++;
    }
    if (C < 9) {
        cout << 0;
        exit(0);
    }
   bool check[10];
    for (int i = 0; i < 10; ++i){
        if (i == 0 || i == 1) check[i] = false;
        else check[i] = true;
    }
    int ans[9];
    //for (int i = 0; i < 9; ++i) ans[i] = C - i;
    //int ans[9];
    //int check[10];
    ll lastAns = 1;

    for (int i = 0; i < 9; ++i){
        ans[i] = C - i;
        for (int j = 2; j < 10; ++j){
            if (ans[i] % j == 0 && check[j] == 1){
                ans[i] /= j;
                check[j] = 0;
            }
        }
        lastAns *= ans[i];

    }
    //for (int i = 0; i < 9; ++i) lastAns *= ans[i];
    for (int i = 2; i < 10; ++i){
        if (check[i] == 1) lastAns /= i;
    }
    cout << lastAns; 
    return 0;

	}

