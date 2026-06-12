---
title: "Will Not Start After Update"
date: 2023-04-19
forum: General Help
---

### Post by DeadlyOats on 2023-04-19
I did an update, yesterday night (18 Apr 23).  I'm not 100%, but I think I restarted the computer after that.  Today (19 Apr 23), I came home from work and found a message on the task  bar the littler circular arrows that mean that a system restart after update was required.  I restarted my computer.  Now, It won't start.

I power on, and it goes through some steps and then stops at this message:

[PHP][    1.204448] integrity: Couldn't parse dbx signatures: -74
[/PHP]

A flashing line is under the [ character at the beginning of the line.

If I hit the Enter key, immediately the word Kubuntu flashes on the screen as though starting or shutting down.  Then the computer turns off.  If I hit the power button, the whole thing repeats.

How do I fix this?

EDIT:

It's a black screen with all white text.  No colors.

---

### Post by MAFoElffen on 2023-04-20
Go into your UEFI BIOS and disable SecureBoot.

This will not help with some computers. With those the EFI checks the files within the EFI partition and thinks that some of them are not secure...

For those, boot from an Ubuntu 2.04.2 LiveUSB and post the results of:
```

sudo efibootmgr -v

```

---

### Post by DeadlyOats on 2023-04-20
[PHP]kubuntu@kubuntu:~$ sudo efibootmgr -v
BootCurrent: 0016
Timeout: 1 seconds
BootOrder: 0016,0015,0005,0003,0000,0001,0002,0004
Boot0000* Diskette Drive        BBS(Floppy,,0x0)
Boot0001* Internal HDD (IRRT)   BBS(HD,,0x0)SAMSUNG MZ7TD256HAFV-000L9      .
Boot0002* USB Storage Device    BBS(USB,,0x0)USB Storage Device.
Boot0003* CD/DVD/CD-RW Drive    BBS(CDROM,,0x0)P1: TSSTcorp DVD+/-RW TS-U633J.
Boot0004* Onboard NIC   BBS(Network,,0x0)IBA GE Slot 00C8 v1533.
Boot0005* ubuntu        HD(1,GPT,965a5526-f33f-4c42-b2f9-478a36891300,0x800,0xee000)/File(\EFI\ubuntu\shimx64.efi)
Boot0015  UEFI: INT13(RAID,0x80)        PciRoot(0x0)/Pci(0x1f,0x2)/VenHw(aa7ba38a-dabf-40c3-8d18-b55b39609ef7,8001000000005241494420202020ffffffffffffffffffffffffffffffffffffffffffffffff)/HD(1,GPT,965a5526-f33f-4c42-b2f9-478a36891300,0x800,0xee000)
Boot0016* UEFI: INT13(,0x81)    PciRoot(0x0)/Pci(0x19,0x0)/VenHw(aa7ba38a-dabf-40c3-8d18-b55b39609ef7,8101000000000000000000000000ffffffffffffffffffffffffffffffffffffffffffffffff)/HD(2,GPT,e7e777e5-ba64-4290-a759-837b96feb4ed,0x7023fc,0x2130)
kubuntu@kubuntu:~$[/PHP]

I used Ubuntu 22.04.1 USB installer, cause I don't have 22.04.2 USB installer.  Will that make a huge difference in the output?

Also, I couldn't find where to disable SecureBoot.  I'm using a Dell Latitude E6520 laptop.

---

### Post by MAFoElffen on 2023-04-20
No. That is not important nor will it make a difference with this.

Your computer was released in 2011, and did not support SecureBoot. Hmmm. 

Have you checked Dell Support to see if there is a newer BIOS available? I would first update the BIOS to what is the newest.

Then from a terminal session from the LiveUSB, do
```

sudo fwupdmgr update --force -y

```
Then reboot and test.

---

### Post by DeadlyOats on 2023-04-20
It seems that I already have the latest version of the BIOS for the laptop.  Ver. A22.

[PHP]kubuntu@kubuntu:~$ sudo fwupdmgr update --force -y
WARNING: UEFI capsule updates not available or enabled in firmware setup
  See https://github.com/fwupd/fwupd/wiki/PluginFlag:capsules-unsupported for more information.
Devices with no available firmware updates: 
 &#8226; MZ7TD256HAFV-000L9
No updatable devices
kubuntu@kubuntu:~$[/PHP]

Stand by as I reboot this computer.

EDIT:

I tried rebooting, but I ended up at the same message that I reported at the beginning of this thread.  Only the first numbers in the [ brackets ] are different.  1.****** .  Those digits change each time.  However, now I seem to have two Ubuntu boot choices instead of one.  I think they're identical, but there are two listed instead of one.

---

### Post by DeadlyOats on 2023-04-23
I gave up on this, and just did a clean install.  Installed, Kubuntu 22.04.2  (LTS).

---

