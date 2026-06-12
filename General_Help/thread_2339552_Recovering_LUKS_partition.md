---
title: "Recovering LUKS partition"
date: 2016-10-10
forum: General Help
---

### Post by lucassith on 2016-10-10
Hello everyone.I have very tough problem to solve. I wanted to try new windows on my external HDD and after installing such my internal SSHD with LUKS got overwritten by 512 megabytes of "System reserved"  NTFS partition. Of course Windows didn't even ask me to do such thing, it just happened suddenly without me noticing it. Could you please help me recover my partition? It contains very important files.

---

### Post by oldfred on 2016-10-10
I do not know LUKS.

Windows does not work from external drives. It is licensed for one internal system only.
Windows always installs a boot partition to the drive set as boot in BIOS. That usually is sda. And why most suggest always installing Windows to sda, or removing other drives when installing it.

Do you have the standard size /boot partition that Ubuntu creates. That is smaller the 512MB that Windows just used. If you manually installed and created a 512MB /boot, then it probably would be possible to restore the /boot partition, but if into LUKS it is a much larger issue, which then I do not know about.

---

### Post by lucassith on 2016-10-10
Basically I wanted to install  Windows from an USB stick. I was able to install it on "/dev/sda" but this goddamn MS product has overwritten 512MB of "/dev/sdb" with the "Windows Restore" files and did not even mind to ask. I read that only if I had an GPT partition then the copy of LUKS headers would be backed up at the end of a partition. However my partition was MBR and now I am probably toasted...

---

### Post by Herman on 2016-10-10
There's still a chance you might be able to get your data back with TestDisk. You will need a Ubuntu Live CD or Ubuntu installed in a different disk, possibly a USB external disk of some kind for installing and running TestDisk. TestDisk is a program for scanning a hard disk for file system starting sectors and registering the start points of old deleted partitions to MBR. The usual procedure for data recovery is to get another disk of equal or greater capacity and use a dd command to make a copy of the original as a backup before starting. TestDisk has excellent instructions at their website. You would probably be best to practice with TestDisk first on an old spare disk or a USB flash memory stick or something. It would be best to practice and experiment with TestDisk a little to learn how to use it before trying on your real disk.  If it's only your /boot partition that got clobbered, there's some possibility your data will be okay. I'm not sure, but I think Ubuntu comes with the necessary software for decrypting and mounting LUKS partitions. If it doesn't just pop up and present you with a dialog box for a password for mounting it, you might need to install some extra software. ```
sudo apt-get install lvm2 hashalot cryptsetup
``` ```
sudo modprobe dm-crypt
``` You should be able to access your files if all goes well.

---

### Post by lucassith on 2016-10-10
Thank you for your time Herman.However my /dev/sdb was from the beggining to the vary end, ext4 LUKS encrypted partition. I've accepted the fact that I'm going to recover my data. Now for everyone who is reading this post and uses LUKS encryption, please consider making backup of the header, it's really simple. I have lost my salt that is needed to recover the data.

---

