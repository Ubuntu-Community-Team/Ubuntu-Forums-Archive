---
title: "Read only hard drive!!"
date: 2007-04-19
forum: General Help
---

### Post by yelserpdog on 2007-04-19
HI there,

I have an external hard drive that I store all my msic and pictures on. When I try to move or save anything onto it in Ubuntu, it keeps saying it's read only. I can't seem to change it. Can anyone help? 
Its a 300 gb western digital. On the permissions tab it says read only. I've tried logging in as root and trying to change it but it keeps saying it's read only.

---

### Post by zeekay on 2007-04-19
Is it formatted in NTFS? If it is, I don't think Ubuntu can write in it. Try changing the file system to a FAT or something.

---

### Post by yelserpdog on 2007-04-19
It is NTFS!!
Oh poo, it's gonna be a right pain as I have 250 gig of music and pics on it!!

ah well, thanks for the info

---

### Post by ghandi69_ on 2007-04-19
There is a program or a "patch" for ubuntu that allows it to write to nfts... its called like ntfs 3g or something like that??  I'm sure if you search a little you would be able to find it.

---

### Post by zeekay on 2007-04-19
Hm, didn't knew that, interesting.

Since I only used NTFS mounting for OS partitions, it wasn't really much of a problem. But indeeed, search on the web and you can find everything you need about Ubuntu and any other Linux distro. Remember: you are not alone!

---

### Post by namityadav on 2007-04-19
As mentioned, use [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/) and you'll be able to read/write to the drive without any problems. I've been using it for quite some time (To manage my videos) and have had not even a single problem.

Do note, however, that if you still access that external drive from Windows, you should use 'Safely remove hardware' to remove the drive instead of just unplugging.

---

### Post by DaSkiDude on 2007-04-23
I installed the ntfs-3g thing.  I can write to my windows partition, however, it will not let me write to my external hdd with all my videos on it.  Any reason for that?

---

### Post by bg1256 on 2007-04-23
sudo ntffs3g --help

---

