---
title: "Reformatting external hard drive"
date: 2007-06-10
forum: General Help
---

### Post by ZeldaFan on 2007-06-10
I bought a MyBook 160 gb external hard drive which was formatted in the fat32 format. Is there anyway, I can reformat it so that I could still write to it from my ubuntu system. The problem is that with the fat32, the file size limit often hinders me from larger files on it, so I wanted to reformat it another format so I can files of large sizes. Which format would best allow me to do, can I even do that in the first place, and how would I do so? By the way, it connects to my computer through a USB port

---

### Post by logos34 on 2007-06-10
why not ext3?  If you're dual booting windows and need r+w access to it, get fs-driver, or else format it NTFS and use ntfs-3g driver to add write capability from linux

sudo apt-get install ntfs-3g ntfs-config

---

### Post by nqsonk9 on 2007-06-10
Yeah, ntfs-3g is the right choice for you. Remember to change /etc/fstab as follow:

> ntfs --> ntfs-3g
nls=utf8 --> locale=en_US.utf8

for each partition you wish to make writable with Ubuntu

---

### Post by logos34 on 2007-06-10
Actually, the ntfs-config gui will edit fstab for you automatically.  And when you disable write support, it restores the settings to read-only. Also, it might be a good idea to get **ntfsprogs** utilities also, in the highly unlikely event you need to run 'ntfsfix' to correct any errors on the ntfs partitions.  (I had to use it once months ago to check for what appeared to be some data corruption.  Fixed whatever it was in a jiffy and never a problem since).

---

### Post by ZeldaFan on 2007-06-10
So how do I format the ext. HD to ntfs then. Is there any application in Ubuntu? Do I use gParted? Sorry I am new to this.

---

### Post by logos34 on 2007-06-10
> **ZeldaFan said:**
> So how do I format the ext. HD to ntfs then. Is there any application in Ubuntu? Do I use gParted? Sorry I am new to this.

Use 
sudo gparted

Opens up the Gnome partition manager.  If you don't have it:
sudo apt-get install gparted

Unmount the external hdd first before formatting it.  Go to system>prefs>removable drives and storage.  On the first tab, make sure the 'mount removable drives and media' boxes are unticked (usb drives sometimes want to keep trying to mount).   Then format.

---

