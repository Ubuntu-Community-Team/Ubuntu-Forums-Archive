---
title: "Dual-boot Ubuntu (14.04.3) on a Windows 8.1 laptop?  Pretend I'm an idiot."
date: 2015-10-21
forum: General Help
---

### Post by t0p on 2015-10-21
[COLOR=#000000]I have a HP15-G261SA w/8.1, and I want to dual-boot Ubuntu. I have a Ubuntu 14.04.3LTS iso ready to rock and roll. My problem is finding easy-to-follow dual-boot instructions. Although I've been using Ubuntu for many years, I have next-to-no Windows know-how, and as soon as instructions start babbling Windows jargon I'm lost (I'm the man who still doesn't understand why you have to go to the "Start" menu to turn the machine off...). My last Ubuntu installation was on a laptop w/ Windows 7, which was sweet. But now this UEFI business has got me stumped.[/COLOR]

[COLOR=#000000]I've defragged Windows 8.1, I have created the Windows 8.1 recovery DVDs... and that's it. I read I should use the Windows partition tool to create the Linux partitions... but that's all she wrote. No info on how many partitions I can make, what [/COLOR][I]kind of partitions they should be... I'm scared I might screw the machine up, notwithstanding my recovery disks. I haven't got a lot of money, and I can't afford to kill the laptop.

[B]HP15-G261SA specs:
1TB HDD, 4GB RAM, [COLOR=#000000][FONT=Arial]quad-core AMD APU; DVD-RW drive, [/FONT][/COLOR][COLOR=#000000][FONT=Arial]USB 3.0 x 1, USB 2.0 x 2.

[SIZE=2]On a related note: if I decided to forget the Windows 8.1 on the laptop (I wouldn't use it v much anyway), and if I chose to install Ubuntu 14.04.3 on the entire disk, would that installation be as straightforward as it would be on a computer with BIOS? Or has UEFI changed everything?  Because, if necessary I will wipe the Windows off the machine and go for a Ubuntu-only install... if that's easier...?

Cheers!
t0p[/SIZE][/FONT][/COLOR][/B][/I]

---

### Post by tristan16 on 2015-10-21
First and foremost, did the laptop come pre-installed with Windows 8.1, and is the UEFI setting already turned on? If so, just make sure UEFI is turned on when you install Ubuntu. If you decide to get rid of Windows and install Ubuntu on the entire disk, you don't have to worry about UEFI, and you can just install like normal.

This information was taken from the Ubuntu wiki page: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

The main point is you have to install both OSes in the same mode. If one is installed in BIOS, so should the other. If one is installed in UEFI, so should the other. If Ubuntu is the only OS, you don't have to worry about it because there's no other OS to boot.

---

### Post by tristan16 on 2015-10-21
As far as your concerns about partitions, Linux plays very nicely with different formats. Extension 4 Journalling (ext4) is the default partition type for Linux, but it works just as well on NTFS, which is the Windows default. All you need for Linux is a partition to install it on, and a small partition for swap, which is usually at least the size of your RAM. Just make sure you select the right partitions when you're installing, and you should be good to go.

And as always, you should make a copy of **_*ALL*_** of your data just in case something goes wrong.

---

