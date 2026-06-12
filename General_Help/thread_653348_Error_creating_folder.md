---
title: "Error creating folder"
date: 2007-12-29
forum: General Help
---

### Post by tmarino on 2007-12-29
I went to create a new folder today and I got the following error:
Error creating new folder. Error "i/O error" creating new folder.

If I move up a leve in the directory structure I can create a folder with no error. I know I created some new folders like this one just a few days ago with no error. I have made no system changes. If I try to create from the command prompt I get "Input/Output Error". Strange but I can create a new file in the folder but not a new folder.

What's going on?

---

### Post by Furat on 2007-12-29
try to check your disk using fsck but first backup and important data and u have to unmount the disk first too before you check it

---

### Post by tmarino on 2007-12-29
Not sure how to run fsck. I have seen advice to boot from cd so the disk is not mounted. I tried that but have no idea how to get fsck to read the disk in question!

---

### Post by nick_h on 2007-12-30
To force a check on the next boot:
```
cd /
sudo touch /forcefsck
```
and reboot.

---

### Post by tmarino on 2007-12-30
Thanks for that tip to force fsck. Now it ran fsck against /dev/hda1 but that isn't the drive in question. I thought fsck would read fstab and process all the drives. Is there a way to force the check on the other drives installed?

---

### Post by tmarino on 2007-12-30
Answered my own question, I didn't have fstab set up to check the device in question. Now when I run fsck I get a lot of buffer i/o errors on the device. Final error message is
Error reading block 8847363 (Attempt to read block from filesystem resulted in short read) while doing inode scan.
/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY

I am now in over my head, what do I need to do (step by step please) to resolve this? Is it fixable or is the drive itself failing?

Thanks for the guidance so far!

---

### Post by nick_h on 2007-12-30
With that kind of error it would be worth downloading a disk checking tool from your disk drive manufacturer's web site.  Your drive may be failing.

---

### Post by tmarino on 2007-12-30
I did some further checking and I had a twin to this drive in a windows box that went bad so I'm not going to fool around, I will replace it. Would someone offer a step by step guide to pull the old drive and swap in a new one? I've got the data copied and it is not a boot drive. It appears to be formatted as ext3. Will ubuntu see new the drive and automatically set it up?

---

