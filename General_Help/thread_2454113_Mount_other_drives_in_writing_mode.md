---
title: "Mount other drives in writing mode"
date: 2020-11-23
forum: General Help
---

### Post by dam034 on 2020-11-23
Dear users,

I have ubuntu 18.04 desktop. When I try to mount another disk drive in my pc, it mounts in read-only mode.

I need to mount them in writing mode.

In this screenshots there are the disk drives present in the computer:
[ATTACH=CONFIG]287433[/ATTACH]

When I click, it mounts, but not in writing mode.

How can I fix?

Thanks

---

### Post by CelticWarrior on 2020-11-23
Are those NTFS partitions in a dual-boot with Windows 8 or newer? It seems so.
Disable the Fast Startup "feature" in Windows and you should be fine.

That said, you SHOULDN'T write to the Windows system partition, typically the "C:\ drive", or you risk having an unbootable Windows. Other non-system NTFS partitions should be fine.

---

### Post by dam034 on 2020-11-23
Those are all NTFS partitions. In Windows, the fast startup is disabled.

I don't want to write in C: drive, but in other partitions, where I archive documents, photos, movies.

I still can't resolve.

Help!

---

### Post by CelticWarrior on 2020-11-23
Are the same partitions writable in  Windows?

---

### Post by dam034 on 2020-11-23
Yes, they are.

In windows those partitions are D:\, E:\, F:\, etc...

---

### Post by CelticWarrior on 2020-11-23
I would run the error correction tool in Windows to be sure.
I would also make sure Fast Startup is actually disabled. Major Windows updates (feature updates) tend to re-enable it.

---

### Post by dam034 on 2020-11-23
Sorry, you were right.

The fast startup was enabled and so only when I restarted from windows to ubuntu, I could mount the partitions in write mode.

Now I finally disabled it and it works fine.

Thanks for the help!

---

