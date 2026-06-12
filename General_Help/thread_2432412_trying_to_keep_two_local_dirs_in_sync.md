---
title: "trying to keep two local dirs in sync"
date: 2019-12-02
forum: General Help
---

### Post by mattdawolf on 2019-12-02
I maintain a windows 7 dual boot. I have to because I am unable to get KVM to work right... I need to sync two local directories in quasi-realtime in Linux, as my homedir is on an LVM array and windows is too stupid to understand what that is. Ext2FSD is no help. What should I do? Disk space is an issue. I don't feel like paying a third party piece of software.

---

### Post by dragonfly41 on 2019-12-02
I have Windows 10 + Ubuntu 18.04 dual boot.
A simple mechanism I use to share notes and files between both systems is to create a third NTFS partition.
Then I can mount this shared partition from either OS boot mode.
Of course you can also use an external NTFS formatted drive.

---

