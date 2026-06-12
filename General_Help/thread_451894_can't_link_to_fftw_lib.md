---
title: "can't link to fftw lib"
date: 2007-05-22
forum: General Help
---

### Post by detector on 2007-05-22
I installed fftw3 in ubuntu.  When I use gcc -lfftw3 -lm with my own program,  the libraries are not found.
I have an identical installation in Fedora core 5 which works.  I checked that the libraries, include files are in the same places. 
Is there some difference in the setup causing gcc not to look in the default places /usr/local/lib/ ?

Incidentally, I am new to Ubuntu forum.  How do I search past postings?

---

### Post by WW on 2007-05-22
How did you install fftw3?  If you used the Ubuntu packages **fftw3** and **fftw3-dev**, then the libraries are in /usr/lib and the headers are in /usr/include.  (Ubuntu packages never install files to /usr/local.)

---

### Post by WW on 2007-05-22
On the other hand, if you installed fftw3 from source into /usr/local, then you should add the options **-I/usr/local/include** when you compile and **-L/usr/local/lib** when you link.

---

