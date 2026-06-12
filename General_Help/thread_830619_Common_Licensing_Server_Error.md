---
title: "Common Licensing Server Error"
date: 2008-06-16
forum: General Help
---

### Post by tarekeldeeb on 2008-06-16
Hello all,

I googled a lot before posting this thread. Many programs use the lmgrd licensing server to check for the installed license. The lmgrd server must run properly and see the license file, then the main program is run. If the licensing server is not set properly, the program will not run.

Programs like Matlab, Synopsis design compiler, Cadence use such method.

When I install the server it seems like running, but gives the following error on ubuntu:
>  8:20:41 (lmgrd) -----------------------------------------------
 8:20:41 (lmgrd)   Please Note:
 8:20:41 (lmgrd) 
 8:20:41 (lmgrd)   This log is intended for debug purposes only.
 8:20:41 (lmgrd)   There are many details in licensing policies
 8:20:41 (lmgrd)   that are not reported in the information logged
 8:20:41 (lmgrd)   here, so if you use this log file for any kind
 8:20:41 (lmgrd)   of usage reporting you will generally produce
 8:20:41 (lmgrd)   incorrect results.
 8:20:41 (lmgrd) 
 8:20:41 (lmgrd) -----------------------------------------------
 8:20:41 (lmgrd) 
 8:20:41 (lmgrd) 
 8:20:41 (lmgrd) Can't make directory /usr/tmp/.flexlm, errno: 2(No such file or directory)
 8:20:41 (lmgrd) Can't make directory /usr/tmp/.flexlm, errno: 2(No such file or directory)
 8:20:41 (lmgrd) Can't open /usr/tmp/.flexlm/lmgrdl.17205, errno: 2
license manager: can't initialize
 8:20:41 (lmgrd) Can't remove statfile /usr/tmp/.flexlm/lmgrdl.17205: errno No such file or directory


Note that the server runs perfect on other distributions like CentOS.

Did anyone face this problem ?
Any ideas? clues?

Thanks in advance,
Tarek

---

### Post by tarekeldeeb on 2008-06-16
Mmm..

---

### Post by geirha on 2008-06-16
How did you install it? 

It sounds like it expects /tmp to be in /usr/tmp. You probably don't have that directory there. What happens if you make a symlink there? ```
sudo ln -s /tmp /usr/tmp
```

---

### Post by tarekeldeeb on 2008-06-18
> **geirha said:**
> How did you install it? 

It sounds like it expects /tmp to be in /usr/tmp. You probably don't have that directory there. What happens if you make a symlink there? ```
sudo ln -s /tmp /usr/tmp
```

Perfect !!

Thanks a lot, the link fixed the problem ..
The synopsys design compiler is now running under ubuntu !
:)

---

