---
title: "Backing up with tar to USB Stick - Says I am out of space - but I am not"
date: 2018-10-27
forum: General Help
---

### Post by robertcull1 on 2018-10-27
I am backing up with tar to a usb stick. It says I am out of space but I have up to ten more gigs.

```
user@machine:/media/robert/32GB$ tar -czvf archive.tar.gz /home/user >> stdout.txt 2> stderr.txt
gzip: stdout: No space left on device
tar: archive.tar.gz: Wrote only 8192 of 10240 bytes
tar: Child returned status 1
tar: Error is not recoverable: exiting now
```
I still have over 10G of space left on my USB stick.

Can someone please tell me what I am doing wrong? Any help would be greatly appreciated.

---

### Post by cbraxton on 2018-10-27
The USB stick is probably formatted FAT32, which allows a maximum file size of 4GB. If you try to create a larger file than that you will get an "out of space" error. If you need large file support you'll need to reformat with a suitable filesystem.

---

### Post by DuckHook on 2018-10-27
&#8593;+1

@robertcull1

If you will only be using this stick for Linux (and it sounds like you will, else tar/gz wouldn't make sense), then consider formatting either with ext2 or with ext4 possibly minus journaling.

*Gparted* will format the drive to your filesystem of choice.

To turn off ext4 journaling:```
sudo tune2fs -O ^has_journal /dev/sdxN
```…where "xN" is the specific device number of your USB stick.

*Note* You don't really have to turn off journaling and keeping it adds data integrity which you may want, but disabling it extends the life of your USB stick.

---

