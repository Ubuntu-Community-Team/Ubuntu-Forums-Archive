---
title: "Acer Aspire Switch 10 can't boot 14.04 LTS"
date: 2014-07-13
forum: General Help
---

### Post by claire3 on 2014-07-13
Brand-new Acer Switch 10, can't get Ubuntu to boot. I've done the following:

* Disabled secure boot
* Added boot EFI for both Bootx64.efi and grubx64.efi to the EFI bootloader settings
* Tried several USB drives on both the microUSB and USB ports on the device

I cannot get the machine to boot anything other than Windows.

---

### Post by Bucky Ball on 2014-07-13
*Post moved to own thread.*

---

### Post by yancek on 2014-07-13
I'm not familiar with uefi so I doubt I will be able to help with that but, just to clarify, have you installed Ubuntu and are not able to boot it?  or are you unable to boot from the installation medium, the flash drive?

---

### Post by claire3 on 2014-07-13
I can't boot off the installation flash drive. Tried using Rufus and formatting with GPT for UEFI, no dice.

---

### Post by yancek on 2014-07-13
What software did you use to create the bootable flash drive?
Have your tried booting the flash on another computer to see if it works?
What have you tried formatting, I'm not clear about that?
Do you have an option in the BIOS to disable 'Fastboot' which deals with w8 hibernation?

---

### Post by claire3 on 2014-07-14
We have made progress! After successfully booting a GParted LiveUSB (with secure boot turned off, since unlike 64-bit Ubuntu, GParted and even 32-bit Ubuntu kernels are not digitally signed by Microsoft), we were able to dig into things and determine that this device only supports 32-bit UEFI bootloaders. This is a tablet with an Intel Atom CPU, and it ships with 32-bit Windows 8.1 (even though the processor is actually 64-bit). Some other research came up with an article on getting Ubuntu on a somewhat similar device - the ASUS Transformer T100TA, which has the same CPU as this tablet.

Link to article for T100TA and Ubuntu is here: [http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/](http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/)

We were able to install Ubuntu successfully, but it does not boot. Next step is to get boot working. We can get it to boot into Grub by enabling Secure Boot in the Acer UEFI and trusting /HDD1/Ubuntu/bootia32.efi, but so far we have to manually direct Grub to boot using the following:
```
linux (hd1,gpt2)/boot/vmlinuz-3.13-xxxx root=/dev/mmcblk0p2 video=VGA-1:1366x768e reboot=pci,force
initrd (hd1,gpt2)/boot/initrd-3.13-xxxx
boot
```

Also worth noting that we may have done something stupid in deleting a small partition between the EFI partition and the Windows 8 installation, which seems to have borked being able to get into the UEFI firmware or bootloader without having a Windows 8 recovery drive attached via USB. So don't do that.

So, 64-bit Ubuntu is working using the 32-bit signed EFI bootloader with Secure Boot enabled. Hooray!

---

### Post by claire3 on 2014-07-15
I filed a bug in Launchpad for this.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1341944](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1341944)

Getting Ubuntu working on an Atom-based tablet is doable, but it's a giant PITA. It requires compiling Grub2, which requires disabling Secure Boot since compiling Grub2 removes the digital signature in the official Ubuntu version that allows keeping Secure Boot enabled.

---

### Post by Bucky Ball on 2014-07-15
? You filed a bug report? If the small partition you deleted was a FAT partition, then you probably deleted the EFI boot partition. That is not a bug. ;)

I just read your bug report. That is not a bug report, it is a suggestion to the devs to include a 32bit EFI bootloader. Very different and doesn't belong in bug reports. They'll get back to you there in due time. Good luck. ;)

---

### Post by Reggie_Guevara on 2014-07-15
Hi Claire,

Good for you :-)

So you were able to boot 14.04LTS 32bit via LiveUSB? Could you walk me through it? I created such a LiveUSB using the 993,280KB iso, vs. the 950,272KB 64bit iso, using Universal-USB-Installer-1.9.5.4, but I still couldn't get it to boot, whether SecureBoot was enabled or not. Either it goes straight to Windows, or if I force a USB boot, I get a  system has no usb boot capability.

---

### Post by claire3 on 2014-07-15
> **Reggie_Guevara said:**
> Hi Claire,

Good for you :-)

So you were able to boot 14.04LTS 32bit via LiveUSB? Could you walk me through it? I created such a LiveUSB using the 993,280KB iso, vs. the 950,272KB 64bit iso, using Universal-USB-Installer-1.9.5.4, but I still couldn't get it to boot, whether SecureBoot was enabled or not. Either it goes straight to Windows, or if I force a USB boot, I get a  system has no usb boot capability.

I'm going to have to collect what we did. There is an ia32 Grub package in apt for Ubuntu; it's just not included on the LiveCD (for no justifiable reason). What we ended up doing was using a gparted LiveUSB, which has the 32-bit UEFI Grub binary, to boot into Grub and manually boot into the Ubuntu LiveUSB from there. Once we were in the LiveUSB, we could install Ubuntu on the machine.

After that we had to manually boot into Ubuntu from a Grub command line, and once it was booted up we could compiled 32-bit Grub for UEFI. I think if you just take the 32-bit Grub binary and drop it onto the LiveUSB you should be able to boot, though. We tried using someone else's compiled version and ran into problems because the configuration couldn't find the Linux kernel.

Once I have everything in a coherent format from start to finish I will definitely be writing about it. :)

> **Bucky Ball said:**
> ? You filed a bug report? If the small partition you deleted was a FAT partition, then you probably deleted the EFI boot partition. That is not a bug. ;)

 I just read your bug report. That is not a bug report, it is a suggestion to the devs to include a 32bit EFI bootloader. Very different and doesn't belong in bug reports. They'll get back to you there in due time. Good luck. ;)

I didn't delete the EFI partition. I'm not that stupid. We deleted a partition that the Windows bootloader uses, but once we got Grub working that was no longer an issue.

And for anyone else interested, yes, the inability of Ubuntu to boot on 32-bit UEFI is a bug. It's fixable, it impacts the functionality of the OS and the bootloader, and the only reasons thus far for not fixing have been "because we don't want to" and "because there aren't any 32-bit UEFI machines anymore" (which is completely false).

---

### Post by Bucky Ball on 2014-07-16
> **claire3 said:**
> 
And for anyone else interested, yes, the inability of Ubuntu to boot on 32-bit UEFI is a bug. It's fixable, it impacts the functionality of the OS and the bootloader, and the only reasons thus far for not fixing have been "because we don't want to" and "because there aren't any 32-bit UEFI machines anymore" (which is completely false).

All pointing to the fact that it is quite do-able but the devs just aren't interested in doing it. Therefore, not a bug, just a function the devs aren't interested in spending any time on. A bug is a problem with an existing program that can be, and is, replicated on numerous machines (and repeatable on the same machine reliably).

You've filed a bug report saying you want a specific functionality back. That is not a bug report, that is a request to the devs to implement a functionality they seem to have made clear they are not going near. At least, not for now. ;) 

Good luck with it all. Back to the topic ...

---

### Post by Reggie_Guevara on 2014-07-16
I was able to boot as well from a GParted LiveUSB! I had to disable SecureBoot though else I get a SecureBoot failed screen.

My joy was shortlived though as upon trying to exit to transfer the 32bit Grub to my original LiveUSB, I probably did something wrong & my Switch 10 went into an endless loop. I can't send my pix of it cuz trying to send an attachment always brings me to the login page & then the forums home page. Anyway my problem now is trying to reboot cuz none of the key & switch combinations I've tried works. Not even the power switch.

I'll post this problem on a new thread but back to topic, once I get this problem fixed, which 32 bit Grub binary do I transfer? I only see grub.cfg.

---

### Post by Reggie_Guevara on 2014-07-16
Having been able to reset my Switch 10 using the reset hole, I just tried guessing & copied my GParted LiveUSB \EFI\boot\bootia32.efi to my 14.04LTS 32bit LiveUSB \boot. Of course, that didn't work hehehe. I'm just excited to boot my Switch 10 from the 14.04LTS LiveUSB even if I can't install it yet-which Grub binary do I transfer & where? ;-)

---

### Post by Bucky Ball on 2014-07-16
When you boot from the USB you don't have and install icon on the dekstop? What happens when you hit that? Sorry if you've already said it, but just for clarity as a lot has gone on and just wanting to know where things stand now.

You can boot from a USB and get to a desktop using 'Try Ubuntu'?
What happens at the desktop when you hit the 'Install' icon?

If you don't want to install, try running:

```
sudo grub-install /dev/sda
```

Reboot with the stick out if you have an existing OS on the drive.

---

