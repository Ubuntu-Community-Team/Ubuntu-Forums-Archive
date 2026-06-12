---
title: "A particular PC fails to boot any Ubuntu Live version"
date: 2019-10-23
forum: General Help
---

### Post by bsodx on 2019-10-23
So, I have this PC (one of HP's old towers, 2 GB RAM, 32bit architecture, BIOS properly configured for USB boot) where I want to have a Live USB working. The problem is, on any Ubuntu version I tried (I tried 19.04, 18.04, 16.04 and 14.04, the last two being i386, and they had persistence):

19.04:Ignores the USB
18.04:Ignores the USB
16.04:SYSLINUX line shown, Ubuntu loading screen for a second, falls back to initramfs with no error
14.04:"Press a button for options",Ubuntu loading screen for 30 seconds, falls to initramfs

The initramfs behavior: Nothing is on the screen except BusyBox lines and initramfs prompt, help prints commands, any wrong written command turns into an inline and makes no response until reboot, if written "exit":
1)Kernel Panic: not syncing, attempted to kill init (panic dump)
2)System gets softbricked, prompt and cursor freezes, holding power button won't work, need to plug it off

What I have tried:
1)Different USB drives
2)Different PC's of the same model
3)Different burner with/without persistence (Rufus/YUMI)
4)Different PC (it works properly)
5)All USB's used are checked against bad sectors

Any idea of why this happens?

---

### Post by Skaperen on 2019-10-23
are there any removable device cards in it?

---

