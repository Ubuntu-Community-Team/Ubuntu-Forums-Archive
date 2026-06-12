---
title: "automaticly mount at startup"
date: 2005-04-21
forum: General Help
---

### Post by ultima2k on 2005-04-21
I mounted my ntfs-partitions so that I could read from it, but the next time I booted ubuntu, the mounted partitions were gone.

How do I make the partitions automaticly mount at startup?

---

### Post by mirtux on 2005-04-21
Hi,
   you have to add the following lines to /etc/fstab

**/dev/hda1    /media/win ntfs        defaults    0 0 **

Regards
MC

---

### Post by ultima2k on 2005-04-21
N00b question: how do I do that when it's writeprotected?

---

### Post by XDevHald on 2005-04-21
You'll need to do: sudo  gedit /etc/fstab

Then you'll be prompt for an admin password. Then continue on with the device manual addon :)

---

### Post by ultima2k on 2005-04-21
Yeah, editing the file works now :)
The problem is only that if I try to check out the mounted partition it says I don't have permission :S

And I couldn't mount the partitions in the /media-folder.

EDIT:
Solved it. Ran mkdir to create som dirs in media-folder and replaced "defaults" you wrote to "umask=0222" and it works fine now :)

---

### Post by dutler on 2005-11-05
So, I have appropreatly edited the /etc/fstab several times, but it doesnt stick past the reboot.

nice wiki page on mounting:
[https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28windows%29](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28windows%29)

---