### Post by jon-zendatta on 2014-07-16
Here [http://ubuntuforums.org/showthread.php?t=2147295&p=13060678#post13060678](http://ubuntuforums.org/showthread.php?t=2147295&p=13060678#post13060678) post #7

---

### Post by claire3 on 2014-07-16
> **Reggie_Guevara said:**
> Having been able to reset my Switch 10 using the reset hole, I just tried guessing & copied my GParted LiveUSB \EFI\boot\bootia32.efi to my 14.04LTS 32bit LiveUSB \boot. Of course, that didn't work hehehe. I'm just excited to boot my Switch 10 from the 14.04LTS LiveUSB even if I can't install it yet-which Grub binary do I transfer & where? ;-)

There's a couple things you can try:

Copy the bootia32.efi to /EFI/BOOT/ on your LiveUSB and try to boot from there. I **think** that's what we did, but the USB stick we used before isn't booting properly anymore, so I may actually be wrong about that.

If you can't get that to work, use a USB hub to connect both the GParted LiveUSB and the Ubuntu LiveUSB. Boot off the GParted one to get to Grub, and hit C to access the Grub console. From there, you can manually boot the Linux kernel on the Ubuntu LiveUSB so that you can get to the desktop and the installer.

For manually booting, use the following commands - you can use tab completion to get the correct names for the kernel and the initrd:

```
linux (hd1,gpt2)/boot/vmlinuz-3.13-xxxx root=/dev/mmcblk0p2 video=VGA-1:1366x768e reboot=pci,force
initrd (hd1,gpt2)/boot/initrd-3.13-xxxx
boot
```

The **(hd1,gpt2)** part will be different depending on the order of your disks. You can type **linux (hd** and then hit tab to see a list of disks and partitions. You should be able to figure out from there which disk and GPT partition to use for Ubuntu.

Once you've actually installed Ubuntu, you'll have to manually boot into it from the Grub console and install **grub-ia32-efi-bin** from apt or Synaptic Package Manager. You MIGHT need to manually configure Grub to boot your new Ubuntu installation.

A few really important things to note right off:
* The keyboard and trackpad don't work. The trackpad will work after you update to the latest kernel, but the keyboard doesn't work due to a longstanding bug in the base Linux kernel that *still* hasn't been patched. You'll want a USB keyboard handy. The touch screen does work (and normal multitouch gestures work in Chromium), so that helps. We (partner and I) are actively working on a patched kernel to fix the keyboard along with other stuff like SDIO and ACPI support.
* Wifi doesn't work at all. You'll want to have a USB network stick (wired or wireless) handy in order to do much of anything. The wireless card is a Broadcom-based one, but it uses Acer-specific NVRAM that we haven't figured out how to dump yet.
* ACPI also doesn't work. Change the power settings and display settings to never go to sleep and never turn off the display. As soon as the display turns off you won't be able to get it back on and will have to hard reset the machine.

> **jon-zendatta said:**
> Here [http://ubuntuforums.org/showthread.php?t=2147295&p=13060678#post13060678](http://ubuntuforums.org/showthread.php?t=2147295&p=13060678#post13060678) post #7

That post is useless - this device does not have a legacy BIOS compatibility mode option.

...which is why Ubuntu absolutely must support 32-bit UEFI Grub. This issue is only going to get worse, not better.

> **Bucky Ball said:**
> When you boot from the USB you don't have and  install icon on the dekstop? What happens when you hit that? Sorry if  you've already said it, but just for clarity as a lot has gone on and  just wanting to know where things stand now.

You can boot from a USB and get to a desktop using 'Try Ubuntu'?
What happens at the desktop when you hit the 'Install' icon?

If you don't want to install, try running:

```
sudo grub-install /dev/sda
```

Reboot with the stick out if you have an existing OS on the drive.

He specifically said that he still can't get the Ubuntu LiveUSB to boot. This is a very different situation from booting a LiveUSB or LiveCD normally. It is not automatic and does require some manual work. Unless you have recent experience with booting Ubuntu in a 32-bit UEFI environment, there's not much to contribute to this discussion where getting the thing booted and installed is concerned.

---

### Post by Reggie_Guevara on 2014-07-19
Progress! I just played around with your suggestions, Claire, & I was able to start the boot process ;-) But SecureBoot had to be disabled, else no bootable USBs are seen at all. Copying my GParted LiveUSBs /efi/boot/bootia32.efi to my 14.04LTS 32bit LiveUSBs /efi/boot/ (I had to create it, actually; I previously copied to /boot/ as that was the only existing directory structure suitable for a wild guess hehehe) did the trick. I also had to use /casper/vmlinuz & /casper/initrd.lz as those were the only existing such files (I configured persistence in that LiveUSB).

But the boot process didn't complete hehehe. The attached files show how far I got into a seeming endless loop. Any ideas how to proceed?

Thanks for the heads up on which hardware work & which don't. I can live with that, as long as I can boot 14.04LTS on my Switch 10 & play with it without installing it yet. You were able to do that, right, even if you did install it eventually?

---

### Post by claire3 on 2014-07-21
The messages you're seeing are related to a buggy implementation of SDIO and MMC/SD mass storage in Linux. It's another long-standing bug that has inexplicably gone unaddressed. I can't remember off the top of my head what boot flags we had to use to get that error to go away. With everything default, it can take nearly an hour to boot - but it does boot if you wait long enough. Let it sit and see if it eventually finishes booting into Unity. If it doesn't, let me know.

The custom 3.16 kernel we compiled resolved some issues but did not resolve the lack of keyboard support. I'm pretty baffled on that one - we might have to write our own driver, which kind of sucks. You don't expect to have to do that with an AIO Linux like Ubuntu in 2014...anyhow, I was stupid and forgot to back up the kernel before wiping the machine and reinstalling Windows.

We went back to Windows 8 in order to more closely examine all the hardware and figure out some more stuff before trying Linux again. I've ordered a 64GB MicroSD card, and we're going to try installing Ubuntu on that so that we can dual-boot without using up the very small 32GB internal eMMC. Once that arrives, we'll get back into this. I think we MIGHT also have figured out how to get the NVRAM for the Broadcom wifi/BT chip, which we'll need to get wifi working reliably in Linux.

Someone else figured out how to get a lot of the SDIO hardware working on an ASUS T100TA, which has very similar hardware (but a different keyboard dock), so we should be able to get most stuff working based off of that, including sound and ACPI for sleep and battery support.

I am **really** disappointed in how poorly Ubuntu works on Atom devices. This is now the second generation of the modern Atom SOC, and Intel is only going to do more with it, not less - at this point it sounds like the next Atom release is going to be even more hardware reduced so that EVERYTHING is in a single chip. If that's the case, Canonical is very short-sighted to continue refusing to support the platform.

But that's a different topic. :)

---

### Post by claire3 on 2014-08-04
We are slowly but surely seeing success!

We decided to install Ubuntu to a 64GB SDHCI card instead of the internal storage, so we can still boot Windows. This is doable, but the UEFI on the Switch 10 won't boot off the SD slot directly. Instead, you have to put Grub2 and the actual kernel on the internal storage on a separate partition, and use that to run Linux off a MicroSD card. More to come on that.

Keyboard is still not working. We did glean some information from kmesg about the hardware and what's happening, though. The below log is everything that happened by disconnecting and immediately reconnecting the keyboard:

```
6,2287,3501760402,-;usb 1-4: USB disconnect, device number 2
 SUBSYSTEM=usb
 DEVICE=c189:1
6,2288,3501760425,-;usb 1-4.3: USB disconnect, device number 3
 SUBSYSTEM=usb
 DEVICE=c189:2
6,2289,3505212636,-;usb 1-4: new high-speed USB device number 13 using xhci_hcd
 SUBSYSTEM=usb
 DEVICE=+usb:1-4
6,2290,3505230324,-;usb 1-4: New USB device found, idVendor=05e3, idProduct=0608
 SUBSYSTEM=usb
 DEVICE=c189:12
6,2291,3505230347,-;usb 1-4: New USB device strings: Mfr=0, Product=1, SerialNumber=0
 SUBSYSTEM=usb
 DEVICE=c189:12
6,2292,3505230362,-;usb 1-4: Product: USB2.0 Hub
 SUBSYSTEM=usb
 DEVICE=c189:12
6,2293,3505233439,-;hub 1-4:1.0: USB hub found
 SUBSYSTEM=usb
 DEVICE=+usb:1-4:1.0
6,2294,3505233954,-;hub 1-4:1.0: 4 ports detected
 SUBSYSTEM=usb
 DEVICE=+usb:1-4:1.0
6,2295,3505508796,-;usb 1-4.3: new full-speed USB device number 14 using xhci_hcd
 SUBSYSTEM=usb
 DEVICE=+usb:1-4.3
6,2296,3505533749,-;usb 1-4.3: New USB device found, idVendor=06cb, idProduct=2968
 SUBSYSTEM=usb
 DEVICE=c189:13
6,2297,3505533773,-;usb 1-4.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
 SUBSYSTEM=usb
 DEVICE=c189:13
6,2298,3505533788,-;usb 1-4.3: Product: ITE Device(8595)
 SUBSYSTEM=usb
 DEVICE=c189:13
6,2299,3505533802,-;usb 1-4.3: Manufacturer: ITE Tech. Inc.
 SUBSYSTEM=usb
 DEVICE=c189:13
3,2300,3505539725,-;hid (null): usage index exceeded
 SUBSYSTEM=hid
 DEVICE=+hid:(null)
3,2301,3505541271,-;hid-generic 0003:06CB:2968.000A: usage index exceeded
 SUBSYSTEM=hid
 DEVICE=+hid:0003:06CB:2968.000A
3,2302,3505541294,-;hid-generic 0003:06CB:2968.000A: item 0 2 2 2 parsing failed
 SUBSYSTEM=hid
 DEVICE=+hid:0003:06CB:2968.000A
4,2303,3505541364,-;hid-generic: probe of 0003:06CB:2968.000A failed with error -22
6,2304,3505594925,-;input: ITE Tech. Inc. ITE Device(8595) as /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.3/1-4.3:1.1/input/input15
6,2305,3505596919,-;hid-multitouch 0003:06CB:2968.000B: input,hiddev0,hidraw0: USB HID v1.10 Mouse [ITE Tech. Inc. ITE Device(8595)] on usb-0000:00:14.0-4.3/input1
 SUBSYSTEM=hid
 DEVICE=+hid:0003:06CB:2968.000B

```

We've already tried increasing HID_MAX_USAGE in the kernel to fix the above error without any luck.

---

### Post by pierre-bornancin-gmail on 2014-09-10
Hello,

Is there any progress on this device with ubuntu?

I am very interested in this device but if ubuntu cannot run on it, it is a showstopper for me.

Has anyone been able to have better result?

Thank you anyway for trying :)

Pierre.

---

### Post by kylar3 on 2014-09-27
Hi, I'm having some trouble with the device's keyboard in console (grub) it's acting as the function keys are pressed. What I'm trying to do is run a liveUSB with tails OS and install Android on the tablet. The Tails OS is actually runnable on Atom devices but I haven't been able to boot it from a normal liveUSB for some reason, and used your method to run the 32 bit UEFI.

I'm having trouble shrinking the main partition. 

Same progress with linux on the Asus t100 is made with android as well, the live USB run's without a hitch and I can get into the operating system but it runs extremely slow.

---

### Post by Reggie_Guevara on 2014-09-27
Hi Kylar3, 

You are able to run a 14.04 LTS LiveUSB? Could you walk me thru the procedure, which installer did you use, etc.? I still can't get my setup to work.

---

### Post by Timori on 2014-10-03
Im grouping up with Reggie_Guevara..
Did use LiLi USB Creator to make a GParted LiveUSB, i disabled Secure Boot, I did put up USB HDD to Position 1 in the list, but still:
Just the Acerlogo Pops up and im thrown to Windows... What are you guys doint different than me? Do i have to use the USB Slot on the Keyboard or the microUSB?

Should I use an USB Stick or an extern HDD? All changes I make doesn't seem to affect anything :(

---

### Post by Kale_Freemon on 2014-10-05
Anyway to get any pics of this device in action? Would be quite interesting to see Ubuntu on this thing. Thanks! :)

---

### Post by ArchiMark on 2014-10-10
Any progress on getting Ubuntu working?

Like the Switch 10 hardware and sizewize, but if no go with linux, then will look at other options....

Thanks!

---

