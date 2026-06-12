---
title: "Move GRUB from HD to SSD?"
date: 2022-10-09
forum: General Help
---

### Post by daanheuvelbeuk on 2022-10-09
Recently I acquired a new system which came with an SSD. I moved my Ubuntu hard drive to the new system, and installed Ubuntu fresh while keeping the data on the HD. I went left where I should have gone right so my GRUB menu is on the Ubuntu HD, and not on the SSD. Booting Linux is now a game of change. My system boots very fast on the SSD so I seldom am able to open the boot menu pressing F11 while booting (? sorry if I use the incorrect terms). And only then do I pass the GRUB menu (sigh).

You can find my current config on [Pastebin]("https://paste.ubuntu.com/p/ynVrtN8kMh/").

Booting Ubuntu is a problem. So **my question is, how do I move GRUB to my SSD**?

PS: grub-repair needs a Live CD session, and that is a problem as the SSD boots so fast I seldom am able to boot from USB.
PSS: I know I have a lot of partitions.
PSSS: grub-install (GRUB) 2.04-1ubuntu26.15

---

### Post by daanheuvelbeuk on 2022-10-09
I tried:
```
Daan@Alfheimr:~$ sudo grub-install /dev/nvme0n1
[sudo] password for Daan: 
Installing for x86_64-efi platform.
grub-install: error: cannot find EFI directory.

```
So no luck on that command

---

### Post by yancek on 2022-10-09
Your boot repair output shows you have an EFI partition and beginning at line 10 it shows both windows and Ubuntu EFI files necessary to boot both systems.  Beginning at line 22, it shows the second partition but does not indicate what is installed there.  Is this where you installed Ubuntu?  At line 99, it shows another EFI partition with only Ubuntu EFI files.  Beginning at line 115, it shows Ubuntu 20.04 installed on sdb3 and at line 131, it shows Ubuntu 22.04 installed on sdb5.  Which Ubuntu are you trying to boot?

Line 168 shows you were booted into 20.04 when you ran boot repair.  Lines 190-192 shows 3 EFI entries for Ubuntu when you should have only one.  Line 404 shows the UUID for sdb5 (22.04) in the grub.cfg file on the EFI partition on the SSD and line 354 shows that UUID is 22.04 on sdb5.  Line 410 shows the UUID  for sdb3 in the grub.cfg file on sdb drive.  Which drive is set to first boot priority?  If you are booting 20.04, I would think that sdb is set to first boot priority so change that to the SSD in the BIOS firmware.  If you do this, it should boot 22.04.  If you set it to the HD, it should boot 20.04.

Beginning at line 423, you see the contents of the /etc/fstab file for 20.04 on sdb3 which are all incorrect.  Run blkid command to get the correct UUID for each partition and change the entries on that file.

In your second post,, you indicate you ran grub-install and got an error.  Did your run that from the usb or one of the installed Ubuntu's?  You should not need to do that as you already have the Ubuntu EFI file on the SSD.

If you have problems accessing the BIOS or boot options, try tapping the F11 key earlier in the boot process, even before you see the logo.

---

### Post by oldfred on 2022-10-09
If booting real fast, then you may have the fast boot setting on in UEFI settings, that is different than fast start up in Windows. Fast boot assumes no system changes and immediately boots previous configuration.

What brand/model system. If HP or a few others, you can only change boot order in UEFI settings (not UEFI boot menu).

---

### Post by tea for one on 2022-10-09
Line 170 - OS#3:   Windows 7 on nvme0n1p3
Is that really Windows 7?
> My system boots very fast on the SSD so I seldom am able to open the boot menu pressing F11 while booting
Have a look in your UEFI Settings, there may be a user option to display the boot screen for a certain period (5 or 10 seconds or more).

---

### Post by dragonfly41 on 2022-10-10
> Have a look in your UEFI Settings, there may be a user option to display the boot screen for a certain period (5 or 10 seconds or more).

I have that option of delay in my rEFInd GUI installation in lieu of grub.

---

### Post by oldfred on 2022-10-10
Grub or rEFInd setting is separate & different from a UEFI setting. 

UEFI setting would control keys before system starts to boot.

Grub or rEFInd setting would be related to how long menu is shown.

---

