---
title: "Problem when using USB-sticks. They kill KDE-Partmgr. and File mngr. (20.04)"
date: 2021-05-01
forum: General Help
---

### Post by GhX6GZMB on 2021-05-01
On one of my laptops I've run into the following problem:

When inserting a USB-stick (FAT32 formatted), it is recognized perfectly.
With KDE Partition Manager, I then wish to set it up as an .ext4 stick (by assigning a "sdb1" partition).
Opening KDE Partition Manager, I see my main HD correctly displayed, and also the USB-stick as "sdb".
Clicking on the "sdb" drive, the Partition Manager closes. Huh?
In the File Manager (PCmanFM-Qt), clicking on the stick, the file manager closes as well. Huh?

I'm completely lost here, I've never seen this kind of behaviour before in Lubuntu.

Any ideas?

Thank You.

---

### Post by GhX6GZMB on 2021-05-01
I think I just solved it myself.
Apparently, the USB-stick was marked as "encrypted" somehow (dunno why?).
Installed Gparted, which indicated this, and I was able to resolve the issue.

KDE Partition Manager is now deinstalled on all my laptops. I don't need useless SW.

---

### Post by guiverc on 2021-05-01
I don't think I've found anything that KDE Partition Manager cannot do.

I do often find `gparted` easier as I've been using it for years, and thus know it better (*I spend more time looking for how to do things in KDE Partition Manager is all; that'll change I suspect with time*).

It's a bit late now, but if you'd filed a detailed bug report, enough that we could re-create the issue, we could explore it & if it's a bug, file upstream so it gets fixed.

I suspect it's only that that you hadn't found how KDE Partition Manager expects you to work, how it was designed... (*there are somethings it actually does better than `gparted too*).   KDE Partition Manager is used as it's far more efficient (*lighter on resources*) as it uses libraries/toolkits already in memory as used by the LXQt desktop.

---

### Post by GhX6GZMB on 2021-05-02
You may right that the problem is my failure to work with the KDE Manager.
But that doesn't explain why the File Manager (PCManFM-Qt) gets killed as well.

---

