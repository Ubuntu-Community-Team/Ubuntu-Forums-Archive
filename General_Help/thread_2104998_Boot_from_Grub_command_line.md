---
title: "Boot from Grub command line"
date: 2013-01-14
forum: General Help
---

### Post by elkingrey on 2013-01-14
My sister has ubuntu on her computer, she's a total noob. She's been running Ubuntu for a year or so. Today, she calls me up and tells me that things have crashed on her and she can't get her computer to work. She wants me to tell you all what her computer says, and maybe get some help. So, here goes: GNU GRUB version 1.99-12ubuntu5.1 minimal BASH-like line editing is supported. For the first word, TAB lists possible command completion. anywhere else TA B lists possible device for file completion. grub >

If she had a second machine I'd have her do this herself, but she doesn't, so I'm doing it. 

I've found several resources on line concerning grub, even directions on how to boot from grub, such as root > kernal > boot sequences and such, but those commands require arguments to go with the commands, and what those arguments are suppose to be, I have no idea. 

Can somebody explain to me why all of a sudden something like this would happen, what the steps are to be taken to get it to boot, and also how to prevent this from happening every time she wants to boot?

Thanks a bunch!

---

### Post by elkingrey on 2013-01-14
So, I found this page which looks really good. So, I started to walk my sister through the directions, but at the very beginning the ls command returned:

error: out of disk

and then returned her to the grub> prompt. I searched for that, and everything I found talked about grub being in rescue mode, hence giving the grub rescue> prompt. This is not what she's getting. She's only getting the grub> prompt.

So, she can't even get the lousy ls command to work, and she's not in rescue mode. What gives?

---

### Post by synapsys on 2013-01-14
The first thing I would look at is disk space. It sounds like the disk is either corrupt or out of space. Boot up a Live CD and check the disk space. If there is plenty of free space, you may need to go about running fsck and repairing grub.

---

### Post by elkingrey on 2013-01-15
She hasn't run out of diskspace because she never puts things on there.

She has a thumb drive but even that will not load because it doesn't even load the bios, so she can load from that.

---

### Post by Herman on 2013-01-15
If you want to try to boot from GNU-GRUB's command line, first you need to find out what partition number contains your Linux kernel or symlinks to the Linux kernel,
```
search -f /vmlinuz
```Then you need to find out what partition number contains /sbin/init, (your root partition),
```
search -f /sbin/init
```Now you have the information you need and you can use it in the following commands to boot with
```
linux  (hd0,1)/vmlinuz root=/dev/sda1
```Where: Your partition containing your kernel is (hd0,1) and your root partition is /dev/sda1, (you need to know that in GRUB numbering HD),1 is the same as /dev/sda1 in Linux numbering).
```
initrd  (hd0,1)/initrd.img
``````
boot
```

---

### Post by Herman on 2013-01-15
Your computer should automatically boot into GRUB's Command Line Interface when there is no /boot/grub/grub.cfg file present, or if GRUB can't find a grub.cfg file. 
When GRUB cannot find its grub.cgf file and presents you with a GRUB prompt instead of a GRUB Menu the chances are high that your Ubuntu installation may have a corrupted file system. If that's the case you won't be able to boot your operating system. You may need to boot a Live CD or USB containing Ubuntu and run a file system check to fix the problem.

Your computer must go through the BIOS before it will boot the hard disk and get to GRUB, but it may be too quick. You may need to be ready and quickly hit the pause key at the right instant to catch it. Then you should be able to get it to boot your CD or USB.

---

