---
title: "Dual Boot system without Grub menu?"
date: 2020-11-16
forum: General Help
---

### Post by Macamba on 2020-11-16
My computer is a dual boot, dual HD, AMD system that does not display a Grub menu. First things first my boot-repair result [https://paste.ubuntu.com/p/dRKN6Tnt5t/]("https://paste.ubuntu.com/p/dRKN6Tnt5t/").

My BIOS is now instructed to load EFI. My Windows 10 runs UEFI, and so does my Linux (obviously).

Boot repair advices is:
```
The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of
sdb4,
using the following options:        sdc2/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s  use-standard-efi-file  
```

Is that the way to go?

I do not know if this is the same error, but while booting I got the following error message:
```
Failed to Set MokListRT: Invalid Parameter
Could not create mokListRT: Invalid Parameter
Importing MOK states has failed: import_mok_state() failed: Invalid Parameter
Continuing boot since secure mode is disabled.
```

Looking [around]("https://itectec.com/ubuntu/ubuntu-ubuntu-20-04-failed-to-set-moklistrt-invallid-parameter/") I found the following solution:
```
sudo su -
cd /boot/efi/EFI/ubuntu
cp grubx64.efi shimx64.efi
reboot
```

I do not use a Mac, but a regular clone PC. Follow that (too)?

---

### Post by tea for one on 2020-11-16
Before we go any further, can you clarify whether both Windows 10 and Ubuntu boot successfully?

---

### Post by oldfred on 2020-11-16
Mok list is related to UEFI Secure Boot, so issue is only a warning.

Do not copy grubx64.efi to shimx64.efi.
Some are missing /boot/efi/EFI/ubuntu/MokManager.efi but usually missing from /EFI/Boot where booting fallback/drive entry not Ubuntu entry.
You typically cannot get to /boot/efi folder as mount permissions in fstab restricts access for security reasons.
Running Boot-Repair does also reset those permissions, so you can access ESP folder.
Originally Ubuntu allowed easy access to ESP with defaults, now 0077 or no permissions:

```
14.04 fstab entry defaults
UUID=FD76-E33D  /boot/efi       vfat    defaults        0       1
16.04 fstab entry umask=0077
UUID=68CD-3368  /boot/efi       vfat    umask=0077      0       1

```

---

### Post by Macamba on 2020-11-16
> **tea for one said:**
> Before we go any further, can you clarify whether both Windows 10 and Ubuntu boot successfully?

Yes. Both could be booted.

Edit:
FWIW: A sudo fdisk -l informed me that > The backup GPT table is corrupt, but the primary appears OK, so that will be used.

I would not know what disk has a corrupt GPT table. The Ubuntu disk?

---

### Post by tea for one on 2020-11-16
> **Macamba said:**
> Yes. Both could be booted.

Splendid - That is good news.

Therefore, is this a matter of grub menu not appearing and you have to boot each OS via UEFI boot menu?

---

### Post by Macamba on 2020-11-16
> **tea for one said:**
> Splendid - That is good news.

Therefore, is this a matter of grub menu not appearing and you have to boot each OS via UEFI boot menu?

I did not see an UEFI boot menu.

---

### Post by tea for one on 2020-11-16
How do you boot both systems without grub and without seeing a UEFI boot menu?

UEFI boot menu would contain Windows Boot Manager and Ubuntu Boot Manager (or sometimes identified by Vendor Disk Name i.e. Sandisk, Kingston etc)

---

### Post by Macamba on 2020-11-16
> **tea for one said:**
> How do you boot both systems without grub and without seeing a UEFI boot menu?

UEFI boot menu would contain Windows Boot Manager and Ubuntu Boot Manager (or sometimes identified by Vendor Disk Name i.e. Sandisk, Kingston etc)

I have a "one boot system only" at the moment. If I restore the MBR I can boot Windows. If I install from Live DVD I can run Ubuntu. Not an ideal situation.

How does an UEFI boot menu look like. Is it comparable with GRUB? Do you have a website I can look at, or is [GRUB2 & EFI recovery - Tutorial]("https://www.dedoimedo.com/computers/grub2-efi-recovery.html") a good one?

---

### Post by CelticWarrior on 2020-11-16
[https://ubuntuforums.org/showthread.php?t=2451612](https://ubuntuforums.org/showthread.php?t=2451612)

Please, not again...

> [COLOR=#000000]If I install from Live DVD I can run Ubuntu[/COLOR]
Yes, and if you boot and install in LEGACY/BIOS mode you'll be able to boot Ubuntu AND Windows.

---

### Post by tea for one on 2020-11-16
> **Macamba said:**
> I have a "one boot system only" at the moment. If I restore the MBR I can boot Windows. If I install from Live DVD I can run Ubuntu. Not an ideal situation.

How does an UEFI boot menu look like. Is it comparable with GRUB? Do you have a website I can look at, or is [GRUB2 & EFI recovery - Tutorial]("https://www.dedoimedo.com/computers/grub2-efi-recovery.html") a good one?

I do not understand [COLOR="#0000FF"]If I install from Live DVD I can run Ubuntu.[/COLOR] 
I thought that you had already installed both Ubuntu and Windows 10 in GPT and UEFI mode.

Anyway, when you power on your PC, do you see anything like this?

F2 to Enter Set up
F7 to Update UEFI/BIOS
F10 to Enter Boot Menu

Your equivalent of F10 is the UEFI Boot Menu, where you should be able to select a bootable disk.

---

### Post by Macamba on 2020-11-16
> **tea for one said:**
> I do not understand [COLOR="#0000FF"]If I install from Live DVD I can run Ubuntu.[/COLOR] 
I thought that you had already installed both Ubuntu and Windows 10 in GPT and UEFI mode.


The only way I can get Ubuntu started is by installing it from Live DVD. If I remember correct, the last installation even failed.

On the other question, yes, I indeed have a 
```
<F12> Boot menu
```
option, which leads to a Boot Menu with, among others a
[CODE\+ Hard Disk[/CODE]
which leads to
```
CH3 M.   : ST4000DM004
CH3 S.    : TOSHIBA DT01
```

Bunt when I choose the first one, expecting to boot Windows my machine hangs on "Verifying DMI Pool Data ....". 

@CelticWarrior: I tried that already, installed 18.04, but the installation program insists on UEFI.

---

### Post by CelticWarrior on 2020-11-16
It doesn't, it can't.

If you have UEFI with CSM enabled there will be TWO options for the same media, DVD or USB, one with "UEFI:..." in its name, the other without. Self-explanatory.
If you have UEFI only it'll boot in UEFI mode (but then the Legacy installed Windows won't boot).
If you have CSM only it boots and installs in Legacy mode.

Again, installing everything in UEFI mode in GPT drives is way easier to manage.

This is all there is.

Unless you understand once and for all that you need to be consistent, i.e., all OSes must be installed in the same mode otherwise the dual-boot can't work, and understand that you need to familiarize yourself with the requirements for the chosen mode and your own firmware settings this will easily turn into another 5+ pages thread, painfully dragged for another couple of weeks or more, leading nowhere and a waste of time for everybody involved.

---

### Post by tea for one on 2020-11-16
I'm trying to imagine the situation you have but it doesn't make much sense yet.

Please physically remove all drives except the disk where Windows 10 resides.

Does Windows 10 boot normally?

---

### Post by Macamba on 2020-11-17
> **Macamba said:**
> My computer is a dual boot, dual HD, AMD system that does not display a Grub menu. First things first my boot-repair result [https://paste.ubuntu.com/p/dRKN6Tnt5t/]("https://paste.ubuntu.com/p/dRKN6Tnt5t/").

[COLOR="#FF0000"]My BIOS is now instructed to load EFI. My Windows 10 runs UEFI, and so does my Linux (obviously)[/COLOR].

Are you thinking I am still working with a mixed mode UEFI/Legacy BIOS system? I stated in my original post (quoted above, with the relevant part [COLOR="#FF0000"]red[/COLOR]) that everything is working UEFI.

@CelticWarrior IF you mean with "UEFI with CSM": "UEFI with CSM" usually means mixed mode in which both native (UEFI) and CSM-based (BIOS) boot is available? No, that is not the case anymore (see the quote in this post).

@TeaForOne: That means some work, but I will check.

---

### Post by Macamba on 2020-11-17
> **tea for one said:**
> I'm trying to imagine the situation you have but it doesn't make much sense yet.

Please physically remove all drives except the disk where Windows 10 resides.

Does Windows 10 boot normally?

No.

On your request I disconnected the Linux HD and booted. It now hangs on the following error message:
> **Macamba said:**
> I do not know if this is the same error, but while booting I got the following error message:
```
Failed to Set MokListRT: Invalid Parameter
Could not create mokListRT: Invalid Parameter
Importing MOK states has failed: import_mok_state() failed: Invalid Parameter
Continuing boot since secure mode is disabled.
```

As I wanted to print, which is not possible under Linux, I booted the rescue DVD and used it to reset the MBR. Booting now ended on a GRUB prompt.

I see on [Aioboot]("https://www.aioboot.com/en/boot-windows-grub2/") I can use the following commands to boot, which I will try:
```
search -s root -f /EFI/Microsoft/Boot/BCD
chainloader /EFI/Microsoft/Boot/bootmgfw.efi
boot
```

Edit: I could boot Windows using these commands, only from DVD.

Edit 2: And I found out I can boot using the 'F12 Boot Menu' on my system. Sadly I am only able to boot Linux.

---

### Post by CelticWarrior on 2020-11-17
> (...) [COLOR=#000000]understand that you need to familiarize yourself with the requirements for the chosen mode and your own firmware settings (...)[/COLOR]

Windows strictly requires GPT partitioning for UEFI (and MBR for BIOS/Legacy). GPT partitioned drives still have a protective MBR so old non-GPT aware tools don't mess the drive.
The boot order is selected directly in the firmware (UEFI) from files existing in the EFI partition. Not by drives as it was before with BIOS, reading the respective MBRs.
> [COLOR=#000000]I booted the rescue DVD and used it to reset the MBR.[/COLOR]
This very likely blew it right then and there. We don't "reset the MBR" in UEFI mode.

Please understand that typically there's only one EFI partition, typically located at the beginning of the drive where the first OS (Windows in this case) has been installed, unless you explicitly made different provisions when installing.

As already explained to you in another thread, with BIOS and two drives for two different OSes, it makes sense to change the drive order to boot from the second drive (future Ubuntu) before installing Ubuntu to have Grub installed in that drive and leave the Windows bootloader in the first one intact. If anything happens to grub and/or Ubuntu you can still boot Windows directly by simply changing the boot order to the first drive. If using only one drive for both then obviously you won't be able to boot Windows directly in this scenario unless the Windows bootloader gets reinstalled replacing Grub (only one bootloader per MBR). In this case "reset the MBR" to Windows makes sense. NOT IN UEFI!

With UEFI you don't change the drives order. The boot drive must always be the one containing the EFI partition. Then, in a different setting (typìcally in the UEFI's Boot menu), you choose what to boot (many bootloaders can co-exist in the EFI partition).

---

### Post by oldfred on 2020-11-17
Run a new copy of the Boot-Repair summary report & post the link it gives.

---

### Post by Macamba on 2020-11-17
@CelticWarrior May bad. I will change the drive order of my machine in the BIOS to start with the Ubuntu disk. 

@OldFred Will the Boot-Repair summary report be different of the one I posted at the beginning of this [thread]("https://paste.ubuntu.com/p/dRKN6Tnt5t/")? I will connect the Ubuntu HD again and boot to it (after changing the drive order off course). and generate a new summary report.

Edit: Yes, the summary report is different. May bad again.

---

### Post by Macamba on 2020-11-17
The new Boot-Repair summary report can be found [here]("https://paste.ubuntu.com/p/jw4pm8Z5Pp/").

---

### Post by oldfred on 2020-11-17
Still confused.

You show grub in MBR of sda for BIOS boot and Windows boot loader in MBR of sdb for BIOS boot.
But all drives are gpt. Windows would only boot in UEFI mode if gpt.
You show no Windows UEFI boot entry, but do have Windows UEFI boot files in ESP, sdb2 for UEFI boot.

I would think if you attempt to boot in BIOS/CSM/Legacy mode then boot would fail/give errors.
Grub might boot Windows, since it only looks for the .efi boot files in the ESP, not UEFI boot entry.
But grub only boots working Windows, and Windows will do an update and then you can only boot from UEFI, but have no UEFI entry to do that.

It also looks like you did something recent to install a Windows BIOS boot loader to Windows drives. Not sure how, since Windows repairs on gpt drive should only be UEFI repairs.
They changed device order meaning you did not install to same SATA port when you removed & reinstalled drives.

First report showed only gpt drives. But Windows partitions look more like a BIOS install (no system reserved which Windows always has just before first NTFS partition with UEFI/gpt). Not sure then how you would have Windows boot files in ESP??

---

### Post by tea for one on 2020-11-17
> **Macamba said:**
> No.

On your request I disconnected the Linux HD and booted. It now hangs on the following error message:


As I wanted to print, which is not possible under Linux, I booted the rescue DVD and used it to reset the MBR. Booting now ended on a GRUB prompt.

I see on [Aioboot]("https://www.aioboot.com/en/boot-windows-grub2/") I can use the following commands to boot, which I will try:
```
search -s root -f /EFI/Microsoft/Boot/BCD
chainloader /EFI/Microsoft/Boot/bootmgfw.efi
boot
```

Edit: I could boot Windows using these commands, only from DVD.

Edit 2: And I found out I can boot using the 'F12 Boot Menu' on my system. Sadly I am only able to boot Linux.

If your Windows 10 fails to boot (having removed all other devices), then it is very unlikely that boot-repair will magically help you to boot both Windows 10 and Ubuntu.

Here are some suggestions (based on the knowledge that Ubuntu is more flexible than Windows):-

Forget about dual-booting for now.
Investigate why Windows fails to boot from your F12 menu
Fix Windows boot manager first
Use Windows user forums to help you
When Windows 10 boots [COLOR="#000080"]correctly[/COLOR] from one disk, then install Ubuntu on second disk with Windows disk [COLOR="#0000FF"]removed, isolated or de-activated[/COLOR].
Always use GPT and UEFI.
Don't forget backups.

---

### Post by Macamba on 2020-11-18
I will do that. I have to correct the "set MBR back" error and am hoping on feedback from Windows forums on that account.

Edit: This is no fun for me either. My system is down since the beginning of October, and I am actually considering buying a new system because I can not solve this problem. And might I say, a problem caused by the installation program of Ubuntu that decided to go for UEFI instead of keeping a running Legacy BIOS system going. And that is me being angry about one and a half month troubleshooting, and making errors along the way.

---

### Post by CelticWarrior on 2020-11-18
The first mistake was installing a modern Windows in Legacy/"BIOS" mode and MBR in a UEFI machine. This case scenario is absolutely NOT recommended by Microsoft, has ZERO advantages and a couple or more of disadvantages. But having done that then you have to be consistent and install Ubuntu in the same mode.

The second mistake therefore was installing Ubuntu in UEFI mode with Windows in Legacy. This derived from the user's choice at the external media boot time, as explained many times before.

The third mistake also stems from a fundamental misunderstanding about modes and partitioning when you tried to apply old BIOS-only concepts and troubleshooting to a new UEFI installation - the "detail" about "resetting the MBR" I commented about above. This probably led to the very unusual situation oldfred alluded to:
> [COLOR=#000000]Still confused.[/COLOR]

[COLOR=#000000]You show grub in MBR of sda for BIOS boot and Windows boot loader in MBR of sdb for BIOS boot.[/COLOR]
[COLOR=#000000]But all drives are gpt. Windows would only boot in UEFI mode if gpt.[/COLOR]
[COLOR=#000000]You show no Windows UEFI boot entry, but do have Windows UEFI boot files in ESP, sdb2 for UEFI boot.[/COLOR]


Knowing this please STOP blaming Ubuntu for wrong user choices pilling up on top of other wrong choices. A new machine won't solve the fundamental misunderstandings that persist in spite of a collective best effort in educating you about the different modes, requirements and consequences of your choices in the matter.   

Things to know:
[LIST]
[*]'sdb2' is your EFI partition; 'sdb' is your 1TB Toshiba drive and it must be the first in the drive boot order
[*]'sdb' must be connected to boot any installed OS irrespective of its location being in this same drive or other
[*]In UEFI and when multi-booting the drive order should remain unchanged but NOT the OS order; this - again - is a DIFFERENT setting
[*]In UEFI and when dual-booting Windows and Ubuntu you want to select "Ubuntu" (Grub) instead of "Windows bootloader manager" **while keeping the same drive at the top of the list** (both "Windows and "Ubuntu" are entries in the same and only EFI partition) because Grub can boot Ubuntu AND chainload the Windows bootloader to finally boot Windows if so desired, whereas the Windows bootloader only boots Windows
[*]You can at any time change the UEFI settings > Boot > OS boot back to "Windows" in order to boot Windows directly
[/LIST]
 
As oldfred correctly pointed out "y[COLOR=#000000]ou show no Windows UEFI boot entry" but it was there at some point, it must have been there. Windows still does lots of dumb things but not that. At some point you were able to at least boot Windows directly provide the aforementioned conditions were met (they are right after a successful Windows installation regardless of other partitions and/or OSes). the Windows (EFI) bootloader was likely gone after the already mentioned huge user mistake of messing with the "MBR", BCD and all.

And all of this is - should have been - so simple as disabling Secure Boot in UEFI, installing Windows in the chosen drive/partitions, assuring it boots correctly, install all the pending updates while rebooting (to Windows) as many times as needed then disabling Fast Startup in Windows. Then, and only then proceed with the Ubuntu installation that should be uneventful and should end up with changing the OS boot order to "Ubuntu" (whenever this is done automatically users do it manually in UEFI settings > Boot).  [/COLOR]

---

### Post by Macamba on 2020-11-18
> **CelticWarrior said:**
> The first mistake was installing a modern Windows in Legacy/"BIOS" mode and MBR in a UEFI machine. This case scenario is absolutely NOT recommended by Microsoft, has ZERO advantages and a couple or more of disadvantages. But having done that then you have to be consistent and install Ubuntu in the same mode.

The second mistake therefore was installing Ubuntu in UEFI mode with Windows in Legacy. This derived from the user's choice at the external media boot time, as explained many times before.

The third mistake also stems from a fundamental misunderstanding about modes and partitioning when you tried to apply old BIOS-only concepts and troubleshooting to a new UEFI installation - the "detail" about "resetting the MBR" I commented about above. This probably led to the very unusual situation oldfred alluded to:


Knowing this please STOP blaming Ubuntu for wrong user choices pilling up on top of other wrong choices. 

I bought this system in the UK. I had to install Windows on it. I did not made the conscious decision to "install [a] modern Windows in Legacy/"BIOS" mode and MBR in a UEFI machine".

Next I did not made the conscious decision to "install[] Ubuntu in UEFI mode with Windows in Legacy."

I take full responsibility for making the third mistake, as I wanted to get a running system back, and now see what consequences that has. Installation programs are meant to help uninformed users with installing systems. Most of the time this goes without problems. In my case not.

---

