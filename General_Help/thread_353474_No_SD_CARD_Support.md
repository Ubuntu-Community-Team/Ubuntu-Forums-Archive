---
title: "No SD CARD Support?"
date: 2007-02-04
forum: General Help
---

### Post by battleroyalex on 2007-02-04
I have an sd card, its not working is there a way i can get it to work? I use it almost everyday and cannot go without it

---

### Post by mgmiller on 2007-02-04
SD cards are normally formatted as FAT volumes and are natively read and written to by Ubuntu.  I use an internal USB card reader for this prupose and everything "just works" without any drivers or configuration at all.  You don't say how you are trying to read this card.  If it's in your camera, most, but not all cameras will simply appear when plugged into USB.  More information is needed to help you.

---

### Post by teaker1s on 2007-02-04
if its usb one then posting output of this command will help-in terminal
[COLOR="Red"]lsusb[/COLOR]

---

### Post by fragos on 2007-02-04
Desktop SD readers are USB connected, even if internal.  Laptops however some times use non-USB hardware to interface to SD readers.  There may not be a Linux driver for these proprietary interfaces.

---

### Post by teaker1s on 2007-02-04
unless it's incorporated into a cd drive like emprex ones

---

### Post by mgmiller on 2007-02-04
This is why I told him we need more info.  It would help if he posted his relevant hardware specs.

---

### Post by battleroyalex on 2007-02-04
Its a sd card reader built into my laptop.

It reads all types of SD and I use a pro-duo sd card inside of it

---

### Post by teaker1s on 2007-02-05
wiki page i created for my laptop someone has added this
> In most cases, the onboard media card reader will not work without a little persuasion. The driver for internal card readers is present in kernel 2.6.17, but is turned off by default. To enable it, do the following:

lspci

Look for SD/SDIO/MMC/MS/MSPro Host Adapter and note the number at the beginning of the line. For example, 05:05.2. Then run (inserting your number in place of mine):

sudo setpci -s 05:05.2 4c.b=0x02

Now put in an SD card, and it should work. The driver is still buggy, but should perform well nonetheless.

This method is not permenant, we're working on that.

**could be set to boot with update-rc.d**
now you may also have different hardware that requires a driver or it may not have a driver in linux-either way above is a starting point

---

### Post by battleroyalex on 2007-02-05
I type ispci in console and get this:
```

jim@jim-laptop:~$ ispci
bash: ispci: command not found

```

---

### Post by teaker1s on 2007-02-05
it's a little "L"
[COLOR="Red"]lspci[/COLOR]

---

### Post by DaveT on 2007-02-24
Hi
when i type in that command

sudo setpci -s 06:03:3 4c.b=0x02
setpci: Warning: No devices selected for `4c.b=0x02'.

ive absolutely no idea what '4c.b=0x02' means could anybody please assist me in getting this to work

Thanks

DaveT

---

### Post by derekguy on 2007-04-26
Thanks heaps for this thread it worked(ish) for me but I have had no luck with other solutions so far.

DaveT, `4c.b=0x02' as far as my limited knowledge tells me is a command assigning a driver to a certain PCI card. I read a bit about what the numbers 0x02 mean but I can't remember exactly.

A suggestion, perhaps post the output of lspci for us to see then we can help you better.

Now to my problem. I am using Edgy Eft on a Compaq Presario B1800 laptop. It has a built in card reader (SD/MS/Pro/MMC) which is controlled by this line in my lspci output

[COLOR="Red"]06:07.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller[/COLOR] 

I input your command and it worked! Cool except it rendered one photo and the rest are I/O errors... I suppose this is because of proprietary drivers but if anyone has some help for me it would be greatly appreciated.

---

### Post by silverglade00 on 2007-04-26
Derekguy, this might work for yours:

```
1. In Terminal, sudo modprobe tifm_sd
2. Insert an SD-card and then check for the existence of /dev/mccblk0p1
3. mkdir /media/sd (or /media/mmc, or wherever you want to mount it)
4. If this goes right, then mount /dev/mmcblk0p1 /media/sd

```

---

### Post by fragos on 2007-04-26
If in the end this card reader refuses to comply with sanity there is a backup solution to consider.  Buy a small USB card reader and you'll be back to using what's already there and works.  There are even SD cards available that have a flip down USB connector while maintaining standard SD dimentions.

---

