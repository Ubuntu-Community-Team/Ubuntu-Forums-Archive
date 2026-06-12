---
title: "Nautilus shortcut in the left panel"
date: 2008-05-01
forum: General Help
---

### Post by gwu777 on 2008-05-01
Hi there,

As many I have upgraded to ubuntu 8.04, I have several problems with it.

1) In Nautilus I used to be able to drag a folder on the bottom left pane and it will create a direct link to that place, I know doesn't work, which is a shame as I would like to have a direct link to some important folder on my windows network. It used to work perfectly in 7.10

2)My windows partition (I am on dual boot) used to be mounted automaticaly and I didn't have the mounted icon on the desktop, why is it that now I have to manually mount it everytime I want to use it.

I know these are simple problems, it is just I was used to them in the previous version and I don't understand why it doesn't work as well in 8.04

Thank you for your help

---

### Post by Ziggy72 on 2008-05-01
You may need to give me more info, but try this:
Find out using Gparted or fdisk-l what your partitions are called.

Let's assume that fdisk -l gives a line like this which is one of your ntfs partitions which you want to mount automatically:

> /dev/sda5            7836       20368   100671289+   7  HPFS/NTFS

As root, make the directory /media/sda5. 
As root, edit /etc/fstab and add the following:
```

# /dev/sda5
/dev/sda5	/media/sda5     ntfs    defaults,umask=007,gid=46 0       1

```
Save.

You will now be able to mount this straight away using sudo mount -a in a terminal.

On reboot, provided that your Windows partition shut down normally, the sda5 partition will mount automatically.

Good luck:)

---

### Post by gwu777 on 2008-05-01
I will give the above a try for mounting, but how can I create permanent link/shortcut to folder on the bottom left panel of Nautilus, like My documents and my pictures.

In 7.10 you just dragged a folder down the pane, and it created a direct link, is it only me, I found this so useful! Why doesn't it do it anymore, I would like to understand...

---

### Post by bollix47 on 2008-05-01
Open nautilus.

Navigate to and open the folder you want to appear in the list on the left.

Click on Bookmarks - add bookmark.

---

