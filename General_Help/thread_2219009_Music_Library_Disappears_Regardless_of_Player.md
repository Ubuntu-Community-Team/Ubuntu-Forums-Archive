---
title: "Music Library Disappears Regardless of Player"
date: 2014-04-22
forum: General Help
---

### Post by Keane_Smith on 2014-04-22
Hello, 

I recently set up an Ubuntu partition on my ASUS notebook with Windows 8.1 on it. I had amassed quite a library of music and so naturally I just wanted to tap into the folders on my Windows partition in my Ubuntu players. I initially used Rhythmbox and that worked fine until I put my computer to sleep. When I brought the computer back out of sleep, my library was gone. All of the music was still in the folder on the other partition and the import directory was still listed as that folder. To try to fix this issue I downloaded Clementine and that worked great until the exact same thing happened. Now neither of my music players want to find that music. 
 
Is this an issue with my computer, my players, or the fact that I'm reaching across partitions for my music?

---

### Post by papibe on 2014-04-22
Hi Keane_Smith. Welcome to the forum ):P

My first guest is that since your music is on the Windows partition, it is not available for the player by default. I imagine you have to double click your Windows partition every time so that it gets mounted and thus the files become available again.

If that the case, it is possible to mount the Windows partition automatically so it is always available after a boot.

Let us know if you need more directions to accomplish this.
Regards.

---

### Post by Keane_Smith on 2014-04-22
Thank you so much!

Please, tell me your secrets.
How would I go about doing that?

---

### Post by papibe on 2014-04-22
Sure thing.

Let start getting some info about your partitions.

Could open a terminal, run these commands, and post back the results (you can copy/paste the text)?
```
sudo fdisk -l

sudo blkid

cat /etc/fstab
```
Regards.

---

### Post by Keane_Smith on 2014-04-22
I hope this is what you were looking for. Thank you so much for all of the help. > WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x01a8a7c0


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT
Partition 1 does not start on physical sector boundary.
keane@keane-K55N:~$ 
keane@keane-K55N:~$ sudo blkid
/dev/sda1: LABEL="SYSTEM" UUID="78D9-C1C4" TYPE="vfat" 
/dev/sda2: LABEL="Recovery" UUID="885202085201FC26" TYPE="ntfs" 
/dev/sda4: LABEL="OS" UUID="A478065E7806301A" TYPE="ntfs" 
/dev/sda5: UUID="78C617FCC617B978" TYPE="ntfs" 
/dev/sda6: LABEL="Restore" UUID="FAC20D83C20D44FB" TYPE="ntfs" 
/dev/sda8: UUID="7600b3ce-0ad6-4803-86ef-e4de52569b7a" TYPE="ext4" 
/dev/sda9: UUID="ca236ce4-bfe9-4701-af2f-e8d14ace6944" TYPE="swap" 
keane@keane-K55N:~$ 
keane@keane-K55N:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda8 during installation
UUID=7600b3ce-0ad6-4803-86ef-e4de52569b7a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=ca236ce4-bfe9-4701-af2f-e8d14ace6944 none            swap    sw              0       0

---

### Post by papibe on 2014-04-22
Thanks.

It looks like your Windows partition is /dev/sda4.

The safest way is to use sda4's id instead of mounting it directly to /dev/sda3:
```
/dev/sda4: LABEL="OS" UUID="A478065E7806301A" TYPE="ntfs" 
```
You need to decide where to mount it and create a mount point (basically a directory). For instance, if you want it on /windows:
```
sudo mkdir /windows
sudo chown youruser:youruser /windows
```
(replace youruser for your actual username).

Open the editor like this:
```
gksudo gedit /etc/fstab
```
Finally, you can create the fstab entry at the end of the file:
```
# mount sda4 on /windows
UUID="A478065E7806301A"  /windows  ntfs uid=1000,gid=1000,defaults  0       2
```
Don't reboot just yet. Test if everything works by doing:
```
sudo mount -a
```
If the partition is mounted and you get no errors, reboot and double check if everything went OK.

You are going to need to add the Music folder to the player so that it rescan your library from the new localtion (probably will be on /windows/User/YourUser/Music)

Hope it helps. Let us know if that worked.
Regards.

---

### Post by Keane_Smith on 2014-04-22
It worked fine in the terminal, and now the Windows partition is no longer listed in the Devices part of the file directory, and now it is in my Ubuntu partition, is that what was supposed to happen? Will my Windows installation still work?

---

### Post by papibe on 2014-04-23
Yes.

It does not affect the process of booting Windows.

Go ahead and rescan your Music, and then reboot so you can test if it is working.

Regards.

---

### Post by Keane_Smith on 2014-04-24
Well, I tried to put to Windows this morning and it no longer works, it comes up with a message about an error and forces me to restart. Do you suppose undoing this mounting process will fix that?

---

### Post by jamesisin on 2014-04-24
Assuming you performed those commands in the order given, none of it should have written to (and thus changed) your Windows partition.  That being said, did you do any writing to that partition once you had it mounted.

On a related note, I would recommend a couple of changes to the setup as it currently stands.

First, I would not mount *anything* at slash (papibe suggested /windows for your mount point).  I use **/media/ **and others may prefer **/mnt/**.  So I would create your mount-point at **/media/windows** (or **/media/whateveryouwanttonameit**).

Second, I would recommend creating a partition specifically for your music.  Then I would have both Windows and Ubuntu connect to that partition.  The advantage here is that you are not mounting your Windows (bootable) partition just to access your music.

This second suggestion does make things more complicated to set up but it also makes your setup a lot safer to use.

Is the error you get when attempting to boot into Windows a Windows error?

---

