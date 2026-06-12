---
title: "cannot find my partition"
date: 2012-12-23
forum: General Help
---

### Post by okeytheone on 2012-12-23
Hi guys
 
i have got 2 partitions on my laptop hdd, 1 partition has windows 7 on it, and the other has xbmc ubuntu latest eden version.
 
Everything runs fine, but i am tryin to use the rom collection within xbmc.
 
Now the problem i have is that i cannot find my windows 7 partition within xbmc.
 
I am not hot on with linux, 
 
I have read that the drive needs to be automounted, but not sure how to do this
 
I have installed pysdm, but when i log into ubuntu linux screen, i cant find pysdm program
 
hope you can help

---

### Post by vanadium on 2012-12-23
You can list the existing partitions in your system with the command
```

sudo blkid

```
An internal partition is not automounted by default. In order to automount it, you need to add an entry for the partition in the configuration file /etc/fstab

Make sure your Windows partition is "clean" before attempting to mount it in Ubuntu. If that is not the case, have it checked from within MS Windows, then shut down Windows completely (= no hibernation).

---

### Post by grahammechanical on 2012-12-23
What are you looking for? Something called drive C: ? You will not find it because Linux does not use the Microsoft naming convention for drives and partitions.

You might see an icon of a disk drive. It might be labelled 'file system.' You should also be told the size of the file system. That will give you a clue as to what partition you are about to open in the file manager. Opening a partition in the file manager is the same as mounting it.

I am speaking of a standard Ubuntu and not XBMC built upon Ubuntu. So, things might be done slightly differently.

I have a music collection and documents on another partition and the music player and Libreoffice cannot find those music files and documents until I first mount that other partition by opening it in the file manager.

There is a way to automatically mount a partition at boot time but I have never tried it.

Regards.

---

### Post by vanadium on 2012-12-23
> **grahammechanical said:**
> 
There is a way to automatically mount a partition at boot time but I have never tried it.
That is then by adding an entry in /etc/fstab.

---

### Post by GameX2 on 2012-12-23
Automounting a partition graphically is really easy, when you know the easy way - I use " pysdm ", also (Not familiar with fstab, yet).  You have to run it from the terminal:

```
gksudo pysdm
```Enter your password.  You'll see this screen:

[http://img90.imageshack.us/img90/8779/capturedu20121223101643.png](http://img90.imageshack.us/img90/8779/capturedu20121223101643.png)

Next, you'll want to open GParted ( gksudo gparted, in the terminal.  If it's not installed, type sudo apt-get install gparted); this show up:

[http://img853.imageshack.us/img853/4782/capturedu20121223101819.png](http://img853.imageshack.us/img853/4782/capturedu20121223101819.png)

In my case, my Windows 7 partition is SDA2.  So go back to pysdm, and click on SDA2.
You'll probably see a message "/dev/sda2 hasn't been configured.  Do you want to configure it now?"  click Yes.
Next, click on "Mount", then "Assistant:

[http://img189.imageshack.us/img189/8075/capturedu20121223102239.png](http://img189.imageshack.us/img189/8075/capturedu20121223102239.png)

Make sure that "The file system is mounted at boot time" checked.  If so, you can close pysdm and reboot.  That should work.

Hope this help!

---

