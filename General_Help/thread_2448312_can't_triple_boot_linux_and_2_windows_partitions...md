---
title: "can't triple boot linux and 2 windows partitions..."
date: 2020-08-05
forum: General Help
---

### Post by Kris_M on 2020-08-05
Mint 20/ Ubuntu 20.4

I asked at mint as temp using that because of random copy/paste inconsistancies problem with ubuntu since 10.
alternately use 20.4

This is a deeper well.

Normally run ubuntu and win8.1 dual boot no prob.
If I add win10(bored!) before i boot ubuntu, i can access either windows partition/build no problem.
But first time through ubuntu(grub), it re-does the grub menu windows pointer from a pointer to a menu, to, a pointer to a build.
Thereafter, the other windows partition is inaccessible no matter what.

For testing I power off, power on, choose target, and boot, but though "windows boot manager" (when finally gotten to via F9 after error) will show both windows partitions, it will only boot to the one that I booted to first time I went through grub menu. ubuntu remains bootable and fine.

Method used for changing boot:
after installing win10, boot order in BIOS is "windows boot manager" first (as it should be) and subsequent boots to that work normal/as expected.
UNTIL
first boot to "ubuntu", which immediately says something like "lost boot order, rebuilding" and then boots straight to ubuntu.
subsequent boots to ubuntu show the normal grub menu:
  boot to ubuntu works fine.
  boot to windows will only get to first windows accessed via this  and any subsequent method. "windows boot mgr" now shows error and option F9 will show normal windows boot either of 2 choices, but only 1 works - the first one used. 

Would like to know how to set up grub so it will boot to both (individually) windows partition.

I was just thinking...maybe that's a Grub Customizer thing but the question would remain - how to access grub BEFORE it has 
a) recognized that there is a new win10 bootable partition, and yet,
b) not sensed that order is wrong and changed things.

I initially tried to re-install ubuntu after installing win10 but seemed to have bad boot problems (every other boot would hang in BIOS), but did not do that rigorously.

Thanks for your time and thoughts.

---

### Post by oldfred on 2020-08-05
Windows typically overwrites first install's boot files and updates BCD with entries for both Windows installs, so you can dual boot Windows.
But then there is only one UEFI boot entry for Windows.

And grub finds only one UEFI boot entry for Windows to boot.
(Assumes UEFI, but similar issue with BIOS).

You can only have one ESP - efi system partition per drive, but can have multiple FAT32 formatted partitions. And I believe some have moved boot/esp flags to second FAT32 and .efi boot files get updated into it. And then grub does not care whether ESP or not and can boot both Windows. You would have to manually edit BCD to only have each one, if desired.  And only have boot/esp flag on FAT32 with /EFI/ubuntu.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by dragonfly41 on 2020-08-05
Add rEFInd to the drinking well.

---

### Post by Kris_M on 2020-08-05
@dragonfly41 - how?

@oldfred - thanks!!! 
I am sitting on a clean build at the moment (clonezilla)(ubuntu and 8.1)
so I will assume what you want is a system after win10 has been added, so I will go do that, but NOT boot yet to ubuntu. and will enclose Boot repair info

by the by, on boot repair, it always askes me to get the latest version and when I tell it to it tells me again. I built my stick on 6-17-20.
Back in a few!

---

### Post by oldfred on 2020-08-05
Better to use Boot-Repair from your Ubuntu 20.04 live installer or from within your system (but may not do updates then).

My one system with Windows is only used to watch Comcast/Xfinity recordings from house at condo, had Windows 8, but I updated to Windows 10 as soon as it came out. Originally lots of issues even with Comcast. Firestick worked a lot better but could not do Comcast. Then condo updated to fiber to door and much better HD TV, so only use Windows occasionally. And Windows maintenance is a pain when you do not really know it. Somewhat like when I first converted from XP to Ubuntu. :)

---

