---
title: "SD = Write Only / Read Once Memory ??"
date: 2018-01-22
forum: General Help
---

### Post by Timothy Taylor on 2018-01-22
I recently bought a new 16GB Micro-SD card, which I connect to my PC using a USB-stick adapter.

I can save files to the card - they appear in the directory listing, but can only read files OK the first time!
Subsequent reads, or attempted reads after I remove and re-insert the card produce errors.  Text files are corrupted / garbage.  Trying to view graphics files (with image viewer) gives messages of the form "Fatal error reading PNG image file: Not a PNG file" "Error interpreting JPEG image file (Not a JPEG file: starts with 0xff 0xff)", etc.

I thought I had a faulty Micro-SD card at first.  I tried re-formatting, but no change.  Other (previously working) cards give similar results.
I have tried using a different adapter - same problem.
I tried plugging the USB adapter into rear (on-board) USB ports - no change.

This is recent behaviour - the USB-SD combination has worked well in the past, but now seems to corrupt any data stored on any card.

I have no idea how or why this issue should appear now or how to troubleshoot further.

---

### Post by capedbaldy on 2018-01-22
Using GParted try to create a new partition table and create fat32 partition.

---

### Post by QIII on 2018-01-22
Perhaps the user has already tried that.  Did you ask?

Also, the user has indicated that the issue occurs with other devices.

Let's stay on track here and attempt to help the user with the stated issues.

---

### Post by Timothy Taylor on 2018-01-22
> **QIII said:**
> Perhaps the user has already tried that
I had only used the "disks" utility - so I tried GParted.
It seemed to work at first, but re-connecting the USB adapter, I observed the same behaviour as before.

It *can* work, but seems to lose the plot after the first read..

??

---

### Post by Timothy Taylor on 2018-01-23
I've just tried a "normal" USB pen-drive, which works properly, as does my old USB multi-adapter with Compact Flash card.
If try this old adapter with SD or µSD cards, the errors return.  This problem seems to affect SD / Micro SD cards only.

As I've said, these have worked fine in the past, so I don't know why this is a problem now?

---

### Post by sudodus on 2018-01-23
I suspect that there might be a hardware problem,

- either the SD card(s) or the adapter

-  or a problem with the communication between your computer hardware or operating system and the adapter.

You can try according to the tips (particularly the list) in the following link,

[Can't format my usb drive. I have already tried with mkdosfs and gparted](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035)

> - On some pendrives and on many memory cards there is a small mechanical switch for write protection, that can toggle between read/write and read-only. You might have set it read-only without intention.

-Reboot the computer and try again to restore or wipe the first megabyte with mkusb.

- Disconnect other USB devices. Sometimes USB devices can disturb the function for each other.

- Try other USB ports, and/or other card adapters.

- Try another computer.

- Try another operating system (Windows, MacOS) in another computer.

- If you still cannot wipe the first megabyte of the drive, and the drive is read-only, it is probably 'gridlocked', and the next stage is that it will be completely 'bricked'. There is a limit, when you have to accept that the pendrive is damaged beyond repair, at least with tools available to normal users like you and me.

---

### Post by Timothy Taylor on 2018-01-23
> **sudodus said:**
> I suspect that there might be a hardware problem

I'm coming to that conclusion too.

I thought I'd found the answer: [Fix SD Card Reader not working after Ubuntu 16.04 upgrade]("http://www.fosslinux.com/1985/fix-sd-card-reader-not-working-after-ubuntu-16-04-upgrade.htm"), but no change.

:(

PS
Almost no change: small text files are now readable, but image, office & pdf files remain unreadable.

Time for a new motherboard?

---

### Post by sudodus on 2018-01-23
Did you test according to the list in my previous post?

You could try live (booted from a DVD disk or USB pendrive or memory card with a cloned copy from the iso file (not only with the installed Ubuntu MATE 16.04 LTS(?) system), but also some other linux system, for example Ubuntu 16.04.1 LTS and Ubuntu 17.10.1 'artful dot one' or some corresponding community flavour, Ubuntu MATE or Lubuntu or Ubuntu Budgie or Xubuntu.

You can find them via the following links

[http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

This way you will find out if the problem is specific to your installed operating system or more general.

---

### Post by Timothy Taylor on 2018-01-25
I tried restoring the drive with mkusb and click "reload" in Caja, files can be re-read OK.  If I unplug the drive and re-connect, all files are corrupted & unreadable.

I tried booting off a live DVD and observed the same behaviour.

I have tried this on a laptop also running MATE 16.04 - same behaviour.

I tried with some older, bigger Micro-SD cards and everything works fine!

I think I have bought a batch of duff / dodgy Micro-SD cards.

Not sure why I was able to read "refreshed" data OK - I guess it was still cached somewhere?

Anyway, mystery solved.

Thanks for all replies.

TT

---

### Post by C.S.Cameron on 2018-01-25
I bought a 128GB Micro-SD card for $12 that did the exact same thing, Don't worry, if the card is like mine, soon it will not read or write at all.
Go Amazon.

---