### Post by bsodx on 2019-10-26
Nope, verified that nothing else is plugged in except the USB drive. BIOS set up correctly (it's too old to be an UEFI, so no CSM/UEFI switch present) to look for USB boot first. There are no boot/administrator passwords blocking anything on it. Also got a AIDA64 report for it, but unfortunately it's in my local language, so here's the catch of it:

PC:HP 500B Microtower (x86)
Processor: Dual-Core Intel Pentium E5500, 2800 MHz (14x200, I guess this count means threads, but might be wrong) and guess what, it's an 64-bit processor wasted on a x86 board, supports SSE/2
RAM: 2 GB DDR3
Graphics:Intel G41 Express Chipset (801404 KB)
BIOS Firmware Release Year:2010
Booting Drivers :Floppy Disk, Hard Disk, CD-ROM, ATAPI ZIP, LS-120
BIOS Capabilities:Flash BIOS, Shadow BIOS, Selectable Boot, Network Service Boot, EDD, BBS
Supports PAE/NX, VMX/Vanderpool

---

### Post by mörgæs on 2019-10-26
> **bsodx said:**
> it's an 64-bit processor wasted on a x86 board


That would surprise me. Anyway, with 2 GB of memory it makes little difference whether you install a 32 or 64 bit Buntu.

Let's try a different approach. Are you able to install Lubuntu from the [alternate ISO]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO") using a DVD (or from the minimal ISO using a CD)?

---

### Post by bsodx on 2019-10-27
Pulling both of them and trying tomorow, but I forgot to say that I need to liveboot only. The main reason I want to get that working is so I can have a rather safe system running on a completely unprotected PC.

---

### Post by mörgæs on 2019-10-27
None of them are able to do a live boot. For this purpose you need the standard ISO.

---

### Post by bsodx on 2019-10-27
Then I'll be pulling a standard Lubuntu and try that, if there is one.

---

### Post by sudodus on 2019-10-27
**Text screen and CD**

Would it be OK with only a text screen, no graphics? In that case a live [Debian 8.11 standard iso file](https://cdimage.debian.org/mirror/cdimage/archive/8.11.0-live/i386/iso-hybrid/debian-live-8.11.0-i386-standard.iso) might work for you. It can fit on a CD disk.

**DVD**

If you can write and run a DVD disk, you can make a more modern Debian live drive for 32-bit systems, for example with the light-weight LXDE, LXQt or XFCE desktop environments via [this link (iso files or torrent files)](https://www.debian.org/CD/live/).

**Otherwise cloning to USB drive**

If you get something working via CD or DVD, fine.Otherwise you can try **cloning** from such Debian 32-bit systems into a USB pendrive.

The **Ubuntu Startup Disk Creator** and  **Disks** (alias gnome-disks) and **mkusb** are cloning tools for live-only USB drives.

In Windows you can use **Win32 Disk Imager** or **Rufus in dd-mode**.

[HR][/HR]
**mkusb** can also create **persistent live** drives, but I suggest that you **wait** with that until you have a cloned live-only drive that works well.

---

### Post by bsodx on 2019-10-28
Will try DD Mode at Debian 12.04, and if not, 6.04. Wish me luck, the place is closed for 2 days so I won't pretty much be able to try it on until Wednesday.

---

### Post by sudodus on 2019-10-28
I think DD mode will work with Ubuntu 12.04.5 LTS, but probably not with for example 12.04.1 LTS. Do you mean 16.04 LTS? 6.04 is really too old. Anyway, good luck :-)

---

### Post by MoebusNet on 2019-10-28
One of the issues with Ubuntu versions after 14.04 is that support was dropped for many older video cards, so you may not have any display at all on screen for a system this old. If you are able to swap in a newer video card, you may find that newer versions will work for you. Also, many BIOS for older systems are unable to boot from USB, so you may need to Live-boot from DVD since Live-boot CD's are no longer supported.

---

### Post by crip720 on 2019-10-28
I have an much older laptop, found that from 12.10 up to including 15.10 ubuntu and other ubuntu types did not like my graphics.  Almost any 16.04s I put in, would work very well, except the lubuntu LTS(LDXE?) that I was using since 12.04.

---

### Post by mörgæs on 2019-10-29
> **MoebusNet said:**
> One of the issues with Ubuntu versions after 14.04 is that support was dropped for many older video cards, so you may not have any display at all on screen for a system this old. If you are able to swap in a newer video card, you may find that newer versions will work for you.

Only a few, old cards have dropped out recently. Intel G41 is supported, and in general Intel is doing a lot to support their hardware: [https://01.org/linuxgraphics](https://01.org/linuxgraphics)

> **MoebusNet said:**
> Live-boot CD's are  no longer supported.
It's still supported but not many ISO's fit to a CD these days.

---

### Post by MoebusNet on 2019-10-29
@morgaes - While I do not have a list of the video cards no longer supported in Linux by their manufacturers, in my experience both with my antique D800 notebook with an obsolete AGP bus-type video card and with my dumpster salvage server, a change to a newer video card brought me the ability to run the newer Ubuntu versions. The dividing line seemed to be when video cards VRAM changed from MB to GB in capacity for both NVidia & Radeon. YMMV. While other distros indeed support Live-CD, I was thinking more along the line of Ubuntu's offerings. Perhaps the mini-iso will fit on a Live-CD; I haven't checked. The main versions of Ubuntu, Kubuntu, Lubuntu, Xubuntu and so forth seem to be all sized to fit on a DVD even when the OS without added applications  (ie, LibreOffice and others)would fit on a CD. I didn't mean to be misleading.

---

### Post by bsodx on 2019-10-30
Okay-I think I have pinpointed the issue- it's persistence. Today I tried on Debian 10.0.4 (in both DD/ISO image mode, no persistence) and Ubuntu 16.04 (ISO mode with no persistence) and both booted normally. Though when I put 1 GB of persistence on Ubuntu ISO it threw me back to initramfs. So, any clues?

---

### Post by MoebusNet on 2019-10-30
Here's the most recent article I found on persistent-live-USB drives: [https://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/](https://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/) 

The one from the Ubuntu wiki hadn't been updated lately. One thing I seem to remember from the past was that there was sometimes an issue using larger USB flash drives (ie, 32GB, 64GB). If you've been using a large USB drive, why not try a smaller (~8 to 16GB) flash drive?

---

### Post by bsodx on 2019-10-30
No, I have been using my trusty 8 GB SanDisk Cruzer for the work. Swapped once with an 32 GB Cruzer Blade though.

---

