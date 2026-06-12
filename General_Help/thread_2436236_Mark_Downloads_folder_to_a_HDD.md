---
title: "Mark Downloads folder to a HDD"
date: 2020-02-03
forum: General Help
---

### Post by katsu-kiogin on 2020-02-03
I have been looking online, but I am a complete noob to Linux and I just switched from windows. I just want to not download to my main computer drive and to an external 500GB HDD I have. I don't want to have to type in cd /mnt/dev/XXXXXXXXXXXXXXXXX/ each time and would just like to enter cd ~/Downloads/ The reason this is a big deal is that my main drive is an NVME drive and I don't want to take up a bunch of write cycles and space from how much stuff I download in the course of a day. Not looking to move my whole home folder just my Downloads folder. Thank you.

---

### Post by guiverc on 2020-02-03
This (like most things in GNU/Linux) can be done in many ways.

You could shadow your ~/Downloads/ directory by doing the `mount` over it  (which will cause what you want, but can be somewhat confusing, as if the drive isn't mounted, it'll use the real ~/Downloads/ directory and then should you remount it later, those files suddenly become shadowed (ie. they aren't there; at least until you at least `umount`)).  You could experiment with this, it's both really handy, but can be confusing and potentially risky

An alternative is to mount wherever you want, eg. the `/mnt/external` via entry in your file system table (/etc/fstab) or whatever means you decide to use, and make your ~/Downloads a link to that directory.  (`ln`)

I've provided these two, as I've used them both (usually not external drives, but for network storage).

---

### Post by vanadium on 2020-02-03
The most easy and safe way to do this (no root permissions needed) is to delete your Downloads directory, then replace it by a symbolic link that points to the Downloads folder on the drive you want to use. A symbolic link, for practical purposes, behaves like a folder, so you can continue to refer to the ~/Downloads folder.

To create a symbolic link, open two nautilus windows, one open on your external drive where your target Downloads folder is, and one in your home folder. Delete the Downloads folder in your home folder. Then, in the other window, click and hold the mouse button on the Downloads folder there, hold Ctrl+Shift and drag the folder to your home folder. This will create a symbolic link "Downloads" in your home folder.

---

### Post by katsu-kiogin on 2020-02-03
Thanks I changed /etc/fstab/ to mount the hdd to /home(my username)/Downloads and boom

---

