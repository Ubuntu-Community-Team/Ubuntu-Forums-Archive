---
title: "Xubuntu will not load, drive cache data issue"
date: 2012-12-21
forum: General Help
---

### Post by JoshuaMiller0 on 2012-12-21
Hello.

I have a dualboot of both Xubuntu and Ubuntu (12.04) and when I boot with Xubuntu it simply will not load. After going to the blue xubuntu loading screen it turns into a black screen with white raw text messages and the following error comes up:

```

@[Timestamp] sd 6:0:0:0: [sdb] Asking for cache data failed
[Timestamp] sd 6:0:0:0: [sdb] Asking for cache data failed

``````

[Timestamp + 30 ish] Repeat
[Timestamp + 30 ish] Repeat

```And it keeps looping for ages without achieving anything. I have tried simply booting in recovery mode, but without actually doing anything, it didn't work. I am forced to use Ubuntu at the moment, even though my computer is very old and unable to run it very well.

Edit: Apparentally, this is a very common error which is a bug based around hardware failures?

Anyway I saw that to detect hardware issues you should run: "lsusb", although by the usb, it may only be usb errors?

Anyway this is what I got from running "lsusb" on my Ubuntu 12.04 desktop (I will try it on Xubuntu recovery mode in a bit):

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 008 Device 104: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
josh@JoshuaMiller1997:~$ 

