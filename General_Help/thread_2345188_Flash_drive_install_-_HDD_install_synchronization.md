---
title: "Flash drive install - HDD install synchronization"
date: 2016-12-01
forum: General Help
---

### Post by mdbenderjr on 2016-12-01
I have a USB flash drive that I've been running Ubuntu from, but of course it's not as fast as a SATA connected drive. During the day I use a laptop and a desktop for work, and a desktop at home. The laptop primarily uses the flash drive, but I was thinking it should be possible to have the desktops restore their system from the flash drive as soon as it's plugged in and keep the systems synced as it's being used. Naturally only the software and user data locations, kind of like having a dropbox folder attached to the user account and software directory. But before I go reinventing the wheel I was wondering if there was some method someone has already been using to accomplish this. Thanks in advance.

---

### Post by oldfred on 2016-12-01
I used to use laptop when traveling & Desktop at home.
I used rsync to copy files from one system and back.
And it is not really different than the rsync I use to backup my system to a flash drive, anyway.

But to make it easier I set up NFS as part of every install. But some have suggested for my type of use SSH would be even easier.

The main issue I have is which script to run and not do it backwards. I have one script from desktop to flash drive and one flash drive to desktop. And separate mount points in NFS for remote system.

My flash drive is larger & has a full install of Ubuntu and then a larger data partition which is large enough for what data I want to copy.

---

