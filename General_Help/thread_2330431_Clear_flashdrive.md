---
title: "Clear flashdrive"
date: 2016-07-11
forum: General Help
---

### Post by Camilia on 2016-07-11
I need to clear a flashdrive which has a ubuntu iso on it. I have tried formatting and get message Error synchronizing after initial wipe: Timed out waiting for object (udisks-error-quark, 0)

Any other suggestions?

---

### Post by sudodus on 2016-07-12
Try with ***mkusb*** according to this link. It can wipe the first megabyte, create a new partition table and file system. Use the wipe menu :-)

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

Install the mkusb PPA, install and update the mkusb package like all the other program packages.

If you run standard Ubuntu, you need an extra instruction to get the repository Universe. (Kubuntu, Lubuntu ... Xubuntu have the repository Universe activated automatically.)

```
sudo add-apt-repository universe  # only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb
```

---

### Post by Camilia on 2016-07-17
> **sudodus said:**
> Try with ***mkusb*** according to this link. It can wipe the first megabyte, create a new partition table and file system. Use the wipe menu :-)


It wiped it clean. Didn't understand how to use it to format the flashdrive. Got the flashdrive formatted on PC with windows os. Somethings are just easier to do with windows os.

---

### Post by sudodus on 2016-07-18
I'm glad you managed to get your flashdrive working again and thanks for sharing your solution! :-)

-o-

Next time you can try one of the other entries (not only wiping) of [mkusb's wipe menu](https://help.ubuntu.com/community/mkusb/wipe).

These options wipe *and* create new partition tables and file systems:

[B]s "Standard: create MSDOS partition table with FAT32 partition"
b "Big drive: create GUID partition table with NTFS partition"
g "General: use 'gparted' to make partition table and partition(s)"  [COLOR="#696969"]# gparted must be installed for it to work[/COLOR]
a "Advanced: create GUID partition table (skeleton for installing an OS)"[/B]

The following options 'wipe clean', but do not create any new partition tables and file systems:

[B]f "wipe the First megabyte (mibibyte)"
w "wipe the Whole device - consider other options except for special cases" [/B]

---

### Post by Camilia on 2016-07-18
Very interesting. thanks!

---

