---
title: "Problems with SMB shairing premissions!"
date: 2014-12-24
forum: General Help
---

### Post by Hans_Eirik on 2014-12-24
Hi! I just bought an Asus Chromebox, and after installing Ubuntu 14.04 LTS, I finally got rid of some HDMI related bugs. My plan is to run XBMC/Kodi on this device. I got a big external hard drive that I store all my contents on (exfat formatted), and I want to access this device from my mac through samba sharing. When I manually mount the hard drive in KDE desktop, the mount point is located at /media/<user> . 
When the disk is mounted at this directory, I can read and write files to the hard drive, from my mac, through SMB. My problem is that I want this hard drive to automatically mount at boot or when plugged in, and I want to be able to read and write to the hard drive through SMB. The only way I've been able to do this is if I manually mount the drive in the /media/<user> directory, but I can't get it to automatically mount to this point! I've tried the command "sudo mount -a" but nothing happens.

I can get auto mounting working by edit the settings in the disks-app, but then I'm only able to read the disk, not write to it.

How can I fix this? How can I automatically mount my hard drive, and still get the same permissions as I get when I manually mount it in KDE GUI?

---

### Post by Holger_Gehrke on 2014-12-24
Don't use (any kind of) FAT. This filesystem can't store ownership and  permissions. When mounted automatically at boot time, a disk gets owned  by root, and noone else can write to it. If you format the disk with one  of the ext filesystems, you can make a directory owned by a specific  user with write, read and execute permission given to the user and his  group (in the shell: sudo mkdir  /media/<user>/<diskname>/files; sudo chown  <user>:<group>  /media/<user>/<diskname>/files;sudo chmod ug+rwx  /media/<user>/<diskname>/files). Then it doesn't matter that  the disk is owned by root, because you can write to this directory.

---

### Post by Hans_Eirik on 2014-12-24
I actually figured it out! I can't use NTFS, because my mac can only read, and not write to a NTFS formatted drive.
in the /etc/samba/smb.conf I needed to add the line **force user = root **to the external hard drive

---

