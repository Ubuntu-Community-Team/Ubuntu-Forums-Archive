---
title: "How To Remove A File In Root Directory - Without Destroying Anything"
date: 2017-12-12
forum: General Help
---

### Post by DeadlyOats on 2017-12-12
I did this:

```
username@machinename:~$ sudo [COLOR="#FF0000"]rm[/COLOR] /usr/share/wallpapers/Haircolor_by_Dale_Trombley.jpg
[sudo] password for username: 
rm: cannot remove '/usr/share/wallpapers/Haircolor_by_Dale_Trombley.jpg': Read-only file system
username@machinename:~$ sudo [COLOR="#FF0000"]rm -f[/COLOR] /usr/share/wallpapers/Haircolor_by_Dale_Trombley.jpg
rm: cannot remove '/usr/share/wallpapers/Haircolor_by_Dale_Trombley.jpg': Read-only file system

```

As you can see, I failed in both attempts.  Since this is in the Root directory, I don't want to do more on my own without understanding why this failed, even though I used sudo.

Why do I want to remove that jpg file?  Because I have a slide show of wallpapers showing on my desk top, and every time that one comes up, it annoys me.  I don't like that image, and I don't want it showing up.  I want it permanently gone.

How do I get past the whatever is stopping me from removing that file, without breaking my install?

Thank you.

---

### Post by Frogs Hair on 2017-12-12
Try usr/share/backgrounds.

---

### Post by deadflowr on 2017-12-12
You need to remount the file system
It's mounted as read-only.
How are you running the system?

---

### Post by yancek on 2017-12-12
If this is actually an 'installed' system, the primary reason for it changing to read-only is problems with the filesystem and you would need to do a filesystem check if a simple remount rw fails.

---

### Post by Holger_Gehrke on 2017-12-12
If this is a normally installed Ubuntu, than a read-only root file system is a sign that something went wrong with that file system; you probably have a line in the file '/etc/fstab' that says something like 
```
UUID=<a long string of numbers and letters>  /  ext4  **errors=remount-ro**  0  1
```
Check the output of dmesg or journalctl for errors that have anything to do with your hard disk.
You should boot a live CD / DVD / USB-stick and thoroughly check the partition.

Holger

---

### Post by QIII on 2017-12-12
> **deadflowr said:**
> 
How are you running the system?

Before speculating on uncommon circumstaces, this is an important question to have answered.  This is the key to the result of the application of Ockham's Razor.

---

