---
title: "Total Lockup even on fresh install"
date: 2015-02-26
forum: General Help
---

### Post by sbmontgomery on 2015-02-26
Hey, I've been using Ubuntu for about a month now and all of a sudden I'm getting total system lockups at seemingly random points, REISUB sometimes works, but usually not, and I can't open a terminal or anything, just have to hold down the power key....

I was running 14.04 and installed Gnome 3.14 shell on top of it. It was fine for a while until I started getting really sluggish performance, like something was using all of the memory, I would move the mouse and it would take about a minute to respond and would just glide around, couldn't click on anything, then after 5-10 minutes pop back to normal. Eventually when trying to log in one day I couldn't log in anymore and kept getting the 'Failed to start session' error.

I assumed that this was because of Gnome shell. Because I have a separate home partition I decided to do a clean install of Ubuntu Gnome 14.10. That was also fine for about a day and then the lockups started. I did a clean install for a second time, assuming that Gnome was just being unstable and installed Ubuntu 14.10.

The lockups started again immediately even before a single piece of software has been installed. I usually get about 30 seconds after logging in (if I make it through the login process) before it locks up and has to be manually switched off again.

I have a dual-boot system with Windows 10 technical preview. I'm wondering if perhaps there is something wrong with my partitions or if the root partition or one of the others isn't being properly formatted during installation and whatever is causing the issue is still sitting there?

My laptop is a Lenovo Yoga 13", Intel i7 with 4GB Ram and a 120GB (ouch) SSD with UEFI and GPT.

Partitions are as follows:

1. free space | 1 MB (I don't know how this happened..)
2. /dev/sda1 | ntfs | 314 MB | Recovery partition (I think Windows created this)
3. /dev/sda2 | efi | 104 MB | Windows Boot Manager
4. /dev/sda3 | ext4 | 134 MB | Mount point: /boot
5. /dev/sda4 | ntfs | 30 GB | Windows 10 C: partition
6. /dev/sda5 | fat32 | 1GB | Share partition to move small files between Windows and Linux
7. /dev/sda6 | 4095 MB | Swap partition
8. /dev/sda7 | ext4 | 70 GB | /home
9. /dev/sda8 | ext4 | 20GB | /root


Ideally I'd like to run Ubuntu Gnome as it seems that it wasn't Gnome causing the issue (as I'd thought) but something else. If anyone can offer some tips to fix this then I'll follow those and then put Ubuntu Gnome 14.10 back on there.

Thanks so much for any help!!

---

### Post by QIII on 2015-02-26
Hello!

Does Win 10 boot and operate normally?

---

### Post by tgalati4 on 2015-02-26
Boot without the battery.  Sometimes a bad cell will cause a sudden low-voltage condition which trips the emergency (BIOS) shutdown.

---

### Post by sbmontgomery on 2015-02-26
Yeah Windows 10 is absolutely fine. The problem is that I gave it 30GB intending never really to use it and I'm now having to use it more and more as Ubuntu is unuseable.

I can't actually remove the battery from this laptop but don't think it's that given that Win 10 is working fine (and had been for months prior to implementing the dual-boot).

Thanks for the suggestions!

---

