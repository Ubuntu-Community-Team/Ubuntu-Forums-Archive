---
title: "Unable to boot after Windows 8.1 -&gt; 10 Upgrade"
date: 2016-01-21
forum: General Help
---

### Post by th1bill on 2016-01-21
Product Name: Pavillion 400-225
Operating System: Microsoft Windows 10 (64-bit) and Ubuntu 14.04 (64=bit)

Dual boot with 8.1 was not an issue but I allowed the, can I say, nice people of MS to update my 8.1 partition to 10 and bingo, vatta voom!  My half terra partition is till in place but there is not a chance in Hell I can boot into it.  Nor have I been able to boot the system from my Ubuntu 14.04 DVD no matter how I set the UEFI.  I really do not want to go back to BIOS by setting it to Classic.

 

Anyone, please, pick up your spears, bows, arrows and swords and help me defeat the MS dragon!

---

### Post by oldfred on 2016-01-22
Windows does turn its fast start up back on, you need to turn that off.
And Windows resets itself to be first in UEFI boot order.

But you have an HP, they only boot Windows, using description in UEFI, which is not per UEFI standard. So which work around did you do to enable booting Ubuntu. There are several and you need to redo one of the work arounds.
If dual booting generally best to copy shimx64.efi to bootx64.efi which is a fallback or hard drive boot entry and use the hard drive entry to boot Ubuntu.
Details in link in my signature and several others with UEFI HP systems.
       HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

    
Boot-Repair suggests the BCD edit in Windows. I believe that uses the one time reboot in UEFI. So you boot into Windows & in BCD choose Ubuntu and it will then let you reboot into Ubuntu.
 HP Envy 700-430QE desktop used bcdedit to dual boot
[http://ubuntuforums.org/showthread.php?t=2260681](http://ubuntuforums.org/showthread.php?t=2260681)

---

### Post by Nuno_Abreu on 2016-01-22
UEFI BIOS is a pain for dual-boot system - what I really recommend is to use the legacy BIOS, if possible.
Also, probably the boot record has been overwritten when the upgraded took place (something that Microsoft likes to do).

If you can, boot a live CD and go to the Terminal and type this out:
```
sudo grub-install --root-directory=<Directory where your OS is> --boot-directory=<directory where your boot partition is> /dev/sdX
```

Being X the device identifier from what you want to boot from.

Hope this helps.

---

### Post by oldfred on 2016-01-22
If you have an UEFI system and Windows in UEFI boot mode, you cannot boot Ubuntu in BIOS mode and be able to boot Windows from grub menu. You can dual boot from UEFI boot menu or one time boot key like f10 or f12. HP requires several keys to get to one time boot menu.

Generally best to have all systems installed in same boot mode. 
And UEFI is more complicated, just because it offers the old BIOS boot mode also. Which means more settings in UEFI to have correct for boot mode system is installed.

---

### Post by Nuno_Abreu on 2016-01-22
> **oldfred said:**
> If you have an UEFI system and Windows in UEFI boot mode, you cannot boot Ubuntu in BIOS mode and be able to boot Windows from grub menu. You can dual boot from UEFI boot menu or one time boot key like f10 or f12. HP requires several keys to get to one time boot menu.

Generally best to have all systems installed in same boot mode. 
And UEFI is more complicated, just because it offers the old BIOS boot mode also. Which means more settings in UEFI to have correct for boot mode system is installed.

Legacy BIOS is the best for this. The problem is most of the hard drives today are formatted in GPT, causing Ubuntu to install EFI data to a specific partition.
I always have used MBR, with the exception of when I bought my laptop with Windows (unfortunately) and unninstalled it afterwards - it was formatted in GPT and I immediately changed it to MBR because I knew everybody was having problems with it.

This conversion method might help:
[http://www.ehow.com/how_12119053_convert-gpt-mbr-linux.html](http://www.ehow.com/how_12119053_convert-gpt-mbr-linux.html)

---

### Post by oldfred on 2016-01-22
I have used gpt since about 10.10 as my Ubuntu boot drive. And all new or totally reformatted drives since then. No issues with gpt. You do have to have a bios_grub for BIOS boot or the ESP - efi system partition for UEFI boot. All new drives I partition in advance and have both, whether currently planning BIOS or UEFI boot as later I may change.

But if you have gpt Windows only boots in UEFI mode. 
And Windows only boots in BIOS mode from MBR. 
So issue usually is more Windows than gpt partitioning.

---

### Post by Nuno_Abreu on 2016-01-23
I'm not sure, but is it possible to merge Ubuntu's EFI partition with the Windows EFI one? That would save me a lot of time repartitioning on friends' computers, being all of their drives GPT formatted.

One thing is for sure though: the BIOS boot is certainly less problematic, but it's less secure - anyway, what should be secured is your OS and files (if you want some secrecy), encrypting them... Especially when we're talking about proprietary software, which most of the BIOSes and UEFI systems are.
I wish one day I could flash my BIOS ROM with Libreboot or something similar.

---

### Post by oldfred on 2016-01-23
You should only have one ESP - efi system partition per device. And Windows & Ubuntu can easily share one ESP.

Some do support multiple ESPs on one drive, but generally better to have one per device. And most systems just boot from the one.
With Ubuntu grub only installs to sda's ESP, even if you specify to install to sdb. I understand other distributions give a choice that works.

---

### Post by Nuno_Abreu on 2016-01-23
Probably that's automatically done if we choose the automatic partition option on the installer - I always have done my partitioning in the advanced tab and always created another EFI partition for Linux, which Grub recognizes when the **update-grub **trigger starts.

Now, how do you merge on the advanced partitioning? Do I specify the existing EFI Windows partition as /boot and I don't format it?

---

### Post by oldfred on 2016-01-23
The ESP is not a /boot partition and generally with desktops you do not need a /boot partition. With LVM you automatically do have an ESP, /boot and one physical partition for all the LVM logical partitions inside the LVM.
If installing in UEFI mode, grub will automatically create a new /ubuntu folder in an existing ESP on sda. And add a entry in fstab so updates go to that partition.
Only one partition on a drive can have boot flag which then makes the FAT32 formatted partition the ESP. If you try two boot flags, then system usually will not boot at all. 

As usual oldfred not paying attention. 
@Nuno_Abreu 
Did you just hijack OPs thread? If you have your own questions, they should be in a separate thread. This thread should be trying to help th1bill with his issues.

---

### Post by Nuno_Abreu on 2016-01-25
I see that I don't do the process right. Thank you for the precious information you gave me?

Do you mean hijacking as in asking pertinent questions about the subject? I know it is his own thread, but this is space for our needs and not a niche - I tried to help th1bill, still have no answers (probably he/she already solved it by checking our answers). But I will respect the forum rules - let's live in peace, ok?

---

### Post by oldfred on 2016-01-25
Its really that everyone's boot issue is different. Very few are identical. And only if a user can understand & apply general instructions, it can be difficult to post answers to specific issues on one system without confusing the issues on another.

So unless exactly the same issue or just responding or trying to help OP - original poster, better to start your own thread with your own more specific title. Also then when your issue is resolved, you can post [Solved] as only the OP can do that.

---

