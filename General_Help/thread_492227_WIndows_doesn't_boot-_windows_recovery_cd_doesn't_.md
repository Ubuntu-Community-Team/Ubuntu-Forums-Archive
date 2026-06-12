---
title: "WIndows doesn't boot- windows recovery cd doesn't help"
date: 2007-07-04
forum: General Help
---

### Post by sphim on 2007-07-04
i'm running feisty and windows on a dual boot running off of one hard drive
windows is on the first partition, and the ubuntu partitions follow.

ubuntu itself is currently working ok

windows worked ok until I tried installing openSUSE over my ubuntu install, just to try something new
grub still had windows listed, but it gave an error message when i tried to boot into windows for some reason, so i went back to ubuntu
upon reinstalling ubuntu, windows is on the grub list, but it still gives this error message: 

```
Windows could not start because of a computer disk hardware configuration problem.
Could not read from the selected boot disk. Check boot path and disk hardware.
Please check the Windows documentation about hardware disk configuration and your hardware referenece manuals for additional information.
```

i tried the windows cd in recovery mode, and it is unable to do anything
in recovery mode, microsoft's recommends using 'bootcfg /rebuild' as a fix, but it gave an error message saying that there was a hardware problem
when i type "dir" it just says the same thing, a hardware problem

here is my windows boot.ini (i don't know if its that important, but microsoft said it was)

```
[boot loader]

timeout=30

default=signature(d53dbf81)disk(1)rdisk(0)partition(1)\WINDOWS

[operating systems]

signature(d53dbf81)disk(1)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect

```

i'm not sure if the ntfs file system is corrupt, but i can still get at all  the files in ubuntu
usually ubuntu complains about a corrupt file system before windows does

since ubuntu is on the same hd, i don't think its a hardware problem

i'm wondering if there is a good filesystem integrety utility for ntfs to see if thats the problem, or if its something completely different

thanks in advance

---

### Post by louieb on 2007-07-04
Your probably looking at coping your data off and reinstalling XP. But first try.   
[SystemRescueCd]("http://www.sysresccd.org/Main_Page") or [Trinity Rescue Kit | CPR for your computer]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12")

---

