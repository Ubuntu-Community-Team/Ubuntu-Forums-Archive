---
title: "fun with Gparted"
date: 2008-05-19
forum: General Help
---

### Post by jeamer on 2008-05-19
Hey so I wiped a couple hundred gigs of a NTFS partition and switched it to ext3 seeing as it was just storage and I don't EVER boot into windows anymore  (it's been a couple years now). My problem with Gparted is twofold:

1. I can't access the drive. I probably can as root, but haven't tried yet as it doesn't really matter; I didn't create a storage partition so that I have to log in as root every time I want to store something on it. Changing the permissions to allow read/write doesn't do anything either (in fact I had read/write right off the bat anyways). 

2. The only place it will mount is in /media and that defaults onto the desktop. I like ubuntu and it's clean desktop look, I don't want one single ugly drive on there. How can I change that? 

I realize there IS a solution to this, and it is reinstalling the whole OS and in partitioning my drives that way everything will be available. This would be a big pain in the butt though, and welcome anyone else's advice. Thanks!

PS I have also already tried the "Storage Device Manager" package as per another thread, but to no avail. I couldn't even get the drive to mount on boot in that program, and that's supposed to be the claim to fame for that package.

---

### Post by sdennie on 2008-05-19
One thing you could do would be to manually add it to fstab and mount under /mnt/whatever.  That will do two things: 1) Allow you to chmod/chown the mount point to something you find more suitable (after that, normal ext3 permissions will come into play on the partition).  2) It will not show the disk on the desktop.

---

### Post by jeamer on 2008-05-20
Thanks, that worked great. One thing to note if anyone ever reads this thread is that the only way I could get permanent access to the drive was sudo chmod.
Editing Fstab or using Storage Device Manager (who's only purpose is to modify Fstab :lolflag:) couldn't permanently do it.

---

### Post by drs305 on 2008-05-20
Hey, if you REALLY like a clean Desktop, run this. Note: you can restore the normal look by changing the 'false' to 'true'.

```
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop 'false'
```

---

