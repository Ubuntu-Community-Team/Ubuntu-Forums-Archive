---
title: "undefined reference to TCanvas in Ubuntu 12.04"
date: 2014-11-25
forum: General Help
---

### Post by Gunnnn on 2014-11-25
I am using ROOT framework for Physics data analysis. And for the complex analysis my group has developed a software which is working fine on OpenSUSE, but when I try to run it on Ubuntu 12.04, it gives following error:

```
$ make
g++ -g -o FBBA FBBA.o  libFBBAnal.so  -L../FBRun libFBRun.so\
       -L/usr/local/root/lib -lRint -L/usr/local/root/lib -lGui -lCore  -lCint -lRIO -lNet -lHist -lGraf -lGraf3d -lGpad -lTree -lRint  -lPostscript -lMatrix -lPhysics -lMathCore -lThread -pthread -lm -ldl  -rdynamic -m64 -L/usr/local/root/lib -lCore -lCint -lRIO -lNet -lHist  -lGraf -lGraf3d -lGpad -lTree -lRint -lPostscript -lMatrix -lPhysics  -lMathCore -lThread -pthread -lm -ldl -rdynamic -lGpad -lHist -lGraf  -lGraf3d -lTree -lRint -lPostscript -lMatrix -lPhysics -lMathCore -lRIO  -lNet -lThread -lCore -lCint -pthread -lm -ldl -rdynamic  -lTMVA  -lMinuit -lXMLIO -lMLP -lTreePlayer -L/usr/lib64/ -lstdc++
libFBBAnal.so: undefined reference to `TCanvas::TCanvas(char const*, char const*, int, int, int, int)'
collect2: ld returned 1 exit status
make: *** [FBBA] Error 1
```

When I comment out all the instances with TCanvas, I get no error. Little research plus communication with ROOT comunity tell that this is problem caused by smart linking issue in Ubuntu.
Help please !

---

### Post by Gunnnn on 2014-11-26
SOLVED:

I had to manually attach ROOT libraries in my Makefile at the place where this *.so file is giving error. And it solved the problem. 
As I expected it was the problem due to Ubuntu's linker's behaviour, it doesn't automatically link all the libraries, one has to manually (by force or explicitly) link it.

---

