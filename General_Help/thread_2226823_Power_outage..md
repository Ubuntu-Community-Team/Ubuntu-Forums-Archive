---
title: "Power outage."
date: 2014-05-29
forum: General Help
---

### Post by ClassyJakey on 2014-05-29
I was downloading wine on my ubuntu and Windows dualboot, but it froze. Nothing worked. I had to force-shut it down, which i did by holding the power button. Now it says stuff like 
mount: mounting /sys on /root/sys failed: No such file or directory
something is screwed up.
I press CTRL + D to escape, then it had a kernel panic.
I had to drain the battery for this, even the force shutdown didnt work!
So yeah, can someone help me?

---

### Post by TheFu on 2014-05-29
Welcome to the forums. Wish it wasn't over an issue like this.  We cannot know the answer, but have to start with a few relatively simple things.

Boot off a liveCD/flash drive - the way you did to install Ubuntu is fine. login to the live-environment "Try Ubuntu" is the menu item.  Other distros should be fine too, if you have one of those handy.

Then run **sudo parted -l** <--- that is an el, not a one
So you can get the partition types and numbers.  Ignore NTFS, FAT, and SWAP partitions.
Now you'll need to determine the device for each partition.  These are usually /dev/sda1 or /dev/sda5 or something like that.

Run **sudo fsck /dev/sda1** replaceing sda1 with whatever the partition devices are for your system.
[http://askubuntu.com/questions/353732/how-to-use-fsck-in-ubuntu](http://askubuntu.com/questions/353732/how-to-use-fsck-in-ubuntu) might help with a little more information about fsck.

It would be good to know if this is an SSD - some disk tools aren't safe with SSDs. fsck is fine.

---

### Post by stalkingwolf on 2014-05-29
try running the recovery mode from grub.then fixbroken packages from the net menu

---

