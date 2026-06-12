---
title: "Big problem with Root Partition"
date: 2007-06-02
forum: General Help
---

### Post by Uuranor on 2007-06-02
Hi.
Today I made an upgrade of my feisty and I discovered /dev/sda3 (the root partition) is full. It is an ext3 partition of 10 GB, so it can't be possible the space is left, 'cause /home is mounted elsewhere. 
But ... gnome-system-monitor recognize it as a partition of 2.7 GB, and gparted of 10.0 GB ... so, what can I do to restore my partition?

---

### Post by Herman on 2007-06-02
Hello Uuranor,
You could try running 'sudo resize2fs /dev/sda3' from a live cd. ```
sudo resize2fs /dev/sda3
```
If you have [GParted -- LiveCD]("http://gparted.sourceforge.net/") you could just boot that up and then right-click on the partition and click 'check', that will do it too.
Regards, Herman :D

---

### Post by Uuranor on 2007-06-02
> **Herman said:**
> Hello Uuranor,
You could try running 'sudo resize2fs /dev/sda3' from a live cd. ```
sudo resize2fs /dev/sda3
```
If you have [GParted -- LiveCD]("http://gparted.sourceforge.net/") you could just boot that up and then right-click on the partition and click 'check', that will do it too.
Regards, Herman :D

Thanks a lot, resize2fs works!
You saved me :D

---

### Post by Herman on 2007-06-02
Okay, thanks for the good feedback, glad I could help,
Regards, Herman :D

---

### Post by NorthernSuze on 2007-07-26
Thank-you for pointing the way to GParted's LiveCD. It nicely solved my too small root partition dilemma. 

I also want to thank you (and all the rest of you great people) for your willingness to bail so many of us out of the mud-puddles we find ourselves in!! I know I would be lost without the helping hands on this fantastic forum.  You are making my transition to a new OS possible.
Suzanne:KS

---

### Post by LaRoza on 2007-07-26
> **NorthernSuze said:**
> Thank-you for pointing the way to GParted's LiveCD. It nicely solved my too small root partition dilemma. 

I also want to thank you (and all the rest of you great people) for your willingness to bail so many of us out of the mud-puddles we find ourselves in!! I know I would be lost without the helping hands on this fantastic forum.  You are making my transition to a new OS possible.
Suzanne:KS

Soon you will be offering advice and the beginners will look up to you :D. Have fun!

---

