---
title: "Can't start up after boot repair"
date: 2013-01-09
forum: General Help
---

### Post by marksch on 2013-01-09
Hi,

I have a problem similar to [http://ubuntuforums.org/showthread.php?t=2023086](http://ubuntuforums.org/showthread.php?t=2023086)

I have bought a new Acer laptop with UEFI support and Windows 8 pre-installed. After installing Ubuntu 12.10, I was able to start up, but I couldn't start Windows 8 anymore. I followed the [instructions described here](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system#_=_) and ran Boot Repair. The result was that I was completely unable to start my laptop. I got the following error: "file '/grub/i386-pc/normal.mod' not found". 

At the end of the procedure, Boot Repair displayed the message: "Please do not forget to make your BIOS boot on sda2/EFI/ubuntu/grubx64.efi file!" as you can read at [http://paste.ubuntu.com/1494353](http://paste.ubuntu.com/1494353). I don't understand how to do this. Any help would be greatly appreciated.

I have now re-installed Ubuntu. The original Windows 8 partition is still on my hard disk. I can now start Ubuntu again, but I still can't use Windows 8. Please help.

Kind regards,

Mark

---

### Post by YannBuntu on 2013-01-10
Hi
> **marksch said:**
>  [http://paste.ubuntu.com/1494353](http://paste.ubuntu.com/1494353). 

You used Boot-Repair from your installed Ubuntu, which had been installed in Legacy mode. This can cause problem when B-R needs to install grub-efi.

Please use Boot-Repair from live session (liveCD or liveUSB), click Recommended Repair, and tell us the new URL that will appear. Then reboot and tell us what you observe.

---

### Post by marksch on 2013-01-10
HI,

Thanks for your reply. Now I get to see the GRUB menu with options like:
Ubuntu
Adavanced options
Memory test
Memory test (serial)
Windows UEFI bootmgfw.efi
Windows Boot UEFI loader
EFI/OEM/Boot/bootmgfw.efi
efi/EFI/Microsoft/Boot/bootmgfw.efi
efi/EFI/Boot/bootx64.efi

If I choose any of the last 5 options, I get either "incorrect signature" or "file not found".

The new Pastebin url is
[http://paste.ubuntu.com/1516618](http://paste.ubuntu.com/1516618)

I can still start the Ubuntu install, fortunately.

What should I do next?

Kind regards,

Mark

---

### Post by marksch on 2013-01-11
Does anyone have an idea what to do next? I'm dead in the water now.

Mark

---

### Post by YannBuntu on 2013-01-12
hi Mark
> **marksch said:**
> I can still start the Ubuntu install, fortunately.

What should I do next?

Please boot your installed Ubuntu (not your disc), open a terminal and tell me the output of :
```
[ -d /sys/firmware/efi ] && echo EFI || echo Legacy
```

---

### Post by marksch on 2013-01-12
Hi Yann,

Thanks for the reply. I've entered the terminal command and all I got was "Legacy". Did I do something wrong?

You can see a screenshot of the terminal window at [http://qery.us/3dk](http://qery.us/3dk) .

Kind regards,

Mark

---

### Post by YannBuntu on 2013-01-12
ok.
Currently, your BIOS is set up to boot both the HDD and the CD/USB disks in Legacy mode.

However, your Windows is installed in UEFI mode only.

So you need to :
1) set up your BIOS to boot the HDD and the CD/USB disks in UEFI mode. See [https://help.ubuntu.com/community/UEFI#Set_up_the_BIOS_in_EFI_or_Legacy_mode](https://help.ubuntu.com/community/UEFI#Set_up_the_BIOS_in_EFI_or_Legacy_mode)
2) then run Boot-Repair's Recommended Repair from a CD/USB disc

---

### Post by marksch on 2013-01-12
Hi Yann,

I can't do this as it is described in that link. If I set the Boot Mode to UEFI, the secure boot is enabled automatically. However... if I start up the computer in UEFI mode, I get to Windows 8 now and if I start up in Legacy mode, I get to see Ubuntu. At least, I have access to both OS's now. 

When I go to the BIOS and switch from UEFI to Legacy, I see a comment in the right side panel, saying that I could choose Dual Mode, but when I press enter to see the sub menu of the Boot Mode, I see Legacy and UEFI only. 

Would it be possible to fix something and get the GRUB menu while booting in UEFI mode and let me choose either Windows 8 or Ubuntu?

Please note that there is no way for me to start up a Linux in UEFI mode and I can't run the boot repair utility without Linux.

Kind regards,

Mark

---

### Post by oldfred on 2013-01-12
Part of the Microsoft specification is that the USER be able to turn secure boot off. So their has to be a way. 
Some UEFI just have a on or off. Some have a setting to turn UEFI on, which means turn off secure boot, and then another setting for legacy boot. But every vendor seems to be different.

Another Acer:
       Acer V5-571P-6815 secure boot off worked
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)

    
Both systems have to be legacy or UEFI as each reports system info differently to the operating system for Booting.

---

### Post by YannBuntu on 2013-01-12
> **marksch said:**
> If I set the Boot Mode to UEFI, the secure boot is enabled automatically. 

ok.
Please set the Boot Mode to UEFI, then run Boot-Repair's Recommended Repair from a CD/USB disc, and tell us the new URL that will appear.
Then reboot the pc, and look into the "Boot Mode" screen of the BIOS, there should be an "Ubuntu" entry. Please select it and tell us what you observe.

---

