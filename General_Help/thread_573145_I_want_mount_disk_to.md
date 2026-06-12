---
title: "I want mount disk to /"
date: 2007-10-11
forum: General Help
---

### Post by Masterj15 on 2007-10-11
I have ubuntu ultimate cd edition. I had an eroor code 18 on my hard drive so I decieded to partition my drive. I have the part with the boot grub on it, 5g.b. The rest was 234 g.b left on my computer. When I started up the computer the error code wasn't their anymore!

Everything was fine intil I saw my 234 g.b in /media/disk. I need that space, its important to me! I only have 2 g.b left to use on my computer without mounting the disk.

Is their anyway to mount the disk to the "/". If not, is their anyway to put the "/" onto the /media/disk so I can have my spaceback?

edit Here are the specs:```
Disk /dev/hda 250.0 G.B, 250059350016 bytes
255 heads,63 sectors/tracks, 30401 cylinders
units=cylinders of 16065*512=8225280 bytes

Device Boot   Start     end      Block      Id      Systems

[COLOR="DarkRed"]/dev/hda1    *               1                     767               6160896                      83                              linux[/COLOR]
[COLOR="DarkSlateGray"]/dev/hda2                 30262               30401            1124550                 5           extended[/COLOR]
[COLOR="Red"]/dev/hda3                   768                 30261           236910555            83                                     linux[/COLOR]
[COLOR="Blue"]/dev/hda5                 30262              30401     1124518+    82                                          linux swap/solaris[/COLOR]

Partition table entries are not in disk order

 
```

In other words, how can I get my file system to the bigger partion without moving the grub install?

---

### Post by vanadium on 2007-10-11
Post the output of 

sudo fdisk -l 

and

mount

here, then we will see what you are talking about and there will be no wild guess work needed on what you mean. I understand that what you really want is to mount a partition of 234 GB into your file system, so you can use it, but I am not sure I understood it well.

---

### Post by Masterj15 on 2007-10-11
> **vanadium said:**
> Post the output of 

sudo fdisk -l 

and

mount

here, then we will see what you are talking about and there will be no wild guess work needed on what you mean. I understand that what you really want is to mount a partition of 234 GB into your file system, so you can use it, but I am not sure I understood it well.

I will do that right now. I just have to write it down. (this is my mothers windows computer)

---

### Post by Masterj15 on 2007-10-11
Ok heres what it says:

```
Disk /dev/hda 250.0 G.B, 250059350016 bytes
255 heads,63 sectors/tracks, 30401 cylinders
units=cylinders of 16065*512=8225280 bytes

Device Boot   Start     end      Block      Id      Systems

[COLOR="DarkRed"]/dev/hda1    *               1                     767               6160896                      83                              linux[/COLOR]
[COLOR="DarkSlateGray"]/dev/hda2                 30262               30401            1124550                 5           extended[/COLOR]
[COLOR="Red"]/dev/hda3                   768                 30261           236910555            83                                     linux[/COLOR]
[COLOR="Blue"]/dev/hda5                 30262              30401     1124518+    82                                          linux swap/solaris[/COLOR]

Partition table entries are not in disk order

 
```

I hope this makes sense!

---

### Post by Masterj15 on 2007-10-11
soory for double post but I need to know how to do this soon before Install homa.

---

### Post by Masterj15 on 2007-10-11
bump (i hate doing this) :(

---

### Post by Masterj15 on 2007-10-11
nevermind. I'm just going to reinstall everything again. I didn't know this was so hard for people. 

Oh well, I learned my lesson with hard questions!

---

### Post by strabes on 2007-10-11
I think the reason no one was able to help you is because you weren't very clear and specific in your original post.

---

### Post by Masterj15 on 2007-10-11
> **strabes said:**
> I think the reason no one was able to help you is because you weren't very clear and specific in your original post.

I gave the specs like the other person said. I didn't really know how to explain it. if you want the specs in the orignal post than here you go.

---

### Post by vanadium on 2007-10-12
One important reason why you did not get an answer yet is that we are not 24 hours a day on this forum! I will look into your issue anyway and post my suggestions (if I can help). If not useful for you, it might help other people.

---

### Post by vanadium on 2007-10-12
I still would need the output of the "mount" command to be sure, but I guess that currently, you are booting with your sda1, which is only 4 GB, and that sd3 is the partition that currently is not accessible. You indeed need to mount sd3 into your file system, for example under /mount, in order to access it. To mount it automatically during startup, the partition will need to be added to /etc/fstab. Since this is not the absolute beginners part of this forum, I am not supposed to post specific instructions here.

In your specific case, where you have such a small /home partition, I strongly recommend you to move your /home directory to that large partition sd3. Typing "ubuntu home separate partition" in google yields

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

among others (the second site is frequently cited on this forum). The first step will be indeed to mount that partition, but all that is included in the steps in the links mentioned, including the inclusion in /etc/fstab.

If you need specific and detailed help during these procedures, post in the Absolute Beginners forum and allow people something more than two hours to help you. Also head the warning of strabes: be careful and as precise as you can in posting your problem.

---

