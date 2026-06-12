---
title: "Can't get into Ubuntu"
date: 2013-06-09
forum: General Help
---

### Post by Jayhawker on 2013-06-09
I have Ubuntu inside Windows by wubi. When starting my computer, I must decide between Windows and Ubuntu. But, all of a sudden, when I choose Ubuntu, the screen gets frozen the moment it shows up the word Ubuntu and some five points under it. They tinckle from white to orange one after the other and finally all five get in orange and nothing more happens.   

Is there any solution without losing data?

Thanks

---

### Post by Impavidus on 2013-06-09
Maybe you can recover your data, it really depends in the extend of the damage in the Ubuntu file system. Begin with telling us your Windows version and your Ubuntu version and make a backup of your root.disk file in Windows.

---

### Post by Jayhawker on 2013-06-09
WIndows Vista, and Ubuntu 12.04. Must the back up be done with WIndows one? 

THank You

---

### Post by The Cog on 2013-06-09
With wubi, all the Ubuntu data is held in a virtual disk on the windows filesystem. So windows backup will back up that file, but it is an image of an unbootable system. 
I would advise that you back it up before you do anything else anyway.

I think the file can be mounted from an Ubuntu live CD so you can copy the data off (maybe to the windows partition for now).
I hope somebody familiar with wubi can tell you where to find the file.

---

### Post by Jayhawker on 2013-06-09
Thanks for your concern. I know where the file is: root.disk. BUt how can I access it from a live CD in an effective way?

Thanks  again

---

### Post by The Cog on 2013-06-09
You have to mount the windows partition first. 

I would probably do it all on the command line, working as root so you get all the access you need. I'm guessing what the windows partition is (sda2) and where the virtual disk is (wubi/root.disk). You will have to adjust accordingly:
```
sudo -i
mkdir /mnt/windows
mkdir /mnt/wubi
mount -t ntfs /dev/sda2 /mnt/windows
mount -o loop /mnt/windows/wubi/root.disk /mnt/wubi
```
So now your linux filesystem is visible in /mnt/wubi. It's probably easiest to remain root to copy the stuff off as you don't then have to worry about the ownership of the files you're reading. You can just run the command nautilus from the command line where you are root, and nautilus will start, with full root access.

---

