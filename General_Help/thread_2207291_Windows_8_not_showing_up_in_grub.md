---
title: "Windows 8 not showing up in grub?"
date: 2014-02-22
forum: General Help
---

### Post by Alex_McNurlin on 2014-02-22
Ok so a couple of days ago I got a brand new lenovo y510p with windows 8.1 pre-installed. Since then I have been struggling to get Ubuntu (12.04 lts) to dual boot. I've done a bunch of different things to get the dual boot to work and here's where I'm at right now: When I turn on the computer it will boot into whatever os I used last. To change operating system, I have to set the bios to use "ubuntu" or "windows boot manager" as the first priority. (i used to have to switch to legacy mode, but now it is all under uefi) 
When I choose ubuntu, grub loads and gives me 7 options:
[LIST]
[*] Ubuntu, with Linux 3.11.0-15generic
[*]Ubuntu, with Linux 3.11.0-15generic (recovery mode)
[*]Windowf UEFI recovery bootmgfw.efi
[*]Windows Boot UEFI recovery
[*]Windows UEFI recovery LrsBootmgr.efi
[*]Windows Boot UEFI recovery bkpbootx64.efi
[*]System setup
[/LIST]
Should there be a Windows option that doesn't say recovery? The last thing I did was run boot-repair (paste.ubuntu.com/6977362), and that's what got me here. Before that there was a non-recovery windows option, but it gave me some error message when I used it. 

Additional, probably irrelevant, info: When I set the bios to legacy mode, I get a grub command line. 
I can run either Ubuntu or Windows 8 without any problems but its switching from one to the other that is hard. 
I ran boot repair earlier in this whole process and the paste thingy was paste.ubuntu.com/6973048
I'm not too experienced with linux but I did install ubuntu on a different laptop rather painlessly. Windows 8 is just a pain in the *** with dual booting

Any help would be appreciated and thanks in advance!

---

### Post by oldfred on 2014-02-23
Some systems do not report partition type correctly and they often will say recovery when they are not. 

If you originally installed Ubuntu in BIOS mode, then you may have grub in protective MBR to boot in BIOS. But if converted to UEFI boot, by Boot-Repair, then the BIOS boot grub will not work.

Best to see details:
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

If you just need to change descriptions, I have instructions on housecleaning or editing 25_custom in link in my signature. The 25_custom is all of the new boot stanzas that Boot-Repair adds.

---