```I tried booting up without my mouse in the computer, lol.

Edit2: I tried the same again but via root in Xubuntu's recovery mode and got the exact same results.

---

### Post by 2F4U on 2012-12-21
It seems as if there are several users with the same problem and there even seems to be a bug report:

[http://askubuntu.com/questions/167343/what-is-a-asking-for-cache-data-failed-warning](http://askubuntu.com/questions/167343/what-is-a-asking-for-cache-data-failed-warning)
[http://askubuntu.com/questions/132100/errors-in-dmesg-test-wp-failed-assume-write-enabled](http://askubuntu.com/questions/132100/errors-in-dmesg-test-wp-failed-assume-write-enabled)

However, since the problems mentioned in these posts are hardware related, only you can tell if you are in the same situation.

---

### Post by JoshuaMiller0 on 2012-12-22
Bump (this really is urgent)

---

### Post by rnerwein on 2012-12-23
> **2F4U said:**
> It seems as if there are several users with the same problem and there even seems to be a bug report:

[http://askubuntu.com/questions/167343/what-is-a-asking-for-cache-data-failed-warning](http://askubuntu.com/questions/167343/what-is-a-asking-for-cache-data-failed-warning)
[http://askubuntu.com/questions/132100/errors-in-dmesg-test-wp-failed-assume-write-enabled](http://askubuntu.com/questions/132100/errors-in-dmesg-test-wp-failed-assume-write-enabled)

However, since the problems mentioned in these posts are hardware related, only you can tell if you are in the same situation.
hi
i red the threads and i can top it !
Dec 23 11:46:25 tschang kernel: [10114.279966] sd 10:0:0:0: [sdc] Test WP failed, assume Write Enabled
Dec 23 11:46:25 tschang kernel: [10114.281970] sd 10:0:0:0: [sdc] Asking for cache data failed

wrote about this a couple of month ago.
but the best joke is: there is [COLOR=Red]no[/COLOR] disk /sdc in my system ;-)
got no problem with my system (12.04 LTS) but the thousends of messages hassle me.
cheers

---

### Post by Pjotr123 on 2012-12-23
Was there a memory stick / memory card in the machine during installation, which is now removed?

---

### Post by rnerwein on 2012-12-24
> **Pjotr123 said:**
> Was there a memory stick / memory card in the machine during installation, which is now removed?
hi
thats possible. where can i look for the lost commemoration of my system (which file) ?
cheers

---

### Post by Pjotr123 on 2012-12-24
Can you post the contents of fstab:
```
leafpad /etc/fstab
```

---

### Post by JoshuaMiller0 on 2013-01-18
> **Pjotr123 said:**
> Was there a memory stick / memory card in the machine during installation, which is now removed?

Yes, there was, however my system worked fine for ages without it... I cannot even remember what memory stick I used to install Xubuntu 12.04, Do I need to to fix the problem.

Bump.

---

### Post by JoshuaMiller0 on 2013-03-04
Bump.

---

### Post by sudodus on 2013-03-04
Have you been living without Xubuntu for months? Or is it working somehow? Please give an updated status report about your system to help us give advice.

- What is your hardware (at least cpu, ram, graphics card/chip, wifi card/chip)

- What is your system (OSs, partitions, ...)?

- What is your main tasks to do with your computer?

- Why do you want Xubuntu (along with Ubuntu)?

(Otherwise my advice would be to reinstall Xubuntu if you still want it along with Ubuntu.)

---

### Post by JoshuaMiller0 on 2013-03-18
> **sudodus said:**
> Have you been living without Xubuntu for months? Or is it working somehow? Please give an updated status report about your system to help us give advice.

- What is your hardware (at least cpu, ram, graphics card/chip, wifi card/chip)

- What is your system (OSs, partitions, ...)?

- What is your main tasks to do with your computer?

- Why do you want Xubuntu (along with Ubuntu)?

(Otherwise my advice would be to reinstall Xubuntu if you still want it along with Ubuntu.)

Sorry, I have not been in touch much.

Update:
[LIST]
[*]I have been living without Xubuntu for months, ocassionally bumping this thread, but very busy with school work which I am able to do on windows.
[*]Processor: Intel Core i5-2410M CPU @ 2.30 GHz 2.30 GHz
[*]Installed memory (RAM): 4.00 GB
[*]Graphics: Intel HD Graphics 3000
[*]Wireless: WAN Miniport (SSTP)
[*]Dual-boot Windows 7 Enterprise without admin and not working Xubuntu 12.04
[*]Main tasks I use are just general usage such as word processing, gaming, surfing the net and managing files
[*]Xubuntu is faster and better for gaming, plus I like the look and style better as it is more like windows which I grew up with.
[/LIST]

---

### Post by sudodus on 2013-03-18
> **JoshuaMiller0 said:**
> Sorry, I have not been in touch much.

Update:
[LIST]
[*]I have been living without Xubuntu for months, ocassionally bumping this thread, but very busy with school work which I am able to do on windows. 
[*]Processor: Intel Core i5-2410M CPU @ 2.30 GHz 2.30 GHz 
[*]Installed memory (RAM): 4.00 GB 
[*]Graphics: Intel HD Graphics 3000 
[*]Wireless: WAN Miniport (SSTP) 
[*]Dual-boot Windows 7 Enterprise without admin and not working Xubuntu 12.04 
[*]Main tasks I use are just general usage such as word processing, gaming, surfing the net and managing files 
[*]Xubuntu is faster and better for gaming, plus I like the look and style better as it is more like windows which I grew up with. 
[/LIST]

You wrote in the opening post, that you have dual boot Ubuntu and Xubuntu (but Xubuntu is no longer working). Now you write that you have dual boot Windows 7 and not working Xubuntu. What about Ubuntu? Did you wipe it?

I would suggest the following paths.

1 - If you still have a working Ubuntu, you can run
```
sudo apt-get install xubuntu-desktop
```
and install the Xubuntu desktop. Choose which desktop environment to run at the log in screen!

2 - If the only working operating system is Windows, and you want to run Xubuntu, do something like this:

- Download the iso file of Xubuntu 12.04.2 LTS with long time support until April 2015. Make an install CD/DVD/USB drive.

- Backup your personal files.

- Make a fresh installation of Xubuntu. It is problably much easier to make a new installation than to find the error in your present system.

At the partitioning screen (during installation), select ***Something else***, and reformat the drive with the old Xubuntu and reuse that drive for the new Xubuntu.

---

### Post by JoshuaMiller0 on 2013-03-18
> **sudodus said:**
> You wrote in the opening post, that you have dual boot Ubuntu and Xubuntu (but Xubuntu is no longer working). Now you write that you have dual boot Windows 7 and not working Xubuntu. What about Ubuntu? Did you wipe it?


My bad, I was confused with my other computer which has boot errors on windows... I have two computers with xubuntu installed that I cannot use... The computer we are talking about in this thread is dual boot Ubuntu and Xubuntu. I wish to access the Xubuntu which has all my important files on it, so installing xubuntu desktop on Ubuntu will not help me. Plus it does not stop the fact that this computer cannot handle Ubuntu and Xubuntu is a good light replacement.

---

### Post by sudodus on 2013-03-19
> **JoshuaMiller0 said:**
> My bad, I was confused with my other computer which has boot errors on windows... I have two computers with xubuntu installed that I cannot use... The computer we are talking about in this thread is dual boot Ubuntu and Xubuntu. I wish to access the Xubuntu which has all my important files on it, so installing xubuntu desktop on Ubuntu will not help me. Plus it does not stop the fact that this computer cannot handle Ubuntu and Xubuntu is a good light replacement.

I see. What happens when you boot Ubuntu and try to access the file system of Xubuntu? Can you mount it? In that case you can also save all your important files (and I think it would be the easiest way).

*** Otherwise you might be able to do it via a live session booted from a Xubuntu install CD/USB drive.***

But if the installed Xubuntu file system won't mount, you might succeed after repairing its file system with e2fsck. Maybe the situation is not too bad. Maybe 'only' a problem with a corrupt file system because of a dirty shut down.

Please post the output of the following commands
```
sudo fdisk -lu
```
```
sudo blkid
```
```
df
```
and I or someone else will suggest what command to run (without knowing more I suggest something like this)

```
sudo umount /dev/sdxy
```
```
sudo e2fsck -f /dev/sdxy
```
where x is the drive letter (probably a) and y is the partition number. x  and y are to be found by the output of those three commands above.

After the e2fsck command you can try to reboot from the internal drive.

---

### Post by JoshuaMiller0 on 2013-03-19
> **sudodus said:**
> I see. What happens when you boot Ubuntu and try to access the file system of Xubuntu? Can you mount it? In that case you can also save all your important files (and I think it would be the easiest way).

*** Otherwise you might be able to do it via a live session booted from a Xubuntu install CD/USB drive.***

But if the installed Xubuntu file system won't mount, you might succeed after repairing its file system with e2fsck. Maybe the situation is not too bad. Maybe 'only' a problem with a corrupt file system because of a dirty shut down.


I cannot access my files on xubuntu via ubuntu. It cannot mount and just appears as locked.

> **sudodus said:**
> 
Please post the output of the following commands
```
sudo fdisk -lu
```
```
sudo blkid
```
```
df
```


I will try this when I get home and reply as soon as possible.

---

### Post by JoshuaMiller0 on 2013-03-23
Bump

---

### Post by sudodus on 2013-03-25
> **JoshuaMiller0 said:**
> I cannot access my files on xubuntu via ubuntu. It cannot mount and just appears as locked.


What can you see from a live session booted from a CD/USB drive?
- The partition table via fdisk, blkid or gparted?
- Any files? (Can you mount your xubuntu file system?)
> 

I will try this when I get home and reply as soon as possible.

Did you try the commands suggested in post #12?

---

### Post by JoshuaMiller0 on 2013-03-25
> **sudodus said:**
> What can you see from a live session booted from a CD/USB drive?
- The partition table via fdisk, blkid or gparted?
- Any files? (Can you mount your xubuntu file system?)

Umm, not entirely sure how to mount the system. Searching the net doesn't help because I do not know what partitions Xubuntu and Ubuntu are on.


> **sudodus said:**
> Did you try the commands suggested in post #12?

Erm, I seem to have forgotten. I do not use this computer very often due to it's slowness, but I might as well have some speed when I do use it...

---

### Post by sudodus on 2013-03-25
> **JoshuaMiller0 said:**
> Umm, not entirely sure how to mount the system. Searching the net doesn't help because I do not know what partitions Xubuntu and Ubuntu are on.




Erm, I seem to have forgotten. I do not use this computer very often due to it's slowness, but I might as well have some speed when I do use it...
Running a live session, you can mount partitions on the other drives (internal and external) using the file browser. Click on the icon of each partition on the left panel, and it will be mounted (if it can be mounted). Then you can browse the files of that partition.

---

