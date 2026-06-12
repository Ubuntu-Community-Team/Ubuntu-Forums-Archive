---
title: "How to prevent hard drive full"
date: 2013-02-21
forum: General Help
---

### Post by AtariBaby on 2013-02-21
Hi there,

A couple of times now I've had to pull my ubuntu machine back from the brink after filling up the internal HDD 100%. I'm using it as media file server and so when it's unable to move files to one of the final destinations, it fills up.

What can I do to reserve a minimum amount of space and prevent this happening again? And what should that minimum space be?

---

### Post by JRV on 2013-02-21
A good guide to how much space should be free is twice the capacity of the largest file.

As for preventing it from filling up again; be observant.

---

### Post by Elfy on 2013-02-21
You could use tune2fs to set a reserved space 

sudo tune2fs -m *n* /dev/sd*xy*

where *n* = % to reserve

and *xy* are the partition you wish to work with

eg sudo tune2fs -m 10 /dev/sda1

would reserve 10% of sda1

---

### Post by strid3r on 2013-02-21
use bleachbit to clear cache and other uselesss stuff, saves Gigabytes on my machine:

```
sudo apt-get install bleachbit
```

---

### Post by Paqman on 2013-02-21
> **AtariBaby said:**
> I'm using it as media file server and so when it's unable to move files to one of the final destinations, it fills up.


Do you mean that when you try to copy to an external share (and the share isn't accessible) it dumps the data onto the local drive instead of the network share?

If you're moving the data via a script then you could add a check to the script to ensure the share is mounted before attempting to write to it.

---

### Post by AtariBaby on 2013-02-21
> **Elfy said:**
> You could use tune2fs to set a reserved space 

sudo tune2fs -m *n* /dev/sd*xy*

where *n* = % to reserve

and *xy* are the partition you wish to work with

eg sudo tune2fs -m 10 /dev/sda1

would reserve 10% of sda1

^this. thank you.

---

### Post by AtariBaby on 2013-02-21
> **strid3r said:**
> use bleachbit to clear cache and other uselesss stuff, saves Gigabytes on my machine:

```
sudo apt-get install bleachbit
```

great tip. thank you.

---

