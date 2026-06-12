---
title: "Non-PAE system updating to PAE kernels?"
date: 2013-03-14
forum: General Help
---

### Post by d4m1r on 2013-03-14
Hey guys, I just had a Ubuntu system of mine completely die on me after upgrading it and now I am confused....Basically, it is an older machine (Intel P3, 512MB RAM, etc) that I use as a command line only test bed. It's CPU does NOT support PAE extensions. PAE is mandatory when installing 12.04 LTS so what I basically did was install 11.10 x86 and then updated to 12.04 LTS and that worked fine. It even detected the CPU didn't support PAE, ignored the PAE kernels, and updated all the relevant non-PAE packages correctly (including using non PAE kernels under 12.04 LTS). Fast forward a few months as I hadn't used the thing so I wanted to update it. Did apt-get update and it listed a bunch of packages including a new kernel. At the top, it did say something along the lines of "these packages are being ignored" and then listed several *PAE packages. So I proceeded with the update as everything it was going to do looked OK to me, however, the update failed (see screenshot below) and now the machine won't even boot....

[IMG]http://i.imgur.com/xa6vRAW.png[/IMG]

What is going on? Is it not possible to update 12.04 LTS anymore on non-PAE machines? How come it tried to (seemingly) update to *PAE packages when my CPU can't support them? I feel like this is the root of the problem but if you have any other idea's or suggestions, please mention them! :(

---

### Post by ibjsb4 on 2013-03-14
What about installing xubuntu 12.04 or lubuntu and then install the ubuntu-desktop (post#39)?  I have not tried this, but it looks doable.

[http://ubuntuforums.org/showthread.php?t=1959675](http://ubuntuforums.org/showthread.php?t=1959675)

---

### Post by d4m1r on 2013-03-14
Thanks for the reply but this is a server actually so I don't need a desktop...I don't want to install anything other than a default ubuntu image anyway though.

---

### Post by bab1 on 2013-03-14
There must be some other problem.  P3 CPU's support running PAE.  I have 2 running myself.  Here is the info on one of them

```
bab@ventura:~$ uname -r
3.2.0-23-generic-pae

bab@ventura:~$ sudo lshw -C cpu

  *-cpu                   
       description: **CPU**
       product:** Pentium III (Coppermine)**
       vendor: Intel Corp.
       physical id: 4
       bus info: cpu@0
       version: 6.8.6
       slot: J4L1
       size: 1GHz
       capacity: 1GHz
       width: 32 bits
       clock: 133MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pse36 mmx fxsr sse up

```

[COLOR="#0000CD"]Edit:  Looking at your attachment a little closer, it appears to be a HDD I/O problem.  See the references to "read only file system"?  This is a sign that the drive is failing and has been mounted read only.  I would start by using **fsck** on the partition in question first and then check the drive health. [/COLOR]

---

### Post by d4m1r on 2013-03-14
Not all P3's supported PAE, unfortunetly mine doesn't support it and I know this for a fact.

---

### Post by bab1 on 2013-03-14
Can you show the your output of this```
sudo lshw -C cpu
```
...just my curiosity.

---

### Post by d4m1r on 2013-03-14
Nope considering I can't even boot into the machine now :(

@Disk I/O and read only errors, couldn't those have been caused by trying to load/install a PAE kernel on a non PAE system?

---

### Post by bab1 on 2013-03-15
> **d4m1r said:**
> Nope considering I can't even boot into the machine now :(

That's too bad.  I'd be curious to see if the PAE flag is present of not.  > 

@Disk I/O and read only errors, couldn't those have been caused by trying to load/install a PAE kernel on a non PAE system?
Not in my experience.  Disk I/O and the remounting of the partition is usually associated with failing hard drives.  The remount read only is so that the system doesn't cause further damage while attempting to leave the system up and running.

If you were to try and load or install the kernel that was inappropriate it should just fail completely.

I would try a LiveCD or a USB boot and check the CPU for PAE compatability.  If you need to revert to an earlier version then do that .  You can check the flags with the command I gave you.  If the flag is there the CPU is PAE capable.
```
       capabilities: fpu fpu_exception wp vme de pse tsc msr **[COLOR="#FF0000"]pae[/COLOR]** mce cx8 mtrr pge mca cmov pse36 mmx fxsr sse up
```

[COLOR="#0000FF"]**Edit:**  I wonder if the HDD had already failed and was in read only mode when the update was attempted?[/COLOR]

---

### Post by d4m1r on 2013-03-15
If read only mode is caused by HDD failure, then it had definitely not failed before the update. Everything looked normal to me and I used the system how I wanted to months back when I first set it up and the day it died (before the update). Because of that, I think the upgrade/install of a PAE kernel triggered this but yes, it could be a random hardware failure as well.

---

### Post by bab1 on 2013-03-15
> **d4m1r said:**
> If read only mode is caused by HDD failure, then it had definitely not failed before the update. Everything looked normal to me and I used the system how I wanted to months back when I first set it up and the day it died (before the update). Because of that, I think the upgrade/install of a PAE kernel triggered this but yes, it could be a random hardware failure as well.
I guess we won't know until we test it all.   Was the OS on a separate disk or partition from the data?

---

### Post by d4m1r on 2013-03-15
No, it was all 1 partition on 1 disk.

---

