---
title: "Big problem with GRUB/GPARTED error 22"
date: 2008-04-11
forum: General Help
---

### Post by felipebarroeta on 2008-04-11
First of all I want to send you a warm, kind hello!!!

Well, as my problem is so big and I am a little bit freaked out at the moment, I want to apologize if this topic repeats itself, but no one in the Spanish forum has answered me yet and I thought you would know this better!

Let s see if i make myself clear...


First, I wanted to assign 16GB that appeared as un-assigned. I could not do it. Anyhow, I think i pressed cntrl+z, someone was talking to me i stopped seeing the display and when I turned back, it says that my 150GB of the hard disk was un assign... I freaked out a little and opened my windows folder (very important files here!!!!) and i saw they were there... however I closed gparted and reopened it to see that it still said that my hard drive was un assigned. I said to mysefl i am going to reboot, and as I did the black display before grub remained still and said (error 22 could not finf grub, i think)  (I had a partition of 100GB with XP, a second one 14GB as FAT32, a third 15GB as Ubuntu, and the other 16GB i culdnt assgin i dont know why).

Now I have this big problem because I cannot access my files neither via windows nor ubuntu and I just sont know how to resolve this error 22 of grub...

If anyone knows anything I would be sooo thankful... I got my internships inform there and if i have to format the drives I am going to lose all that work!!!!

Please, if any can give some help I would appreciate it...

Felipe

---

### Post by confused57 on 2008-04-11
Here's a description of grub error 22:
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

Also, you might want to post the output of:
```
sudo fdisk -l
```
-l is a small "L"

Added:  You can use the Ubuntu live cd to post the above.

Another thing to consider is reinstalling grub, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by felipebarroeta on 2008-04-11
First of all, THANK YOU A LOT confused57 for your interest...

Here I post the sudo fdisk -l result

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95f3457a

   Device Boot      Start         End      Blocks   Id  System

I've tried with supergrub but it also does not recognize anything... I just can't believe that there isn't any chance to recovery these files...  i'm so worried because the thing is that i just have no idea...

Well, again thank you very much!!!

---

### Post by confused57 on 2008-04-11
About all I can do is refer you to this link for data recovery:
[http://www.users.bigpond.net.au/hermanzone/p21.html](http://www.users.bigpond.net.au/hermanzone/p21.html)

Sorry, wish I could help your more, but I don't know why "fdisk -l" doesn't show your partitions, nor why Super Grub Disk can't boot your OSes...hopefully you'll find something in the above link that will help you...good luck.

---

### Post by felipebarroeta on 2008-04-11
oh my god...

well, thanks a lot anyway !!!

---

### Post by felipebarroeta on 2008-04-11
confused57, the link you gave me, testlink seems to be working... at least I could recover a lot of files, actually I can see them all, what i still can-t do is to boot form any of the OSes... ill let you know later how it went...

thx again!

---

### Post by felipebarroeta on 2008-04-11
Thank you testdisk worked... I am now writing in windows... most important I got my files back!

Thank you sooo much confused57

---

### Post by confused57 on 2008-04-11
> **felipebarroeta said:**
> Thank you testdisk worked... I am now writing in windows... most important I got my files back!

Thank you sooo much confused57
Nice job recovering your system...I've never used testdisk, so I couldn't give you any advice from personal experience.  Great you were able to get everything working again.

---

### Post by felipebarroeta on 2008-06-09
> **confused57 said:**
> Nice job recovering your system...I've never used testdisk, so I couldn't give you any advice from personal experience.  Great you were able to get everything working again.

Yes... testdisk seems to be a powerful tool.. I have used it a couple of times and it always works... wish all the software worked like linux software does...

Thank you again!!!

---

