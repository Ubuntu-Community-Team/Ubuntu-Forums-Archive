---
title: "Getting grub back after vista"
date: 2006-12-10
forum: General Help
---

### Post by chalewa on 2006-12-10
ok so i installed vista onto my machine...ended up deleting it, but whatever

anyhow, now i can't seem to get grub to load again. i tried to reinstall by going through the ubuntu live cd and several other livecds as well as the command line. 

for some reason it just can't find the root...

i know that the patition still exists because i can see it in gparted. 

any ideas?

---

### Post by meng on 2006-12-10
Have you tried this?
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by chalewa on 2006-12-10
when i type in rescue, it just tells me that it couldn't find the kernel

---

### Post by meng on 2006-12-10
> **chalewa said:**
> when i type in rescue, it just tells me that it couldn't find the kernel
This is with the Alternate CD? Or the Live CD? Because according to the instructions, you only type rescue with the Alternate Cd.

---

### Post by chalewa on 2006-12-10
> **meng said:**
> This is with the Alternate CD? Or the Live CD? Because according to the instructions, you only type rescue with the Alternate Cd.



i guess it is with the live cd, i used the one that they sent me in the mail.

---

### Post by riven0 on 2006-12-10
Are you sure Vista did not somehow corrupt your ubuntu installation. I know it happened to me before when I used to dual-boot xp.

---

### Post by chalewa on 2006-12-10
> **riven0 said:**
> Are you sure Vista did not somehow corrupt your ubuntu installation. I know it happened to me before when I used to dual-boot xp.


no...i am on the ubuntu live disc and can see everything that is on my other partition, including my boot folder that contains on my grub information, i just can't get grub to load that when i start my computer.

---

### Post by meng on 2006-12-10
> **chalewa said:**
> i guess it is with the live cd, i used the one that they sent me in the mail.
Yes that is the Live CD. Read the instructions carefully!

---

### Post by chalewa on 2006-12-10
> **meng said:**
> Yes that is the Live CD. Read the instructions carefully!

yea i guess i didn't realize that there was a difference.

---

### Post by chalewa on 2006-12-10
so now i just get a blinking cursor when i start up...

---

### Post by riven0 on 2006-12-10
> **chalewa said:**
> so now i just get a blinking cursor when i start up...

I don't know, but this is starting to sound suspiciously similar to what happened to me. When I was in xp, I can see my linux partition fine and everything, but trying to boot up would get me nowhere; just a blank screen. I knew grub was correct because I didn't change it in anyway, but it would never boot up. That's when I realized xp did something really bad. ](*,) 

In either case, when you get to the blinking cursor, can you you hit alt+ctrl+F1 and get to the terminal?

---

### Post by meng on 2006-12-10
> **chalewa said:**
> so now i just get a blinking cursor when i start up...
Assuming that I can provide any further help, which is not by any means certain, you'd be best advised to outline what you've actually done in some detail. I've better ways to spend my weekend than engaging in a long exchange of brief messages to try and work out exactly which instructions you followed and how far you got.

---

### Post by chalewa on 2006-12-10
Haha Ok. Thanks for your help thus far. 


Here is essentially what I have done thus far. 

I first started out trying to do the 'install method' as outlined in that wiki...the end result was that the installer crashed.

then i tried to do the terminal method, which appeared to work, no error messages or anything

from the grub prompt i entered 
root (hd0,0)
setup (hd0,0)
quit

and then rebooted.. still no grub

i didn't try to get the terminal from the cursor...but i couldn't really get anything to work, i couldn't even restart without hitting the power button..


so i really don't know at this point why i can't get grub to load

---

### Post by meng on 2006-12-10
What partition is /boot located on? (If you don't have a separate /boot, what partition is / located on?)

---

### Post by chalewa on 2006-12-10
i don't have a /boot partition...

/ is location on hd0,0 or /dev/sda1

---

### Post by bulldog on 2006-12-10
Try this to find out where root is.
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a grub> prompt 
```
find /boot/grub/stage1
```
This will return a location which you have to use in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.

---

### Post by chalewa on 2006-12-10
> 
grub> find /boot/grub/stage1
 (hd0,0)

grub> root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.


that is what i get when i do that...


i have done that before, but to no avail

---

### Post by chalewa on 2006-12-10
still no dice


and i also tried the rescue method from the alternate cd


and i can't get to the terminal through alt+ctrl+f1


is there a way to see if the partition is active through the command line?

---

### Post by bulldog on 2006-12-10
Stupid question maybe.........but have you more than one disk?

---

### Post by riven0 on 2006-12-10
Perhaps it'll be better if chalewa checks the filesystem with fsck? It could done through the liveCD.

---

