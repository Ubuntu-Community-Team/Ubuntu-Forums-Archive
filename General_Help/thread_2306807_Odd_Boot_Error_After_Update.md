---
title: "Odd Boot Error After Update"
date: 2015-12-19
forum: General Help
---

### Post by llanitedave on 2015-12-19
I'm running Ubuntu 15.10 on an Acer Aspire V3-772G-9460 Laptop.  It came with Windows 8.1, which I removed right away, and for about 2 years now I've had only Ubuntu on it.

It's always had boot issues.  I often have to reboot it two or three times to get it to take, and the errors cycled in a fairly predictable pattern.  When I finally got to the login screen, the screen would go black after three or four seconds, and I'd have to type the password blind.  However, once logged in it always operated with no complaints.  These problems persisted from 14.04 through 15.10.  I decided it was just a fundamental incompatibility with my particular hardware, and always just worked around it.

Now, however, I have a problem I can't work around.  A few days ago I did a standard downloaded update via the Software Updater.  When it was done, I rebooted the computer, and went through the standard chain of idiosyncratic messages, and used it as normal the rest of the day.  Next day, however, when I turned it on, I got a very odd error, and I can't get past it.

As soon as the laptop gets past its "Acer" brand display, I get a blue dialog box with the message "HDD2:  has been blocked by the current security policy."
The Ok button takes me to another blue box, which reads:
"Default Boot Device Missing or Boot Failed
Insert Recovery Media and Hit any Key
Then Select 'Boot Manager' to choose a new Boot Device or to Boot Recovery Media"

Unfortunately, the only recovery media I have here is the USB stick I installed from.  And it's a couple of versions behind, since the last upgrades I did were via the web.

I hit the Ok button there, and another screen appears, the "Boot Option Menu".  It gives me two choices:
1.  USB Entry for Windows To Go <No Device>
2.  HDD2:  <KINGSTON RBU-SMS100xxxxxxxxxxxxxGA>

Neither one of those gets me anywhere, it just cycles between those three screens.

When I use F2 while booting, and go to the Setup Utility, I get a list of Boot devices, and HDD2 is not among them.  In fact, the  Kingston RBU-SMS100xxxxxxxxxxxxxGA is identified in the Setup Utility as HDD0!

I did boot up with my installation stick, and downloaded and ran Boot Repair.  That claimed to have fixed some files, but it made no difference in my booting success.

If it's any help, I'm booting in UEFI mode, and secure boot, which is not deselectable on my system.  My system BIOS version  is V1.13.  I've tried disabling Fast Boot, but that made no difference either.

I suspect there's something corrupted in GRUB that's mis-identifying my hard drive, but I have no idea how to repair it.  I want to avoid a complete re-installation if I can, and I'm hoping somebody here can give me alternatives.

Ideas?

---

### Post by oldfred on 2015-12-19
Microsoft with Windows 8 systems required vendors to allow users to turn off UEFI secure boot. (Windows 7 down grade would not work with Secure boot). So somewhere in UEFI you have a UEFI secure boot setting, UEFI only setting and BIOS/CSM setting. Some combine the three choices into 2 that may not always seem logical.

All Acer we have seen require you to set a UEFI password (your setting may then show up) and set trust on the Ubuntu/grub efi boot files.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[URL="https://help.ubuntu.com/community/Boot-Info"]https://help.ubuntu.com/community/Boot-Info

[/URL]
 Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)

[URL="https://help.ubuntu.com/community/Boot-Info"]
[/URL]

---

### Post by llanitedave on 2015-12-19
Thank you kindly for that.  Here is my boot-info report:

[http://paste2.org/GOe2DnLj](http://paste2.org/GOe2DnLj)

I looked it over, and interestingly enough I saw no operating system for 15.10.  I don't think that's good.

There are a couple of NTFS partitions there, one from a spare hard drive I installed after it borked on me to see if the old system on it was still usable.  Other than all that, I'm not real sure about what I'm looking at.  I'll be checking over the other links you offered me shortly.  Thanks again!

---

### Post by oldfred on 2015-12-19
You show BIOS/MBR installs in sda and an UEFI install of 15.10 in sdb.
The grub in the MBR is booting the install in sda5, but you have another  BIOS install in sda8.

With multiple drives do not run any auto fix from Boot-Repair. That will install grub to the MBR of every drive. In advanced mode you can choose an install and which drive you want to install into. And you can use advanced total uninstall/reinstall of grub which sometimes fixes bigger issues. But make sure Internet is working as it has to download a new copy of the grub files.

UEFI and BIOS are not really compatible. You can only boot other installs from grub that are installed in the same boot mode. But from UEFI boot menu or one time boot key, often f10 or f12 you can choose which system to boot.

Grub normally only installs to an ESP - efi system partition in sda. To get grub to boot from other drives added parameters are required or the standard fallback entry of /EFI/Boot/bootx64.efi where bootx64.efi really is shim.

You may want to turn off UEFI - Secure Boot.

Windows only boots in BIOS mode from MBR(msdos) partitioned drives.

Often best once you start using UEFI to make all drives gpt partitioned and always boot in UEFI mode. But I had gpt partitioned drives for Ubuntu and my old XP with MBR booting in BIOS mode on old system. Best to decide how you want to boot and install in that mode. Either the 35 year old BIOS/MBR or newer UEFI/gpt.

---

### Post by llanitedave on 2015-12-21
So, I removed the spare hard drive and ran Boot-repair again.  It seemed to be a completely different application this time, and it gave me the option to purge Grub and reinstall it.  I had to run the utility a couple of times, as the first time failed.  The second time, it worked.  I can now boot as before.

Of course, booting as before also means that the screen blacks out just a few seconds after displaying the login, and I have to type in the password blind.

But at least I can get in now!  I'll mark this "solved".

---

