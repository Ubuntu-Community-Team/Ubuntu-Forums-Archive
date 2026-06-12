---
title: "chmod directory"
date: 2007-03-11
forum: General Help
---

### Post by drito on 2007-03-11
Hi,
How to change permission for complete directory, which means all subdirectories and files as well with a single type? I have got bunch of photos in complicated directory tree, and I need to change everything to 777.

---

### Post by drito on 2007-03-11
> **drito said:**
> Hi,
How to change permission for complete directory, which means all subdirectories and files as well with a single type? I have got bunch of photos in complicated directory tree, and I need to change everything to 777.

Sorry, I have found: 

```
sudo chmod 777 -R directoryname
```

---

### Post by PriceChild on 2007-03-11
```
chmod ### -R /path/to/dir
```EDIT - probs best not to use sudo if they're your files, just incase.

---

### Post by Andy_D on 2007-03-11
Have you tried this?

chmod -R 777 dirname

It should change the permissions recursively.

---

### Post by Stoodle on 2008-02-15
I'm having a problem. I did sudo chmod -R 777 /media/Seagate\ Drive/

and I got
```

chmod: `/media/Seagate Drive/Recycled': No such file or directory
chmod: `/media/Seagate Drive/Network Share': No such file or directory
chmod: `/media/Seagate Drive/Kenshin': No such file or directory
chmod: `/media/Seagate Drive/Songs I\'ll listen to': No such file or directory
chmod: `/media/Seagate Drive/System Volume Information': No such file or directory
chmod: `/media/Seagate Drive/iPod music': No such file or directory
chmod: `/media/Seagate Drive/Sonic The Hedgehog': No such file or directory
chmod: `/media/Seagate Drive/StepMania CVS': No such file or directory
chmod: `/media/Seagate Drive/$recycle.bin': No such file or directory
tetrix@Gateway:~$ sudo chmod -R 777 /media/Seagate\ Drive/
chmod: `/media/Seagate Drive/Songs/Keyboard Mega Pack': No such file or directory
chmod: `/media/Seagate Drive/Songs/Reach': No such file or directory
chmod: `/media/Seagate Drive/Songs/Reivaj Originals': No such file or directory
chmod: `/media/Seagate Drive/Songs/Skor': No such file or directory
chmod: `/media/Seagate Drive/Songs/XXXPlizit Originals': No such file or directory
chmod: `/media/Seagate Drive/Recycled': No such file or directory
chmod: `/media/Seagate Drive/Network Share': No such file or directory
chmod: `/media/Seagate Drive/Kenshin': No such file or directory
chmod: `/media/Seagate Drive/Songs I\'ll listen to': No such file or directory
chmod: `/media/Seagate Drive/System Volume Information': No such file or directory
chmod: `/media/Seagate Drive/iPod music': No such file or directory
chmod: `/media/Seagate Drive/Sonic The Hedgehog': No such file or directory
chmod: `/media/Seagate Drive/StepMania CVS': No such file or directory
chmod: `/media/Seagate Drive/$recycle.bin': No such file or directory
tetrix@Gateway:~$ sudo chmod -R 777 /media/Seagate\ Drive/
chmod: `/media/Seagate Drive/Recycled': No such file or directory
chmod: `/media/Seagate Drive/Network Share': No such file or directory
chmod: `/media/Seagate Drive/Kenshin': No such file or directory
chmod: `/media/Seagate Drive/Songs I\'ll listen to': No such file or directory
chmod: `/media/Seagate Drive/System Volume Information': No such file or directory
chmod: `/media/Seagate Drive/Sonic The Hedgehog': No such file or directory
chmod: `/media/Seagate Drive/StepMania CVS': No such file or directory
chmod: `/media/Seagate Drive/$recycle.bin': No such file or directory

```

---

