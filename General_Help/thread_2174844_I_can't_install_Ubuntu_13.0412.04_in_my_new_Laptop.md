---
title: "I can't install Ubuntu 13.04/12.04 in my new Laptop."
date: 2013-09-16
forum: General Help
---

### Post by jorge3 on 2013-09-16
Hello,


I just bought a new Acer Aspire V5-572g-5579 with windows 8 pre installed and i´m desperatly in the need of changing the operating system completly to Ubuntu. I have a 4 gb USB on which I used universal usb installer to install the iso from 13.04 version(I also tried installed the 12.04 but the same problem ocurred).  After I have installed the USB correctly I restart the computer pressing shift( which I saw was the way to do it on this webpage)and afterwards on the new menu I go on to troubleshoot, advanced optiones and then UEFI Firm ware settings. 
After I reboot the system and it acces the bios I disable the secure boot and chance the order of booting for the USB to be the first. Although, I have tried changing the  boot mode to legacy and I keep having the same problem. I read that the main problem between Linux and Windows is the secure boot. After I restart the PC, It opens the Ubuntu menu, which is not normally the screen you see(purple), but just a black screen on which you can try ubuntu, install or check your memory. Despite which one I choose, after clicking on them I get a black screen with a bunch of sentences formulating and then stops on "trying to unpack rootfs image as initramfs". After it goes on with a couple of more sentences the screen just goes black stays that way not ever booting or presenting anything else. So I have to restart the pc manually and try another thing.


Please let me know how can I fix this problem since I need to install Ubuntu.
Thanks. 
I download both ubuntu versions for 64 bit, just in case.
[IMG]http://tecnoubuntu.files.wordpress.com/2012/12/power-button-i.jpg[/IMG][IMG]http://tecnoubuntu.files.wordpress.com/2012/12/windows-8-safe-mode.png[/IMG]

[IMG]http://tecnoubuntu.files.wordpress.com/2012/12/windows-8-advanced-boot-option_thumb.jpg[/IMG]

---

### Post by oldfred on 2013-09-17
You need to turn off secure boot (although Ubuntu will install with it on), turn off fast boot (or hibernation) and if you have Intel SRT remove the RAID meta-data from hard drive & SSD.

See link in my signature for lots more info.

       Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)
Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)

---

### Post by SB21487 on 2013-12-14
I just recently installed Ubuntu 12.04.3 on my Acer-Aspire V5-572G however I added an additional 32GB mSATA drive for $39. Here is how I proceeded and it worked flawless:

1. Assuming you don't want any windows in dual boot, erase/format all your drives ( I did this with a by change to "legacy" mode in the BIOS and booting with a live CD)
2. In the BIOS make sure your in UEFI mode. I had to do this since I could not get the mSATA drive to be seen as the boot device in "legacy" mode.
3. Boot from live CD or USB, you should see:  [http://i.stack.imgur.com/rL6Jh.jpg](http://i.stack.imgur.com/rL6Jh.jpg)
4. If your using just the HDD then you can do a standard install and don't have to worry about partitions. For me I had to do the following:
[LIST]
[*]On the mSATA I have a UEFI partition that is 200Mb. This is necessary to actually boot the system.
[*]The boot loader should also be on the mSATA drive.
[*]I put the root ( / ) on the mSATA.
[*]2 GB of swap on the HDD
[*]/home on HDD
[/LIST]

This setup boots Ubuntu 12.04.3 with no problems and does so in about 11 seconds.

Major Issue:

I've had some additional issues with the Acer-Aspire V5-572G such as the backlight is turned off on startup I used this fix:

In /etc/default/ I edited grub file set to:GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"
GRUB_CMDLINE_LINUX="acipi_osi=Linux acpi_backlight=vendor"

However this fix disabled the Unity brightness indicator and has the wrong brightness level ranges.

Other thoughts:

The touchpad works fairly well except for I haven't figured out how to set the emulation of the middle button for the 1st clipboard paste.
It seems that all function keys work correctly.
Wireless adapter is having issues staying connected consistently, but it connects back right away.
No issues with installing bumblebee for the nvidia geforce 720m on this machine.
I've verified that intel turbo boost is working.
battery life is about 6 hours on lowest brightness and bumblebee/bbswitch active.

Hope this info helps,
SB

---

### Post by Gordonbp531 on 2013-12-15
You don't need to turn off Secure boot or SRT or remove the Raid metadata at all. 13.04 certainly will install and run perfectly well without doing all that.

---

### Post by oldfred on 2013-12-15
Each new update to Ubuntu has improvements and better support for UEFI.
Ubuntu has support for secure boot.

There is a bug on secure boot with Windows 8 booting from grub.
 Unable to chainload Windows 8 with Secure Boot enabled  Also post #11 on using refind
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464)
Windows will not chain load from grub -
file path: /ACPI(a0341d0,0)/PCI(2,1f)/UnknownMessaging(12)/HD(2,96800,32000,7c043777b8608641,87,f6)/File(\EFI\Microsoft\Boot)/File(bootmgfw.efi

---

