---
title: "darktable wont upgrade"
date: 2024-02-17
forum: General Help
---

### Post by guine on 2024-02-17
I've been trying to get darktable 4.4(ubuntu version, I've had issues with the snap and flatpack versions crashing constantly and not being usable) to upgrade to 4.6 but I haven't been able to get it to upgrade any way. If I use software or ubuntu software it looks like it is going through the update with the progress bar but at the end gives an unable to upgrade message and if I try sudo apt-get update or sudo apt-get upgrade nothing happens there either. Any ideas on how to force an upgrade, I've been trying for a week or 2 now with no luck.
Thanks

---

### Post by TheFu on 2024-02-17
Wild guess. Any chance you are out of space in /var/?   Or out of inodes?  May need to clean up some logs and put tighter controls over how large log files are allowed to get.
It is possible to have 20TB of free storage, but still run out of inodes, so check that too.

---

### Post by guine on 2024-02-17
I may be running out of space in /var, I'm not sure if I'm reading this output correctly
```
df -h
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           1.6G  2.6M  1.6G   1% /run
/dev/nvme0n1p2  938G  790G  101G  89% /
tmpfs           7.7G   16M  7.7G   1% /dev/shm
tmpfs           5.0M  8.0K  5.0M   1% /run/lock
efivarfs        128K  119K  4.1K  97% /sys/firmware/efi/efivars
/dev/nvme0n1p1  511M  6.1M  505M   2% /boot/efi
tmpfs           1.6G  2.6M  1.6G   1% /run/user/1000

```
but in files it says /var is taking up 4.7 gb with over 100 gb free.
I'm hoping this is the correct thing to check for inodes
```
df -ih
Filesystem     Inodes IUsed IFree IUse% Mounted on
tmpfs            2.0M  1.6K  2.0M    1% /run
/dev/nvme0n1p2    60M  605K   59M    1% /
tmpfs            2.0M    55  2.0M    1% /dev/shm
tmpfs            2.0M     5  2.0M    1% /run/lock
efivarfs            0     0     0     - /sys/firmware/efi/efivars
/dev/nvme0n1p1      0     0     0     - /boot/efi
tmpfs            392K   223  392K    1% /run/user/1000
```
Were these the correct things that I should be looking at?

---

### Post by Holger_Gehrke on 2024-02-18
What version of Ubuntu are you on ? The versions of an application in the official repositories stays fixed at the version of the release and only gets bugfixes for critical bugs (crashes or security problems). So if you installed it from the repos on 23.10 you get 4.4 and you won't get a newer version until you upgrade the whole distro to one that has a newer version of darktable (and 24.04 will - as far as packages.ubuntu.com can tell - also feature version 4.4). The only way I can see to get a newer version through apt is to use the packages from [SuSE's Open Build Service]("https://software.opensuse.org/download.html?project=graphics:darktable&package=darktable") that are linked on [www.darktable.org](www.darktable.org).

Holger

---

### Post by TheFu on 2024-02-18
My guess was a shot in the dark. It missed, completely.
You have plenty of space and plenty of inodes.

Unrelated to your current issue, 
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/nvme0n1p2  938G  790G  101G  89% /
/dev/nvme0n1p1      0     0     0     - /boot/efi
```
is the only real storage used. The others are pseudo-devices and don't use real storage.
I'm not a fan of having 1 huge storage area for everything and placing everything under it on /.  It makes some things harder and more dangerous in the future, but it is easier for the installer program.  Next time you do an OS install, please consider splitting up allocations for /var/ and /home/ into separate areas.  

This has nothing to do with your current issue, which I haven't any clue about. Sorry.  I don't use Darktable.

---

### Post by guine on 2024-02-18
I'm on 23.10 but I'm pretty certain the past couple of darktable releases have had updates before the next version of ubuntu came out and both ubuntu software and software are claiming there is an update available.

---

### Post by guine on 2024-02-18
> **TheFu said:**
> My guess was a shot in the dark. It missed, completely.
You have plenty of space and plenty of inodes.

Unrelated to your current issue, 
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/nvme0n1p2  938G  790G  101G  89% /
/dev/nvme0n1p1      0     0     0     - /boot/efi
```
is the only real storage used. The others are pseudo-devices and don't use real storage.
I'm not a fan of having 1 huge storage area for everything and placing everything under it on /.  It makes some things harder and more dangerous in the future, but it is easier for the installer program.  Next time you do an OS install, please consider splitting up allocations for /var/ and /home/ into separate areas.  

This has nothing to do with your current issue, which I haven't any clue about. Sorry.  I don't use Darktable.

No worries and thanks for the idea to check, that was beyond the ideas of what I had to check.

---

