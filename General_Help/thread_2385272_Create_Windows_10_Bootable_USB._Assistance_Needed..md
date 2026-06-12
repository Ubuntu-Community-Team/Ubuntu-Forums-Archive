---
title: "Create Windows 10 Bootable USB. Assistance Needed."
date: 2018-02-18
forum: General Help
---

### Post by alekstr on 2018-02-18
Hey im new to this forum and linux in general, but im now using ubuntu for a couple of days since i wont to achieve being fully open source, or at least, as close as possible by end of this year.

So im a big Age of Empires 3 fan and i tried installing Steam but it wont let me play AoE3 unfortunately. My idea was just to try to install Windows for dual boot just to see how it works with ubuntu for me but i got stuck here now.

What i did so far:

 - I downloaded windows10.iso from the official website (gonna use the "trail version")
 - I downloaded GParted (which i used to format my USB-stick to NTSF)
 - I downloaded WoeUSB (which i used to create a bootable windows 10 stick)
 - rebooted my system -> boot menu -> selected win10 usb -> followed instructions -> no NTSF partition available.

So i figure my next step would be to create a new partition but i dont know how this works.

Please correct me if have done anything wrong. I think i just need to create the new partition to install my bootable win usb.

looking forward to your answers!

---

### Post by oldfred on 2018-02-18
Is system UEFI or BIOS?
Did you install Ubuntu in UEFI or BIOS boot mode.
UEFI uses gpt normally and BIOS uses MBR.
Windows requires gpt for UEFI boot and requires MBR for BIOS boot.
And how you boot install media is then how it installs.
If your system is UEFI and came with Windows you have the product key in UEFI.
If you do not have product key you will have to purchase one within 30 days.

 Make Windows bootable installer from Ubuntu
[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)
[https://ubuntuforums.org/showthread.php?t=2328513&p=13557011#post13557011](https://ubuntuforums.org/showthread.php?t=2328513&p=13557011#post13557011)
[http://askubuntu.com/questions/289559/how-can-i-create-a-windows-bootable-usb-stick-using-ubuntu](http://askubuntu.com/questions/289559/how-can-i-create-a-windows-bootable-usb-stick-using-ubuntu)
 How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html)
[https://superuser.com/questions/676249/clean-install-of-windows-7-pro-64-bit-on-a-uefi-laptop-with-gpt-partition](https://superuser.com/questions/676249/clean-install-of-windows-7-pro-64-bit-on-a-uefi-laptop-with-gpt-partition)
You cannot use the Win7 DVD in UEFI mode, you need to use BIOS mode or modify to USB with UEFI. 

      
 Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[URL="http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c"]http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c

[/URL]
 BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations) 

[URL="http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c"]
[/URL]

---

### Post by alekstr on 2018-02-18
i dont know if its UEFI or BIOS im using a thinkpad x220 at the moment.

i was able to boot windows with the usb stick but i couldnt install it since no partition was available for it (not formatted right)

its ok for not having a product key its just to lern how to do it and play some AoE3 :P

thanks for the quick reply !

---

### Post by coffeecat on 2018-02-18
Closed for staff review.

---

### Post by coffeecat on 2018-02-19
After staff discussion, re-opened.

> **alekstr said:**
> its ok for not having a product key its just to lern how to do it and play some AoE3 :P


Please note that discussion about circumventing a EULA is not allowed here. From the forum [Code of Conduct]("https://ubuntuforums.org/misc.php?do=showrules"):

> We do not support circumventing TOS, EULA, etc here. 

It is not entirely clear what you are proposing to do in that quoted sentence. If your intention was to attempt to activate it without a legitimate key in order to install games software, that would be a contravention of the EULA, which we would be unable to support here.

---

### Post by kerry_s on 2018-02-28
> **coffeecat said:**
> After staff discussion, re-opened.



Please note that discussion about circumventing a EULA is not allowed here. From the forum [Code of Conduct]("https://ubuntuforums.org/misc.php?do=showrules"):



It is not entirely clear what you are proposing to do in that quoted sentence. If your intention was to attempt to activate it without a legitimate key in order to install games software, that would be a contravention of the EULA, which we would be unable to support here.

it's okay, it don't need a key. it's the trial version you join the windows program & run there tests, it gets upgraded & activated for free.
i used it when i helped my son build his gaming rig.
it totally legit, straight from microsoft.

i just looked in email trash, it's called "the windows insider program" you get emails like this:
[ATTACH=CONFIG]278713[/ATTACH]

theres more in the email, but you get the jest.

---

### Post by C.S.Cameron on 2018-02-28
Using a Linux tool on Windows is like using a metric wrench on an imperial bolt, 

sometimes it works.

Microsoft's Media Creation Tool works well for creating a Windows installer USB.

---

### Post by kerry_s on 2018-02-28
if i remember right, i just used dd to put windows.iso on the usb.

---

### Post by coffeecat on 2018-12-05
Closed to prevent more pointless necromancy.

---

