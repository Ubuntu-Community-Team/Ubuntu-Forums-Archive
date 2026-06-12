---
title: "glibcxx_3.4.20 missing error when installing R package Rcpp"
date: 2014-11-16
forum: General Help
---

### Post by leejayd on 2014-11-16
Hi,

I have gcc 4.9.1 installed but when I try and install an R package (Rcpp) I receive the error that glibcxx_3.4.20 missing is missing :


```
1/Rcpp/libs/Rcpp.so':  /usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.20' not found (required by /home/user/R/x86_64-pc-linux-gnu-library/3.1/Rcpp/libs/Rcpp.so)
```

I've checked the lib folder and libstdc++so.6 is linked to libstdc++so.6.0.19 


Any ideas how I resolve this?

---

### Post by steeldriver on 2014-11-16
What version of g**++** do you have installed?

---

### Post by matt_symes on 2014-11-16
Hi

R, the stastical package ?

How did you install it ? Your path to R is in your home directory.

Kind regards

---

### Post by leejayd on 2014-11-16
I have g++ 4.9.1

The R app is stored in : usr/bin/R

The user settings/packages for R are stored in my home folder.

---

### Post by leejayd on 2014-11-16
It seems I install packages that use gcc but the packages that use G++ fail.    Do I need add G++ to my path?

---

### Post by matt_symes on 2014-11-16
Hi

You never answered my question :)

Did you install it from the repositories ?

Just trying to eliminate something.

Kind regards

---

### Post by leejayd on 2014-11-16
I installed R from a [COLOR=#000000][FONT=inherit]repository ppa[/FONT][/COLOR][COLOR=#666600][FONT=inherit]:[/FONT][/COLOR][COLOR=#000000][FONT=inherit]marutter[/FONT][/COLOR][COLOR=#666600][FONT=inherit]/[/FONT][/COLOR][COLOR=#000000][FONT=inherit]rrutter


[/FONT][/COLOR]

---

### Post by leejayd on 2014-11-16
I've checked /opt/gcc-4.9.1/lib64 and the file libstdc++.so.6 is linked to libstdc++.so.6.0.20. 

The path for gcc in [COLOR=#000000][FONT=Ubuntu Mono]/usr/lib/x86_64-linux-gnu/libstdc++.so.6 is linked to [/FONT][/COLOR][COLOR=#000000] libstdc++so.6.0.19 

[/COLOR]Could this be the reason for the error?

[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

### Post by matt_symes on 2014-11-16
Hi

> **leejayd said:**
> I installed R from a [COLOR=#000000][FONT=inherit]repository ppa[/FONT][/COLOR][COLOR=#666600][FONT=inherit]:[/FONT][/COLOR][COLOR=#000000][FONT=inherit]marutter[/FONT][/COLOR][COLOR=#666600][FONT=inherit]/[/FONT][/COLOR][COLOR=#000000][FONT=inherit]
[/FONT][/COLOR]

I would have said that is the reason for the error. It's linking to a newer version of liibst dc++ in the ppa version.

It is available in the universe repository as metapackage r-recommended.

> **leejayd said:**
> I've checked /opt/gcc-4.9.1/lib64 and the file libstdc++.so.6 is linked to libstdc++.so.6.0.20. 

The path for gcc in [COLOR=#000000][FONT=Ubuntu Mono]/usr/lib/x86_64-linux-gnu/libstdc++.so.6 is linked to [/FONT][/COLOR][COLOR=#000000] libstdc++so.6.0.19 

[/COLOR]Could this be the reason for the error?[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

This looks to be the problem.

Is there any reason you must use the ppa version and not the version in the repos ? You will not have this issue then.

Kind regards

---

### Post by leejayd on 2014-11-16
The version of R in the official repos is not kept up to date with the latest releases.

What's weird is that I have a similar set-up on another machine but with an older version of GCC (4.7 I think) and I have no issue installing packages.

The thing is it's not R that I'm compiling, moreover, R packages.   R works fine.  

Hmm.

---

### Post by leejayd on 2014-11-16
I've sorted the issue by reinstalling g++ from [COLOR=#000000][FONT=Consolas]ppa:ubuntu-toolchain-r/test[/FONT][/COLOR]

---

### Post by matt_symes on 2014-11-16
Hi

You need to load the correct libstdc++ library when running you program.

Adding it's location to your PATH will not work as it's a library.

For a quick fix read up on LD_LIBRARY_PATH when calling the executable.

Be aware this can be a security issue and is maybe not the best way to do it.

Kind regards

---

### Post by matt_symes on 2014-11-16
Hi

> **leejayd said:**
> I've sorted the issue by reinstalling g++ from [COLOR=#000000][FONT=Consolas]ppa:ubuntu-toolchain-r/test[/FONT][/COLOR]

Good. I'm glad you found a suitable fix.

Kind regards

---