### Post by tristan-sneider on 2014-10-30
Well, I see people are well interested in this. I myself, also have bought the same device. It is truly a great device.
So well, I have something useful to say:
I got Archlinux booting and detecting the internal storage. There are some r/w errors for the eMMC internal storage but I did not figure out a solution for that.
So now how I did it:
I am using grub as a bootloader.
First I formated a USB flash drive to fat32 adn named it ARCH_201410 and downloaded the ISO file for arch, then I installed grub onto the drive:
```

# grub-install --target=i386-efi --efi-directory=<mountpoint>boot/efi/ --bootloader-id=arch_grub --recheck --debug

```
After that I added the arch iso to boot to boot:
- First you need to edit the grub.cfg in /boot/grub/grub.cfg and add this line of code (find out the UUID value of your thumb drive with lsblk -f):
```
set imgdevpath="/dev/disk/by-uuid/<UUID-VALUE>"
```
- Then add this into the same file:
```

menuentry '[loopback]Archlinux' {
    set isofile='/boot/iso/archlinux-2014.10.01-dual.iso'
    loopback loop $isofile
    linux (loop)/arch/boot/x86_64/vmlinuz archisolabel=ARCH_201410 img_dev=$imgdevpath img_loop=$isofile earlymodules=loop
    initrd (loop)/arch/boot/x86_64/archiso.img
}
```
- Now just add the iso to the /boot/iso directory of the flash drive and name it the same as the isofile name is.
Plug in the drive and reboot your switch. Press F12 (If it's enabled) and you'll see a bootable USB.
Sorry for some typos or unclear information. I wrote it fast.

Cheers,
Tristan

---

### Post by IGI.222 on 2014-11-09
> **tristan-sneider said:**
> 
Later this week I think I'm going to write some drivers for the keyboard and touchscreen if I figure out 
I'm using arch myself and got it to boot using [that guide]("http://www.taylorbyte.com/docs/wiki/archlinux/uefi-gpt-usb#install-kernel-that-has-baclkight-patches") for the T100 which has similar 32-bit EFI.
The keyboard not working is a huge issue though, and i'm no driver programmer so i dearly hope someone gets around it.
Good luck with that.

P.S.: Here's [some info]("http://mageiacauldron.tuxfamily.org/InstallNetbookAspireSwitch10") gathered by a Magaia user.

---

### Post by tristan-sneider on 2014-11-20
> **IGI.222 said:**
> I'm using arch myself and got it to boot using [that guide]("http://www.taylorbyte.com/docs/wiki/archlinux/uefi-gpt-usb#install-kernel-that-has-baclkight-patches") for the T100 which has similar 32-bit EFI.
The keyboard not working is a huge issue though, and i'm no driver programmer so i dearly hope someone gets around it.
Good luck with that.

EDIT: I got the trackpad and keyboard to work. Touch is working out-of-the-box. And I got wifi to work but it keeps disconnecting all the time. As claire3 said, the NVRAM file is acer-specific and that ruins it. I'm going to write a mail to them and ask for some info.
So the link for the keyboard & trackpad:
[https://github.com/SWW13/hid-synaptics](https://github.com/SWW13/hid-synaptics)
Download this, then:
```

cd hid-synaptics
make clean
make
./installdriver.sh

```

You can get more info about wifi here: [https://wireless.wiki.kernel.org/en/users/Drivers/brcm80211](https://wireless.wiki.kernel.org/en/users/Drivers/brcm80211)
/EDIT
Then there is the eMMC problem, it keeps showing errors. This I even don't know where to look.

> **IGI.222 said:**
> P.S.: Here's [some info]("http://mageiacauldron.tuxfamily.org/InstallNetbookAspireSwitch10") gathered by a Magaia user.
Sorry but I do not understand French.

regards,
Tristan

PS: Never write info in your language, ALWAYS use English. God I hate localized info.

---

### Post by pf-frailediaz on 2014-11-29
Answering post #19
> **claire3 said:**
> We've already tried increasing HID_MAX_USAGE in the kernel to fix the above error without any luck.

I have recompiled 3.18.0-rc5 with HID_MAX_USAGE = 65536 and the keyboard works at last.

---

### Post by vasantha on 2014-12-05
Hi Claire,

I have the same Ubuntu issue with the same computer. Would you be able to give me a step by step procedure that I can follow (newbie).

Thanks in advance. 

Vas

---

### Post by sww132 on 2014-12-14
Hey guys,

working on a Arch Linux installation.
With a current Linux 3.18 Kernel and an UEFI 32bit Grub booting is pretty is.

After a long time of searching I got the RTL8723BS (Wi-fi / WLAN) working with added device id, see [https://github.com/SWW13/rtl8723as](https://github.com/SWW13/rtl8723as)
Touchscreen is working out of the box in Gnome 3.14, touchpad needs 'xf86-input-synaptic' drivers.

But I still can't get the "builtin"/plugable keyboard working, anyone success so far?
And everything else seems like much more work to get it working, has someone information about the other hardware?

Some links I collected so far:
[http://ubuntuforums.org/showthread.php?t=2253934](http://ubuntuforums.org/showthread.php?t=2253934)
[https://wiki.gnome.org/BastienNocera/Ondav975w](https://wiki.gnome.org/BastienNocera/Ondav975w)
[https://github.com/AdamWill/baytrail-m](https://github.com/AdamWill/baytrail-m)
[https://github.com/hadess/iio-sensor-proxy](https://github.com/hadess/iio-sensor-proxy)

---

### Post by tristan-sneider on 2014-12-18
Thanks for the info sww132. The keyboard seems to work with HID_MAX_USAGE=65536, but I'm not sure what it does.
I still have a graphics problem with X, it doesn't seem to recognize the Intel HD gpu. How did you solve this problem?

---

### Post by sudhanshu2 on 2015-02-13
has any progress been made on this front?i want to install elementary os on my switch 10,which is based on Ubuntu.if anyone's figured out how to do this,please help me in achieving the same.

---

### Post by ricky-johansson-c on 2015-03-14
This is what I did to get the keyboard working on my Switch [B]11
[/B]
Download this,
[https://github.com/SWW13/hid-synaptics/archive/master.zip](https://github.com/SWW13/hid-synaptics/archive/master.zip)
Edit the file **hid-ids.h** (may not be needed on Switch 10)
Change value USB_VENDOR_ID_ACER_SYNAPTICS_TP **0x2968** to USB_VENDOR_ID_ACER_SYNAPTICS_TP **0x2991**
you can double check the value you need to enter by running **lsusb**.
run make and ./installdriver.sh


Touchscreen did not work for me after resuming from sleep/suspend, I solved this by reloading the **hid_multitouch** module after resume:
**/sbin/rmmod hid_multitouch && /sbin/modprobe hid_multitouch**

As i'm using Ubuntu 15.04 which uses systemd I used this solution to make it autoreload on resume:
**[https://bbs.archlinux.org/viewtopic.php?pid=1484947#p1484947](https://bbs.archlinux.org/viewtopic.php?pid=1484947#p1484947)**

Some powersaving options suggested by Intels PowerTop tool and ehm myself :)

/etc/modprobe.d/ath9k.conf:
**options ath9k ps_enable=1**

/etc/rc.local:

**sleep 5**
**echo 0 > /sys/devices/system/cpu/cpu3/online** #disable core 3
**echo 0 > /sys/devices/system/cpu/cpu2/online** #disable core 2
**echo 0 > /sys/devices/system/cpu/cpu1/online** #disable core 1
#This will leave you will only one cpu core, just so you know
#Also i got the Core i3 model which is pretty fast on only one core.



**iw dev wlan0 set power_save on** #requires that modprobe.d config file option above.

**echo '0' > '/proc/sys/kernel/nmi_watchdog' **
**echo 'min_power' > '/sys/class/scsi_host/host2/link_power_management_policy'**
**echo 'min_power' > '/sys/class/scsi_host/host3/link_power_management_policy'**
**echo 'min_power' > '/sys/class/scsi_host/host0/link_power_management_policy'**
**echo '1' > '/sys/module/snd_hda_intel/parameters/power_save'**
**echo 'min_power' > '/sys/class/scsi_host/host1/link_power_management_policy'**
**echo '1500' > '/proc/sys/vm/dirty_writeback_centisecs'**
**echo 'auto' > '/sys/bus/usb/devices/1-7/power/control'**
**echo 'auto' > '/sys/bus/pci/devices/0000:00:00.0/power/control'**
**echo 'auto' > '/sys/bus/pci/devices/0000:00:02.0/power/control'**
**echo 'auto' > '/sys/bus/pci/devices/0000:00:03.0/power/control'**
**echo 'auto' > '/sys/bus/pci/devices/0000:00:04.0/power/control'**
**echo 'auto' > '/sys/bus/pci/devices/0000:00:1f.6/power/control'**
**echo 'auto' > '/sys/bus/pci/devices/0000:00:16.0/power/control'**
**echo 'auto' > '/sys/bus/pci/devices/0000:00:1d.0/power/control'**
**echo 'auto' > '/sys/bus/pci/devices/0000:00:1b.0/power/control'**
**echo 'auto' > '/sys/bus/pci/devices/0000:00:1c.0/power/control'**
**echo 'auto' > '/sys/bus/pci/devices/0000:00:1f.0/power/control'**
**echo 'auto' > '/sys/bus/pci/devices/0000:00:1f.2/power/control'**
**echo 'auto' > '/sys/bus/pci/devices/0000:00:1f.3/power/control'**
**echo 'auto' > '/sys/bus/pci/devices/0000:00:1f.3/power/control'**
**echo 'auto' > '/sys/bus/pci/devices/0000:01:00.0/power/control'**
**echo 'auto' > '/sys/bus/pci/devices/0000:00:14.0/power/control'**


**thermald &** #Intels new thermal daemon, a bit unsure of its effectiveness to be honest.
**exit 0**

This gives me a cpu temp of about 40-45C and a battery life of 4-6 hours of active usage.

---

### Post by miatawnt2b on 2015-04-21
I was able to get 14.10 to boot from USB last night. I used rufus to create a fat32 UEFI compatible usb stick using the 64bit Ubuntu iso. Then copy the bootia32.efi file into the /EFI/BOOT directory of the stick. To set the bios to boot unsecure EFI, you need to first set the admin password in bios. I also enabled the f12 option to select boot device. 

bam, 14.10 booted from usb stick, though it didn't have keyboard or wifi. looks like I can fix that from a few posts above.

my question is, what do I need to do now to format the drive and install this on the internal? Im sure there is something specific I need to do, but I don't know where to begin. Any advice?

---

### Post by miatawnt2b on 2015-04-22
I attempted to install 15.04 from the live USB stick, but it fails with a critical error when installing grub. So I rebooted the switch with the usb stick and dumped into the grub command line. I seem to be able to select the correct kernel and initramfs, but it still will not boot completely.

Can anyone give some advice on how to get this thing to install correctly?

---

### Post by Nipu011 on 2015-04-26
Kudos to the people helping here.... is there any progress on this front? I am thinking to install elementary os(freya- ubuntu based)  on my switch 10.if anyone's figured out how to  do this,please help me :)

---

### Post by miatawnt2b on 2015-05-01
would you be able to share your edited sdio_intf.c that you used to get wireless working?  I cannot seem to get it to detect my wifi

> **sww132 said:**
> Hey guys,

working on a Arch Linux installation.
With a current Linux 3.18 Kernel and an UEFI 32bit Grub booting is pretty is.

After a long time of searching I got the RTL8723BS (Wi-fi / WLAN) working with added device id, see [https://github.com/SWW13/rtl8723as](https://github.com/SWW13/rtl8723as)
Touchscreen is working out of the box in Gnome 3.14, touchpad needs 'xf86-input-synaptic' drivers.

But I still can't get the "builtin"/plugable keyboard working, anyone success so far?
And everything else seems like much more work to get it working, has someone information about the other hardware?

Some links I collected so far:
[http://ubuntuforums.org/showthread.php?t=2253934](http://ubuntuforums.org/showthread.php?t=2253934)
[https://wiki.gnome.org/BastienNocera/Ondav975w](https://wiki.gnome.org/BastienNocera/Ondav975w)
[https://github.com/AdamWill/baytrail-m](https://github.com/AdamWill/baytrail-m)
[https://github.com/hadess/iio-sensor-proxy](https://github.com/hadess/iio-sensor-proxy)

---

### Post by jeuxtraffic-fr on 2015-05-02
Hello, i have installing ubuntu 15.04 on my acer because windows has crashing in his update.
But i have some question :
How to set up the keyboard on boot ? I've building the driver but i need to do : "sudo ./installdriver.sh" before using my keyboard.
How to get the wifi (and maybe bluetooth) working ?
How to get sound working ? (is the byt-rt5600 is correct ?)
How to boot whithout using usb, (i need to have a grub install on a usb stick that boot my ubuntu install).
And optional, how to get the camera ?

---

### Post by miatawnt2b on 2015-05-02
It looks like my wifi card is the broadcom since my device ID says 0x4324 in the mmc1:0001:1/data file however, the vendor id in the same directory is 0x02d0 which as far as I can tell is not standard broadcom. probably why none of the standard drivers  does nto work. lspci does not show any broadcom device at all. 

Anyone have ideas on getting this working?

---

### Post by miatawnt2b on 2015-05-09
OK, I'm going to try and summarize some things here. I was able to get the broadcom wifi working after a lot of help in this thread.
[http://ubuntuforums.org/showthread.php?t=2276504](http://ubuntuforums.org/showthread.php?t=2276504)
I am using the brcmfmac driver with brcmfmac43241b4-sdio.bin and brcmfmac43241b4-sdio.txt firmware.

Networkmanager will not show the SSID's at all, so I had to remove it and install WICD. I don't like it as much, but hey... it works.
disable ipv6 for best performance.

I was able to clear up the SD R/W errors by enabling trim. Edit your /etc/fstab with the discard command.  mine looks like this:
```

UUID=a9ef0dba-18c9-424f-a494-e443be7df223 /               ext4    errors=remount-ro,discard 0       1

```

*edit* enabling TRIM actually didn't solve the R/W issues.

I still cannot get grub to boot on its own. I was able to get it to drop to a grub prompt on its own (without a USB stick) by dropping the 32bit bootloader from the usb stick into /boot/efi/Boot directory. At least I don't need the usb stick now anymore, but still have to type the grub commands manually to boot linux. 

I've tried compiling grub as outlined in the TF100 thread but no luck. If anyone can help on this I would appreciate.

I still don't have sound working either.

---

### Post by jeuxtraffic-fr on 2015-05-16
My install has crashed but i don't know why...
I've tried to get the wifi working, (it see the BBOX but not my Free Box with the "brcmfmac43241b4-sdio.txt". sometime, it see my Free Box but i can't connect, i don't try with phone.)
Now, i try to install (again) but i have some copy error or grub-install issue on 14.04, 14.04.2, 14.10, 15.04, 15.10 desktop next, and i can't finish the setup, I think I will try on another computer and copy the install on my Acer if i can't or maybe install on my 15GB SD card ...

---

### Post by cocolas-nicolas on 2015-05-18
Hello and thanks to anyone who helps running Ubuntu on this device.

I managed to install Ubuntu 15.04 on my Acer Aspire Switch 10 (which was quite long because of the many I/O errors I'm getting from mmcblk0).

jeuxtraffic-fr, I got the same grub-install error as you I guess, but Ubuntu was correctly installed and I could boot using Grub on an external USB drive.

I found a particularly strange behaviour on my device.
Apparently randomly and without any reason, every animations speed up and some user interactions get repeated or sustained (eg. I'm still grabing a window I released 2 seconds ago when touching the screen again). This is mainly visible on the graph page of the system monitor: every graphs will suddenly progress faster.
This is not a critical problem for now (I hope it doesn't hurt watching a movie), but it's quite strange…

I will tell you later (in at least 2 days) if I managed to enable wifi and connect to my Freebox v6, jeuxtraffic-fr. (good to see some French people here by the way ;))

---

### Post by miatawnt2b on 2015-05-20
I've been following the Asus T100 Google+ community and they have a lot of info over there. I found a custom 4.0 kernel for that device that has the mmc patch. installed it and my boot time is about 10 seconds. No more R/W errors.

I also installed the edgers xorg ppa and grabbed a new intel video driver. Now the screen isn't as choppy with video.

So, the last thing to get working before I can really start using this thing is the sound. I have downloaded several intel firmware packages and stuck them in /lib/firmware/intel and I installed an asound.state file into /var/lib/alsa but am still getting dummy device. Here is the interesting part...

```

root@switch:~# cat /proc/asound/cards
--- no soundcards ---
root@switch:~# sudo alsa force-reload
Unloading ALSA sound driver modules: snd-soc-sst-byt-rt5640-mach snd-intel-sst-acpi snd-intel-sst-core snd-soc-sst-mfld-platform snd-soc-rt5640 snd-soc-rl6231 snd-seq-midi snd-seq-midi-event snd-soc-core snd-rawmidi snd-compress snd-pcm-dmaengine snd-seq snd-pcm snd-seq-device snd-timer snd-soc-sst-acpi.
Loading ALSA sound driver modules: snd-soc-sst-byt-rt5640-mach snd-intel-sst-acpi snd-intel-sst-core snd-soc-sst-mfld-platform snd-soc-rt5640 snd-soc-rl6231 snd-seq-midi snd-seq-midi-event snd-soc-core snd-rawmidi snd-compress snd-pcm-dmaengine snd-seq snd-pcm snd-seq-device snd-timer snd-soc-sst-acpi.
root@switch:~# cat /proc/asound/cards
 0 [baytrailcraudio]: baytrailcraudio - baytrailcraudio
                      baytrailcraudio
root@switch:~# alsactl -f /var/lib/alsa/asound.state restore

```

Can someone shed light on how to get sound working?

Oh... and I still can't get grub to boot into ubuntu on its own. Any help there also appreciated.

---

### Post by cocolas-nicolas on 2015-05-24
> **miatawnt2b said:**
> Oh... and I still can't get grub to boot into ubuntu on its own. Any help there also appreciated.

I've got a fully working dual boot using grub by following these steps (probably a bit brutal) :
[LIST=1]
[*]Remove package grub-efi-amd64 and install packages grub-efi-ia32, grub-efi-ia32-bin and efibootmgr.
[*]sudo grub-install /dev/mmcblk0p1 so that grub for 32 bits EFI is installed in EFI partition.
[*]sudo update-grub so that grub detects Windows and the kernel and the initrd.
[*]sudo mv /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi /boot/efi/EFI/Microsoft/Boot/bootmgfw.old.efi to move the Windows bootloader (this is the brutal part).
[*]sudo cp /boot/efi/EFI/ubuntu/grubia32.efi /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi to replace it with grub.
[*]Open the file /boot/grub/grub.cfg with a text editor and copy everythin between ### BEGIN /etc/grub.d/30_os-prober ### and ### END /etc/grub.d/30_os-prober ### to paste it in the file /etc/grub.d/40_custom after everything else.
[*](Optional : prevent /etc/grub.d/30_os-prober from running if you don't want a duplicate Windows entry, with the first one not working. I simply deleted the file.)
[*]sudo update-grub to take changes into account.
[/LIST]

I didn't manage to get wifi working, I followed [https://github.com/T100Ubuntu/T100Ubuntu/wiki/Setup-Wifi](https://github.com/T100Ubuntu/T100Ubuntu/wiki/Setup-Wifi) but it doen't work at all…

---

### Post by miatawnt2b on 2015-05-25
> **cocolas-nicolas said:**
> I've got a fully working dual boot using grub by following these steps (probably a bit brutal) :
[LIST=1]
[*]Remove package grub-efi-amd64 and install packages grub-efi-ia32, grub-efi-ia32-bin and efibootmgr.
[*]sudo grub-install /dev/mmcblk0p1 so that grub for 32 bits EFI is installed in EFI partition.
[*]sudo update-grub so that grub detects Windows and the kernel and the initrd.
[*]sudo mv /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi /boot/efi/EFI/Microsoft/Boot/bootmgfw.old.efi to move the Windows bootloader (this is the brutal part).
[*]sudo cp /boot/efi/EFI/ubuntu/grubia32.efi /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi to replace it with grub.
[*]Open the file /boot/grub/grub.cfg with a text editor and copy everythin between ### BEGIN /etc/grub.d/30_os-prober ### and ### END /etc/grub.d/30_os-prober ### to paste it in the file /etc/grub.d/40_custom after everything else.
[*](Optional : prevent /etc/grub.d/30_os-prober from running if you don't want a duplicate Windows entry, with the first one not working. I simply deleted the file.)
[*]sudo update-grub to take changes into account.
[/LIST]

I didn't manage to get wifi working, I followed [https://github.com/T100Ubuntu/T100Ubuntu/wiki/Setup-Wifi](https://github.com/T100Ubuntu/T100Ubuntu/wiki/Setup-Wifi) but it doen't work at all…

really really nice. Thank YOU!

For your wifi, take a look at the link I posted a couple posts up. Additionally your switch will work a lot better with the 4.0 kernel from the T100 Google+ community.  The last thing for me to figure out now to get this thing workable is the sound. I've posted several posts around here but no-one has replied. I'm pretty stuck on it.

---

### Post by cocolas-nicolas on 2015-05-26
> **miatawnt2b said:**
> For your wifi, take a look at the link I posted a couple posts up. Additionally your switch will work a lot better with the 4.0 kernel from the T100 Google+ community.  The last thing for me to figure out now to get this thing workable is the sound. I've posted several posts around here but no-one has replied. I'm pretty stuck on it.

I feel so, SO stupid! I didn't read the little sticker on the tablet telling "RTL8723BS inside" #-o
In 4 commands problem solved (for the record):
[LIST=1]
[*]mkdir rtl && cd rtl
[*]git init && git pull [https://github.com/hadess/rtl8723bs.git](https://github.com/hadess/rtl8723bs.git) (git needs to be installed, of course)
[*]make
[*]sudo make install
[/LIST]

I'm already running Linux 4.0 thanks to your precedent post, so thank you too ;) 
I don't have much idea about how to get sound working, since I never had any problem with any sound card…

@jeuxtraffic-fr, my wifi now works flawlessly, but I've got the Realtek card, so…

---

### Post by miatawnt2b on 2015-05-26
It's always something with this thing. 

I bought a 32Gb SD so I could move my home dir to it. Turns out the stupid thing is RO, even after unmounting. WTF.

---

### Post by wyndlass on 2015-05-27
claire, is your atom proc the n270? if so it is 32-bit only, that's what i have in my netbook.  64-bit devices(tmk) never ship with a 32-bit os installed. what would be the point of that? a 32-bit os on a 64-bit machine wouldn't be able to access all the proc's abilities so you'd be missing out. check out your atom's specs to be sure that it's 64-bit. i wish i had a 64-bit proc so that i could get 64-os's and programs. go to the intel website for your proc's specs. here's the specs for the n270

[code]


[COLOR=#53565A][FONT=intel-clear][TABLE="class: specs infoTable, width: 531"]
[TR="class: tech odd"]
[TD="class: lc"]Launch Date[/TD]
[TD="class: rc"]Q2'08[/TD]
[/TR]
[TR]
[TD="class: lc"]Processor Number[/TD]
[TD="class: rc"]N270[/TD]
[/TR]
[TR="class: tech odd"]
[TD="class: lc"]L2 Cache[/TD]
[TD="class: rc"]512 KB[/TD]
[/TR]
[TR="class: tech"]
[TD="class: lc"]FSB Speed[/TD]
[TD="class: rc"]533 MHz[/TD]
[/TR]
[TR="class: tech odd"]
[TD="class: lc"]FSB Parity[/TD]
[TD="class: rc"]No[/TD]
[/TR]
[TR="class: tech"]
[TD="class: lc"]Instruction Set[/TD]
[TD="class: rc"]32-bit[/TD]
[/TR]
[TR="class: tech odd"]
[TD="class: lc"]Instruction Set Extensions[/TD]
[TD="class: rc"]SSE2, SSE3, SSSE4[/TD]
[/TR]
[TR="class: tech"]
[TD="class: lc"]Embedded Options Available[[IMG]http://ark.intel.com/inc/images/fusionmobile/search-glass.png[/IMG]]("http://ark.intel.com/search/advanced?Embedded=true&MarketSegment=MBL")
[/TD]
[TD="class: rc"][COLOR=#FFFFFF]Yes[/COLOR][/TD]
[/TR]
[TR="class: tech odd"]
[TD="class: lc"]Lithography[/TD]
[TD="class: rc"]45 nm[/TD]
[/TR]
[TR="class: tech"]
[TD="class: lc"]VID Voltage Range[/TD]
[TD="class: rc"]0.9V-1.1625V[/TD]
[/TR]
[TR="class: tech odd"]
[TD="class: lc"]Recommended Customer Price[/TD]
[TD="class: rc"]TRAY: $32.00[/TD]
[/TR]
[TR]
[TD="class: lc"]Datasheet[/TD]
[TD="class: rc"][Link]("https://www-ssl.intel.com/content/www/us/en/processors/atom/atom-processor/atom-technical-resources.html")[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]
[COLOR=#53565A][FONT=intel-clear][TABLE="class: specs infoTable, width: 531"]
[TR="class: infoSection odd"]
[TD="bgcolor: #0071C5 !important, colspan: 3"][COLOR=#0071C5][FONT=monospace]**-**[/FONT][/COLOR]
Performance[/TD]
[/TR]
[TR="class: tech"]
[TD="class: lc"]# of Cores[/TD]
[TD="class: rc"]1[/TD]
[/TR]
[TR="class: tech odd"]
[TD="class: lc"]Processor Base Frequency[/TD]
[TD="class: rc"]1.6 GHz[/TD]
[/TR]
[TR="class: tech"]
[TD="class: lc"]TDP[/TD]
[TD="class: rc"]2.5 W[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]
[COLOR=#53565A][FONT=intel-clear][TABLE="class: specs infoTable, width: 531"]
[TR="class: infoSection odd"]
[TD="bgcolor: #0071C5 !important, colspan: 3"][COLOR=#0071C5][FONT=monospace]**-**[/FONT][/COLOR]
Package Specifications[/TD]
[/TR]
[TR="class: tech"]
[TD="class: lc"]T[SUB]JUNCTION[/SUB][/TD]
[TD="class: rc"]90°C[/TD]
[/TR]
[TR="class: odd"]
[TD="class: lc"]Package Size[/TD]
[TD="class: rc"]22mm x 22mm[/TD]
[/TR]
[TR]
[TD="class: lc"]Processing Die Size[/TD]
[TD="class: rc"]26 mm2[/TD]
[/TR]
[TR="class: odd"]
[TD="class: lc"]# of Processing Die Transistors[/TD]
[TD="class: rc"]47 million[/TD]
[/TR]
[TR="class: tech"]
[TD="class: lc"]Sockets Supported[/TD]
[TD="class: rc"]PBGA437[/TD]
[/TR]
[TR="class: odd"]
[TD="class: lc"]Low Halogen Options Available[/TD]
[TD="class: rc"]See MDDS[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]
[COLOR=#53565A][FONT=intel-clear][TABLE="class: specs infoTable, width: 531"]
[TR="class: infoSection odd"]
[TD="bgcolor: #0071C5 !important, colspan: 3"][COLOR=#0071C5][FONT=monospace]**-**[/FONT][/COLOR]
Advanced Technologies[/TD]
[/TR]
[TR="class: tech"]
[TD="class: lc"]Intel® Turbo Boost Technology ‡[/TD]
[TD="class: rc"]No[/TD]
[/TR]
[TR="class: tech odd"]
[TD="class: lc"]Intel® Hyper-Threading Technology ‡[[IMG]http://ark.intel.com/inc/images/fusionmobile/search-glass.png[/IMG]]("http://ark.intel.com/search/advanced?HyperThreading=true&MarketSegment=MBL")
[/TD]
[TD="class: rc"][COLOR=#FFFFFF]Yes[/COLOR][/TD]
[/TR]
[TR]
[TD="class: lc"]Intel® Virtualization Technology (VT-x) ‡[/TD]
[TD="class: rc"]No[/TD]
[/TR]
[TR="class: tech odd"]
[TD="class: lc"]Intel® Virtualization Technology for Directed I/O (VT-d) ‡[[IMG]http://ark.intel.com/inc/images/fusionmobile/search-glass.png[/IMG]]("http://ark.intel.com/search/advanced?VTD=true&MarketSegment=MBL")
[/TD]
[TD="class: rc"]No[/TD]
[/TR]
[TR="class: tech"]
[TD="class: lc"]Intel® 64 ‡[[IMG]http://ark.intel.com/inc/images/fusionmobile/search-glass.png[/IMG]]("http://ark.intel.com/search/advanced?EM64=true&MarketSegment=MBL")
[/TD]
[TD="class: rc"]No[/TD]
[/TR]
[TR="class: tech odd"]
[TD="class: lc"]Idle States[/TD]
[TD="class: rc"]No[/TD]
[/TR]
[TR="class: tech"]
[TD="class: lc"]Enhanced Intel SpeedStep® Technology[[IMG]http://ark.intel.com/inc/images/fusionmobile/search-glass.png[/IMG]]("http://ark.intel.com/search/advanced?SpeedstepTechnology=true&MarketSegment=MBL")
[/TD]
[TD="class: rc"][COLOR=#FFFFFF]Yes[/COLOR][/TD]
[/TR]
[TR="class: tech odd"]
[TD="class: lc"]Intel® Demand Based Switching[[IMG]http://ark.intel.com/inc/images/fusionmobile/search-glass.png[/IMG]]("http://ark.intel.com/search/advanced?DemandBasedSwitching=true&MarketSegment=MBL")
[/TD]
[TD="class: rc"]No[/TD]
[/TR]
[TR="class: tech"]
[TD="class: lc"]Thermal Monitoring Technologies[/TD]
[TD="class: rc"][COLOR=#FFFFFF]Yes[/COLOR][/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]
[COLOR=#53565A][FONT=intel-clear][TABLE="class: specs infoTable, width: 531"]
[TR="class: infoSection odd"]
[TD="bgcolor: #0071C5 !important, colspan: 3"][COLOR=#0071C5][FONT=monospace]**-**[/FONT][/COLOR]
Intel® Platform Protection Technology[/TD]
[/TR]
[TR="class: tech"]
[TD="class: lc"]Trusted Execution Technology ‡[[IMG]http://ark.intel.com/inc/images/fusionmobile/search-glass.png[/IMG]]("http://ark.intel.com/search/advanced?TXT=true&MarketSegment=MBL")
[/TD]
[TD="class: rc"]No[/TD]
[/TR]
[TR="class: tech odd"]
[TD="class: lc"]Execute Disable Bit ‡[/TD]
[TD="class: rc"][COLOR=#FFFFFF]Yes[/COLOR][/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]


[code]

ot at least some of them and this is directly from intel's site, here's the link  http://ark.intel.com/products/36331. this link is for the atom n270. only but you can get to the one for your. i used wikipedia  and had that link when i clicked on the n270 and took me right there.  i believe you actually have a 32-bit proc not 64.

---

### Post by miatawnt2b on 2015-05-28
Has anyone looked at this thread for info that may apply to our tabs?

[http://ubuntuforums.org/showthread.php?t=2254322](http://ubuntuforums.org/showthread.php?t=2254322)

I'm betting they are much the same hardware.

---

### Post by dillera on 2015-05-30
[QUOTE=cocolas-nicolas;13291397]I've got a fully working dual boot using grub by following these steps (probably a bit brutal) :
[LIST=1]
[*]Remove package grub-efi-amd64 and install packages grub-efi-ia32, grub-efi-ia32-bin and efibootmgr.
[*]sudo grub-install /dev/mmcblk0p1 so that grub for 32 bits EFI is installed in EFI partition.
[*]sudo update-grub so that grub detects Windows and the kernel and the initrd.
[*]sudo mv /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi /boot/efi/EFI/Microsoft/Boot/bootmgfw.old.efi to move the Windows bootloader (this is the brutal part).
[*]sudo cp /boot/efi/EFI/ubuntu/grubia32.efi /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi to replace it with grub.
[*]Open the file /boot/grub/grub.cfg with a text editor and copy everythin between ### BEGIN /etc/grub.d/30_os-prober ### and ### END /etc/grub.d/30_os-prober ### to paste it in the file /etc/grub.d/40_custom after everything else.
[*](Optional : prevent /etc/grub.d/30_os-prober from running if you don't want a duplicate Windows entry, with the first one not working. I simply deleted the file.)
[*]sudo update-grub to take changes into account.
[/LIST]
[QUOTE]


[SIZE=2]I have been fooling with this fedlet ISO ([/SIZE]https://www.happyassassin.net/fedlet-a-fedora-remix-for-bay-trail-tablets/) - it boots and has wifi support. You need to build the keyboard fix however.

Anyways, I fought the UEFI battle and had the booting issues where my 10 would only go into the Windows Recovery boot - but I had blown away all the windows partitions. I was trying to get fedora to boot.

All you have to do is mount the UEFI (boot) partition and change the name of the Microsoft dir- i.e.

cd /boot/efi/EFI
mv Microsoft 1Microsoft

Even when I was changing the boot order, something was making it go and find the Microsoft dir no matter what-- once that was gone (because I renamed it) it used the grub boot loader normally and just booted right into fedora. I googled and saw somewhere that it could be hardcoded into the BIOS to try that MS directory first on these systems.

Now I'm just waiting for a nice ubuntu release- but for now the fedlet ISO at least lets me use Linux on this thing. I'm surprised its taken this long.

---

### Post by leona on 2015-07-08
Will be watching this thread with interest, I have just ordered a refurbished switch 10 64Gb version which I would like to dual boot linux on (flavour undecided yet) but as this seemed the most active community trying to sort this out, great work, please keep it up.
I don't know if this blog post is of any use, with getting wifi going [http://www.zdnet.com/article/installing-opensuse-fedora-and-ubuntu-on-my-new-acer-aspire-e11/](http://www.zdnet.com/article/installing-opensuse-fedora-and-ubuntu-on-my-new-acer-aspire-e11/)

---

### Post by miatawnt2b on 2015-07-09
Has anyone had any luck getting sound to work?

---

### Post by leona on 2015-07-11
On the link I gave, they had sound working on a switch 11, could it use the same driver?

---

### Post by leona on 2015-07-11
No, the Switch 10's use a Intel Atom Z3735F Quad-core 1.33 GHz which is a 64bit chip!

From [http://ark.intel.com/products/80274/Intel-Atom-Processor-Z3735F-2M-Cache-up-to-1_83-GHz](http://ark.intel.com/products/80274/Intel-Atom-Processor-Z3735F-2M-Cache-up-to-1_83-GHz)
[table="width: 500"]
[tr]
	[td]Status: [/td]
	[td]Launched[/td]
[/tr]
[tr]
	[td]Launch Date:  [/td]
	[td]Q1'14[/td]
[/tr]
[tr]
	[td]Processor Number:  [/td]
	[td]Z3735F[/td]
[/tr]
[tr]
	[td]L2 Cache: [/td]
	[td]2 MB[/td]
[/tr]
[tr]
	[td]Instruction Set: [/td]
	[td]**64-bit**[/td]
[/tr]
[tr]
	[td]Lithography: [/td]
	[td]22 nm[/td]
[/tr]
[tr]
	[td]# of Cores: [/td]
	[td]4[/td]
[/tr]
[tr]
	[td]# of Threads: [/td]
	[td]4[/td]
[/tr]
[tr]
	[td]Processor Base Frequency: [/td]
	[td]1.33 GHz[/td]
[/tr]
[tr]
	[td]Burst Frequency: [/td]
	[td]1.83 GHz[/td]
[/tr]
[tr]
	[td]Scenario Design Power (SDP):[/td]
	[td]2.2 W[/td]
[/tr]
[/table]
etc....

> **wyndlass said:**
> claire, is your atom proc the n270? if so it is 32-bit only, that's what i have in my netbook.  64-bit devices(tmk) never ship with a 32-bit os installed. what would be the point of that? a 32-bit os on a 64-bit machine wouldn't be able to access all the proc's abilities so you'd be missing out. check out your atom's specs to be sure that it's 64-bit. i wish i had a 64-bit proc so that i could get 64-os's and programs. go to the intel website for your proc's specs. here's the specs for the n270

[code]


[COLOR=#53565A][FONT=intel-clear][TABLE="class: specs infoTable, width: 531"]
[TR="class: tech odd"]
[TD="class: lc"]Launch Date[/TD]
[TD="class: rc"]Q2'08[/TD]
[/TR]
[TR]
[TD="class: lc"]Processor Number[/TD]
[TD="class: rc"]N270[/TD]
[/TR]
[TR="class: tech odd"]
[TD="class: lc"]L2 Cache[/TD]
[TD="class: rc"]512 KB[/TD]
[/TR]
[TR="class: tech"]
[TD="class: lc"]FSB Speed[/TD]
[TD="class: rc"]533 MHz[/TD]
[/TR]
[TR="class: tech odd"]
[TD="class: lc"]FSB Parity[/TD]
[TD="class: rc"]No[/TD]
[/TR]
[TR="class: tech"]
[TD="class: lc"]Instruction Set[/TD]
[TD="class: rc"]32-bit[/TD]
[/TR]
[TR="class: tech odd"]
[TD="class: lc"]Instruction Set Extensions[/TD]
[TD="class: rc"]SSE2, SSE3, SSSE4[/TD]
[/TR]
[TR="class: tech"]
[TD="class: lc"]Embedded Options Available[[IMG]http://ark.intel.com/inc/images/fusionmobile/search-glass.png[/IMG]]("http://ark.intel.com/search/advanced?Embedded=true&MarketSegment=MBL")
[/TD]
[TD="class: rc"][COLOR=#FFFFFF]Yes[/COLOR][/TD]
[/TR]
[TR="class: tech odd"]
[TD="class: lc"]Lithography[/TD]
[TD="class: rc"]45 nm[/TD]
[/TR]
[TR="class: tech"]
[TD="class: lc"]VID Voltage Range[/TD]
[TD="class: rc"]0.9V-1.1625V[/TD]
[/TR]
[TR="class: tech odd"]
[TD="class: lc"]Recommended Customer Price[/TD]
[TD="class: rc"]TRAY: $32.00[/TD]
[/TR]
[TR]
[TD="class: lc"]Datasheet[/TD]
[TD="class: rc"][Link]("https://www-ssl.intel.com/content/www/us/en/processors/atom/atom-processor/atom-technical-resources.html")[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]
[COLOR=#53565A][FONT=intel-clear][TABLE="class: specs infoTable, width: 531"]
[TR="class: infoSection odd"]
[TD="bgcolor: #0071C5 !important, colspan: 3"][COLOR=#0071C5][FONT=monospace]**-**[/FONT][/COLOR]
Performance[/TD]
[/TR]
[TR="class: tech"]
[TD="class: lc"]# of Cores[/TD]
[TD="class: rc"]1[/TD]
[/TR]
[TR="class: tech odd"]
[TD="class: lc"]Processor Base Frequency[/TD]
[TD="class: rc"]1.6 GHz[/TD]
[/TR]
[TR="class: tech"]
[TD="class: lc"]TDP[/TD]
[TD="class: rc"]2.5 W[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]
[COLOR=#53565A][FONT=intel-clear][TABLE="class: specs infoTable, width: 531"]
[TR="class: infoSection odd"]
[TD="bgcolor: #0071C5 !important, colspan: 3"][COLOR=#0071C5][FONT=monospace]**-**[/FONT][/COLOR]
Package Specifications[/TD]
[/TR]
[TR="class: tech"]
[TD="class: lc"]T[SUB]JUNCTION[/SUB][/TD]
[TD="class: rc"]90°C[/TD]
[/TR]
[TR="class: odd"]
[TD="class: lc"]Package Size[/TD]
[TD="class: rc"]22mm x 22mm[/TD]
[/TR]
[TR]
[TD="class: lc"]Processing Die Size[/TD]
[TD="class: rc"]26 mm2[/TD]
[/TR]
[TR="class: odd"]
[TD="class: lc"]# of Processing Die Transistors[/TD]
[TD="class: rc"]47 million[/TD]
[/TR]
[TR="class: tech"]
[TD="class: lc"]Sockets Supported[/TD]
[TD="class: rc"]PBGA437[/TD]
[/TR]
[TR="class: odd"]
[TD="class: lc"]Low Halogen Options Available[/TD]
[TD="class: rc"]See MDDS[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]
[COLOR=#53565A][FONT=intel-clear][TABLE="class: specs infoTable, width: 531"]
[TR="class: infoSection odd"]
[TD="bgcolor: #0071C5 !important, colspan: 3"][COLOR=#0071C5][FONT=monospace]**-**[/FONT][/COLOR]
Advanced Technologies[/TD]
[/TR]
[TR="class: tech"]
[TD="class: lc"]Intel® Turbo Boost Technology &#8225;[/TD]
[TD="class: rc"]No[/TD]
[/TR]
[TR="class: tech odd"]
[TD="class: lc"]Intel® Hyper-Threading Technology &#8225;[[IMG]http://ark.intel.com/inc/images/fusionmobile/search-glass.png[/IMG]]("http://ark.intel.com/search/advanced?HyperThreading=true&MarketSegment=MBL")
[/TD]
[TD="class: rc"][COLOR=#FFFFFF]Yes[/COLOR][/TD]
[/TR]
[TR]
[TD="class: lc"]Intel® Virtualization Technology (VT-x) &#8225;[/TD]
[TD="class: rc"]No[/TD]
[/TR]
[TR="class: tech odd"]
[TD="class: lc"]Intel® Virtualization Technology for Directed I/O (VT-d) &#8225;[[IMG]http://ark.intel.com/inc/images/fusionmobile/search-glass.png[/IMG]]("http://ark.intel.com/search/advanced?VTD=true&MarketSegment=MBL")
[/TD]
[TD="class: rc"]No[/TD]
[/TR]
[TR="class: tech"]
[TD="class: lc"]Intel® 64 &#8225;[[IMG]http://ark.intel.com/inc/images/fusionmobile/search-glass.png[/IMG]]("http://ark.intel.com/search/advanced?EM64=true&MarketSegment=MBL")
[/TD]
[TD="class: rc"]No[/TD]
[/TR]
[TR="class: tech odd"]
[TD="class: lc"]Idle States[/TD]
[TD="class: rc"]No[/TD]
[/TR]
[TR="class: tech"]
[TD="class: lc"]Enhanced Intel SpeedStep® Technology[[IMG]http://ark.intel.com/inc/images/fusionmobile/search-glass.png[/IMG]]("http://ark.intel.com/search/advanced?SpeedstepTechnology=true&MarketSegment=MBL")
[/TD]
[TD="class: rc"][COLOR=#FFFFFF]Yes[/COLOR][/TD]
[/TR]
[TR="class: tech odd"]
[TD="class: lc"]Intel® Demand Based Switching[[IMG]http://ark.intel.com/inc/images/fusionmobile/search-glass.png[/IMG]]("http://ark.intel.com/search/advanced?DemandBasedSwitching=true&MarketSegment=MBL")
[/TD]
[TD="class: rc"]No[/TD]
[/TR]
[TR="class: tech"]
[TD="class: lc"]Thermal Monitoring Technologies[/TD]
[TD="class: rc"][COLOR=#FFFFFF]Yes[/COLOR][/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]
[COLOR=#53565A][FONT=intel-clear][TABLE="class: specs infoTable, width: 531"]
[TR="class: infoSection odd"]
[TD="bgcolor: #0071C5 !important, colspan: 3"][COLOR=#0071C5][FONT=monospace]**-**[/FONT][/COLOR]
Intel® Platform Protection Technology[/TD]
[/TR]
[TR="class: tech"]
[TD="class: lc"]Trusted Execution Technology &#8225;[[IMG]http://ark.intel.com/inc/images/fusionmobile/search-glass.png[/IMG]]("http://ark.intel.com/search/advanced?TXT=true&MarketSegment=MBL")
[/TD]
[TD="class: rc"]No[/TD]
[/TR]
[TR="class: tech odd"]
[TD="class: lc"]Execute Disable Bit &#8225;[/TD]
[TD="class: rc"][COLOR=#FFFFFF]Yes[/COLOR][/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]


[code]

ot at least some of them and this is directly from intel's site, here's the link  http://ark.intel.com/products/36331. this link is for the atom n270. only but you can get to the one for your. i used wikipedia  and had that link when i clicked on the n270 and took me right there.  i believe you actually have a 32-bit proc not 64.

---

### Post by leona on 2015-07-11
Another site of interest [http://liliputing.com/2015/03/ubuntu-on-the-acer-aspire-switch-11-2-in-1-tablet-video.html](http://liliputing.com/2015/03/ubuntu-on-the-acer-aspire-switch-11-2-in-1-tablet-video.html)

---

### Post by mike200 on 2015-07-12
Hi, has anyone had any luck getting the buttons on the tablet to work? Or DPMS?

---

### Post by leona on 2015-07-15
Ok mine has just arrived, only had a few minutes at work to check it out, first thing I noticed though when I checked out PC info in Windoze is that I have a Realek wifi adapter, as apposed to others having Broadcom's 
I believe this is because there are several different models, 11 I think,  (see here [http://www.acer.co.uk/ac/en/GB/content/models/laptops/aspireswitch10](http://www.acer.co.uk/ac/en/GB/content/models/laptops/aspireswitch10)) most differences are to so with internal storage is 32Gb, 64Gb or 500Gb SSD's but also in my case I looked for the the model with the high resolution screen, the standard models have a WXGA (1280 x 800) (NT.L4 models) screens (I am thinking these also have the broadcom wifi adapters), I sent for the WUXGA (1920 x 1200) 64Gb NT.L6 model (found a recon one of Amazon) this seems to have other different hardware hencei the Realtek card.
Now I have the daunting task of trying to boot and install linux, so will go re-read this thread and ensure I have everything I need. ;)

---

### Post by miatawnt2b on 2015-07-27
> **leona said:**
> Ok mine has just arrived, only had a few minutes at work to check it out, first thing I noticed though when I checked out PC info in Windoze is that I have a Realek wifi adapter, as apposed to others having Broadcom's 
I believe this is because there are several different models, 11 I think,  (see here [http://www.acer.co.uk/ac/en/GB/content/models/laptops/aspireswitch10](http://www.acer.co.uk/ac/en/GB/content/models/laptops/aspireswitch10)) most differences are to so with internal storage is 32Gb, 64Gb or 500Gb SSD's but also in my case I looked for the the model with the high resolution screen, the standard models have a WXGA (1280 x 800) (NT.L4 models) screens (I am thinking these also have the broadcom wifi adapters), I sent for the WUXGA (1920 x 1200) 64Gb NT.L6 model (found a recon one of Amazon) this seems to have other different hardware hencei the Realtek card.
Now I have the daunting task of trying to boot and install linux, so will go re-read this thread and ensure I have everything I need. ;)

Any updates on your progress?

---

### Post by leona on 2015-07-31
Sorry about the delay, I've been so busy I haven't had an evening to sit down and try this until tonight so I am now just about to start the install process,  I'm going to try, what I hope is the, easy route and use the 32bit distro, my reasons are that its a lot of hassle to try to mod the 32 bit EFI firmware to take the 64 bit distro and as it only has 2gb ram I'm not going to loose much, I feel this might be an easier option, time will tell.
So I am going to install the latest release 15.04 32bit, GNOME variant,  well I will try to boot it first of the key, see how that goes. Fingers crossed. wish me luck.

---

### Post by leona on 2015-07-31
Fallen at first fence, I have created a bootable key, tested on my desktop to confirm it boots, I have disabled Secure boot on the tablet (by setting password), enabled f12 menu, moved usb cd to the top of the list, inserted key into usb port in keyboard, hit f12, only windows boot showed, ok I thought I try the usb OTG port with the correct cable, tried again, nothing, only windows boot manager, will need further research, hum, ran out of time tonight, will try tomorrow. night all.
Edit: just before going to bed I tried
> Copy the bootia32.efi to /EFI/BOOT/ 
No joy, this wouldn't make it book, no change.
Further update, yes going to bed now!   
I was being a total tool and had formatted the usb key to ext4 (my default setting), after formatting it correctly to FAT32 and writing the ISO to it, I can now boot to a grub command prompt, but that's it for tonight, I'll try t figure out how to get further tomorrow.

---

### Post by halfnote52 on 2015-07-31
> **leona said:**
> Fallen at first fence, I have created a bootable  key, tested on my desktop to confirm it boots, I have disabled Secure  boot on the tablet (by setting password), enabled f12 menu, moved usb cd  to the top of the list, inserted key into usb port in keyboard, hit  f12, only windows boot showed, ok I thought I try the usb OTG port with  the correct cable, tried again, nothing, only windows boot manager, will  need further research, hum, ran out of time tonight, will try tomorrow.  night all.
Edit: just before going to bed I tried

No joy, this wouldn't make it book, no change.
Further update, yes going to bed now!   
I was being a total tool and had formatted the usb key to ext4 (my  default setting), after formatting it correctly to FAT32 and writing the  ISO to it, I can now boot to a grub command prompt, but that's it for  tonight, I'll try t figure out how to get further tomorrow.


I  got 15.04 working GREAT on my Switch 10 except for Wifi and sound.  Waiting for better drivers, and playing with Win10 in the meantime.  (Switch 11 works PERFECTLY, after some fiddling. And no need for the bootia32.efi trick - it's core i3/i5.)

I used the bootia32.efi but **here's the trick.**   Go to BIOS. Turn secureboot ON (Eeeyup. On.)  Then go back to the menu  where you ADD secure boot sources. Browse to the bootia32.efi, add it,  give it a name like Liveboot or something, and then reboot, go back into  BIOS, turn secure boot back OFF again, and the bootia option will still  be available on the f12 menu. 

Load up the live disc, and you're good. 

Now  here's the difference:  I was wanting a 100% clean X/Ubuntu-only  install so I then did a dd clone of the whole drive off to a .raw file  on an external HD  (saved Windows for later).  I blew out the HD,  installed Xubu 15.04, rebooted.  

To do this, use the Ubiquity installer if you wanna install permanently (using the  NO BOOTLOADER switch from the command prompt) and reboot.

At this  point you STILL have to boot from live. Grub isn't ready yet.  When you  get to the grub choice screen, use the c option,  use the linux command  and the initrd command to pick out your drive, partition, root dir,  kernel, etc. 

You'll boot into the PROPER linux installation. You'll wanna compile 32-bit (Yep - THIRTY-TWO BIT) grub, even though the OS you're using is 64-bit. 

I  followed a great article by John Wells.   [http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/](http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/)  

Upon googling it, the site's down and won't pull up, so I stuck  a copy of google's cached version here:  [http://zombie-process.com/asust100.pdf](http://zombie-process.com/asust100.pdf)   (It printed funny. It's terrible. Zoom in.)

This (above) is for the Asus T100 and so there ARE some differences, but the basic stuff is pretty similar.

[https://github.com/SWW13/rtl8723as](https://github.com/SWW13/rtl8723as)   fixes the keyboard. HOWEVER!!! There is a caveat.  If you boot the  system with the keyboard DETACHED, everything is ALWAYS fine. 

If  you boot it with it ATTACHED, it's fine until you detach it.  Reattaching it will restore the keyboard, and the mouse buttons, but not  touchpad movement.  I think if it's attached when the system boots, a  different driver gets loaded in the background, and takes over when the  thing toggles. 

Rotation is achieved easily with a CTRL+ALT+R  keyboard shortcut attached to a script (I'll post mine for the Switch  11, which I got FULLY working with Xubu 11 later, and you can swap out  the hardware names/IDs) . I didn't bother with auto-rotate because it  annoys the hell out of me anyway, but you could map the same script to  the ACPI event.

Onboard is the best Onscreen Keyboard. There IS a  problem with the version of the lightdm greeter that ships with the  disk. You have to update it to v2.X or it WILL NOT accept input from the  onscreen keyboard. Luckily, it's in the repos. 

Touchscreen dies  on resume on the Switch 11. I dunno about the Switch 10. There's a  sleep.d/resume script for that somewhere. I'll post mine on that, too,  when I get the chance, but it's floating around the net somewhere, as  well. 

Cinnamon desktop on top of Xubuntu does the trick for me,  for the Switch 11, as well as playing around on the Switch 10.  Cinnamon  seems to really like the touchscreen, and Thunar and the XFCE desktop  stuff fills in the corners. 

IF you get sound and/or WiFi working  (the only things that don't for me on the Switch 10) PLEEEASE let us  know.  I've got the broadcom version, and if you're interested I have  the BIN file from the Win8.1 driver package, but the NVRAM txt files  floating around the internet DO NOT work with it.  I kept swapping out  BINs and TXTs and got the wifi to SEE an SSID, and maybe connect once or  twice for a few minutes (usually only if another WiFi card was plugged  into the USB to "goose" the network manager.)

Sound on this is  Intel Baytrail with some sort of Realtek RTL codec.  Work is progressing  on drivers, but no joy for me yet.  Again, my Switch 11 is working  PERFECTLY, and if I could get the Switch 10 up and going, much like for  you, it'd be a dream. Although Win10 on it is nice at the moment - I can  use it with my Akai EIE Pro. ; )

Cheers, and good luck!

---

### Post by leona on 2015-08-01
I thought I would try this approach, but when I try the grub install I get
> grub-install: error: /usr/lib/grub/i386-efi/modinfo.sh doesn't exist.
> **tristan-sneider said:**
> Well, I see people are well interested in this. I myself, also have bought the same device. It is truly a great device.
So well, I have something useful to say:
I got Archlinux booting and detecting the internal storage. There are some r/w errors for the eMMC internal storage but I did not figure out a solution for that.
So now how I did it:
I am using grub as a bootloader.
First I formated a USB flash drive to fat32 adn named it ARCH_201410 and downloaded the ISO file for arch, then I installed grub onto the drive:
```

# grub-install --target=i386-efi --efi-directory=<mountpoint>boot/efi/ --bootloader-id=arch_grub --recheck --debug

```


---

### Post by leona on 2015-08-01
Tried this approach too, but still just boots to a grub console, and that's it.

> **halfnote52 said:**
> I  got 15.04 working GREAT on my Switch 10 except for Wifi and sound.  Waiting for better drivers, and playing with Win10 in the meantime.  (Switch 11 works PERFECTLY, after some fiddling. And no need for the bootia32.efi trick - it's core i3/i5.)

I used the bootia32.efi but **here's the trick.**   Go to BIOS. Turn secureboot ON (Eeeyup. On.)  Then go back to the menu  where you ADD secure boot sources. Browse to the bootia32.efi, add it,  give it a name like Liveboot or something, and then reboot, go back into  BIOS, turn secure boot back OFF again, and the bootia option will still  be available on the f12 menu. 

Load up the live disc, and you're good. 


---

### Post by leona on 2015-08-01
Ok, seems my issue was with the .efi file I was using, even though I took it from a gparted.iso, it didn't work, so after a bit of googling I found the one from > [https://github.com/jfwells/linux-asus-t100ta/raw/master/boot/bootia32.efi](https://github.com/jfwells/linux-asus-t100ta/raw/master/boot/bootia32.efi) which gave me a grub menu, yay!
So I have Ubuntu Gnome 15 64bit liveUSB booting, now to try and install it.

Ok will my first install attempt failed with a fatal grub error,so I'll have to look at an alternative approach.  I don't give up that easily.

---

### Post by halfnote52 on 2015-08-01
> **leona said:**
> I thought I would try this approach, but when I try the grub install I get

etc. etc.

# grub-install --target=i386-efi --efi-directory=<mountpoint>boot/efi/ --bootloader-id=arch_grub --recheck --debug


Try this instead:

sudo ../grub-install -d . --efi-directory /boot/efi/ --target=i386

In fact, here's the order that worked for me:


sudo apt-get update && sudo apt-get install git bison libopts25 libselinux1-dev autogen m4 autoconf help2man libopts25-dev flex libfont-freetype-perl automake  autotools-dev libfreetype6-dev texinfo ia32-libs build-essential 

(adjusting of course for different distributions' package names. I think I had to install a much larger package to get the ia32-libs?)

Then get the Grub source:

git clone git://git.savannah.gnu.org/grub.git

Now build it:

cd grub
./autogen.sh
./configure --with-platform=efi --target=i386
--program-prefix=""
make


And install to efi:

cd grub-core
sudo ../grub-install -d . --efi-directory /boot/efi/ --target=i386


This will create a directory, ‘gr ub’, in your EFI partition. We want to copy the gr ubia32.efi from there to the
location Ubuntu created during installation:

cd /boot/efi/EFI

sudo cp grub/grubia32.efi ubuntu/grubx64.efi     

##VERY IMPORTANT to note the different file name above!

Then, go back to the BIOS, RE-enable secure boot, add a new secure boot source, browse to this directory, add it, name it, save it, go back and DIS-able secure boot again, reboot, go BACK into the bios, and set the newly names one as boot device #1

---

### Post by leona on 2015-08-07
> **miatawnt2b said:**
> I attempted to install 15.04 from the live USB stick, but it fails with a critical error when installing grub. So I rebooted the switch with the usb stick and dumped into the grub command line. I seem to be able to select the correct kernel and initramfs, but it still will not boot completely.

Can anyone give some advice on how to get this thing to install correctly?

This is as far as I've got so far too.

---

### Post by halfnote52 on 2015-08-09
> **leona said:**
>  					[IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **miatawnt2b** 					[[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("http://ubuntuforums.org/showthread.php?p=13270405#post13270405") 				
 				I attempted to install 15.04 from the live USB  stick, but it fails with a critical error when installing grub. So I  rebooted the switch with the usb stick and dumped into the grub command  line. I seem to be able to select the correct kernel and initramfs, but  it still will not boot completely.

Can anyone give some advice on how to get this thing to install correctly?



This is as far as I've got so far too.

There's the problem in its entirety - you CAN'T install grub during the install. It won't work. You have to do it after the fact.

You have to install 15.04 WITHOUT grub while inside the LiveCD/usb.  You'll want to run Ubiquity from the command line in a terminal, and feed it the no-bootloader switch. 

That will install Ubuntu, yes,  but it STILL won't boot correctly.  You have to boot from the USB, and use the c option to MANUALLY select the HARD DRIVE'S version of the init and linux, and boot that way, and THEN, once you're in, compile and install the THIRTY-TWO bit grub bootloader (as per my instructions above.) 

Cheers!

---

### Post by halfnote52 on 2015-08-09
P.S.  And if you're thinking that can't be right, it actually is - you'll be loading the 64-bit OS with the 32-bit bootloader.

---

### Post by leona on 2015-08-17
> MANUALLY select the HARD DRIVE'S version of the init and linux
oh, ok, so where do I find out what I need to enter here?

---

### Post by leona on 2015-08-17
ok, looking back through this thread I found
> linux (hd1,gpt2)/boot/vmlinuz-3.13-xxxx root=/dev/mmcblk0p2 reboot=pci,force
initrd (hd1,gpt2)/boot/initrd-3.13-xxxx
boot
mine is on gpt5, but I guess I have a problem with my install as when it tries to mount /dev/mmcblk0p2 I get invalid argument.

---

### Post by mike200 on 2015-08-18
For everyone who's still trying to install ubuntu on this laptop I wrote a guide that covers pretty much every aspect of it: [https://gist.github.com/franga2000/2154d09f864894b8fe84](https://gist.github.com/franga2000/2154d09f864894b8fe84)
I might make a video tutorial for it too.

Hope this helps someone

---

### Post by leona on 2015-08-18
Mike that's fantastic, thank you so much, very helpful. ok so now I have it installed and 'working' on my tablet.
I have to manual boot at this stage, though I had to adapt your instructions and use
> 
set root=(hd1,gpt5)
linux /boot/vmlinuz-3.1x-xxxx  root=/dev/mmcblk0p5
initrd /boot/initrd-3.1x-xxxx
boot

but when I open a terminal and type
> sudo apt-get install grub-efi-32ia
I get > Unable to locate package grub-efi-32ia

looking on [https://sturmflut.github.io/linux/ubuntu/2015/02/04/installing-ubuntu-on-baytrail-tablets-version-2/](https://sturmflut.github.io/linux/ubuntu/2015/02/04/installing-ubuntu-on-baytrail-tablets-version-2/)
suggests using > sudo apt-get install grub-efi-ia32-bin
but that produced the same problem, can't find the package.

---

### Post by mike200 on 2015-08-19
I think the problem is that the 32-bit GRUB package package isn't in the 64-bit repo. 
I added instructions on how to compile grub manually. This takes a bit more time, but should work every time.

---

### Post by rradzivil on 2015-08-19
> **mike200 said:**
> For everyone who's still trying to install ubuntu on this laptop I wrote a guide that covers pretty much every aspect of it: [https://gist.github.com/franga2000/2154d09f864894b8fe84](https://gist.github.com/franga2000/2154d09f864894b8fe84)
I might make a video tutorial for it too.

Hope this helps someone

Thx for greate article, mike200! But link [https://gist.github.com/franga2000/a07342b985a7c167668f](https://gist.github.com/franga2000/a07342b985a7c167668f) (about compiling a custom Linux kernel from source) does not work. It says W.I.P. Can you help with this?

---

### Post by mike200 on 2015-08-19
> **rradzivil said:**
> Thx for greate article, mike200! But link [https://gist.github.com/franga2000/a07342b985a7c167668f](https://gist.github.com/franga2000/a07342b985a7c167668f) (about compiling a custom Linux kernel from source) does not work. It says W.I.P. Can you help with this?

I'm glad you found it useful. I aparently forgot to publish the other guide :oops:. It's live now.

---

### Post by leona on 2015-08-19
Ok, I've hit an issue, when I get to this stage.
> ./configure --with-platform=efi --target=i386
I get
> checking for bison... no. 
configure: error: bison is not found

Edit:
Ok, had to install git, bison and flex.
but it seems it needs a whole load more libraries, freetype2, fuse, zfs, how do I get all the required libraries installed?

So when I try 
> sudo grub-install --target=i386-efi --efi-directory=/boot/efi/
I get > grub-install: error: /usr/lib/grub/i386-efi/modinfo.sh doesn't exist please specify --target or --directory. 

Ok this is interesting, googled for similar issues and then found this site
[http://www.cnx-software.com/2015/02/13/how-to-install-ubuntu-15-04-on-mele-pcg03-intel-mini-pc/](http://www.cnx-software.com/2015/02/13/how-to-install-ubuntu-15-04-on-mele-pcg03-intel-mini-pc/)
as this uses a atom cpu.
I then did 
> sudo apt-get install grub-efi-ia32 grub-efi-ia32-bin
and this time it didn't complain! yes!
Interestingly I didn't have a /boot/efi/EFI/ubuntu/ directory mine was in /boot/efi/EFI/grub so have created a /boot/efi/EFI/linux dir and cp'd the file into there.
run > update-grub as root
then do the EFI Secure boot thingy in the bios.
ok now its fingers crossed and see what happens.....
.....
......
It only bl00dy works! oh yes.
Installed realtek network drivers (needed a github account).
Only thing left to do is to make the keyboard work, but I'll come back to that.
oh and is there a way to make it boot Grub as default, rather than having to F12 and selecting it?  It always boos into Windows as default?
Thanks everyone for your help.
One happy bunny.

---

### Post by rradzivil on 2015-08-20
> **mike200 said:**
> It's live now.

Thanks a lot again!

---

### Post by mike200 on 2015-08-20
> **leona said:**
> oh and is there a way to make it boot Grub as default, rather than having to F12 and selecting it?  It always boos into Windows as default?

Yes, you can change the boot priority in the BIOS under "Boot". There should be arrows on the right of the boot entries.

---

### Post by leona on 2015-08-31
Thank you, its only the keyboard i have to get working now

---

### Post by halfnote52 on 2015-09-01
> **leona said:**
> Thank you, its only the keyboard i have to get working now

Check my post of instructions (#62) for a link and instructions on the keyboard.  = )

> **leona said:**
> Ok, I've hit an issue, when I get to this stage.

Installed realtek network drivers (needed a github account).
One happy bunny.

You wouldn't be willing to post the link, would you? I can't find working network drivers for the darned thing (given, I'm currently using 15.04 on mine).

---

### Post by leona on 2015-09-04
Sure I followed the instruction here [https://gist.github.com/franga2000/2154d09f864894b8fe84](https://gist.github.com/franga2000/2154d09f864894b8fe84)

> # Clone the driver repo
git clone [https://github.com/SWW13/rtl8723as](https://github.com/SWW13/rtl8723as)
# Build and install the driver
cd rtl8723as
make
sudo make install
but as I say, it couldn't get the source without a github account, you also need to have git installed. > sudo apt-get install git

I followed he instructions and it was good, there is one issue though, it does cut out now and again, if on for more than an hour, I have to log out and back in to fix it.

My issue with the kernel, but I am stuck at the build stage as I don't know what options to select.

Thank link you give for the keybaord, takes me to tealtek wifi drivers.??

---

### Post by tristan-sneider on 2015-09-04
Doesn't matter if I have 14.10 or 15.04, the OS always freezes when writing/reading to the emmc after some time.
After I switched from 15.04 to 14.10 the MMC errors were gone, but I started seeing I2c errors, but they are not specific.
Does anyone have any solutions to my problem?
+
I have BRCM80211 and I got it working but it keeps disconnecting all the time.

EDIT:
This is the i2c error: (After a minute in TTY1, the screen is full with em')
> i2c i2c-0: i2c read failed

---

### Post by halfnote52 on 2015-09-05
> **leona said:**
> 

Thank link you give for the keybaord, takes me to tealtek wifi drivers.??

[https://github.com/SWW13/hid-acer](https://github.com/SWW13/hid-acer)  Try that one.  

I'd actually been playing with the same GIT you supplied, but it didn't seem to work for me. = /
I'll give it another go - something might have just gone wonky the first time (It IS Linux, after all. Installs NEVER go smoothly, though once everything's in place it tends to stay there, heheh.) ; )

---

### Post by tristan-sneider on 2015-09-05
Well after some research I found a handy tool i2c-tools (that I do not how to do anything with yet) that reads I2C addresses
Using the command i2cdetect -r <range> I found some returned numbers:
[B]Range 0:
[/B]```

$i2cdetect -r 0
WARNING! This program can confuse your I2C bus, cause data loss and worse!
I will probe file /dev/i2c-0 using read byte commands.
I will probe address range 0x03-0x77.
Continue? [Y/n] 
     0  1  2  3  4  5  6  7  8  9  a  b  c  d  e  f
00:          -- -- -- -- -- -- -- -- -- -- -- -- -- 
10: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
20: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
30: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
40: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
50: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
60: -- -- -- -- -- -- -- -- 68 -- -- -- -- -- -- -- 
70: -- -- -- -- -- -- 76 --                         

```

I found a lot if i2c devices in the /dev folder.
The only important one (that's causing the errors) is on range 0.
The error code:
> i2c i2c-0: i2c read failed

EDIT:
After using i2cget <RANGE> 0x<ADDRESS>, I could read data just fine.
0x68 returns 0x9b
0x76 returns 0x00

EDIT2:
Use the battery.patch that is on the ASUS T100 Google Drive.

---

### Post by leona on 2015-09-18
Has anyone tried to update the kernel version to 4.1 or 4.3RC1? Apparently has more support for our type of devices.  Might try a kernel upgrade if I can work out how.

---

### Post by v1nsai on 2015-09-21
I'm having trouble even seeing my wifi hardware.  lshw, lsusb and lspci don't see it at all, not even a warning about it being inactive or anything.

I've installed drivers for BRCM80211 and RTL8723BS just to see if that would work, but no dice so far.

Any suggestions for how to figure out what hardware is actually in here?

ALSO wanted to throw out some help for others that I haven't seen anywhere else:

1) Tether phone to get internet
2) Trackpad and usb port on bottom part work for me in 15.04
3) There is an on screen keyboard called onboard built into Ubuntu, no need for USB hub

---

### Post by leona on 2015-11-04
Ok, I've updated to 15.10 which has the new 4.2 Kernel, while the update seemed to have gone well, I have lost the Wifi, I tried to reapply the patch but it fails, I don't think it's compatible with the Kernel, d'oh, so back to no wifi, I was hoping the Realtek wifi driver would have been baked into the Kernel by now.

Edit: I've had a response from the developer who forked the original branch, he is now saying to use the main branch here.
[https://github.com/hadess/rtl8723bs]("https://github.com/hadess/rtl8723bs") and to speciify the baytrail option (could be why ours used to crash, a few patches have fixed that), though I'm not sure how we specify the option or apply the patches yet, that instruction isn't given in the Readme :(

---

### Post by jeuxtraffic-fr on 2015-11-05
For those who want, The light sensors work for me.

1. Open a Terminal and type : mkdir cm3218_ambiant_light_sensor_driver
2. cd cm3218_ambiant_light_sensor_driver
3. wget [https://github.com/jfwells/linux-asus-t100ta/raw/master/cm3218_ambient_light_sensor_driver/cm3218.c](https://github.com/jfwells/linux-asus-t100ta/raw/master/cm3218_ambient_light_sensor_driver/cm3218.c) && wget [https://github.com/jfwells/linux-asus-t100ta/raw/master/cm3218_ambient_light_sensor_driver/Makefile](https://github.com/jfwells/linux-asus-t100ta/raw/master/cm3218_ambient_light_sensor_driver/Makefile)
4. make
5. sudo make install

now, the ambiant light sensor should work, you can type in a terminal "watch cat /sys/bus/iio/devices/iio\:device0/in_illuminance0_input" to check. You should have a number that varies according to the brightness.
The brightness on the screen doesn't change but it can be easy to do

---

### Post by miatawnt2b on 2015-11-17
I've been away for a while. Has anyone gotten the sound working yet?

---

### Post by leona on 2015-12-30
An update, for Kernel versions greater than 4.2 I have got wifi working by following instructions here.
[https://github.com/hadess/rtl8723bs/wiki/RTL8723BS-module-building-instruction-for-Debian-GNU-Linux]("https://github.com/hadess/rtl8723bs/wiki/RTL8723BS-module-building-instruction-for-Debian-GNU-Linux")

---

### Post by QDR06VV9 on 2015-12-30
Maybe you could send another link or explain how?
Here is what I see from your link..
Kind Regards

---

### Post by leona on 2016-01-05
So sorry, I made a typo with the url, that should now work correctly.

If not then. 

Make and install the module
[LIST=1]
[*]Install build support packages, note that "4.1.X-X" below should be replaced by the result of running "uname -r"
```
# apt-get install unzip build-essential linux-headers-4.1.X-X-all-amd64
```
[*]Download the module
```
# cd /usr/local/src
# wget https://github.com/hadess/rtl8723bs/archive/master.zip
```
[*]Make the module
```
# unzip master
# cd rtl8723bs-xxx
# make
```
[*]Install the module
```
# sudo make install
# sudo depmod -a
# sudo modprobe r8723bs
```
[/LIST]

---

### Post by QDR06VV9 on 2016-01-05
Thank you for taking the time to do this.:D Very clear Instructions..
I am sure it will be most helpful to others..
Kind Regards and Cheers

---

### Post by hilbricht on 2016-01-10
Kernel 4.2 for trusty brings some improvements: Boot screen does not flicker anymore and there is a battery sign in the panel after log in. Wifi and bluetooth works only with the aforementioned rtl8723bs driver from github.com, keyboard still requires extra patch hid-acer, no sound, no camera. All in all still work in construction.

---

### Post by leona on 2016-01-11
Still locks up and crashes frequently for me though, I don't know what is causing this.

---

### Post by BzukTuk on 2016-01-11
Random crashes&freezes - details here:
[https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051)
[https://bugs.freedesktop.org/show_bug.cgi?id=88012](https://bugs.freedesktop.org/show_bug.cgi?id=88012)

In short, you need to use kernel parameter "intel_idle.max_cstate=1", or Kernel <= 4.1.3 where this bug does not occure

---

### Post by leona on 2016-01-22
Implimenting [the keyboard patch]("https://github.com/SWW13/hid-acer") got my keyboard working, thought detaching the screen and reattaching looses the trackpad! so don't do that :)

---

### Post by Benito_Chamberlain on 2016-02-01
Hi Leona , How is ubuntu 15.10 Gnome running on the Switch ? Did you use the same instructions for 15.10 as for 14.04 ?
Im getting one of these tablets tomorrow, Thinking of trying fedlet or ubuntu 14 / 15 , which ever works best. Would appreciate your feedback.

---

### Post by B._Bishop on 2016-02-18
Hello everyone in this thread.

I just want to say i love you guys, because thanks to you all i have successfully installed my switch with ubuntu 15.10.
I still have no sound, and the touchscreen never lets go, for example, wanting to backspace it will hold backspace and erase everything.

I use a usb wifi key, tried to install the onboard the way Leona described above, which went really well, and it recognized my onboard wifi, but actual traffic doesnt come through and now ubuntu freezes when using the network. only hard off and on works then.
Is there something i can do to reverse the process?

Im a noob, been playing with ubuntu back in the day of Breezy Badger but thats some time ago...

Any help to install sound would be wonderful too!

Thank you all very much, windows 10 was awful! i just had to get rid of it!

---

### Post by miatawnt2b on 2016-05-03
Raising the dead on this laptop. I just found this over on github...
[https://gist.github.com/franga2000/2154d09f864894b8fe84](https://gist.github.com/franga2000/2154d09f864894b8fe84)
looks like most things are working in fedora land. I was pretty happy with my ubuntu install but had to go back to windows as I was never able to get sound working. Any further updates from the crew?

-J

---

### Post by mike200 on 2016-05-05
I've heard that sound could work and I'm reading through tons of mailing lists to figure it out.
I'll be posting updated guides (and possibly automated scripts) for 16.04 and Fedora soon™. Hopefully I get it working by then.

---

### Post by miatawnt2b on 2016-05-28
I think I'm getting a bit closer with sound, but still am missing something.
I blacklisted snd-soc-sst-acpi snd_soc_sst_acpi and now aplay -l will show the baytrail audio on boot. I still however have dummy output and no sound. 
Looking for some help if anyone has ideas.
-J

---

### Post by BzukTuk on 2016-06-23
Sound: 
You have to use kernel source code version 4.5 and up.
In **sound/soc/intel/atom/sst/sst_acpi.c** change line
```
 .acpi_ipc_irq_index = 5,
```
to
```
.acpi_ipc_irq_index = 0,
```
(you can change this irq index to the right value also in ACPI DSDT via kernel (I never tried it), but changing value in sst_acpi.c is not very difficult)

Then I also comment out this:
```
#if !IS_ENABLED(CONFIG_SND_SST_IPC_ACPI)
     { "80860F28", (unsigned long)&sst_acpi_baytrail_desc },
#endif
```
in **sound/soc/intel/common/sst-acpi.c** (you could probably just set ```
CONFIG_SND_SST_IPC_ACPI=n
``` in your .config) so you dont have to blacklist the non working one

Last you need to obtain right firmware for sound chip from here 
[https://git.kernel.org/cgit/linux/kernel/git/vkoul/firmware.git/tree/intel/fw_sst_0f28_ssp0.bin?h=byt&id=5b2d50b6970b74705c1b232e3a91ab0a4e77c9d5](https://git.kernel.org/cgit/linux/kernel/git/vkoul/firmware.git/tree/intel/fw_sst_0f28_ssp0.bin?h=byt&id=5b2d50b6970b74705c1b232e3a91ab0a4e77c9d5)
and put it into /lib/firmware/intel/fw_sst_0f28.bin (replace not working firmware).

Sound should be working. If you use kernel <4.5 sound will be very noisy, squeeky, strange, playing from one side only - unusable. On newer kernels sound still has some little background noise, but it is very usable.

Source of this knowledge based on this [http://thread.gmane.org/gmane.linux.alsa.devel/134554](http://thread.gmane.org/gmane.linux.alsa.devel/134554)

Is backlight or some kind of hybernation working for anybody here?

---

### Post by leona on 2016-06-24
> **Benito_Chamberlain said:**
> Hi Leona , How is ubuntu 15.10 Gnome running on the Switch ? Did you use the same instructions for 15.10 as for 14.04 ?
Im getting one of these tablets tomorrow, Thinking of trying fedlet or ubuntu 14 / 15 , which ever works best. Would appreciate your feedback.

So sorry Benito I didn't see your post, from memory what I did was to install 15.04 using the instructions from 14.04, I ran the update to 15.10 and I then had to apply the keyboard and wifi patches to get it all working. 

its ok, but it crashed randomly, I know why that was, but I don't have the expertise required to tweak the kernel and rebuild it, to solve it, hoping that that fix will be baked into future version.

I'm keen to see if 16.04 will finally support our lovely little lappy's, because if so, it'll become my main machine, its only the random crashes that's holding me back, I don't mind much about the sound, that's more of a 'nice to have'.

I know the pain I had to go through to get this all working though, so I'm a little nervous to try installing 16.04 :)

---

### Post by leona on 2016-06-27
Trying to update to 16.04.
Keep running into problems.
First it said I was up to date, to had to change the preference from lts to normal release.
Then it said I had no space left.  noticed my syslog and kiern.log were 750MB! deleted these, but they keep coming back!
So only way I can think of installing it is from usb key again, but after writing it to a key, it'll not recognise it.
So rather frustrating at the moment and getting nowhere fast.

Oh, I know why I can't get it booting, its the whole 32bit efi thing again, I'd forgotten about that, back to step 1 for me  :)
I used this bootia32.efi file [https://github.com/jfwells/linux-asus-t100ta/raw/master/boot/bootia32.efi](https://github.com/jfwells/linux-asus-t100ta/raw/master/boot/bootia32.efi)

Currently installing, with the live usb, I have no wifi, but the keyboard seems to work, will see what works once its installed. Hoping the previous grub install will pick this up and work, I guess I might have to tweak the kernel loader, don't know.

---

### Post by leona on 2016-07-06
Got 16.04 running, but only from the grub on the usb key, can't boot the main grub because I get a  grub error 
> 
GRUB loading:
Welcome to GRUB!

error: file '/grub/i386-pc/normal.mod' not found
Entering rescue mode...
grub rescue>

not hit this before, any help?

---

### Post by miatawnt2b on 2016-07-06
Can I ask how you were able to manage completing the install of 16.04? I created a 32bit live usb with the 32bit efi file as before. It will boot the usb stick and start the live install, but part way through the install quits while installing grub. This leaves the machine basically useless as I still cannot get the internal drive to boot when manually attempting to boot from mmcblk0 using the grub command line.

---

### Post by leona on 2016-07-07
> **miatawnt2b said:**
> Can I ask how you were able to manage completing the install of 16.04? I created a 32bit live usb with the 32bit efi file as before. It will boot the usb stick and start the live install, but part way through the install quits while installing grub. This leaves the machine basically useless as I still cannot get the internal drive to boot when manually attempting to boot from mmcblk0 using the grub command line.

Hi miatawnt2b

I downloaded the 64bit version of ubuntu-gnome 16.04 lts
I created a bootable usb key with Unetbootin.
I then used the 32 bit efi file from my previous post and copied this to the boot/efi dir on the usb stick.
I have secure boot disabled on the swtich10 so just hitting F12 and choosing the USB Stick booted it.
Then select 'Try Ubuntu'.
Now when it booted I made a mistake, I forgot that you couldn't install the grub loader and this I think is what has screwed my grub boot loader.
To install, instead of clicking the icon, launch the terminal and type.
```
ubiquity --no-bootloader
```
This installed it for me.
but I can only boot this with 
```

set root=(hd1,gpt5)
linux /boot/vmlinuz-4.4.xx-generic root=/dev/mmcblk0p5
initrd /boot/initrd-4.4.xx-generic
boot

```
and it boots.
I tried grub-update, but this didn't fix it. :(

On the plus side the keyboard works out of the box, but wifi doesn't :(

---

### Post by miatawnt2b on 2016-07-07
My switch will not boot any 64bit kernel. I've tried ubuntu, debian, fedora. Nothing works. I can boot 32 bit versions. bizarre.

---

### Post by leona on 2016-07-07
> **miatawnt2b said:**
> My switch will not boot any 64bit kernel. I've tried ubuntu, debian, fedora. Nothing works. I can boot 32 bit versions. bizarre.

Even with the 32 bit efi?  Mine wouldn't boot until I used it.

---

### Post by miatawnt2b on 2016-07-07
So if I make a bootable USB with the 64bit image, and put the bootia32.efi file in the /EFI/Boot folder, my switch drops directly into grub command line. How did you get your USB stick to actually boot?

---

### Post by miatawnt2b on 2016-07-08
> **BzukTuk said:**
> Sound: 
You have to use kernel source code version 4.5 and up.
In **sound/soc/intel/atom/sst/sst_acpi.c** change line
```
 .acpi_ipc_irq_index = 5,
```
to
```
.acpi_ipc_irq_index = 0,
```
(you can change this irq index to the right value also in ACPI DSDT via kernel (I never tried it), but changing value in sst_acpi.c is not very difficult)

Then I also comment out this:
```
#if !IS_ENABLED(CONFIG_SND_SST_IPC_ACPI)
     { "80860F28", (unsigned long)&sst_acpi_baytrail_desc },
#endif
```
in **sound/soc/intel/common/sst-acpi.c** (you could probably just set ```
CONFIG_SND_SST_IPC_ACPI=n
``` in your .config) so you dont have to blacklist the non working one

Last you need to obtain right firmware for sound chip from here 
[https://git.kernel.org/cgit/linux/kernel/git/vkoul/firmware.git/tree/intel/fw_sst_0f28_ssp0.bin?h=byt&id=5b2d50b6970b74705c1b232e3a91ab0a4e77c9d5](https://git.kernel.org/cgit/linux/kernel/git/vkoul/firmware.git/tree/intel/fw_sst_0f28_ssp0.bin?h=byt&id=5b2d50b6970b74705c1b232e3a91ab0a4e77c9d5)
and put it into /lib/firmware/intel/fw_sst_0f28.bin (replace not working firmware).

Sound should be working. If you use kernel <4.5 sound will be very noisy, squeeky, strange, playing from one side only - unusable. On newer kernels sound still has some little background noise, but it is very usable.

Source of this knowledge based on this [http://thread.gmane.org/gmane.linux.alsa.devel/134554](http://thread.gmane.org/gmane.linux.alsa.devel/134554)

Is backlight or some kind of hybernation working for anybody here?

I don't even have the /sound directory that you referenced above, so no sst_acpi.c file. What am I missing?

---

### Post by leona on 2016-07-08
> **miatawnt2b said:**
> So if I make a bootable USB with the 64bit image, and put the bootia32.efi file in the /EFI/Boot folder, my switch drops directly into grub command line. How did you get your USB stick to actually boot?

hum, yep that is what I did.
so you should have 3 files in the dir
/EFI/BOOT/bootia32.efi
/EFI/BOOT/BOOTx64.EFI
/EFI/BOOT/grubx64.efi
and in boot
/boot/grub/efi.img
/boot/grub/font.pf2
/boot/grub/grub.cfg
/boot/grub/loopback.cfg#
and in root
/autorun.inf
/ldlinux.sys
/md5sum.txt
/README.diskdefines
/syslinux.cfg
/ubuntu

This boots mine to a grub menu

---

### Post by miatawnt2b on 2016-07-12
Any updates leona? Mine is working pretty well, still haven't played with sound, the multitouch screen seems messed up, and if the display goes to sleep it won't recover. 
-J

---

### Post by leona on 2016-07-13
> **miatawnt2b said:**
> Any updates leona? Mine is working pretty well, still haven't played with sound, the multitouch screen seems messed up, and if the display goes to sleep it won't recover. 
-J
Good to hear you got yours working.
My grub menu is still messed up, still researching how to fix that.

With 15.10 mine would freeze like that, hitting power would sometimes bring it back, but I think there is an outstanding kernel bug with Atom chips where it will go to deep sleep and it can't be bought back, I hoped the fix would be in the 4.4 kernel, but guess not.

---

### Post by BzukTuk on 2016-07-13
> **miatawnt2b said:**
> I don't even have the /sound directory that you referenced above, so no sst_acpi.c file. What am I missing?Those instructions are for building your own kernel specially for this device. If you want to try it, start here [https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel) (took me many evenings until I figured how to patch and compile kernel - but there are many tutorials and guides on the net). I read somewhere that those "hacks" with sound would be implemented in mainline kernel soon.I just posted this instructions because nowere on the net is Acer Switch 10 disscused

---

### Post by leona on 2016-07-21
I've tried just about everything to rebuild grub, it refuses to find the i386-efi dir, copying i386-oc to i386-efi causes grub to crash so that doesn't work, I've tried rebuilding grub by running the live usb and tried to rebuild grub, while it detected all the operating systems it just didn't write to the right place.
The only thing I can think to do, is reinstall 15.10 or 14.04 and update from there, because no matter what I do 16.04 just will not install,  Even running the installed version with grub boot it freezes constantly, I don't know if there is any mileage in installing the 32bit version, which seems a same when we have a 64bit chip.
I'm out of options so if anyone has any ideas, I'm happy to hear them.

---

### Post by miatawnt2b on 2016-07-23
I was able to fix grub with instructions toward the beginning of the thread. Mine boots fine. As for the freezing, do a quick google search for baytrail intel idle cstate kernel param.

---

### Post by miatawnt2b on 2016-08-17
Any updates anyone?  I've put this down a few weeks, but am thinking about trying a new kernel from the repo to see if the sound fixes have made mainstream.

---

### Post by leona on 2016-08-17
Now I've got a problem trying to boot from the usb using 16.04.1
> 
set root=(hd1,gpt5)
linux /boot/vmlinuz-3.1x-xxxx  root=/dev/mmcblk0p5
initrd /boot/initrd-3.1x-xxxx
boot

I now can;t fine 
> 
initrd /boot/initrd-x.xx-xxxx

Anywhere on the system, is the 16.04.1 broken? (the key also boots straight to grub, no menu).

---

### Post by omeko on 2017-08-14
**A LITTLE UPDATE THAT MAY SAVE YOU A FEW DAYS OF MISERY**

After the [Acerium]("http://acerium.ru/english") install of Ubuntu I got dropped into the newly installed desktop after a hick-up during install mentioning grub-efi-32 errors. Turns out that if you don't want to keep your windows installation for dual boot and you run ubiquity from the GUI  ubiquity doesn't want to install any ia32 grubfiles in a newly created /boot/efi partition that is actualy marked as an efi-partition during install. Maybe it is not mounted, maybe there is some other quirk or maybe you should run it from the terminal with ubiquity --no-bootloader If it won't install, the installer fails and you also run into trouble with any DKMS functionality since that package seems to be corrupted as well.
Maybe it works okay for dual boot and/or if you do not choose to do a fresh install that eliminates the existing efi-partition on the harddisk, but there is no way for me to find out because I basically killed it all. I'm on a 32 Gb disk that doesn't even cater for any Windows-updates in standalone mode so there is no point in dualbooting with Ubuntu. There actually is no point in having windows anyway. Except maybe for the fact that it actually makes all the hardware work out of the box. 
Well never mind that. Here's a trick to actually make an acer aspire switch E10 mono-boot Ubuntu from it's harddisk in less than a week:

To get the installer to work properly, the newly created /boot/efi partition should be JUST FAT32 AND NOT EFI. Mark this partition for installing the boot stuff in the pulldown menu. The installer may assume now you're installing on a regular BIOS-setup and this happens to require a 2Mb partition with the bootgrub flag. Make sure to create one in your initial partition-setup. Store the "Y"-part in /dev/mmcblk1pY for your root-partition on an analog medium (like your memory or a piece of paper) for near-future reference.
With these two workarounds the installer will warn you multiple times that your system will probably not boot, but it won't in any other setup either, so screw that and just continue the installation. It should complete now without any errors.

Now reboot and don't remove your USB/CDrom. At grub press Ctrl-C and boot manually into your fresh installation. 
set root=(hd1,gptY)                      [where Y is the is the number of your rootpartition you stored analogy [or determined by "ls (hd1,gpt2)/" {Y=2 in my setup!}]
linux /vmlinuz root=/dev/mmcblk1pY [where Y is the number of your rootpartition you stored analogy]
initrd /initrd.img
boot

Now transform your /boot/efi partition to ef00 using gdisk and add a fat32-filesystem as you did with the Acerium-bootmedium and mount the partition as /boot/efi.
If it doesn't yet, get the wifi running by copying the r8723bs-drivers to /lib/firmware/rtlwifi (stop end restart networking) connect to a network and run:

apt-get install grub-efi-ia32 grub-efi-ia32-bin
grub-install --target=i386-efi --efi-directory=/boot/efi/
grub-mkconfig -o /boot/grub/grub.cfg

reboot and remove your livemedium just before the acer splashscreen shows.

F2 for "bios"
->secureboot enabled
->trusted uefi hdd->/grub/grubia32.efi
-> name it ubuntu-hdd
F10
F2
-> secureboot disabled
F10

and Ubuntu should boot.
If it doesn't you'll have an existing and valid efi-partition that the installer may be able to use, so try to install again using the existing partition table.

Acerium works as advertised, but I still have a sound problem. I have the headphones working and there is some sound from the speakers, but only at headphone volume. You need to downgrade the kernel to 4.8.17-27.29-acerium+MuQSS [EOL] as advertised on [http://acerium.ru/english/](http://acerium.ru/english/) to accomplish this.

---

