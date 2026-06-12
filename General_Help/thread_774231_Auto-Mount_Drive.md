---
title: "Auto-Mount Drive"
date: 2008-04-29
forum: General Help
---

### Post by Garofoli on 2008-04-29
Hello,
I am dual booting Windows XP and Ubuntu. I have several files on my windows partition that I use for my desktop and music that I need to mount manually. Is there any way to get Ubuntu to automatically mount this drive as my computer turns on? Thanks. :D

---

### Post by duckgoesoink on 2008-04-29
Do you mean you want to automount your Windows partition? If so, you can create an entry for it in your fstab (/etc/fstab). I used the tutorial [here]("http://ubuntuforums.org/showthread.php?t=283131").

---

### Post by Garofoli on 2008-05-01
Heh, This looks like it'll work but it may take a while. It's pretty confusing. :confused: Oh well, Thanks.

---

### Post by Gotit on 2008-05-04
I too have a dual boot machine (2 different drives) and just had to do a fresh install of Hardy and auto-remount my Windows drive.  Maybe this will make it a little easier for you.  

First, open a term session and get a listing of your drives or partitions
```
$ sudo fdisk -l
```
(that's a lower case L not the number 1)
Your XP partition or drive will probably show a system of NTFS.  (If not, and it's FAT 32 don't continue with these instructions as I don't know if they work for FAT 32). It might show a couple drives and partitions, because of swap, boot/grub etc. but you will want the largest one in block size. 

For this example let say it's /dev/sda2

Make a new mount point for XP by 
```
$ sudo mkdir /media/WinXP
```
(I used the name "WinXP" but you can call whatever you want as long as it doesn't already exist in /media)

Go to your "/etc" folder and make a backup of your "fstab" file
```
$ sudo cp -i fstab fstab.bak
```

Open your fstab file for editing
```
$ sudo gedit fstab
```

Enter your new mount point for WinXP
```
# mounting WinXP drive at boot
/dev/sda2	/media/WinXP	ntfs-3g     defaults,locale=en_US.utf8   0    0
```
Reboot and you should see your drive on the desktop.

---

