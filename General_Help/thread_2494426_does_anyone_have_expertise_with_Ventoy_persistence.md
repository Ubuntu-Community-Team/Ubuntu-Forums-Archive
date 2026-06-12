---
title: "does anyone have expertise with Ventoy persistence?"
date: 2024-01-16
forum: General Help
---

### Post by Gatorade on 2024-01-16
hi ,

I set up a multi boot USB stick with ventoy, and everything seems to be functioning correctly after playing around with it for a little bit.
I have dragged a few ISO images into the proper ventoy folder, and can run each one.

I have tested Ubuntu 20 , Ubuntu 22 , kali , Mint 21.2 ,  tails, and a couple others.

I have a problem with the persistence on all but linux mint.
none seems to be able to remember the wifi network and password after I reboot.

If there's anyone that has got this to work, could lend a hand please, it would be appreciated if you could tell me what I need to do to fix this.

I was following a youtube video when I set it up, so I was just copying and pasting the files as the video instructed.
please let me know what info I need to post to explain the situation better , if needed.

---

### Post by sudodus on 2024-01-16
**Multiboot USB drive**

It can be a good idea to have a Ventoy multiboot USB drive to run live sessions and installers. But I would *not* use it for persistent live systems, because you may run into conflicts because the same file system(s) and/or files might be used by more than one of the persistent live systems.

[hr][/hr]
**Live (live-only) operating systems**

I prefer to get (download) current iso files and clone them to an SSD connected via USB. (The content of a multiboot USB drive will soon get old ...) 

**Persistent live systems**

I use [mkusb](https://help.ubuntu.com/community/mkusb) to create a persistent live system of Ubuntu Desktop or Ubuntu family flavours (Kubuntu, Lubuntu ... Xubuntu).

---

### Post by VMC on 2024-01-16
**I** don't use Ventoy with Persistent. Mine's on an external ssd, that I drop ISO's into and boot to install.
You did read this?
[https://www.ventoy.net/en/plugin_persistence.html](https://www.ventoy.net/en/plugin_persistence.html)

---

### Post by Gatorade on 2024-01-16
> **VMC said:**
> **I** don't use Ventoy with Persistent. Mine's on an external ssd, that I drop ISO's into and boot to install.
You did read this?
[https://www.ventoy.net/en/plugin_persistence.html](https://www.ventoy.net/en/plugin_persistence.html)

I did see that, it was linked in the tutorial I was following, and I was using the OS's that were on the list.

---

### Post by Gatorade on 2024-01-16
ok, thx.

I will check that mkusb

---

### Post by sudodus on 2024-01-17
@Gatorade,

If you run your computer in UEFI mode with secure boot, and the computer and/or your UEFI/BIOS system is rather new, you may have problems with persistence by mkusb via 'dus-persistent', but it should work via 'dus-iso2usb' and via 'mkusb-plug'.

Good luck :-)

---

### Post by Gatorade on 2024-01-17
> **sudodus said:**
> @Gatorade,

If you run your computer in UEFI mode with secure boot, and the computer and/or your UEFI/BIOS system is rather new, you may have problems with persistence by mkusb via 'dus-persistent', but it should work via 'dus-iso2usb' and via 'mkusb-plug'.

Good luck :-)


I turned off the secure boot, it would not boot into the USB stick otherwise.
I will let you know if I run into problems with mkusb after I try it.

something did go wrong with my Ventoy USB build , possibly an error with the persistence I was messing around with.
I don't know what the problem is, but none of the OS will connect to the wifi now, whereas it was connecting perfectly before I played around with the persistence.

I think, I may just format the drive and start over again.

---

### Post by C.S.Cameron on 2024-01-18
I played with Ventoy about 5 years ago, it will make persistence files greater than 4GB, which have exFAT file system with "unlimited storage". Information on the persistence plugin is on this page: [https://www.ventoy.net/en/plugin_persistence.html](https://www.ventoy.net/en/plugin_persistence.html).
I recall it took me about a day to build.

I prefer Full-install multi-boot USB's myself  [https://askubuntu.com/a/1293548/43926](https://askubuntu.com/a/1293548/43926)

---

