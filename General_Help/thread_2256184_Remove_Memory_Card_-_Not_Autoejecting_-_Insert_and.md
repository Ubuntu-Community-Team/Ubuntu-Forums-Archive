---
title: "Remove Memory Card - Not Autoejecting - Insert and not showing new images"
date: 2014-12-10
forum: General Help
---

### Post by 777funk on 2014-12-10
I'm having a hard time with this. Everytime I pull the memory card, it's not ejecting. When I put it back in the machine, it's showing files but not new ones since after initially pulling the card. I have to restart the computer to get it to show the new files.

Is there a faster way around this error (besides restarting).

And should Xubuntu auto eject when the card is pulled out of the computer?

---

### Post by sudodus on 2014-12-10
I suggest that you unmount the partition(s) on the card before pulling it out of the slot. Otherwise, if some data are still buffered, they can not be written, and some files will be missing or corrupt or the whole file system might be corrupt.

You can unmount the card with a file browser (press the eject symbol). Then you can pull it out (un-plug) and plug it in again, and it should be updated.

You can also unmount the card with a terminal window command. Identify the card (actually the mounted partitions on the card) with

```
df
```

and unmount with

```
sudo umount /dev/sdxy
```

where x is the drive letter and y is the partition number. If you unmount like this, it should be possible to mount it without un-plugging and re-plugging.

-o-

If there are problems, it might be because the linux driver does not work correctly with the firmware or hardware of the card-reader device.

---

### Post by 777funk on 2014-12-10
I usually do eject the card but it just remounts automatically if it's still physically in there. I've also unmounted through the terminal and it still seems to remount.

---

### Post by sudodus on 2014-12-10
That is very strange. I have never had a drive (HDD, SSD, CD disk, USB pendrive, or flash card) automount after unmounting.

- What linux distro and version are you running?

- Did you install some special program package, that might cause this to happen.

---

### Post by 777funk on 2014-12-10
> **sudodus said:**
> That is very strange. I have never had a drive (HDD, SSD, CD disk, USB pendrive, or flash card) automount after unmounting.

- What linux distro and version are you running?

- Did you install some special program package, that might cause this to happen.

I've got Xubuntu 14.04 and not that I know of.

---

### Post by xubu2 on 2014-12-10
Maybe fiddling with "removable drives and media" in settings helps?

---

### Post by 777funk on 2014-12-10
It's just reloading if I hit eject... peculiar problem. I'll try the removable drives and media option.

---

### Post by sudodus on 2014-12-11
Please tell us about the card reader (the physical device, that reads your flash card). Brand name, model number ... separate unit or built-in.

---

### Post by 777funk on 2014-12-11
Sure, it's a built in device (ASUS factory part).

---

