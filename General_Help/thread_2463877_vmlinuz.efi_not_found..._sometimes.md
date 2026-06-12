---
title: "vmlinuz.efi not found... sometimes"
date: 2021-06-20
forum: General Help
---

### Post by bradleypariah on 2021-06-20
About once out of every five times that I boot my PC, I get an error right after BIOS that says something to the effect of "Failed to execute; EFI\(a long string of characters)\vmlinuz.efi not found"
The system will not go forward from this message.
If I reboot (sometimes twice), the system just comes up.  Once it's up, it acts totally fine.  No read/write problems.  No slowness.  No lagging.  I game on it and watch movies.  Literally no issues.

I have been having this problem ever since I got a new  motherboard a few months ago.  Started on day one.  I should have returned it, but I thought I was going to be able to figure this problem out.  It's an MSI B-450 Max Gaming.  
I tried distro-hopping  between Kubuntu, Ubuntu, Neon, and Pop!_OS, both LTS and point releases, and  the problem happens with them all.  My current install is a little hodgepodge, but effectively it's Kubuntu 20.04.2 with backports.

I have an older GPU (gtx680), so I'm booting EFI with CSM.  I have a boot/efi partition, a slash partition, and swap space.

At the suggestion of the folks on the MSI forums, I did a memtest, and that yielded no errors.
According to the Disks program's SMART Data & Self-Tests, "Threshold not exceeded; Disk is OK."

I Googled "vmlinuz.efi not found," but everyone's discussions seem to revolve around not being able to boot an install disk.  I can't find a discussion that revolved around this happening intermittently on bare metal.

[ATTACH=CONFIG]288696[/ATTACH]

---

### Post by oldfred on 2021-06-20
I am using Kubuntu 20.04 and do not have vmlinuz.efi.

And have this in my notes as I loopmount ISO and have to have correct vmlinuz line.
vmlinuz.efi was used for Ubuntu 64bit from 14.04 to 17.10.
With 18.04 it is back to vmlinuz.

Or you should not even have nor see vmlinuz.efi anywhere.
Is this an upgrade from an old install? Or is it sometimes trying to boot an old installer?

Not sure this will show anything if it does boot at least sometimes.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

```
[FONT=monospace][COLOR=#54ff54]**fred@z97-focal-kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**/**[/COLOR][COLOR=#000000]$ sudo find . -type f -name "vmlinuz*" [/COLOR]
./boot/vmlinuz-5.4.0-74-generic 
./boot/vmlinuz-5.4.0-73-generic 
./boot/vmlinuz-5.4.0-45-generic
[/FONT]
```

---

### Post by bradleypariah on 2021-07-27
TL;DR - I think everything is working now.

Full story, in case anyone else runs into this:

> **oldfred said:**
> Is this an upgrade from an old install? Or is it sometimes trying to boot an old installer?

This was actually a brand new motherboard & CPU, but an SSD from the previous machine.  I installed Kubuntu 20.04 from scratch, but as I said, I tried distro-hopping when I experienced the issue.

Every time I installed my OS, I just formatted the /efi, /, and /home partitions, and reused them, because they were already the sizes I wanted.
Your question made me realize that I didn't see the specific vmlinuz error until after I had Pop!_OS on the system for a short while.
It dawned on me that maybe my /efi partition wasn't really getting wiped, even though I told the installer to format it each time.

> **oldfred said:**
> 
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.


I messed around with Boot Repair's live ISO, and it said it couldn't fix my problem.
Although not as elegant of a solution, because of your theory about the "old installer," I just made a backup of my /home directory, and reinstalled Kubuntu 20.04 with the "Guided: Use entire disk" option, as I knew this would force a full disk wipe and create a clean /efi.

My computer hasn't unexpectedly booted into BIOS in about a week, so I'm nearly positive that the issue is solved, which is a relief.  I was having serious buyer's remorse about my MSI motherboard, and for switching from Intel to AMD.  Looks like the hardware is fine after all.  
:guitar:

Thank you for your guidance.

---

