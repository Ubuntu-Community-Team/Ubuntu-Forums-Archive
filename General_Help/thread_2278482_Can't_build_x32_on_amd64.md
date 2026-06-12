---
title: "Can't build x32 on amd64"
date: 2015-05-16
forum: General Help
---

### Post by dhlii on 2015-05-16
I am trying to switch from 14.04 to 15.04
Possibly my last impediment is that I can not link an x32 application I am working on, on an amd64 system 

Either I do not have the correct x32 packages installed  or I have some link parameters wrong. 
Regardless when linking I get the following messages and errors. 
I get none of this when linking on 14.04

I have what I believe is exactly the same packages installed. 

Thank you

```
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.9/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.9/libstdc++.a when searching for -lstdc++
/usr/bin/ld: cannot find -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.9/libgcc_s.so when searching for -lgcc_s
/usr/bin/ld: cannot find -lgcc_s
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.9/libgcc.a when searching for -lgcc
/usr/bin/ld: cannot find -lgcc
collect2: error: ld returned 1 exit status
make[1]: *** [release] Error 1
make[1]: Leaving directory `/usr/local/workspace/maxima/QuiCRT/Applications/QuiCRT/Build_Environment/Linux'
make: *** [linsimd] Error 2
```

---

### Post by wildmanne39 on 2015-05-16
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by monkeybrain20122 on 2015-05-17
Probably it is not compatible with gcc4.9 which is the compiler in 15.04. You can try installing gcc4.8 from repository and switch to it with update-alternatives before you compile. You can follow the procedure changing gcc4.7 to 4.8 etc from this link.
[http://charette.no-ip.com:81/programming/2011-12-24_GCCv47/](http://charette.no-ip.com:81/programming/2011-12-24_GCCv47/)

  Instead of the command line method from the link, an easy gui way to update alternative compilers would be to install galternatives and choose the default gcc for the session from the gui.

```
sudo apt-get install galternatives
```

---

### Post by steeldriver on 2015-05-17
Did you install the g++-multilib package? that should pull in the 32-bit versions of libstdc++ (and libc6 - via gcc-multilib) development libraries, I think

---

### Post by dhlii on 2015-05-18
Thank you. That did it. 

Can't guess how I missed that. 
I thought I was through all the multilb packages

---

