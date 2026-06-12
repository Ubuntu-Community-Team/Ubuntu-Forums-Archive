---
title: "fsck on Truecrypt disk"
date: 2006-12-13
forum: General Help
---

### Post by btboudreaux on 2006-12-13
I was wondering, how do you do a fsck on an encrypted hard drive, or partition, or volume?

I ask because when a disk is mounted, it gives a clear warning message to not check the file system.

Any suggestions? is it possible?

---

### Post by pay on 2006-12-13
Boot a livecd and then run fsck

---

### Post by btboudreaux on 2006-12-13
I would still have to mount the encrypted harddrive in order to read the disk/file system, and the live cd would have to have truecrypt on it. I don't think that will work.

Anyone else?

---

### Post by pay on 2006-12-13
You don't need to mount the disc to use fsck (thats why you got the error about not running fsck while the drive is mounted;))You can install truecrypt on the liveCD installation but I don't think that you need it to install seeing that fsck fixes filesystem problems, not encryption problems:S

---

### Post by technodigifreak on 2006-12-13
> **pay said:**
> You don't need to mount the disc to use fsck (thats why you got the error about not running fsck while the drive is mounted;))You can install truecrypt on the liveCD installation but I don't think that you need it to install seeing that fsck fixes filesystem problems, not encryption problems:S

There is an important distinction here that needs to be made.  IF the truecrypt container is a file on another filesystem, then you can run fsck on the other filesystem.  IF the truecrypt container is a partition, then do not run fsck on the container itself.  You can fsck the contents of the volume when it's mounted.  See all of the following questions from truecrypt FAQ's before proceeding!

> 
[I]Q: Is it possible to change the file system of an encrypted volume?
[/I]
A: Yes, when mounted, TrueCrypt volumes can be formatted as FAT12, FAT16, FAT32, NTFS, or any other file system. TrueCrypt volumes behave as standard disk devices so you can right-click the device icon (for example in 'My Computer' list) and select 'Format'. The actual volume contents will be lost. However, the whole volume will remain encrypted. **If you format a TrueCrypt-encrypted partition when the TrueCrypt volume that the partition hosts is not mounted, then the volume will be destroyed**, and the partition will not be encrypted anymore (it will be empty).

[I]Q: Can I use tools like chkdsk, Disk Defragmenter, etc. on the contents of a mounted TrueCrypt volume?
[/I]
A: Yes, TrueCrypt volumes behave like real physical disk devices, so it is possible to use any filesystem checking/repairing/defragmenting tools on the **contents of a mounted** TrueCrypt volume.

[I]Q: What do I do when the encrypted filesystem on my TrueCrypt volume is corrupted?
[/I]
A: File system within a TrueCrypt volume may become corrupted in the same way as any normal unencrypted file system. When that happens, you can use filesystem repair tools supplied with your operating system to fix it. In Windows, it is the 'chkdsk' tool. **TrueCrypt provides an easy way to use this tool on a TrueCrypt volume: First, make a backup copy of the TrueCrypt volume (because the 'chkdsk' tool might damage the filesystem even more) and then mount it. Right-click the mounted volume in the main TrueCrypt window (in the drive list) and from the context menu select 'Repair Filesystem'.**

---

### Post by btboudreaux on 2006-12-13
All I want to know is, if I have a truecrypt partition formated as ext3, how do I do a fsck? 

To read the partition, the truecrypt volume would need to be mounted. If the partition is mounted, the fsck can't be done unless you want to risk damage to it. 

Is their any alternative to fsck? And why can't fsck check the filesystem when it's mounted? Is their any way around this problem?

---

### Post by technodigifreak on 2006-12-14
> **btboudreaux said:**
> All I want to know is, if I have a truecrypt partition formated as ext3, how do I do a fsck? 

To read the partition, the truecrypt volume would need to be mounted. If the partition is mounted, the fsck can't be done unless you want to risk damage to it. 

Is their any alternative to fsck? And why can't fsck check the filesystem when it's mounted? Is their any way around this problem?

You may want to ask this question on the forums for TrueCrypt.  You may be able to get a better answer.  

Here is and information file on fsck which includes it's man page.
[http://www.ncsa.uiuc.edu/UserInfo/Resources/Hardware/IBMp690/IBM/usr/share/man/info/en_US/a_doc_lib/cmds/aixcmds2/fsck.htm](http://www.ncsa.uiuc.edu/UserInfo/Resources/Hardware/IBMp690/IBM/usr/share/man/info/en_US/a_doc_lib/cmds/aixcmds2/fsck.htm)

---

### Post by btboudreaux on 2006-12-19
I stumbled upon the answer to this problem for anyone interested.

Just mount the volume without a mount point.

truecrypt /home/user/whatever

Then list mounted volumes

truecrypt -l

The output will be:
/dev/mapper/truecrypt0 (or whatever)

Then do a fsck.

fsck /dev/mapper/truecrypt0

And it will check the volume!

---

### Post by pezmanlou on 2008-06-03
[http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html](http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html)

If you encrypted your hard drive with the hardy installer then you can do maintenance on it like this.

First, boot in to a live cd. (I used a hardy one)

You can look at the link above, that is where I got this information from.  If you are lazy and just want one command then plug this in to the terminal.  This command will unlock the partition so you can actually do things with it.

Note: Replace /dev/sda5 with your partition (ex:/dev/hda5 or /dev/sda7)

```
sudo apt-get install lvm2 cryptsetup; sudo modprobe dm-crypt; sudo cryptsetup luksOpen /dev/sda5 crypt1; sudo vgscan --mknodes; sudo vgchange -ay
```

If you need to run fsck, now is the time.  I used 
```
sudo fsck -pv /dev/mapper/compy-root
```
So change the path and command to suit your needs.


If you need to mount it, this will mount the partition to /volume

(my partition was /dev/mapper/compy-root so replace /dev/paulb-desktop/root as needed)

```
sudo mkdir /volume; sudo mount /dev/paulb-desktop/root /volume
```

I hope this helps anybody else who has this problem, it sure helped me.

---

