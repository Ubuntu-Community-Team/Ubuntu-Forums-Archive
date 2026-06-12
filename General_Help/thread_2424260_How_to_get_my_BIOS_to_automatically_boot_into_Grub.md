---
title: "How to get my BIOS to automatically boot into Grub."
date: 2019-08-05
forum: General Help
---

### Post by pickled-potato on 2019-08-05
On my HP Notebook 2000, the BIOS is set up to where Grub/Ubuntu doesn’t show up in the UEFI Boot Order. From what I’ve read HP has it set to where Windows has to be the OS that it automatically boots into. I was wondering if there is a way to override this. I’m dual booting Ubuntu and Windows. Currently I have to press esc when the laptop first turns on, then press f9, then select Ubuntu, to get it to grub.

Here is my BIOS info:
BIOS Version: F.3C
Vendor: Insyde

Here is my UEFI boot order:

Internal CD/DVD ROM Drive
USB Diskette on Key/USB Hard Disk
USB CD/ROM Drive
OS Boot Manager (Windows)
! Network Adapter
...................................................
Yes, I can place those options before Windows.

Any help is highly appreciated!

---

### Post by pickled-potato on 2019-08-05
I have marked this as solved because this should be under hardware.

---

### Post by QIII on 2019-08-05
It should be under General Help, where I have moved it.

Please do not mark threads as solved when they are not.  The solved tag should not lead others to a dead end.

Also, do not start duplicate threads.  If you believe your thread is in the wrong place, please click on "Report Post" and ask the Staff to move it.

---

### Post by pickled-potato on 2019-08-05
Sorry about that. I'm new to this forum.

---

### Post by oldfred on 2019-08-06
Some with HP have said new UEFI from HP allows it to work with ubuntu entry in UEFI. May not be available with older models. Using Description as part of boot as HP (& others) did is a violation of the UEFI standard. 
Is UEFI newest from HP for your system.

You may just need the recommended fix, but better if someone looks at it first. Sometimes it is not the best fix.
       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 
    
Work around for HP and similar systems that only boot "Windows Boot Manager" is to use the fall back or hard drive entry which is /EFI/Boot/bootx64.efi. Ubuntu/grub used to not install a new bootx64.efi which was normally just a copy of Windows .efi boot file. But now grub does install it. 
Old instructions had users manually copy shimx64.efi or use Boot-Repair to copy files to use hard drive boot entry.

Those not dual booting, could change Ubuntu UEFI description from "ubuntu" to "Windows Boot Manager" and then Ubuntu would boot. 
But when dual booting fallback is the only option.

---

### Post by pickled-potato on 2019-08-06
First of all thank you so much, this has been very helpful! In the link you included, under &#8220;Systems that only boot Windows from UEFI&#8221; you have the sections A, B, C, and D. I&#8217;m assuming these are different methods of getting Grub to automatically boot and not steps of one long process. Is that correct?

---

### Post by oldfred on 2019-08-06
Each is an alternative way to do the work around.
Boot-Repair now re-installs grub and grub now installs a /EFI/Boot/bootx64.efi which on many systems is a fallback or hard drive entry.

UEFI systems that follow UEFI standard should be able to boot any description in UEFI boot entries.
You can see the entries from Ubuntu's terminal with:
sudo efibootmgr -v

Many of the other work arounds are special cases or now older ways to manually do the fixes.

---

### Post by pickled-potato on 2019-08-06
Thank you so much! I was able to to get my bios to boot into grub automatically by using boot repair. Under advanced options I clicked "Backup and rename EFI files." You have no idea how much you have helped me!

---

### Post by oldfred on 2019-08-06
You are welcome. :)

---

