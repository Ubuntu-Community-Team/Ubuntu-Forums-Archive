---
title: "Segmentation Fault (core dumped)"
date: 2014-11-09
forum: General Help
---

### Post by Cristian_Sandu on 2014-11-09
Hi! I am a new Ubuntu User...
I installed CodeBlocks and g++ last hour (from terminal). When I try to "Build and run" a program, on screen (console) appear an Error. 

> Segmentation Fault (core dumped).   Why?

This is my program:
```
#include <fstream>

using namespace std;


ifstream fin ("date.in");
ofstream fout ("date.out");


char h[25]; // Memorare element care ies din stiva


int i, j, b[25], a[25], k, n;


int stiva[25];


int main()
{
    fin >> n;
    for (i=0; i<n; i++)
    {
        fin >> a[i];
    }
    for (i=0; i<n; i++)
    {
        fin >> b[i];
    }
    fin.close();
    int vf = 0;
    j = 0; i = 0; k = 0;
    while (j<n)
    {
        while (stiva[vf] == b[j] && vf  > 0)
        {
            h[k] = 'O';
            vf--;
            j++;
            k++;
        }
        if (a[i] == b[j] && j<n)
        {
            h[k] = 'I';
            k++;
            h[k] = 'O';
            k++;
            i++;
            j++;
        }
        else if (j<n)
        {
            h[k] = 'I';
            k++;
            i++;
        }
    }
    if (vf > 0)
    {
        fout << "Imposibil!";
    }
    else
    {
        for (i=0; i<k; i++)
        {
            fout << h[i] << " ";
        }
    }
    fout.close();
    return 0;
}

```

---

### Post by Cristian_Sandu on 2014-11-09
Solved!

---

