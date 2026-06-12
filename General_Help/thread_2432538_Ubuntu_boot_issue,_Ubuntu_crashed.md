---
title: "Ubuntu boot issue, Ubuntu crashed?"
date: 2019-12-04
forum: General Help
---

### Post by paologiac on 2019-12-04
Hello,
after one year using Ubuntu (do not remember the version), something bad happened to the system:
During boot, after a while, instead of the home page, a list of command appear; many of them successful, but:
- failed to start cryptography setup for cryptswap1
- dependency failed for DEV-MAPPER-CRYPTSWAP1-SERVICE
- [LEFT][COLOR=#222222][FONT=Verdana]dependency failed for /DEV/MAPPER/CRYPTSWAP1

What can I do?
[/FONT][/COLOR][/LEFT]

---

### Post by TheFu on 2019-12-04
When a disk that is properly encrypted with LUKS has logical or physical issues, backups are THE ONLY solution.
I've been running LUKS encrypted laptops for a long time, but have never seen that message.  I have had a few SSDs fail.

First question is do you know the passphrase to unlock the system partitions?  If so, then you can boot from a "Try Ubuntu" flash drive, get into a GUI and use the file manager to unlock the encrypted partition, then use lvm commands to activate the VGs and LVs, then you can access the file systems.  First step is to make a backup of everything you don't want to lose.  This may not be possible, because the disk might have totally failed, but it might just be a few sectors that need to be relocated which cannot. If those sectors are where swap normally sits, then you probably haven't lost any data, yet.

After you mount the root LV, you can look inside /etc/lsb-release to determine the version of Ubuntu on the disk.  Post that back and someone might be able to help with specific commands.

cryptsetup and lvm2 are the packages you'll need to install into the "Try Ubuntu" environment before attempting to unlock the storage.

If you don't know the passphrase .... everything is gone.  There aren't any back doors to unlock it.  With a good passphrase, no govt in the world can crack it.

---

### Post by paologiac on 2019-12-05
thank you.
yes, I know the passphrase. I tried to boot from a USB but the file manager doesn't see any file into my home dir; how can I unlock [LEFT][COLOR=#000000][FONT=Ubuntubeta] the encrypted partition?[/FONT][/COLOR][/LEFT]

---

### Post by oldfred on 2019-12-05
Some examples with details. I do not know nor use LVM. Relay on TheFu.

       For mounting encrypted see first few lines:
[https://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu](https://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu) 
   Recover files on encrypted drive
[https://ubuntuforums.org/showthread.php?t=2382995](https://ubuntuforums.org/showthread.php?t=2382995) & 
[https://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line](https://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line)

---

### Post by TheFu on 2019-12-05
Here are my notes about this:
```
# This is NOT a script. It is manual steps for opening a LUKS encrypted
# partition and looking for LVM LVs inside, which can be mounted and 
# accessed for any needs.
# Whenever using encryption, backups that can be restored perfectly are
# mandatory.  Any physical or logical issue with LUKS can completely
# destroy all access.

# Convenience variables - change for your needs
DEV=/dev/sdb5
PV=c720

# Need to install a few packages if a "Try Ubuntu" desktop environment
# is being used. This also could apply to a recovery system boot.
sudo apt install lvm2 cryptsetup-bin

# Open the container
# Must know the passphrase to unlock the LUKS encrypted 
# container. This is usually just inside a full partition.
sudo cryptsetup luksOpen $DEV $PV

# Activate the LVM VGs
# LVM2 is used with Ubuntu full disk encryption.
sudo vgchange -ay

# Create some temporary mount points.
# A mount point is just an empty directory
sudo mkdir /mnt/slash /mnt/home /mnt/Stuff

# Use lsblk to get a list of the LVs available
lsblk

# Using the found LVs, mount them somewhere
# I'm lazy about typing. Use regex where it makes sense.
sudo mount /dev/mapper/c720*home /mnt/home
sudo mount /dev/mapper/c720*Stuff /mnt/Stuff

# if the storage doesn't mount, perhaps run an fsck?

# access the storage as needed.  Probably want to make a backup if 
# you had to use these steps to get it mounted, right?

```

I talk to myself in my notes. ;)  Hope it helps.

---

