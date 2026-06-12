---
title: "Live Cd HELP"
date: 2006-12-05
forum: General Help
---

### Post by notoriouslou1022 on 2006-12-05
Hey, I booted up with the ubuntu live cd to get files off my windows hdd to put on my exteral hdd.. cuz windows crashed... i need neeed to know were to find the windows files in the ubuntu live cd

---

### Post by IMELucky on 2006-12-05
I usually do it like this:

Boot your live CD and open a terminal

type:

sudo passwd (To create a root password)
su (To become root)

mkdir /mount/windows
mount -t ntfs /dev/hdaX /mount/windows (Assuming your filesystem is NTFS, X is the number of partition on your hardrive, usually /dev/hda1)

cd /mount/windows

That's your windows drive, so you can navigate to your files!

Good Luck

---

### Post by CatKiller on 2006-12-05
> **IMELucky said:**
> type:

sudo passwd (To create a root password)
su (To become root)

I normally do **sudo -s** (only one step) but otherwise, that's what I do too.

---

