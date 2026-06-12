---
title: "Boot locks up on first try"
date: 2007-01-04
forum: General Help
---

### Post by VaebnKehn on 2007-01-04
I am new to Linux, just installed a new hard drive and put on the new Ubuntu 6.10 edgy version.
Now, when I start the boot loader asks me what to start, (default Ubuntu).  It loads the boot-up splash, and then nothing.  No loading bar movement, no hard-drive reading, nothing.  I let it sit there for an hour before giving up.  I press the restart button.  Now when the boot loader loads, I select load default (same as before), but this time it works flawlessly.  This happens ever time I start the computer.  Load -> nothing -> restart -> fine.

(Below is a full account of what I did installing, since I am new, and don't know what is relevant, and what isn't)

I set the new hard drive to slave.

Installed Ubuntu 6.10 Edgy on it.

I ran the updater, and added a few users.

I added
"/dev/hda1    /media/windows ntfs  nls=utf8,umask=0222 0    0
/dev/hda5    /media/windows2 ntfs  nls=utf8,umask=0222 0    0"
to /etc/fstab in order for it to mount my two windows ntfs partitions. 

I would appreciate any incites, thanks.

---

