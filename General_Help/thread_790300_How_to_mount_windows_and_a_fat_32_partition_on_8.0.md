---
title: "How to mount windows and a fat 32 partition on 8.04"
date: 2008-05-11
forum: General Help
---

### Post by fasoulas on 2008-05-11
How can i mount my windows ntfs partition and another fat32 partition that i have all my media from boot in ubuntu 8.04?

I found a tutorial from psychocats website about mounting but it seems to be for older versions 

can anyone please help

---

### Post by metiosarius on 2008-05-11
> **fasoulas said:**
> How can i mount my windows ntfs partition and another fat32 partition that i have all my media from boot in ubuntu 8.04?

I found a tutorial from psychocats website about mounting but it seems to be for older versions 

can anyone please help

Did you try to go to "Places > Computer" and see if it was listed?

---

### Post by fasoulas on 2008-05-11
> **metiosarius said:**
> Did you try to go to "Places > Computer" and see if it was listed?

It is listed but i want them to be mounted from boot and their icons on the desk top

---

### Post by metiosarius on 2008-05-11
> **fasoulas said:**
> It is listed but i want them to be mounted from boot and their icons on the desk top

You need to edit **/etc/fstab** to add them permanently. Just Google for tutorials on how to set it up.

---

### Post by TeoBigusGeekus on 2008-05-11
For the ntfs partition, you should install ntfs-config
```
sudo apt-get install ntfs-config
```
then go to applications->system tools->ntfs configuration, select the volume and check all the boxes.

For the fat32, you need to edit your /etc/fstab file. Do a
```
sudo fdisk -l
```
to see the name of the volume, lets say it is /dev/sdb1.
Then find its mount point by 
```
ls /media
```
lets say it is /media/disk.

Then you should 
```
gksudo gedit /etc/fstab
```
and add this line 
```
/dev/sdb1     /media/disk     vfat     relatime     0     2
```

The last 2 instead of 0 will force the system to check the volume every now and then for errors upon boot up.

If Ubuntu gives you any cr@p about not being able to write to the fat32 volume, you can change its owner by 
```
sudo chown -R yourusername /media/disk
```

PS: Love your avatar!

---

### Post by fasoulas on 2008-05-11
> **TeoBigusGeekus said:**
> For the ntfs partition, you should install ntfs-config
```
sudo apt-get install ntfs-config
```
then go to applications->system tools->ntfs configuration, select the volume and check all the boxes.

For the fat32, you need to edit your /etc/fstab file. Do a
```
sudo fdisk -l
```
to see the name of the volume, lets say it is /dev/sdb1.
Then find its mount point by 
```
ls /media
```
lets say it is /media/disk.

Then you should 
```
gksudo gedit /etc/fstab
```
and add this line 
```
/dev/sdb1     /media/disk     vfat     relatime     0     2
```

The last 2 instead of 0 will force the system to check the volume every now and then for errors upon boot up.

If Ubuntu gives you any cr@p about not being able to write to the fat32 volume, you can change its owner by 
```
sudo chown -R yourusername /media/disk
```

PS: Love your avatar!

Euxaristo file apo tin Ellada tha to dokimaso 

P.S. > To gaiduraki ine kipriako

---

### Post by metiosarius on 2008-05-11
> **fasoulas said:**
> Euxaristo file apo tin Ellada tha to dokimaso 

P.S. > To gaiduraki ine kipriako

English, please?

---

### Post by TeoBigusGeekus on 2008-05-11
> **metiosarius said:**
> English, please?
Translation:
Thanks my greek friend, I will try it.
PS: The donkey is from Cyprus.

:lolflag:  :lolflag:  :lolflag:

---

### Post by metiosarius on 2008-05-11
> **TeoBigusGeekus said:**
> Translation:
Thanks my greek friend, I will try it.
PS: The donkey is from Cyprus.

:lolflag:  :lolflag:  :lolflag:

Ahh...I see :)

---

### Post by Dutar on 2008-06-16
Sorry for hijacking this thread. I followed the TeoBigusGeekus's procedure to mount my FAT 32 file system, but it doesn't mount automatically. when I mount it manually by
sudo mount /dev/sda6 /media/Win-D
it works but it is read only! How can I mount this on boot with read write options?

---

### Post by Victormd on 2008-06-16
Try the link on my signature...

---

### Post by Mark Bowers on 2008-06-24
Dutar:

Were you able to resolve your problem? I've just moved to Hardy Heron from Gutsy, and now have the same problem. I've tried modifying FSTAB to mount my local fat32 partition. It will auto-mount, but not with write permission, and trying the CHOWN routine suggested earlier in this post does not fix it -- I just get a long series of error messages.

If I mount the partition manually everything is fine - I'd just like it to mount automatically when I boot.

Thanks in advance. Mark B

---

### Post by Mark Bowers on 2008-06-25
OK - a dumb question perhaps. Why can't I just mount the fat32 drive manually, then check the MTAB file and copy the bottom entry for the drive just mounted into the FSTAB file? I haven't tried it yet for fear of corrupting something, but it looks to me like it should work?

M. Bowers

---

### Post by bill5555 on 2008-07-14
Fasoulas, did metiosarius solve your problem mounting a fat 32 partition?
I had the exact same problem.  I followed metiosarius' advice and eventually succeeded.  I had one problem...Using Kubuntu 8.04 and KDE I could not save the edited /etc/fstab file.  In order to  save the file I had to go to terminal and enter kdesu Kate where Kate is the name of the application I used to edit /etc/fstab. After I did this, /etc/fstab saved properly.  I shut down, rebooted and found to my great joy and satisfaction that my windows fat32 position was now mounted and accessible.   If you are using Gnome, not KDE you may have to go to Gnome help and find out how to use an editor as superuser. I think you could use Alt-F2 to go to terminal and enter gksu "name of application you will use to edit /etc/fstab".
I am a newbie and not too skillful, but if you still have a problem, e-mail me and I will try!
Bill

---

### Post by bill5555 on 2008-07-14
Fasoulas, did metiosarius solve your problem mounting a fat 32 partition?
I had the exact same problem.  I followed metiosarius' advice and eventually succeeded.  I had one problem...Using Kubuntu 8.04 and KDE I could not save the edited /etc/fstab file.  In order to  save the file I had to go to terminal and enter kdesu Kate where Kate is the name of the application I used to edit /etc/fstab. After I did this, /etc/fstab saved properly.  I shut down, rebooted and found to my great joy and satisfaction that my windows fat32 partition was now mounted and accessible.   If you are using Gnome, not KDE you may have to go to Gnome help and find out how to use an editor as superuser. I think you could use Alt-F2 to go to terminal and enter gksu "name of application you will use to edit /etc/fstab".
I am a newbie and not too skillful, but if you still have a problem, e-mail me and I will try!
Bill

---

