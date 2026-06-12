---
title: "[ubuntu] Can not boot into Ubuntu after using caelinux from usb"
date: 2014-10-23
forum: General Help
---

### Post by nat9 on 2014-10-23
Two days ago I booted with my usb into CAElinux using my computer which has  Ubuntu installed on it. Right after restarting my computer I got the  `error: hd0 read error, grub rescue >` message. I installed boot-repair-disc on an usb and booted into it. It did not  give the `recommended repair` option, only the scanning. So I did that.  The url it gave me was: [http://paste.ubuntu.com/8626818](http://paste.ubuntu.com/8626818)

 
Any ideas what went wrong and what can I do? It is a hardware failure  or a software? And if it is a software, what can I do to recover the os  or at least be able to copy files from the hard disc to an external  hard disc?

 
The usb with the caelinux I use regulary on machines with Windows  without problem. This usb has a few live os on it (doudou and quimo for  my kids, caelinux, knoppix, etc). It still works, though now I can not  boot into CAElinux on my computer with this usb (but I can boot into  Knoppix, i.e).


 Any help is appreciated!



I posted this same topic at answers.launchpad.net also (here: [https://answers.launchpad.net/boot-repair/+question/256063](https://answers.launchpad.net/boot-repair/+question/256063)), but since I don`t yet have an answer there, I`m asking here too. I know it`s only a day, but this computer is my working computer and I really have to work, so I need to know whether I can recover the original install, I have to reinstall or buy a new computer.

Any ideas?

---

### Post by 0310aditya on 2014-10-23
If you want to back up your files the best way is to boot from a live ubuntu disc, back up your files to a external device, and reinstall ubuntu! You should be good to go after that. I have a feeling that caelinux screwed up your filesystem and after that it could not read your hdd with ubuntu on it. Hope i helped!

---

### Post by nat9 on 2014-10-23
Thanks, but right now I`m using a live os (knoppix) with my computer and I can`t see the internal disc of my computer, so I can not back up my files.
I don`t think that it will be any different with live ubuntu but I`ll give it a try.

---

### Post by yancek on 2014-10-23
The boot repair output you posted is incomplete.  The only partition on sda on which you might have the operating system is sda1 and that shows as unknown filesystem type which is bad news.  Grub is in the mbr but there is no output at all relating to all the grub files which need to be on your partition with Ubuntu.  Further down, it shows 'unknown bootloader' on sda1 which also looks bad.

If you have an external drive or some medium on which to copy data, I would do that.  Booting the Knoppix medium, create a mount point for sda1, then mount it and see if you can view folders/files and copy them to the external medium.

---

### Post by nat9 on 2014-10-23
I downloaded ubuntu and booted into. I tried to mount the disc with:
```

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /home/ubuntu/mounted/

```
and got the answer:
```

mount: /dev/sda1: can't read superblock

```

Can I try something else before reinstalling ubuntu and losing all my files?

---

### Post by yancek on 2014-10-24
Google 'testdisk' and you should get their site.  Go there and download it and burn it to a CD.  Make sure you read the instructions.  They have a step by step how to available in a link at their page.  The link to it is below, scroll down to Documentation for the step by step.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by nat9 on 2014-10-31
Thank you yancek for your help. I've tried the TestDisk as you suggested, and it was able to detect all my files. Unfortunately I was not able to recover the boot sector thus could not boot my old system. After a long time I realized that I can copy the files with TestDisk, so as cumbersome as it was I copied every file I wanted and then reinstalled ubuntu.
Not exactly the way I wanted but finally I solved the problem. Thanks again!

---

