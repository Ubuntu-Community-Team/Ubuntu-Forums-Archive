---
title: "Problem with full file system partition"
date: 2007-08-24
forum: General Help
---

### Post by Habitz on 2007-08-24
I'm very new at using Ubuntu and I ran into a problem running out of space in my file system partition when I installed kubuntu desktop package. Now I cannot even login to any desktop. How can I fix this problem? Is there a command I can use to uninstall kubuntu desktop? Also can I re-size my file system partition?

---

### Post by PentaxFollower on 2007-08-24
It's well known problem. You'll have to use text mode and free some disk space. The best choice is purging old/unused deb packages. To do so type:
```
sudo apt-get clean
```
and
```
sudo apt-get autoclean
```
This can free even few hundreds of megabytes. Check if there are some big logs in /var/log, you can safely delete them if you don't need them.
If there are some irrevelant user data, you can delete them as well (old movies, audio, etc).
After reboot you should be able to log in graphic mode again.

To resize partition use GParted. I'm not sure if it corrupts data stored on partition.

---

### Post by laidback on 2007-08-24
Use Gparted to resize. It's on the Live CD, remember that you cannot resize a partition that's mounted, hence you need to use the live CD. Or better still download the Gparted Live CD, Google search gets it, easy to burn etc.

You cannot move partitions across others, only shift from side to side provided that you have enough space. You will probably need to make some first anyway. Suggest you backup important data first.

---

### Post by Habitz on 2007-08-25
I have GParted installed and I have an unused partition that is formatted as NTFS; if I format this partition as ext3, will it extend/expand my existing ext3 partition? And do I still need a live CD for GParted even though it's already installed?

---

