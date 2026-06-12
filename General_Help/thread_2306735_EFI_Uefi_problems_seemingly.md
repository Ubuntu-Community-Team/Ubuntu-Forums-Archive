---
title: "EFI Uefi problems seemingly"
date: 2015-12-18
forum: General Help
---

### Post by Craig_Lindgren on 2015-12-18
I just clean installed Linux 15.10 but there was 1MB at the beginning of the partition table that was utilized or in use, apparently something to do with UEFI or EFI. I have legacy support, for such things, enalbed in the bios, but the computer won't reboot, just blank screen, nothing seemingly.

I may have to format and re-install from scratch. Any help would be appreciated.

The Operating System was up and running once, but I tried to restart the machine, and it has failed.

Thanks,

Looks like we've either got Bill Gates as our Colonel or Linus Torvalds as our Colonel. 
I'd like to suggest, that there's one more Colonel, but only one, and that's the Government, or personal politics. The A.O.

They're hitting (Alt-F4). They're hitting (Alt-F10). I'm suggesting Alt-F6

it's fascinating. There are 10,000 questions, we'll address them one by one. 
I'ts a third computer, it's sorta like an IBM-compatible, sorta like a Mac, except a 3rd computer hardware.
"is caps-lock on or off, when the machine starts, or not"? for 1 question, 1 answer

back, the UEFI, EFI problem though, 
it's possibly a proprietary "IBM-compatible" that only accepts Windows
HP has thrown a UEFI EFI hardball and smashed Linux right in the face
but, who loses? the end user, the purchaser of the machine, myself, seemingly

It's an AMD proc, which means that it is decidedly an IBM-open source architecture compatible, not closed source

They should tread carefully at Law, they seem never to think of Law

Linux will install 99/100 on an IBM-compatible

Just wipe the harddrive clean and every byte is in use by Linux

I hope that somebody can help me with my (UEFI, EFI) problems

[URL="http://www.tumblr.com/blog/saltykryptonitetourist"]www.tumblr.com/blog/saltykryptonitetourist


[/URL]

---

### Post by Craig_Lindgren on 2015-12-18
I seemed to solved my own problem on this one.

I tried formatting and re-installing, however this time instead of 4 Primary partitions, I have employed 5 logical partitions (or 1 primary and 4 logical, that is). 

The 1st MB is still in use by, HP, I assume

I had to make a 100MB or thereabouts initial Primary partition for (EFI System Partition) sorta like a (Swap Area), as opposed to say Ext 4 Journalling Filing System

I wonder what this 1000MB is used for? it apparently is only using 33 MB or so

However, it seems to working

then the 4 logical partitions: root, /boot, /home, and (swap area)

I have turned back on Legacy Support which loads CSM (Compatibility Support Module) in Boot Options in the BIOS for older operating systems like Windows 7 and DOS

I don't know what the difference would necessarily be at this point, but it seems to maybe be working  better with the Legacy Support turned on

"When Legacy Support is enabled, BIOS will load Compatibility Support Module (CSM) to support Legacy OS such as Windows 7, Windows Vista, Windows XP & DOS. When Legacy Support is disabled, BIOS will boot in UEFI Mode without CSM to support newer OS such as Windows 8"...?

---

### Post by yancek on 2015-12-18
> I had to make a 100MB or thereabouts initial Primary partition for /EFI Boot Installation, or something

Using UEFI, you need this partition on which to install EFI files for any system you use.  When using EFI, you have different files and a different method of booting than was used with MBR booting.  The 1MB partition you mentioned is something that is used if you are using GPT without UEFI so if you use, EFI it isn't used.  If you have problems in the future, you could use the boot repair software to get detailed information on your system.  If you don't understand it, you can post the output here.  There is an option to "Create BootInfo Summary" which will give you detailed output which you can then post here and get some input or advice.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Craig_Lindgren on 2015-12-18
Thank you for the reply. I appreciate the input

What is GPT might I ask? btw

---

### Post by Craig_Lindgren on 2015-12-18
Here we have the Boot-Info Report at: [https://paste.ubuntu.com/14088037](https://paste.ubuntu.com/14088037)

(glade2script:9194):IBUS-Warning **:The owner of /home/ubuntu/.config/ibus/bus is not root!

If you can tell what the interpretation of that report is, it would be interesting to me.

---

### Post by grahammechanical on 2015-12-18
GPT = GUID Partition Table. It is part of the UEFI specification. UEFI = Unified Extensible Firmware Interface which replaces the BIOS = Basic Input Output System = software in an integrated circuit that tells the hardware what kind of machine it is every time the machine is switched on. 

With a BIOS firmware we also get MBR partitioning tables that only allow us 4 Primary partitions on each hard disk, This limitation can be bypassed by using one of the allocated primary 
partitions as a special primary partition called an Extended partition and in the extended partition we can have a large number of logical partitions.

The UEFI specification is an attempt to start again & do things better. With GPT we get any number of partitions. There are all primary. If we can still accurately use that term. There is no need for extended & logical partitions. GPT is backwards compatible with motherboards that have a BIOS boot system. So, it is possible to use Gparted to set a hard disk to have GPT as its partition table and not a MBR partition table. I have done this. But the other benefits/restrictions of UEFI are not available for BIOS motherboards.

Regards.

---

### Post by oldfred on 2015-12-18
Boot-Repair says this:
> [FONT=arial]The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.[/FONT]

You show grub installed both the the MBR for BIOS boot and to the ESP - efi system partition for UEFI boot. Only one should work. And grub will not install correctly in BIOS mode on gpt partitoned drives without another tiny 1 or 2MB unformatted partition with the bios_grub flag. But for UEFI you do not need the bios_grub flag.

It also said  Secure boot may be enabled. While Ubuntu will boot with secure boot on, you may need to try with it off. Some sysems just work better with it off for now.

You do not show an ubuntu entry in your UEFI boot menu.

Reboot Ubuntu installer in UEFI mode. You should in your UEFI have two boot options for flash drive. One is UEFI:flash drive name and the other flash drive name which is BIOS boot.

Then when in UEFI boot mode, you can add ubuntu entry to UEFI.

Is this an HP computer. They violate UEFI standard that specially says not to use description as part of UEFI boot. And of course only allowed description is "Windows". Since you are not dual booting you can just change the ubuntu entry to read Windows and it will work.

Run this before & after update just to confirm it worked.
sudo efibootmgr -v

This assumes the ESP is sda1, added parameters needed if not sda1. This makes grub's shim file for Secure boot have a Windows decription:
 
 **d1**:  If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

---

### Post by Craig_Lindgren on 2015-12-21
Thank you all

It is an HP computer
HP Pavilion 15 laptop Model: 15-p284ca
AMD processor A10
8GB memory

I am having one problem, that is I have to restart the computer entirely to re-locate the internet server through the router from time to time.

However, I'll have to go through these recommendations and implement them.

---

