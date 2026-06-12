---
title: "Cloning a microsd card"
date: 2017-07-11
forum: General Help
---

### Post by Evil Wayz on 2017-07-11
I have an openelec box that runs off a 32gb class 10 card that recently has been having problems creating usable backups.  I have a brand new class 10 128gb card I'd like to clone it to.

Obviously I'll need to resize after words but this is the command I was going to use, if someone could double check it for me:


sudo dd if=/dev/sdx of=/dev/sdy bs=4m conv=notrunc,noerror

where x is the 32gb card and y is the 128gb card, using  fdisk -l to find out which is which. 

Running 17.04 with the standard kernel

---

### Post by sudodus on 2017-07-11
I would let [mkusb](https://help.ubuntu.com/community/mkusb) 'wrap a safety belt around dd', and use the command 'dus' (mkusb-dus is mkusb version 12).

```
dus /dev/sdx
``` where x is the drive letter of the source device (the 32 GB card). You will be prompted to select target device via a menu with additional information in order to help you identify the correct target device.

-o-

But if you want to use dd anyway, according to the manual ```
man dd
``` you should use upper case M to specify a block size in mibibytes, so

```
sudo dd if=/dev/sdx of=/dev/sdy bs=4M
```

You need not use 'notrunc' with devices. Do you really want to continue after read errors, 'noerror'?

If there are errors in the source drive, I would recommend using **ddrescue**, which can be set to read 'difficult' blocks in a more detailed way and to try several times. See this link, [Repair the partition table and file system of a pendrive](https://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986) and scroll to the paragraph 'Advanced repair of a partition table, file system and/or recovery of files'.

---

### Post by Evil Wayz on 2017-07-11
I tried dus, and it wouldn't let me open the card, said it needed cleaning.  So I did that, and now it reads, but gparted shows the second partition has five gigs of data on it, but when the partition is mounted it is empty.  Also the second partition needs to be owner changed because i had to use gksudo to put the test files on.

---

### Post by sudodus on 2017-07-12
- Are you talking about the original card (32 GB) or the new cloned card (128 GB)?

- How did you clean the card?

- Did you try to boot openelec from the card (before and/or after cleaning)? (In that case, what happened, what output from the cloning process)?

- Did you try cloning after cleaning? (In that case, which tool did you use)?

---

### Post by Evil Wayz on 2017-07-12
1) the 128gb
2) unmounted both partitions and checked using gparted
3) I tried it once and it got stuck at the Krypton screen
4) I would have but then I remembered the last time i got input/output errors the card was done. or fake.


It doesnt matter, I'm pretty sure the 128gb card is fake.

---

### Post by sudodus on 2017-07-12
4) Fake card! Well, in that case I wish you good luck getting the money back. I guess the chances depend very much on who was selling the card to you.

Anyway if you cannot get the money back, I suggest that you try to format the card with mkusb: 'Restore to a standard storage device'. Will that work (will it be useful as a storage device)? And the correct size? In that case, the card might be working after all.

---

### Post by Evil Wayz on 2017-07-12
Would this work on a  fake Chinese usb device that claims its 128gb?

Ive read that these fake cards were at one time legitimate cards, just way smaller than they tell your computer they are.  I wonder if there is a way to reset whatever file they have altered.  After all, I'm just runnign openelec or xbian, nothing I need loads of storage for anyways.

---

### Post by sudodus on 2017-07-12
I don't know, what happens after you restore the card to a standard storage device because I don't if and how it was tampered with in the first place. But I think that it is worth trying, maybe it works, because sometimes the analyzing tool might show some wrong information and make you think that the card is tampered with even if it is a good card.

After trying to restore the card you should unplug it and reboot the computer and then check it for example with the following commands

```
sudo lsblk -f
sudo lsblk -m
```

---

### Post by C.S.Cameron on 2017-07-13
My OpenELEC RPi worked with a 128GB SD, but the OS would have to rebuild itself each boot.
Changed to a 32GB brand name card and it now works perfect.
The 128GB card will fit 128GB of data OK but it only cost $12.

---

### Post by Evil Wayz on 2017-07-13
I'm not understanding your point.

---

### Post by sudodus on 2017-07-13
Which point?

---

### Post by Evil Wayz on 2017-07-13
Not you, the other person

---

### Post by C.S.Cameron on 2017-07-15
Just confirming that your problem may be due to a cheap card.

---

### Post by kurt18947 on 2017-07-16
> **Evil Wayz said:**
> I'm not understanding your point.

> The 128GB card will fit 128GB of data OK but it only cost $12. 				


If it seems too good to be true ............................

---

