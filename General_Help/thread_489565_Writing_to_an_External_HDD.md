---
title: "Writing to an External HDD"
date: 2007-07-01
forum: General Help
---

### Post by wingdom on 2007-07-01
I'm using a Ubuntu Live cd to copy data off a computer that wont boot. I am trying to copy it off onto a USB external hard drive. When I try it gives a message that says I dont have permission to write to the folder. How do I go about getting permission to write to the external hard drive? It is formatted in NTFS.

---

### Post by CocoAUS on 2007-07-01
Install ntfs-config on the livecd (don't worry, it won't affect your hard drive at all).  Run the program and enable ntfs support.  Then, you might have to change permissions on drive.  To do this, try changing the ownership of the folder that the drive is mounted in.  If the drive is mounted in /media/sdb1, you would use

```
sudo chown -R usernamehere /media/sdb1
```

I think the livecd user is simply called Ubuntu (you can check by opening up a terminal and seeing what name it gives you).

---

### Post by wingdom on 2007-07-01
It says to use NTFS Config, I need to install NTFS 3G, I go to do that, run ./configure for NTFS 3G, and it says "checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details" then stops. What now?

---

### Post by CocoAUS on 2007-07-01
Installing ntfs-config from the repositories also installs ntfs-3g.  Make sure the Universe repository is enabled, then do:

```
sudo aptitude update && sudo aptitude install ntfs-config
```

To run the program:

```
ntfs-config
```

You shouldn't have to compile a single thing.

By the way, Googling "ntfs feisty" returns [this]("http://onlyubuntu.blogspot.com/2007/03/widows-ntfs-partitions-readwrite.html"), along with many other guides.

---

### Post by wingdom on 2007-07-01
I got it. Instead of downloading and configuring it my self, I used the tutorial found [here]("http://ubuntuforums.org/showthread.php?t=217009")  Thanks alot for your help

---

