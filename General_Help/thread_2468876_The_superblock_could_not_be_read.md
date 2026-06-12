---
title: "The superblock could not be read"
date: 2021-11-12
forum: General Help
---

### Post by Dan_Bowser on 2021-11-12
Hi,

I'm using lutris to run a game so I run the install script and now I've got a launcher running in wine. What happen then is the game updates something and eats all the available hard drive space. The last time this happened I was able to use a bootable drive to get into an OS (xubuntu) and from there I could mount the drive the OS is on and delete some stuff.

Now when I'm trying this again I'm unable to mount the drive. I searched for the error message and ended up here, [https://askubuntu.com/questions/539880/cant-mount-an-ide-hdd-cant-read-superblock-error-message](https://askubuntu.com/questions/539880/cant-mount-an-ide-hdd-cant-read-superblock-error-message). The commands seemed innocuous enough so I ran them. The last command, fsck -y /dev/nvme0n1, outputs 
```

fsck from util-linux 2.34
e2fsck 1.45.5 (07-Jan-2020)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/nvme0n1

The superblock could not be read or does not describe a valid ext2/ext3/ext4 filesystem. If the device is valid and it really contains an ext2/ext3/extr4 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock: 

e2fsck -b 8193 <device>

or

e2fsck -b 32768 <device>

Found a gpt partition table in /dev/nvme0n1
```

It looks like I could format the drive and reinstall xubuntu. I can look up how to extract some files from the drive first(?) but I want to know first if there's anything I can do to repair and mount the drive.

---

### Post by mikewhatever on 2021-11-12
You might want to add the output of <sudo fdisk -l> or <sudo parted -l> to check if anything is recognized and /dev/nvme0n1 is the right partition.

---

### Post by Autodave on 2021-11-12
Whenever I see that the message that the super block is bad, that tells me that almost always the drive is bad and you are not likely to retrieve anything from it.  Also, I would not ever trust the drive again.  While you may be able to reformat it and make it usable, it certainly should not be considered reliable.  Personally, for what a spinner HD costs nowadays, I would just get rid of that one and replace it with new.

---

### Post by Dan_Bowser on 2021-11-12
I got into ubuntu live and was able to use testdisk to backup the folders for most of my projects. Many/most of the files I tried to backup are corrupted though.

When I try to reinstall xubuntu I get Input/output error during write on /dev/nvme0n1. So I assume the drive is baked.

---

### Post by QIII on 2021-11-12
You may try to restore your nvme to its factory state using the method found [here]("https://wiki.archlinux.org/title/Solid_state_drive/Memory_cell_clearing").

Just be aware that this will make it utterly and absolutely impossible to ever recover its current data ever again.

---

### Post by ActionParsnip on 2021-11-13
Why do you not have regular backups if your data is important (you say you used testdisk to recover data so it must be worth something). Why so careless with your data?

---

