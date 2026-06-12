---
title: "Booting from a USB HDD with Ubuntu already on it"
date: 2007-05-29
forum: General Help
---

### Post by XmaX on 2007-05-29
Hi,

Quite recently something went wrong on my laptop and since then it doesn't read the hard drive. I thought it was the hard drive issue, so I bought a new one. It appeared that it is not the case, meaning that motherboard's the problem. I don't have enough money to repair it at the moment, so I use the computer from Dapper LiveCD. As I have already Ubunty and Windows XP installed on my hard drive and I have a case to connect it via USB, I tried to run it this way, but it didn't work. I changed the boot order to make the USB go first, but still no effect.

And there is my question - do i need to change anything in the GRUB configuration to boot it?

---

### Post by XmaX on 2007-05-29
Anybody?

I just want to confirm that it is the problem with GRUB/Ubuntu installation/whatever on the external HDD, and not something in BIOS or a USB problem (which might well be the case). Anybody had a similar problem?

Also, can I install Feisty without swap and on FAT? If the above doesn't work, I might just install Feisty on the new USB HDD, but I might return it, so I want to make life easier in formatting it after I'm finished with Ubuntu. As I don't see the merging option in Gparted, I guess that's the only method :)

---

### Post by smoker on 2007-05-29
just a suggestion, did you disable other boot devices when you made usb priority, maybe usb is slow to respond and the bios is skipping it to look elsewhere for an os,

also, did you reinstall grub to point to usb partitions, rather than as internal partitions, as it would have been before?

if you have enough ram, i believe you can dispense with a swap partition, but i don't think you can install feisty to a fat partition, though maybe someone more knowledgable can advise more fully on that,

best of luck,

---

### Post by XmaX on 2007-05-30
I did disable other devices, wireless is off, LAN not connected, CD not inside and internal drive not connected. The only GRUB I've got is on the external drive, which was my internal drive when the computer was still working properly.

---

