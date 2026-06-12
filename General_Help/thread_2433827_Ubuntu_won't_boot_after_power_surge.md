---
title: "Ubuntu won't boot after power surge"
date: 2019-12-26
forum: General Help
---

### Post by jdkcarlson on 2019-12-26
I have an Acer Aspire R5-471t with two partitions, one Windows 10 and very small and the other Ubuntu. My computer experienced a power surge and I had to replace the motherboard. Once I did this, Windows automatically loaded. I turned off Secure Boot, booted Ubuntu from a stick, ran boot-repair, added grub, shim, mok to my boot options, and now grub runs when my computer boots. I select the Ubuntu option, but it no longer boots. I get the following results:


[FONT=Courier New][Firmware Bug]: TSC_DEADLINE disabled due to Errata: please update microcode to version: 0xb2 (or later)
platform MSFT0101:00: failed to claim resources 1: (mem 0xfed40000-0xfed40fff)
acpi MSF0101:00: platform device creation failed: -16
Couldn't get size: 0x800000000000000e
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
CPU: 3 PID: 1 Comm: swapper/0 Not tainted 4.15.0-58-lowlatency #64-Ubuntu
Hardware name: Acer Aspire R5-471T/Luffy, BIOS V1.06 11/20/2015
Call Trace:
 dump_stack+0x63/0x8b
 panic+0xe5/0x244
 mount_block_root+0x1f6/0x2da
 ? set_debug_rodata+0x17/0x17
 mount_root+038/0x3a
 prepare_namespace+0x139/0x18e
 kernel_init_freeable+0x2222/0x24f
 ? rest_init+0xd0/0xd0
 kernel_init+0xe/0x110
 ret_from_fork+0x35/0x40
