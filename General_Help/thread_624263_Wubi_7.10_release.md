---
title: "Wubi 7.10 release"
date: 2007-11-26
forum: General Help
---

### Post by TorontoStorm on 2007-11-26
Any date (approx.) of when Wubi 7.10 will be released as stable (or as stable as Wubi 7.04) is?

---

### Post by ago on 2007-11-26
Not really unfortunately. But feel free to try to the alpha version, that would be the final release if it weren't for an issue with the kernel which in some cases result in a system freeze. For many people the alpha will work as it is though.

---

### Post by linuxblind on 2007-11-26
> **ago said:**
> Not really unfortunately. But feel free to try to the alpha version, that would be the final release if it weren't for an issue with the kernel which in some cases result in a system freeze. For many people the alpha will work as it is though.
And you shouldn't ask such a question to a developer :(

---

### Post by riverstore on 2007-11-27
I get trouble with Wubi 7.10 alpha version. When install with Kubuntu 7.10 (offline install), Wubi download  kubuntu-7.04-desktop-i386. When boot with wubi, it doesn't install kubuntu automatically, When install Kubuntu manually it stop at 88% ( import documents and setting).

Can anyone help me!

---

### Post by ago on 2007-11-27
> **riverstore said:**
> When install with Kubuntu 7.10 (offline install), Wubi download  kubuntu-7.04-desktop-i386.
Wubi 7.10 works only with 7.10 ISOs. To fix the issue about importing documents and settings, before rebooting, edit /ubuntu/install/preseed.cfg and comment out the m-a (migration assistant) section. Also you can press CTRL+Alt+F2 and then run cat /var/log/syslog to have a look at the log.

---

### Post by TorontoStorm on 2007-11-27
> **ago said:**
> Not really unfortunately. But feel free to try to the alpha version, that would be the final release if it weren't for an issue with the kernel which in some cases result in a system freeze. For many people the alpha will work as it is though.

when you say system freeze, will that in any way damage my Windows partition (i install Wubi to its own partition, W: for Wubi, C: for Vista)

---

### Post by riverstore on 2007-11-28
> **ago said:**
> Wubi 7.10 works only with 7.10 ISOs. To fix the issue about importing documents and settings, before rebooting, edit /ubuntu/install/preseed.cfg and comment out the m-a (migration assistant) section. Also you can press CTRL+Alt+F2 and then run cat /var/log/syslog to have a look at the log.
    Thank a lot.I've installed Kubuntu ( I thing so ;) ), and now it boot to Busybox. Please help me!

---

### Post by ago on 2007-11-28
What do you get if you type 
cat /casper.log

---

### Post by riverstore on 2007-11-28
> **ago said:**
> What do you get if you type 
cat /casper.log

I got:
No such file or directory

---

### Post by ago on 2007-11-28
Then you have to modify /ubuntu/disks/boot/grub/menu.lst

find the first line that starts with kernel, remove "quiet splash" and add "debug=2"

now you should have a more verbose boot and a log in /tmp or /var/log/syslog

---

### Post by riverstore on 2007-11-28
Now I got some error messeg:
- /host/ubuntu/disks/root.disk doesn't exist (same to other virtual disk). 
I think it's a terrible error.

---

### Post by ago on 2007-11-28
Do you have /ubuntu/disks/root.disk?

Also try to run chkdsk /r from windows on the drive where you have installed wubi

---

### Post by riverstore on 2007-11-28
PS: I found that these virtual disks are exist!

---

### Post by ago on 2007-11-28
run chkdsk anyway, then try to look for them from the busybox shell (should be under /host/ubuntu/disks)

---

### Post by riverstore on 2007-11-28
I'd installed Wubi on driver D (FAT32), all virtual disks are exist. (D:\ubuntu\disks\...).
I'd googled for a month, now I don't know what to do.
Thank for your help!

---

### Post by ago on 2007-11-28
did you run D: & chkdsk /r?
Then at busybox type 

ls  /host/ubuntu/disks

---

### Post by riverstore on 2007-11-28
I'd run chkdsk /r D: and it report no problem
I found that wubi can't mount drive D, I manually mount D (mount -r -t vfat /dev/sda2 /media) it report: "No such device."
I think that I should forget wubi

---

### Post by abn91c on 2007-11-28
Wubi 7.10 is included in the live 7.10 cd

---

### Post by ago on 2007-11-29
That is a limited-features version. We were supposed to be in the CD with the full monty, but the kernel was hostile (and still is)...

---

### Post by ago on 2007-11-29
> **riverstore said:**
> I'd run chkdsk /r D: and it report no problem
I found that wubi can't mount drive D, I manually mount D (mount -r -t vfat /dev/sda2 /media) it report: "No such device."
I think that I should forget wubi

Make sure that /media folder exists and look into 

cat /proc/partitions to see what devices are available.

---

### Post by riverstore on 2007-11-29
I manually make /media (mkdir /media)
I found that my devices are sda1, sda2 ( boot with LiveCD) and I sure that /dev/sda1 and /dev/sda2 are exist. 
People say that Linux is difficult to learn, but I don't think it too trouble

---

### Post by 135798642 on 2007-11-29
> **riverstore said:**
> I manually make /media (mkdir /media)
I found that my devices are sda1, sda2 ( boot with LiveCD) and I sure that /dev/sda1 and /dev/sda2 are exist. 
People say that Linux is difficult to learn, but I don't think it too trouble

yeah , not too hard to use linux ... but ... with wubi  ... :(

---

### Post by riverstore on 2007-11-29
Thank ago, I'd learn lots of Linux knowledge from you.

---

### Post by ago on 2007-11-30
Are you sure the dives are the right one?
Try to mount each of them and use -v to have more verbose output

---

### Post by riverstore on 2007-12-02
> **ago said:**
> Are you sure the dives are the right one?
Try to mount each of them and use -v to have more verbose output
  I sure the dives are the right one,  I know some about Linux. 
          Have You ever test Wubi 7.10 with Kubuntu. Someone said they successful in install wubi 7.10 with ubuntu. 
        The computer doesn't belong to me ( it belong to my school) so I don't want to install direct Kubuntu to hard drive

---

### Post by riverstore on 2007-12-02
I can't forget Wubi, by fresh install I find out this error:
       [I]Warning: Unrecognized partition table for drive 81. Please rebuild it using a Microsoft- compatible Fdisk tool (err=24) current C/H/S= 62/255/63.
        Warning: Unrecognized partition table for drive 82. Please rebuild it using a Microsoft- compatible Fdisk tool (err=24) current C/H/S= 500/16/32
[/I]

---

### Post by ago on 2007-12-03
> **riverstore said:**
> I can't forget Wubi, by fresh install I find out this error:
       [I]Warning: Unrecognized partition table for drive 81. Please rebuild it using a Microsoft- compatible Fdisk tool (err=24) current C/H/S= 62/255/63.
        Warning: Unrecognized partition table for drive 82. Please rebuild it using a Microsoft- compatible Fdisk tool (err=24) current C/H/S= 500/16/32
[/I]


Well that's there reason why we can't mount.

---

### Post by riverstore on 2007-12-03
> **ago said:**
> Well that's there reason why we can't mount.
Can You help me solve that problem.

---

