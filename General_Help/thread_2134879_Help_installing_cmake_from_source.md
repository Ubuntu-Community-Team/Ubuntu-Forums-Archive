---
title: "Help installing cmake from source"
date: 2013-04-12
forum: General Help
---

### Post by heyup on 2013-04-12
cmake 2.8.7 is in Precise 12.04 repository, but I require 2.8.9 (or later).

Downloaded source from [http://www.cmake.org/cmake/resources/software.html]("http://www.cmake.org/cmake/resources/software.html") and built from source as per the readme file:
```
./bootstrap --prefix=/opt/cmake
make
sudo make install
```

The build seemed to install OK, but when I run:
```
cmake
```

I get:
> The program 'cmake' is currently not installed.  You can install it by typing:
sudo apt-get install cmake

How do I get the system to recognize the install?

---

### Post by steeldriver on 2013-04-12
Is it maybe just a matter of adding the /opt/cmake directory to your path?

```
$ export PATH=$PATH:/opt/cmake
```

(or maybe /opt/cmake/bin if it puts the actual binary in a bin subdir)

---

### Post by heyup on 2013-04-12
Ah! Thank you.   
```
$ export PATH=$PATH:/opt/cmake/bin
```
Fixed the problem.

Perhaps I should have used checkinstall as recommended here:
 
[https://help.ubuntu.com/community/CompilingSoftware?]("https://help.ubuntu.com/community/CompilingSoftware?")

---

### Post by heyup on 2013-04-12
> **heyup said:**
> Ah! Thank you.   
```
$ export PATH=$PATH:/opt/cmake/bin
```
Fixed the problem.

But only temporarily. If I close terminal and open new terminal and run:```
cmake
``` I get same error message, cmake is not installed.

---

### Post by steeldriver on 2013-04-12
Add the export to the bottom of your ~/.bashrc file; or to your ~/.profile if you need it to be set for other shells (that might be the case if you are going to call cmake from other build tools)

---

### Post by heyup on 2013-04-13
OK. Thanks. I'll do that.

Seems that setting the install to /opt/make is the cause of the problem. The default install is to /usr/local/bin which is in $PATH. When I tried to install with checkinstall to /opt/make I had the same problem.

---

