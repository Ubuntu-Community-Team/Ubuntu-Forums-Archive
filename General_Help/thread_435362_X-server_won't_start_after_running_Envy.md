---
title: "X-server won't start after running Envy"
date: 2007-05-06
forum: General Help
---

### Post by galleonway on 2007-05-06
After running Envy KDE won't start.  I tried TS Eliot's guide for reconfiguring XORG but it didn't work.  I installed  Ubuntu into another partition on the hard drive.  If I could mount the older Linux partition maybe I can access the files I want.

Can someone please tell me how to mount the older partition from Ubuntu/gnome?  I really need those files!

Bryan

---

### Post by hanzomon4 on 2007-05-06
Try reinstalling the drivers...

---

### Post by Nythain on 2007-05-06
first, make a place to mount the old partition at... in terminal
sudo mkdir /backup
then find out the /dev/ of the partition
sudo fdisk -l
then mount that partition
sudo mount /dev/whatever /backup

that should do the trick
to permanently mount it, edit your /etc/fstab kinda like this
/dev/whatever    /backup     ext3    defaults    0      2

---

### Post by galleonway on 2007-05-06
> **hanzomon4 said:**
> Try reinstalling the drivers...

Could you please give the apt command for installing those drivers?

Thanks for your assistance.

---

### Post by hanzomon4 on 2007-05-07
Im not sure how envy does it but usually ```
sudo apt-get install nvidia-glx linux-restricted-modules-generic(or whatever kernel you're running)
``` should do it. You can also install the drivers from the nvidia site but it's best to use the repo versions. Also depending on your card you may need nvidia-glx-legacy or nvidia-glx-new instead of nvidia-glx. If you need a gui to fix your drivers just ```
sudo nano /etc/X11/xorg.conf
``` and change the driver in the 'Device' section to vesa. Then ```
sudo /etc/init.d/gdm restart
```

---

### Post by galleonway on 2007-05-07
> **Nythain said:**
> first, make a place to mount the old partition at... in terminal
sudo mkdir /backup
then find out the /dev/ of the partition
sudo fdisk -l
then mount that partition
sudo mount /dev/whatever /backup

that should do the trick
to permanently mount it, edit your /etc/fstab kinda like this
/dev/whatever    /backup     ext3    defaults    0      2

 sudo mount /dev/hda3 /home/bryan/Desktop/backup
mount: you must specify the filesystem type
bryan@metoo-desktop:~$ 

How do I specify the file system?

---

### Post by Nythain on 2007-05-07
what filesystem is it using, try sudo mount -t ext3 /device /whereever
thats taken from the mount man page

---

### Post by galleonway on 2007-05-07
> **Nythain said:**
> what filesystem is it using, try sudo mount -t ext3 /device /whereever
thats taken from the mount man page

It worked! Thank you so much for the help. What a great group of people in these forums!

Where would I find the manual you referred to?

---

### Post by Nythain on 2007-05-07
in terminal type i think its
man 8 mount
or just
man mount
man files are a collection of manual files for easy browsing in command line... you can also find copies of man files posted sporadically on the web, as for where they are actually stored in linux, im not sure

---

### Post by galleonway on 2007-05-07
Thanks again. You saved me a lot of hassle.

---

