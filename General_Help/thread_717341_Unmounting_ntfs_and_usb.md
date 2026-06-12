---
title: "Unmounting ntfs and usb"
date: 2008-03-06
forum: General Help
---

### Post by _godbout_ on 2008-03-06
Hi there!

I would like to be able to unmount an ntfs partition at startup. I don't need it, and I don't want to see it at all in Ubuntu. I don't even want to see it in the "explorer" windows. Is it possible to do this ?

And another point is that when I plug my usb key, I've got 2 disk mounted. One is the content of my usb key, the other one seems to be the files system of the usb key. Usually I don't see this one under Windows. Is it possible that, when I plug the key, I just see the content of the key and not this system partition? Is there a config file where I can force this?

Thanks a lot in advance!

I'm quite new to Linux, so I still have a lot of things to learn :-)

Guillaume

---

### Post by dcstar on 2008-03-06
> **_godbout_ said:**
> Hi there!

I would like to be able to unmount an ntfs partition at startup. I don't need it, and I don't want to see it at all in Ubuntu. I don't even want to see it in the "explorer" windows. Is it possible to do this ?

And another point is that when I plug my usb key, I've got 2 disk mounted. One is the content of my usb key, the other one seems to be the files system of the usb key. Usually I don't see this one under Windows. Is it possible that, when I plug the key, I just see the content of the key and not this system partition? Is there a config file where I can force this?

Thanks a lot in advance!

I'm quite new to Linux, so I still have a lot of things to learn :-)

Guillaume

1:  Either manually edit the /etc/fstab file, or install the **pysdm** package and try that.

2: Not really AFAIK, Ubuntu will automatically mount all partitions in removable devices - if you don't actually use whatever is on the other partition you may consider deleting it and using the space for your data. You can try making it a "Hidden" partition with **gparted** (if it isn't already).

---

### Post by _godbout_ on 2008-03-07
dcstar, thanks for your answers!

1 - The fstab file is ok, I removed what I don't want. BUT the disk is still there in the "explorer". Not mounted, but visible. Is there a way to make it unvisible?

2 - The thing is that if I remove the partition, I'm afraid that the usb key doesn't work that well anymore. Anyway, I'll try to see if I can do something with gparted.

Thanks!

Guillaume

---

### Post by _godbout_ on 2008-03-09
Little up!

---

