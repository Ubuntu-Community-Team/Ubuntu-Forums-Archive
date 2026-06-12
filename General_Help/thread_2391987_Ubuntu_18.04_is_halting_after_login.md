---
title: "Ubuntu 18.04 is halting after login"
date: 2018-05-15
forum: General Help
---

### Post by VectorZero on 2018-05-15
I have an Acer Aspire VX 15 (Intel Core i7, NVidia Geforce GTX 1050, 32 Gb RAM, HDD 1Tb).

I had Ubuntu 17.10 installed and everything was working fine. Then I upgraded to Ubuntu 18.04 and now, after I login via GDM (in graphics mode) the system halts. It becomes completely frozen.

However, if I press Ctrl-Alt-F2, switch to text mode, and then login in the console, the system works fine (in text mode) and do not halt.

Does anybody else has a similar problem? Do you know how to fix this? Do you know how can I diagnose the problem?

Thanks in advance.

---

### Post by hrsetrdr on 2018-05-15
I am thinking a video driver problem, have had similar occurrences, [see this thread]("https://ubuntuforums.org/showthread.php?t=2386398").  

 My Dell Inspiron 15 7567 has specs very close to your Acer Aspire VX 15 Acer, including the GTX 1050  The nouveau video driver  is installed by default, and for reasons I don't [yet] understand, will fail at some point.  

I recently installed the nVidia 384 driver after the last Ubuntu re-install.

---

### Post by VectorZero on 2018-05-16
Hi. Thaks a lot. After installing the NVIDIA driver the system seems to be working ok.

---

### Post by coruja182 on 2018-08-01
> **VectorZero said:**
> Hi. Thaks a lot. After installing the NVIDIA driver the system seems to be working ok.

What is the procedure for upgrading this video driver? Can I do that by command line?
I've tried installing Ubuntu 18, even Mint linux (newest version), but after login my computer freezes. 

It is an Acer VX 15 with a NVIDIA 1050.

---

### Post by jdosio on 2019-01-27
I also would like to know how to update the drivers, i have a similar graphics card an am encountering the same issue. what would be the fastest way of updating or installing the correct drivers i need?

---

### Post by mo3az014 on 2019-02-25
yes, I had the same problem. 
The drivers was missing.
I ran [COLOR=#242729][FONT=Consolas]sudo ubuntu-drivers autoinstall [/FONT][/COLOR]

---

