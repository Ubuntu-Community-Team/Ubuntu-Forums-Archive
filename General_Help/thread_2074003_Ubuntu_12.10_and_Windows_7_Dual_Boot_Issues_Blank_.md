---
title: "Ubuntu 12.10 and Windows 7 Dual Boot Issues Blank screen"
date: 2012-10-20
forum: General Help
---

### Post by DarkAz on 2012-10-20
I'm having a similar issue. sudo os-prober detects both Windows 7 and Ubuntu 12.10 (64 and 32bits respectively), but on boot in shows a blinking cursor in the top right and stays there.

If I fix the MBR with lilo it boots back to Windows, and booting into Ubuntu LiveUSB and reinstalling GRUB repeats this cycle.

My fdisk -l:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   126035967    62914560    7  HPFS/NTFS/exFAT
/dev/sda3       161839104   976773167   407467032    7  HPFS/NTFS/exFAT
/dev/sda4       126038014   161839103    17900545    5  Extended
/dev/sda5       126038016   161839103    17900544   83  Linux

```

and my os-probe:
```
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda5:Ubuntu 12.10 (12.10):Ubuntu:linux

```

Also, one more tidbit: after my first try (the plan was to dualboot Windows 8 RTM and Ubuntu), I removed it completely figuring it was Windows' fault and installed only Ubuntu. Had the same issue, so I'm guessing it's something in GRUB?

---

### Post by oldfred on 2012-10-20
I moved you to a new thead. The old one was dual boot but he was missing Windows boot files. Yours is either grub or video issues.

Lets check & see if grub is installed ok. If you do get grub menu then it is not grub but a video issue.

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by DarkAz on 2012-10-21
> **oldfred said:**
> I moved you to a new thead. The old one was dual boot but he was missing Windows boot files. Yours is either grub or video issues.

Lets check & see if grub is installed ok. If you do get grub menu then it is not grub but a video issue.

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Out of real life, and back to the good stuff! 

So, [here's]("http://paste.ubuntu.com/1295734/") the link of Boot-Repair, I'm off to check if it did the trick.

EDIT:
And still the same. Remembered trying to press L-Shift, which shows a message (loading GRUB), which never loads.

---

### Post by oldfred on 2012-10-21
Did you run the Boot-Repair, it looks like you did.

But grub in MBR says it is looking for partition 72 and there is no core.img in your Ubuntu partition which usually when missing says grub is not installed correctly.

If you already ran the standard boot repair, then run the total uninstall and reinstall that it can run.
See the advanced options of purge before reinstalling. But make sure you have working Internet as once uninstalled you have to be able to download the new one.

---

### Post by DarkAz on 2012-10-21
Purge and reinstall successfull, going to try again.

[Here]("http://paste.ubuntu.com/1296132/")'s the new link.

EDIT:
And STILL nothing. Same exact thing, just a blinking cursor.

---

### Post by oldfred on 2012-10-21
What video card/chip do you have?

If not sure run this and see it works from liveCD.

lspci -nnk | grep -iA3 vga

---

### Post by DarkAz on 2012-10-21
The GPU is a Nvidia G105M.

---

### Post by oldfred on 2012-10-21
Is that one of the Optimus systems? Most seem to get it to work with one driver or the other, then may find bumblebee works.

Optimus
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)

---

### Post by DarkAz on 2012-10-22
No Optimus support, the laptop in question is a Clevo W76TUN, also known as the [Novatech X16]("http://www.hardwareheaven.com/reviews/887/pg1/novatech-x16-hd-pro-notebook-introduction.html") among others.

---

### Post by oldfred on 2012-10-22
Are you working from a current 12.10 disk to run updates?

 You are still showing grub2 1.99 in the MBR and 12.10 is using grub2 2.00. So it does not look like the grub is fully updated.

---

### Post by DarkAz on 2012-10-22
Downloaded the 12.10 iso from ubuntu.com after the announcement, and used UNiversal USB Installer to make a LiveUSB.

---

### Post by oldfred on 2012-10-23
Do not see how you can have grub2 1.99 still in MBR if Boot Repair did a full uninstall and reinstall. You should have grub2 2.00 in the MBR.

I thought this was what Boot-Repair did when you tick the options, but you should try the manual chroot and grub uninstall & reinstall.

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by YannBuntu on 2012-10-23
The installed system has GRUB 2.00, see at the bottom of the report:
```
grub-install (GRUB) 2.00-7ubuntu11,grub-install (GRUB) 2.

Reinstall the GRUB of sda5 into the MBR of sda
Installation finished. No error reported.
grub-install --recheck /dev/sda: exit code of grub-install /dev/sda:0
```

Below is a bug of BIS:
[https://sourceforge.net/apps/trac/bootinfoscript/ticket/13](https://sourceforge.net/apps/trac/bootinfoscript/ticket/13)

```
=> Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 72 for .
```
So i guess GRUB2.00 is correctly installed in the MBR.

**@DarkAz:** please run Boot-Repair --> Advanced options --> GRUB options tab --> tick the "Uncomment GFXMODE" option --> Apply
Tell us the new URL that will appear.
Reboot and tell us what you observe.

---

### Post by DarkAz on 2012-10-23
Tried the TOS (Tactical Orbital Strike) approach, AKA nuke the HDD e reinstall OS'(went with Windows 8 again if it makes any difference). Also downloaded a new ISO and remade the LiveUSB....

It still doesn't work. I'm off to try oldfred's and YannBuntu's suggestions, be right back.

EDIT:
Scratch that, both didn't do a thing. I shall call this the BCOD (Blinking Cursor Of Doom).
[http://paste.ubuntu.com/1300991/](http://paste.ubuntu.com/1300991/)

---

