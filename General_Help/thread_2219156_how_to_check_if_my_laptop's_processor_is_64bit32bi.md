---
title: "how to check if my laptop's processor is 64bit/32bit"
date: 2014-04-23
forum: General Help
---

### Post by AbhimanyuAryan on 2014-04-23
I am currently running ubuntu 14.04 32-bit final beta. I want to upgrade to 14.04 LTS. So, how can i check if i should use 64bit or 32bit version of ubuntu?

With this command: uname -a

i get this: Linux Acer 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 i686 i686 GNU/Linux

which version should i use?

Laptop: Acer Aspire E1-571G

---

### Post by mörgæs on 2014-04-23
It's capable of 64 bit. 
If some day you want to reinstall you could take the 64 bit ISO.

---

### Post by mastablasta on 2014-04-23
also if CPU is 32bit then 64 bit won't boot on it :p

---

### Post by AbhimanyuAryan on 2014-04-23
but they say 64Bit for AMD mine is have an intel processor :o

---

### Post by Elfy on 2014-04-23
That's fine - that is the right image for 64bit.

[http://ubuntuforums.org/showthread.php?t=2123998&p=12549657&viewfull=1#post12549657](http://ubuntuforums.org/showthread.php?t=2123998&p=12549657&viewfull=1#post12549657)

---

### Post by 3rdalbum on 2014-04-23
You don't need to reinstall Ubuntu to get the final version of 14.04. Just run your ordinary system updates to get the latest little changes. If the Update Manager says that your system is up-to-date then you already have 14.04 LTS and you can use it for five years.

---

### Post by Yellow Pasque on 2014-04-23
> **AbhimanyuAryan said:**
> but they say 64Bit for AMD mine is have an intel processor :o

No, it says "amd64" because AMD invented the 64-bit standard. Intel uses it too though.

---

### Post by AbhimanyuAryan on 2014-04-23
in windows settings in can easily see if a machine has 64bit CPU processor or not 

however here i get this result [COLOR=#000000]: Linux Acer 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 i686 i686 GNU/Linux

how can i make out b/w 32bit or 64bit processor?[/COLOR]

---

### Post by Yellow Pasque on 2014-04-23
```
cat /proc/cpuinfo
```
Look for "lm" (long mode) in the flags. Then you have 64-bit goodness.

---

### Post by mörgæs on 2014-04-23
The string 
> **AbhimanyuAryan said:**
> 
[COLOR=#000000]Linux Acer 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 i686 i686 GNU/Linux
[/COLOR]
only tells that your present install is 32 bit, not what the processor is capable of running.

---

