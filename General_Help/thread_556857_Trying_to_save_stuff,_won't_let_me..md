---
title: "Trying to save stuff, won't let me."
date: 2007-09-21
forum: General Help
---

### Post by PLmatt91 on 2007-09-21
First off, I kinda searched, but didn't know what else to type since I didn't see my answer or question any where.

I want to save a torrent file to the folder that I set up in Windows.  I am using Wine and uTorrent for my torrents.  So when I save the torrent file to the folder, I don't see it any where, even if I go to places -> Computer -> And then the partition I want and through the folders.

Can any one help me out? Do I need to enable something or add something through terminal? I'm new to Ubuntu kinda, so I'm just wondering.  Thanks for help,

-Matt.

---

### Post by Buffalo Soldier on 2007-09-21
Which version of Ubuntu are you using? The latest release is 7.04 (Feisty Fawn). If this is the case, then during installation it should have detected the existing partitions on your harddisk and mounted them approriately. 

Another thing, by default Ubuntu does not support writing (saving) to NTFS partition. Hopefully this [guide]("https://help.ubuntu.com/community/MountingWindowsPartitions") will give you a head start.

What's the output from these two command when run in the terminal (command line)?

```
sudo fdisk -l
```

```
cat /etc/fstab
```

---

### Post by bendystraw on 2007-09-21
you can get Utorrent and Azures off the Synaptic Packet Manager and it will set everything up for you (i think thats how u spell it) 

Only use wine if it is a must, might i suggest if you want to download music look for FrostWire

---

### Post by Maestro23 on 2007-09-21
Read & Write to an NTFS partiton:  Install ntfs-3g from the Repositories:

> sudo apt-get ntfs-3g

sudo apt-get ntfs-config

ntfs-3g website: [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

---

### Post by PLmatt91 on 2007-09-21
Yes, I'm using Ubuntu 7.04.  

I did what Buffalo soldier told me to do, but it still won't write to that drive. Or that location for that fact.  So I don't know..

---

### Post by PLmatt91 on 2007-09-22
Any more help guys?

---

### Post by Buffalo Soldier on 2007-09-27
> **PLmatt91 said:**
> Any more help guys?

No one can give further assistance until you've given the neccessary output from these two commands:
```
sudo fdisk -l
```

```
cat /etc/fstab
```

Or you could go straight to [Mounting Windows Partitions guide]("https://help.ubuntu.com/community/MountingWindowsPartitions").

---

