---
title: "Octave eig(L,'vector') not functioning as Matlab"
date: 2017-07-25
forum: General Help
---

### Post by madtom1999 on 2017-07-25
The following runs fine on Matlab but not Octave:
%Form the matrix of weights based on the graph
N = 11;
W = zeros(N,N);
W(1,2) = 0.5;
W(1,5) = 0.5;
W(2,3) = 0.6;
W(3, 4) = 0.6;
W(4,5) = 0.6;
W(4,6) = 0.1;
W(5, 7) = 0.2;
W(6,7) = 0.8;
W(7,8) = 0.4;
W(8,9) = 0.5;
W(9,10) = 0.7;
W(10,11) = 0.7;
W(11,6) = 0.8;
% Since it's undirected add on the transpose to assign the edges in the
% other direction
W = W + W';

% Examine the structure of the weights matrix
spy(W)
% Form the degree matrix, D
D = diag(sum(W,2));
% Form the Laplacian
L = D - W;
 % Find the eigenvectors and eigenvalues
[evec,eval] = eig(L, 'vector');
error: eig: wrong type argument 'sq_string'

---

### Post by steeldriver on 2017-07-25
At least as of v4.0.0, I don't think octave supports the additional matlab `eigvalOption` to specify whether the eigenvalues are returned as a column vector or a (diagonal) matrix

AFAIK it should be equivalent to call

```

[evec,eval] = eig(L);

```

and then diagonalize the output matrix yourself

```

diag(eval)

```

---

### Post by vocx on 2017-07-25
> **madtom1999 said:**
> The following runs fine on Matlab but not Octave:
```
% Find the eigenvectors and eigenvalues
[evec,eval] = eig(L, '**vector**');
error: eig: **wrong type argument 'sq_string'**
```

Remember that Octave is not identical to Matlab. Octave pretty much tries to copy every aspect of Matlab, including the options for many functions. However, many options that are available in Matlab do not necessarily exist in Octave, and the opposite is true as well. For simple scripts Matlab and Octave may be exactly compatible, but for more advanced uses they may diverge. You should check the documentation of the functions in both Matlab and Octave to confirm your code works as you expect. Ultimately, you may decide to stick to one programming language and focus your attention on following only one set of documentation. Breaking compatibility for one of the two systems may be a bit of a headache, but it's a decision you may have to make as your code grows in complexity and number of lines.

The latest version 4.2.1. seems to indicate that the "vector" option exists for "eig()".
[https://www.gnu.org/software/octave/doc/v4.2.1/Basic-Matrix-Functions.html](https://www.gnu.org/software/octave/doc/v4.2.1/Basic-Matrix-Functions.html)

However, you may be using an older version, maybe 4.0.0, which apparently does not have that option.
[https://www.gnu.org/software/octave/doc/v4.0.0/Basic-Matrix-Functions.html](https://www.gnu.org/software/octave/doc/v4.0.0/Basic-Matrix-Functions.html)

Remember that in Ubuntu the software in the repositories is usually a bit behind the latest version available. If you need the absolute most recent version then you need to be prepared to install that yourself.

If you have control of the code, that is, if you are not part of a collaborative team constantly adding to or changing the code, or if you want to stick to free software, then you may chose to use only Octave, or even Python, which also has many numerical libraries. A disadvantage of Octave is that an inexperienced user may not recognize it as a separate language; he or she may think it is Matlab and get frustrated if it actually doesn't work with Matlab. An advantage of Python is that it really is a more modern, general purpose programming language, so learning it may actually bring benefits to the users, in terms of teaching new concepts (object orientation, classes, data structures) that are not widely used in Matlab. I feel in Windows people would prefer Matlab, and only if not available they would use Octave, which has the risk of producing incompatible code in one language or the other, as I mentioned before. On the other hand, Python would work nicely in a dual environment with Windows and Linux, as the code should be, and should work the same.

---

### Post by monkeybrain20122 on 2017-07-25
Works here. Octave 4.2.1. Ubuntu 16.04. I built octave from source.

---

### Post by madtom1999 on 2017-07-27
I filed a bug on the Octave list and it turns out this has been fixed in later versions of Octave.
Hope someone can update the package as I cant get the source to build!

---

### Post by vocx on 2017-07-27
> **madtom1999 said:**
> I filed a bug on the Octave list and it turns out this has been fixed in later versions of Octave.
Hope someone can update the package as I cant get the source to build!
Did you read my previous post? This is not a "bug". A bug is when something is documented and should work, but it doesn't. Octave is not, and will never be, identical to Matlab. If there are "missing" features in an Octave function, this cannot be considered a bug, it's just something that has not been implemented. It is a mistake to consider Octave and Matlab 100% compatible, you should understand this.

As I mentioned, it seems it is not available in 4.0.0, but it seems to be available in 4.2.1. Of course, you yourself have to do the work of getting the newest version if you want to use the most recent features.

---

### Post by monkeybrain20122 on 2017-07-27
You can either install octave 4.2.1 from source (which is not difficult), or you can install it via a ppa [https://launchpad.net/~wdaniau/+archive/ubuntu/custom](https://launchpad.net/~wdaniau/+archive/ubuntu/custom) , or this one [https://launchpad.net/~compdatasci/+archive/ubuntu/octave](https://launchpad.net/~compdatasci/+archive/ubuntu/octave)

---

