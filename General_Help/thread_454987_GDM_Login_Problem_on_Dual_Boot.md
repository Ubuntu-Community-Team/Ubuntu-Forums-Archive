---
title: "GDM Login Problem on Dual Boot"
date: 2007-05-26
forum: General Help
---

### Post by Jose Catre-Vandis on 2007-05-26
Setup:

Dell Inspiron 9300 laptop
Dell Hidden partition on 1st Partition
XP on 2nd parititon
Fiesty on 4th partition
Dell Hidden Fat32 partition on 3rd partition
Swap on 5th partition

Shared profile for Thunderbird on XP and Ubuntu
vmware server from tarball installed
not on a domain
Sharing files between the EXT3 and NTFS partitions using ntfs-3g / fuse (via Automatix2) and ext2IFS on XP
Fiesty installed on an 8gb partition with 2gb free 

Using grub to dual boot

Has all been working fine for 4 weeks

Problem:

Following a boot into Xp for some Windows work, I then rebooted to Fiesty. The gdm login screen came up as normal. I typed in my user credentials but the screen and system hung the black dots of the password greyed out. If I choose restart or shutdown from the options I just get a blue screen (default background colour) and nothing. Have to hard reset.

I can CTRL-ALT-F1 to a console login, but any attempt at login just gives me a flashing cursor

I can boot up in recovery mode, and get the root GUI up if I type startx. if I type gdm from the root command line, I get gdm up, but trying to login as my main user gives the same effect 

I have booted up with quiet and splash removed but do not see any errors, no problems until i get to the gdm login.

I have tried removing and reinstalling gdm to no effect

I have removed network-manager and disabled networking just in case

I have tried creating a new sudoer user. This failed to create a home directory and only gives me a 10 second login. I created a home directory for this user but no change. I can login in in console mode with this new user.

XP boots up and works fine, Thunderbird access shared profile OK, and ext2IFS allows access to Fiesty files.

Can anyone please advise on where I go next to sort out a fix for this problem. I am flummoxed!:(

---

### Post by Jose Catre-Vandis on 2007-05-26
Well, after several hours of panic, and reading every post i could find on the forum, Ubuntu fixed itself. After repeated rebooting, fsck eventually kicked in and found an error, fixed it, and then I could login again. So it seems I managed to create a filesytem / partition error along the way, probably due to the shared profile and file share accessing that goes on on this machine, and the most likely repair will be to run fsck immediately if it happens again!

A happy Jose once again :D

---

### Post by Jose Catre-Vandis on 2007-06-25
I have to revive this thread as This problem is ongoing. I have a workaround but would like to uncover any possible solutions.

Everytime after i have booted into Windows i get refused entry at GDM login and at termial login. So I reboot in recovery mode and type
```
tune2fs -c 1 /dev/sda5
```
and then restart as normal.
This invokes fsck which fixes (as it tells me) an invalid root node and that the HTREE INDEX was cleared. Following a reboot, as requested by fsck, I can login in again

---

