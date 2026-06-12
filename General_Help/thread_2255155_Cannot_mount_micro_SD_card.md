---
title: "Cannot mount micro SD card"
date: 2014-12-02
forum: General Help
---

### Post by CkDGTAT on 2014-12-02
Hi,

Can you please tell me what the micro SD card type is? I guess it is vfat. I cannot find the origin of the problem. I cannot mount it in write mode.

```

sudo mount -o rw -t vfat /dev/mmcblk0p1 /media/u
mount: block device /dev/mmcblk0p1 is write-protected, mounting read-only

```

---

### Post by ajgreeny on 2014-12-02
Is the micro card in an adapter (to enable you to insert it in a card reader), and does that adapter have a physical read-only or lock slide switch?  Mine do; so may yours.

have a look at [http://askubuntu.com/questions/97652/external-hdd-mounted-as-read-only-fat32](http://askubuntu.com/questions/97652/external-hdd-mounted-as-read-only-fat32) which may give you a solution.

---

### Post by CkDGTAT on 2014-12-02
It is an adaptator. Do you have a magical cmd?

---

### Post by ajgreeny on 2014-12-02
> **CkDGTAT said:**
> It is an adaptator. Do you have a magical cmd?
No, I've no magical command.
Have you looked carefully at the link I gave you and tried all that is suggested there using Disk-utility to check the filesystem on the errant disk?

---

### Post by sedawk on 2014-12-03
This can depend on your card reader or your laptop model if it is a built-in reader. Check if other people using the same reader/laptop have similar problems with Linux.
I have various machines with SD card issues, e.g. a mini PC with an unusable SD card slot when running Linux or a laptop with a SD slot that only works read-only.
What kind of card reader/laptop do you have? Can you identify the card reader in the output of "lspci" or "lsusb"? What are the last lines of the output of "dmesg" command after inserting a card?

---

### Post by Yougo on 2014-12-03
Also has the card been used in a windows pc previously? has the card been removed properly from that pc, or any other device? is the card write enabled in other devices?

---

### Post by Impavidus on 2014-12-03
> **CkDGTAT said:**
> Hi,

Can you please tell me what the micro SD card type is? I guess it is vfat. I cannot find the origin of the problem. I cannot mount it in write mode.

```

sudo mount -o rw -t vfat /dev/mmcblk0p1 /media/u
mount: **[COLOR=#ff0000]block device /dev/mmcblk0p1 is write-protected[/COLOR]**, mounting read-only

```
The block device itself is write protected, so the file system is not the problem. It could be a read-only card or the [write-protect tab]("http://en.wikipedia.org/wiki/Secure_Digital#Write-protect_notch") may be set (to the side of the contacts=unlocked, away from the contacts=locked).

---

