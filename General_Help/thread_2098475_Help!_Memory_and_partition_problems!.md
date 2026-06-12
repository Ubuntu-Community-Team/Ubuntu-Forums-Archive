---
title: "Help! Memory and partition problems!"
date: 2012-12-26
forum: General Help
---

### Post by zesterer on 2012-12-26
Hello all,

Recently Ubuntu announced that it was almost out of memory, and so I went to see if I could do anything about it (e.g: expand the Ubuntu partition). The only problem is, I am not sure what partition it is on, or even which disk! (The D drive has become quite full since installing Ubuntu, but thats a recovery drive)

I run a dual boot with Windows 7, and I am pretty sure that it hogs about 95% of the diskspace - I have a 512 GB harddrive. But what do i do? I have looked around on other forums and threads, and have be instructed to use Windows, so I have resized what I THINK is the windows partition and shrunk it to as small as possible. What next? Do I use Gparted on Ubuntu to resize its partition?

Thanks,

Barry Smith

---

### Post by ibjsb4 on 2012-12-26
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
df
```

Whats it say?

---

### Post by Bucky Ball on 2012-12-26
> **zesterer said:**
> Do I use Gparted on Ubuntu to resize its partition?



Yes. But you need to boot from the install CD and 'Try Ubuntu' to do it as the partitions you are resizing need to be unmounted. That can't happen if you are running the OS, if you follow me.

The Ubuntu OS is installed in the / partition. It will be clearly visible in Gparted.

This demonstrates a benefit of having a separate /home partition rather than a /home directory inside /. Then the / partition really only needs to be 15-20Gb (or less) as all your personal data is stored elsewhere and the / won't expand as you accumulate more personal data. 

Good luck.

PS: Windows is probably on the first partition, first drive; in Linux language that would be sda1. Only resize Win with the Win software, NOT Gparted. That can make an awful mess. The Win partition should be defragmented a few times before attempting this as it tends to spit info all over the partition (not the case with a Linux EXT* partition).

---

### Post by zesterer on 2012-12-26
is says:

Filesystem     1K-blocks      Used Available Use% Mounted on
/dev/loop0      17596475  17091595    504880  98% /
udev             1966036         4   1966032   1% /dev
tmpfs             790096       864    789232   1% /run
none                5120         0      5120   0% /run/lock
none             1975232       152   1975080   1% /run/shm
none              102400        28    102372   1% /run/user
/dev/sda2      299158524 152657504 146501020  52% /host

@buckyball thanks for the advise, I will try it... :S

---

### Post by zesterer on 2012-12-26
Sorry for the quick reply - 

I use the Windows Ubuntu installer, and had no boot disk. My internet is quite slow, so do I need to use a boot disk for it? Can it be done in windows, or using another linux system that has a smaller disk image?

---

### Post by ibjsb4 on 2012-12-26
> **zesterer said:**
> is says:

/dev/loop0      17596475  17091595    504880  98% /

That says that you are not dual booting, but instead have a wubi install (Ubuntu inside Windows).

I think you need to go to dual boot.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=dual+boot+with+Windows+7&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=dual+boot+with+Windows+7&as_qdr=all&sa=Google+Search&lang=en)

And yes, its 98% full.

---

### Post by Bucky Ball on 2012-12-26
Got it. You have a Wubi install, not a dual-boot; ie. Ubuntu and Windows on separate partitions. 

Wubi is alien to me and can't really help, sorry. Wubi is really intended as a 'try before you buy', or in this case, install, option. Not a permanent solution ...

If you are intending to use Ubuntu for an extended period of time rather then just trying it out, then a dual-boot is the way to go, not Wubi.

---

