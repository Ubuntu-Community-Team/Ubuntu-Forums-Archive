---
title: "Lubuntu 20.04 - File manager hanging on transfer to external storage (SD card)"
date: 2021-09-21
forum: General Help
---

### Post by steve234 on 2021-09-21
Hi all,

I thought I'd fixed this issue, but it has reared its head again. 

I've run through various fixes available online, mostly involving writing a dirty bytes setting to `/etc/sysctl.conf`

The relevant part of my `/etc/sysctl.conf` looks like this

```
##################################
# doing the "fix" for SD card transfer
vm.dirty_background_ratio = 5
vm.dirty_ratio = 10

```

Am I missing something?

---

### Post by dragonfly41 on 2021-09-21
I have no issues recently transferring data to MicroSD cards, so this is news to me.
I use Krusader as my File Manager.
My /etc/sysctl.conf has no settings.
Looking around I found this explanation of vm.dirty_ratio .. re caching.

[https://lonesysadmin.net/2013/12/22/better-linux-disk-caching-performance-vm-dirty_ratio/#:~:text=dirty_background_ratio%20is%20the%20percentage%20of,to%20write%20it%20to%20disk](https://lonesysadmin.net/2013/12/22/better-linux-disk-caching-performance-vm-dirty_ratio/#:~:text=dirty_background_ratio%20is%20the%20percentage%20of,to%20write%20it%20to%20disk)[.]("https://lonesysadmin.net/2013/12/22/better-linux-disk-caching-performance-vm-dirty_ratio/#:~:text=dirty_background_ratio%20is%20the%20percentage%20of,to%20write%20it%20to%20disk.")

I learn something every day.

---

### Post by ActionParsnip on 2021-09-21
If you fsck the file system with it unmounted, is it clean and contiguous? Could be a bad file system on the card

---

### Post by steve234 on 2021-09-21
Output of fsck is:

```
sudo fsck /dev/sdd1
fsck from util-linux 2.34
fsck.fat 4.1 (2017-01-24)
/dev/sdd1: 104 files, 814087/965534 clusters
```

---

### Post by ActionParsnip on 2021-09-21
Try:
```

sudo fsck /dev/sdd

```
instead

---