Kernel Offset: 0x21400000 from 0xffffffff81000000 (relocation range: 0xffffffff80000000-0xffffffffbfffffff)
---[ end Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
[/FONT]
What should I do?

I'm linking the textfile boot-repair produced as well, in case it helps:

[http://paste.ubuntu.com/p/Y272v8FYN7/]("http://paste.ubuntu.com/p/Y272v8FYN7/")

---

### Post by jdkcarlson on 2019-12-27
Update: I have updated the BIOS to version 1.07 from Acer's website but aside from having to reconfigure the boot order again, everything seems the same. The errors are as far as I can tell identical.

---

### Post by CatKiller on 2019-12-27
Have you tried a fsck on your Ubuntu partition?

---

### Post by jdkcarlson on 2019-12-27
Not yet. Load Ubuntu through the stick and run fsck on the sda7 or whatever it is?

---

### Post by CatKiller on 2019-12-27
> **jdkcarlson said:**
> Not yet. Load Ubuntu through the stick and run fsck on the sda7 or whatever it is?

Yep. You can't do so while it's mounted, so it has to be done from the live installer or as part of the boot process.

---

### Post by jdkcarlson on 2019-12-27
Thank you! The result is the following:

> ubuntu@ubuntu:~$ sudo fsck -n /dev/sda7
fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
/dev/sda7: clean, 240957/28000256 files, 35346688/111997184 blocks

It was almost instantaneous.

---

### Post by oldfred on 2019-12-27
Your list of bootable devices shows unknown. See line 956.

You can see that yourself from live installer:
sudo efibootmgr -v

And the two unknown are the Ubuntu grub & shim entries. They should say ubuntu or with Acer whatever you actually name it as you have to enable the entries with 'trust'. 

These are all essentially the same:
       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust, shows typical screens for all Acer
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)

---

### Post by jdkcarlson on 2019-12-27
Thank you oldfred,

I ran the efibootmgr -v command as you suggested, for sport, but don't know enough to interpret the output.

The suggestions in the links seem to be roughly what I did before my initial post to this thread (I believe I learned them from links you yourself posted on this forum in the past):

* Secure boot was enabled.
* I set a password.
* I navigated through "Select an UEFI file as trusted for executing: HDD0 > EFI > ubuntu > [each of grubx64.efi, shimx64.efi, mmx64.efi, fwupx64.efi, in order]"
* One has to name them something, and I respectively chose the names "grub", "shim", "mok", and "fwup".
* I saved changes and rebooted, holding F2 to get back to the setup utility.
* I changed the order under "Boot" to prioritize, in order, grub, shim, mok, fwup, USB HDD, Windows Boot Manager
* I disabled Secure Boot and unset the supervisor security password
* I saved changes and restarted.

grub does boot first, but selecting *Ubuntu leads to the series of errors in my inital post, including the firmware bug and kernel panic.

---

### Post by oldfred on 2019-12-27
Is this the most current UEFI/BIOS?

>         Hardware name: Acer Aspire R5-471T/Luffy, BIOS V1.06 11/20/2015 
    
This shows many newer versions:
[https://www.acer.com/ac/en/US/content/support-product/6397](https://www.acer.com/ac/en/US/content/support-product/6397)

[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)

---

### Post by jdkcarlson on 2019-12-28
I'm very sorry, the email didn't seem to notify me about this response. This is a newer version than the one that came with the motherboard, but not the newest version. I initially thought each was a separate tweak rather than a whole version overwriting all others and I found reports of people with errors from upgrading their BIOS, so I was hesitant to try it again. You think I should upgrade to the newest version though?

---

### Post by jdkcarlson on 2019-12-28
I've installed bios version 1.14 and reset the boot order and trusted objects. The first error messages when I attempt to boot Ubuntu are now

"platform MSFT0101:00: failed to claim resource 1: [mem <numbers>]
platform MSFT0101:00: platform device creation failed: -16"

followed by "couldn't get size" and a kernel panic. 

The list of error messages is much longer this time. Let me know if I can/should take a photo or transcribe this, as I don't seem to know how to write it to a text file directly.

---

### Post by oldfred on 2019-12-28
While there have been reports of users having errors with BIOS updates, those are rare. I think mostly from power failure in the middle of an update. Many sure system plugged in or battery not low.

Both Windows & Linux have updated kernels & drivers you need UEFI updates.
       Almost all systems need UEFI updates, anyway, for mitigation of Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching.

---

### Post by jdkcarlson on 2019-12-28
OK, I think the BIOS is at the lastest. Did you see the newest error messages? I'm running fsck again off a stick now for lack of better ideas.

---

### Post by oldfred on 2019-12-28
Did you update other settings that a new install needs. New motherboard would have all the defaults.

       Newer Acer -  CTRL S on the main Tab in BIOS to get the option to change SATA to AHCI 
      
 Acer Aspire A315-53-386P remove RAID from drive
[https://askubuntu.com/questions/1167506/the-installation-window-dont-show-a-root-file-system-for-choose-in-the-installa](https://askubuntu.com/questions/1167506/the-installation-window-dont-show-a-root-file-system-for-choose-in-the-installa) 
    
I would also turn UEFI Secure Boot back off.

Not sure then if another boot parameter is needed or not. Most Acer models seem to then work once trust is set.

---

### Post by jdkcarlson on 2019-12-28
Thank you again oldfred, I don't know what else a new install typically needs. In the past the steps I've already done sufficed, but that was with the previous motherboard.

I went into BIOS and ctrl+S didn't do anything, but it said that AHCI was already on in the relevant place, so I don't think I needed to change that.

I tried booting from a stick and following the solution to the askubuntu question you posted, but it told me the relevant thing (/dev/sda7 on mine) is not a raid disk. Erasing the additional parameter in `sudo dmraid -Er` told me I had no RAID drives.

I automatically turn Secure Boot off as it has hung me up/left me access to only the Windows partition in the past.

What are my options now? Is there any information I could transcribe and report back?

---

### Post by oldfred on 2019-12-28
About all I can now suggest is that a boot parameter may work.
Have not seen many Acer needing boot parameters. I try to save links to common issues by brand.

Do you have a NVNe drive?
       Acer Aspire 7 A715-71G NVE not seen Boot parameter: nvme_core.default_ps_max_latency_us=200 
[https://ubuntuforums.org/showthread.php?t=2429323](https://ubuntuforums.org/showthread.php?t=2429323)

---

### Post by jdkcarlson on 2019-12-29
Hi oldfred, it's a Sandisk X400 M.2 2280 512GB

I don't know if that means it's NVNe or not. However, it's the same hard drive as I had before the motherboard replacement. I'll try adding the code anyway on the grounds that it can't load Ubuntu less than it is already doing.

---

### Post by jdkcarlson on 2019-12-29
I've tried. It didn't change anything; however, it's possible I did it wrong. I'll attach a screenshot and say what I did.

[IMG]https://pasteboard.co/INs3zb2.jpg[/IMG]
[https://pasteboard.co/INs3zb2.jpg](https://pasteboard.co/INs3zb2.jpg)

I navigated there by hitting "e" when grub appeared.

Then after the "quiet splash" in the last line I added your incantation "nvme_core.default_ps_max_latency_us=200" (without quotes) and a space before the "$vt_handoff", which I retained. Then I hit F10 and got the same errors as before: failed to claim resource 1, and platform device creation failed.

Would reinstalling Ubuntu help? I'm seriously confused what's happening here.

---

### Post by oldfred on 2019-12-29
If you are getting grub menu that is a lot of the boot process where errors occur.
Most then are video related.

You show low latency kernel.
I might reinstall with standard Ubuntu and then if you really need low latency kernel add that later.
Some have reinstalled & then it works. Never sure what issue was then.

---

