---
title: "Started to Shred a disk and stopped it in only a few GB. Possible to access data?"
date: 2014-06-03
forum: General Help
---

### Post by 777funk on 2014-06-03
This started off as a simple thing and ended up with big trouble.

[http://ubuntuforums.org/showthread.php?t=2227500&page=2](http://ubuntuforums.org/showthread.php?t=2227500&page=2)

There's not much that I had on his partition "/dev/sda" 

However thinking back there were a few files. Is there any way to access the data that I didn't touch (later in the disk)?

If it's a difficult thing, not too interested but if it's practical, I'm all for it.

---

### Post by tgalati4 on 2014-06-03
Run a Live USB session and install *testdisk* then run *photorec*.  Make sure you have a disk or large USB stick to receive the data.

Read about data recovery:  [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Don't shred disks that have data that you want to keep.

---

### Post by 777funk on 2014-06-04
Thanks for the link. I just ran ddrescue (and testdisk) and ended up with an image.img file but I can't mount it. When I try, I get this:

Disk .img doesn't contain a valid partition table ddrescue

Any ideas?

Also, I just got this in Parted from a LiveCD:

```
ubuntu@ubuntu:~$ sudo parted '/mnt/image.img' 
GNU Parted 2.3
Using /mnt/image.img
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) unit
Unit?  [compact]? B                                                       
(parted) print                                                            
Error: /mnt/image.img: unrecognised disk label 

```

---

### Post by sudodus on 2014-06-04
ddrescue is good for saving what can be saved from a failing disk (physical disk problems like bad sectors). It does not repair the file system or retrieve data, when the file system is lost. Testdisk can repair the partition table or file system is some cases, but far from always.

Try ***PhotoRec*** as suggested both in this thread and the other one.

[http://www.cgsecurity.org/](http://www.cgsecurity.org/)

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by 777funk on 2014-06-04
Sounds like I'm probably up a creek. Will try it and thanks. I figured I'd go for the low hanging fruit first (Testdisk, ddrescue, etc) and no go there. I'll see if PhotoRec can help. Normally I'd just do over at the very beginning. That may be what I'll end up doing but part of this is for the challenge anyways. There could come a day that priceless data is lost and then I'll need to have a plan.

---

### Post by sudodus on 2014-06-04
That is a good way to think of this rather dull situation

Good luck with PhotoRec :-)

And for the future: The best plan is to set up a good ***backup*** policy and stick to it.

---

### Post by 777funk on 2014-06-04
Thanks a lot for the help! We'll see what happens and you're right on the backup policy. I did have the most important data backed up. In the future I think I'll also keep an image of the OS's since they're also *fairly* important. lol.

EDIT: No joy on saving anything. But I tried!

---

### Post by 777funk on 2014-06-05
Ok... went to testdisk after a little more learning to talk it's language (found a few examples, read the manual, familiarized myself a bit) and I got the few files I needed. I didn't care for what I saw in photorec, it restored a lot of files but without the structure or file names. Once I figured out testdisk, that was great! I think my grub is gone but I will probably just reinstall the Linux OS at this point. Got the little bit of data that's not replaceable off the drive. Thankfully it didn't have much of that on it.

Thanks for the recommendation. Glad to know about testdisk! This was a good learning experience.

---

### Post by sudodus on 2014-06-06
Congratulations for saving the important files :KS

Well, that is how PhotoRec works. The file types (basically the extension) can be restored, but the file name is lost.

I'm glad you figured out how to use ***Testdisk***, so that it could identify the file system well enough, and you could save the important files :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