### Post by dragonfly41 on 2020-08-05
I stumbled onto rEFInd [when reading some Mint forum threads]("https://forums.linuxmint.com/viewtopic.php?t=233332") .. [and here]("https://forums.linuxmint.com/search.php?keywords=refind") .. (although I am not a Mint user).
Strayed off the Grub piste, and learned a lot about UEFI jargon and now I have Windows 10 + Ubuntu on internal drive;
plus three variants of Ubuntu on external (USB) HDD, SDD, SDD .. all selectable through rEFInd menu. Chose custom theme.
I guess that this is classed as triple boot plus Windows 10.

---

### Post by Kris_M on 2020-08-05
@oldfred - note, I am UEFI/GPT Secure Boot is turned off (to allow booting from install win10 stick) but Bios set to UEFI only and CMS = no.

This is right after I installed win10 and booted back and forth between 8.1 and 10 a few times, but NOT ubuntu.

Now I can:
a) boot to ubuntu and then boot to win a few times to mess it up and then take another rescue boot info, OR
b) install Ubuntu and then do a) which will probably result in the same thing. 
Let me know.
waiting...

(sda5) is /Home

(pastebin link deleted)

[code]
DISKPART> list volume

Volume ### Ltr Label Fs Type Size Status Info
---------- --- ----------- ----- ---------- ------- --------- --------
Volume 0 M DVD-ROM 0 B No Media
Volume 1 D System Rese NTFS Partition 105 MB Healthy
Volume 2 C Win8 NTFS Partition 63 GB Healthy Boot
Volume 3 E E NTFS Partition 35 GB Healthy
Volume 4 F PHONES NTFS Partition 35 GB Healthy
Volume 5 G win10 NTFS Partition 68 GB Healthy
Volume 6 FAT32 Partition 331 MB Healthy System
Volume 7 RAW Partition 95 MB Healthy Hidden
Volume 8 RAW Partition 34 GB Healthy Hidden
Volume 9 RAW Partition 15 GB Healthy Hidden
Volume 10 RAW Partition 4999 MB Healthy Hidden

DISKPART>[\code]

gparted attached[URL="http://paste.ubuntu.com/p/RGvZPvxFr5/"]
[/URL]

---

### Post by pbear42 on 2020-08-05
> **Kris_M said:**
> @dragonfly41 - how?
[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)

I'd recommend putting on a USB flash drive first.  Boots like a live ISO, then drops you into a boot manager which should detect and enable you to boot all EFI OSs on the system.  Never used for your particular case, but keep one on hand for emergency boot of a regular dual install system.  Works for me.

If you like rEFInd and want to get rid of the dongle, you can install to the internal hard drive instead.  Available in repo or by PPA.

---

### Post by Kris_M on 2020-08-05
I stumbled into a solution.

[SIZE=4]**The trick is to NEVER use the entry in the bootup grub menu to boot to windows - IT WILL HOSE THINGS PERMANENTLY.**[/SIZE]

When I want to boot to either windows, interrupt boot/boot order (for me that's F12) and choose "windows boot manager" - it will present you with that "metro like" screen where I can chose either one, choose and off you go.

That is a minor inconvenience and since I rarely access windows, it is no problem. I will use daniel richter's grub customizer, or perhaps someone will show me an easy way to edit that grub menu and remove that line.

Thanks all!!!!!!!!!

:) !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by oldfred on 2020-08-05
Not sure if you have UEFI boot menu or Windows boot menu when it has more than one Windows.
But grub cannot modify either of those.
Typically grub will just have the one entry to chainload the Windows .efi boot file in the ESP.
Windows only has one set of boot files with two entries in its BCD which is not parsed from Linux.

---

### Post by Kris_M on 2020-08-06
> **oldfred said:**
> Not sure if you have UEFI boot menu or Windows boot menu when it has more than one Windows.
But grub cannot modify either of those.
Typically grub will just have the one entry to chainload the Windows .efi boot file in the ESP.
Windows only has one set of boot files with two entries in its BCD which is not parsed from Linux.

I would guess it is a windows 10 boot menu. Possibly a windows 8-or-10 boot menu. 
If I were to use that grub menu line, then I first get an error screen telling me there's a problem with the operating system I linked to - also I believe a product of windows 10 simply trying to have total control over the system.

As long as I DON'T use that grub menu line, all is well.

As to who does what, I can only guess.

many thanks for your time!!!!!!!!!

---

