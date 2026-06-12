---
title: "Removed Partitions Cause Errors!"
date: 2007-04-25
forum: General Help
---

### Post by charleseddy on 2007-04-25
I had my partition layout set up like this:

hda1 primary ntfs windows xp
hda2 primary fat32 No OS
hda3 swap
hda4 extended
hda5 logical ubuntu
hda6 logical openSUSE
hda7 logical fedora

I scrapped the last 2 in order to test out a new distro on whath has now become hda6.  They were, previously, automatically mounted each time Ubuntu started up--courtesy of Gparted's options page in the dapper installer.  now, every time I boot into ubuntu it comes up in a maintenance shell saying fsck can't be completed because 2 drives can't be found.  how do I make this stop?

---

### Post by phidia on 2007-04-25
Edit your /etc/fstab by putting a # (comment) sign in front of those entries.
Make sure you pay attention to which partitions you're commenting out -I just mean be sure to choose the ones that you deleted.
Reboot and see if that works once you have it you can just delete those partition entries in fstab if you want to.

---

