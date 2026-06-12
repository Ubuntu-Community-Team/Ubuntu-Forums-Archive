---
title: "Google Chrome Browser 32bit Support"
date: 2017-03-24
forum: General Help
---

### Post by braznyc on 2017-03-24
Google Chrome is my favorite web browser, but I'm starting to get more and more messages saying that the version I use is no longer supported (Facebook, Gmail, Google Docs etc).

I'm looking for some kind of work around to fix that issue and keep using it, at least temporarily, until I get a 64bit computer.


I know that Firefox and Chromium (this one in some websites) could be alternatives.


Any suggestion?

---

### Post by RobGoss on 2017-03-24
Your best choice would be Chromium the 32 bit if in fact your machine is a 32-bit, Google Chrome is no longer supposed for a 32 bit. If Google Chrome dropped support there's really no work around

---

### Post by dragonfly41 on 2017-03-24
What does command   lscpu    show in terminal?

Could be that you have both 32/64 bit compatibility.
I found that my old laptop (on which I have installed Ubuntu 14.04 32bit)
is surprisingly 64 bit compatible.

---

### Post by slickymaster on 2017-03-24
> **dragonfly41 said:**
> What does command   lscpu    show in terminal?

Could be that you have both 32/64 bit compatibility.
I found that my old laptop (on which I have installed Ubuntu 14.04 32bit)
is surprisingly 64 bit compatible.

@braznyc:
After running the command dragonfly41 said, you should see a result like this:
```
Architecture: x86_64
**CPU op-mode(s): 32-bit, 64-bit**
<---snip--->
```
You need to look for the line that starts with CPU op-mode. As you can see in the above result, that CPU can support 32 bit and 64 bit. This means it has a 64 bit CPU. If you see only 32 bit under CPU op-mode, you have a 32 bit system.

---

### Post by braznyc on 2017-03-24
RobGoss,

I have to customize Chromium to look like Chrome a little bit. I think it hasn't been updated for a while.
Thanks.

---

### Post by braznyc on 2017-03-24
> **dragonfly41 said:**
> What does command   lscpu    show in terminal?

Could be that you have both 32/64 bit compatibility.
I found that my old laptop (on which I have installed Ubuntu 14.04 32bit)
is surprisingly 64 bit compatible.

Hello, Dragonfly41
I got this:

```

CPU op-mode(s):        32-bit, 64-bit 
Byte Order:            Little Endian 
CPU(s):                2 
On-line CPU(s) list:   0,1 
Thread(s) per core:    1 
Core(s) per socket:    2 
Socket(s):             1 
Vendor ID:             GenuineIntel 
CPU family:            6 
Model:                 23 
Model name:            Intel(R) Core(TM)2 Duo CPU     T6400  @ 2.00GHz 
Stepping:              10 
CPU MHz:               1200.000 
CPU max MHz:           2000.0000 
CPU min MHz:           1200.0000 
BogoMIPS:              3990.29 
L1d cache:             32K 
L1i cache:             32K 
L2 cache:              2048K
```

Is it good news?

If it is, how can I enable it to run 64bit programs?

---

### Post by slickymaster on 2017-03-24
> **braznyc said:**
> Hello, Dragonfly41
I got this:

```
CPU op-mode(s):        32-bit, 64-bit 
Byte Order:            Little Endian 
CPU(s):                2 
On-line CPU(s) list:   0,1 
Thread(s) per core:    1 
Core(s) per socket:    2 
Socket(s):             1 
Vendor ID:             GenuineIntel 
CPU family:            6 
Model:                 23 
Model name:            Intel(R) Core(TM)2 Duo CPU     T6400  @ 2.00GHz 
Stepping:              10 
CPU MHz:               1200.000 
CPU max MHz:           2000.0000 
CPU min MHz:           1200.0000 
BogoMIPS:              3990.29 
L1d cache:             32K 
L1i cache:             32K 
L2 cache:              2048K
```

Is it good news?

If it is, how can I enable it to run 64bit programs?

See my post [here]("https://ubuntuforums.org/showthread.php?t=2356574&p=13624661&viewfull=1#post13624661").

---

### Post by dragonfly41 on 2017-03-24
Well the good news is that you can install Ubuntu (64 bit) and so can continue using Google Chrome Browser.

The bad news is that you would need to go through a major transition/reinstall of Ubuntu to 64bit version.
It is up to you whether this is a worthwhile step in order to keep Google Chrome Browser.
I use Chromium Web Browser on 32bit which is just as good in my opinion.


p.s. You have some alternative options to consider.
(a) create dual boot Ubuntu 32 bit (your current OS) and Ubuntu 64 bit (as second boot option).
or
(b) install VirtualBox in your 32 bit OS and install 64 bit Ubuntu VM in VirtualBox.

---

### Post by oldfred on 2017-03-24
I had a similar Core2 Duo. In 2006 I installed 32 bit as back then the 64 bit was new and some said not as stable nor all apps available.
In 2009 I installed 64 bit and kept if for another 5 years. I was going to get a new system in 2011, but got a small SSD as boot drive instead. Could not then justify new system as with 4GB of RAM, SSD and core2 64 bit and Ubuntu with fallback (not Unity) it ran really well.

But you cannot convert. Backup, reinstall 64 bit and restore data.
You have to backup your data, installed apps, perhaps settings in /etc. If all data is in /home then that is most of what you have to backup.
I found new clean install worked so well after many updates from 2006 thru 2009, that now I only do new installs, but usually keep old install and have all data in separate /mnt/data partition so all installs access same data.

       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

---

### Post by braznyc on 2017-03-24
> **dragonfly41 said:**
> Well the good news is that you can install Ubuntu (64 bit) and so can continue using Google Chrome Browser.

The bad news is that you would need to go through a major transition/reinstall of Ubuntu to 64bit version.
It is up to you whether this is a worthwhile step in order to keep Google Chrome Browser.
I use Chromium Web Browser on 32bit which is just as good in my opinion.


p.s. You have some alternative options to consider.
(a) create dual boot Ubuntu 32 bit (your current OS) and Ubuntu 64 bit (as second boot option).
or
(b) install VirtualBox in your 43 bit OS and install 86 bit Ubuntu VM.


I think it will be worth it. I also need the new version of Krita, that only runs on 64bit systems. And as I can see the support for 32 apps is disappering.

Do you think I have enough CPU and RAM to make it run smooth?

---

### Post by dragonfly41 on 2017-03-24
I would first create a Live USB of Ubuntu 16.04 (64bit) and boot into USB and select "Try Ubuntu".

See how it runs, before you decide.

You will need this anyway to install Ubuntu 16.04 so it is not wasting effort.

---

### Post by braznyc on 2017-03-24
> **dragonfly41 said:**
> I would first create a Live USB of Ubuntu 16.04 (64bit) and boot into USB and select "Try Ubuntu".

See how it runs, before you decide.

You will need this anyway to install Ubuntu 16.04 so it is not wasting effort.


Thanks.

I'll do that.

Thank you all for the replies!

---

### Post by vasa1 on 2017-03-24
> **braznyc said:**
> ... I also need the new version of Krita, that only runs on 64bit systems. And as I can see the support for 32 apps is disappering.

Do you think I have enough CPU and RAM to make it run smooth?Ideally, you should have a GPU as well if you plan on running Ubuntu.

---

### Post by oldos2er on 2017-03-24
> **braznyc said:**
> Do you think I have enough CPU and RAM to make it run smooth?

How much RAM does your system have?

---

