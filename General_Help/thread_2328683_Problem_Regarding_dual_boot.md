---
title: "Problem Regarding dual boot"
date: 2016-06-23
forum: General Help
---

### Post by Sankalp_Mittal on 2016-06-23
Hello there.

I tried installing ubuntu 16.04 from bootable USB. I have ASUS ROG gl551vw.. When I boot from usb, I select "try ubuntu without installing". But then at time of booting (where white dots are shown and a sign of ubuntu), my PC hangs. I have tried changing the BIOS settings like disable "fast boot, intel VT" etc. I have even tried disabling secure boot. Next I even tried from bootable DVD but same thing happens.

Also I don't want ubuntu on any VMware.

I am out of options.

Please help!

Thanks in advance...

---

### Post by X-RED_Tech on 2016-06-23
It seems like graphical issues; ergo the thread subject is misleading, it would have happened without any OS installed and irrespective of the dual or single OS scenarios.

At the menu where you see "Try Ubuntu..." press F6 and select "nomodeset".

---

### Post by oldfred on 2016-06-23
X-RED_Tech is correct if a BIOS boot system. 
But is UEFI, you have to manually edit grub menu to add nomodeset.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

New UEFI hardware has 3 ways to boot UEFI with Secure boot, standard UEFI, and BIOS/CSM/Legacy emulation.
       
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

And you can boot installer in any of the three modes and that is how it will install. But then system may not be in that same boot mode. 

      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 

 But Asus seems to need other boot parameters which you add like the nomodeset one. Most often the pci=nomsi

 Asus UX303UB hardware problems - a list  15.10
[http://ubuntuforums.org/showthread.php?t=2319066](http://ubuntuforums.org/showthread.php?t=2319066)
Asus M32CD desktop - Skylake several boot parameters  pci=nomsi  i915.preliminary_hw_support=1
[http://ubuntuforums.org/showthread.php?t=2312977](http://ubuntuforums.org/showthread.php?t=2312977)
ASUS G752 Can't see SSD NVMe Needed UEFI/BIOS update
[http://ubuntuforums.org/showthread.php?t=2307273](http://ubuntuforums.org/showthread.php?t=2307273)
ASUS ROG GL552VW-CN104T
[http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)
Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files
[http://ubuntuforums.org/showthread.php?t=2327103&page=3](http://ubuntuforums.org/showthread.php?t=2327103&page=3)
[http://ubuntuforums.org/showthread.php?t=2327570](http://ubuntuforums.org/showthread.php?t=2327570)

---

### Post by Sankalp_Mittal on 2016-06-23
So I tried changing "quiet spash" with "nomodeset". Hopefully when I clicked on "[COLOR=#000000]try ubuntu without installing", this time it didn't hang at the same place. But instead when it reached a point of loading desktop, it hanged, giving me an error : ubuntu 16.04 has encountered an error. Sorry for your inconvenience.

Also I cant't find pci=".." in grub.config.

Please help.[/COLOR]

---

### Post by oldfred on 2016-06-23
You have to add it just like nomodeset. Or add both nomodeset pci=nomsi in place of quiet splash.
If that works after install, you may have to add it to grub as permanent parameter.

---

### Post by Sankalp_Mittal on 2016-06-23
So I installed ubuntu by changing [COLOR=#000000]"quiet spash" with "nomodeset" and the process was successful. But then I encountered yet another problem. System couldn't load ubuntu after installation. Hangs after loading all the drivers etc.. So should I modify the grub from [/COLOR][COLOR=#000000] "nomodeset" to "[/COLOR][COLOR=#000000]nomodeset pci=nomsi " ? What should I edit grub to ?

Edit: With ubuntu installed I cannot change the grub now. I tried "try without installing" with the above change armed with disabled secure and fast boot but the system still hangs while loading the OS.

Any ideas???[/COLOR]

---

### Post by oldfred on 2016-06-23
If you install a proprietary driver for nVidia, you then will not need nomodeset.

       sudo nano /etc/default/grub
[https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29](https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29)
GRUB_CMD_LINUX


[LIST]
[*]Entries on this  are added to the end of the 'linux' command  (GRUB legacy's "kernel" ) for both normal and recovery modes. It is used to pass options to the kernel.
[/LIST]
 GRUB_CMD_LINUX_DEFAULT="quiet splash"

[LIST]
[*]This  imports any entries to the end of the 'linux'  (GRUB legacy's "kernel" ). The entries are appended to the end of the normal mode only.
[/LIST]
     o To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash".

---

### Post by Sankalp_Mittal on 2016-06-24
I have nvidia as a rendering card. How to feed those entries to grub when my linux is installed. Shall I change grub.config and select "try without installing" instead? Shall I change [COLOR=#000000]GRUB_CMD_LINUX="" ? And to what? quiet splash or nomodeset? Because system hangs while loading ubuntu...[/COLOR]

---

### Post by oldfred on 2016-06-24
Have you added the pci=nomsi in place of or in addition to quiet splash as that parameter seems to be vital on many Asus.

---

### Post by Sankalp_Mittal on 2016-06-25
[COLOR=#000000][COLOR=#000000]I modified the grub.cfg from [/COLOR][/COLOR][COLOR=#000000][COLOR=#000000]"nomodeset" to "[/COLOR][/COLOR][COLOR=#000000][COLOR=#000000]nomodeset pci=nomsi ".. But when I click on "try without installing" the same thing happens. It's not able to "load" desktop screen of ubuntu.
Ok, let me try [/COLOR][/COLOR][COLOR=#000000]"[/COLOR][COLOR=#000000]quiet splash pci=nomsi "

Ok so here's the result of "try ubuntu without installing" :

1. [/COLOR][COLOR=#000000]"nomodeset"

There comes the black screen which loads all the drivers and utilities, but when it comes to loading the desktop screen of ubuntu, the screen hangs.

2. [/COLOR][COLOR=#000000]"[/COLOR][COLOR=#000000]nomodeset pci=nomsi "

[/COLOR][COLOR=#000000]There comes the black screen which loads all the drivers and utilities, but when it comes to loading the desktop screen of ubuntu, the screen hangs.

3. "quiet splash"

[/COLOR][COLOR=#000000] At time of booting (where white dots are shown and a logo of ubuntu), my PC hangs. 

[/COLOR][COLOR=#000000]4. [/COLOR][COLOR=#000000]"[/COLOR][COLOR=#000000]quiet splash pci=nomsi "
[/COLOR]
[COLOR=#000000] At time of booting (where white dots are shown and a logo of ubuntu), my PC hangs.  After some time say 5 min or so another purple screen comes (initial background of ubuntu desktop), and it's there that the system hangs. 

5. "[/COLOR][COLOR=#000000]pci=nomsi"
[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]There comes the black screen which loads all the drivers and utilities. After this, it asks for my ubuntu 16.04 ttyl or sth login on this same black screen. I don't know what that is. I have clicked on "try" option.[/COLOR]

---

### Post by oldfred on 2016-06-25
Are all these from installer or after you have installed?
Try option should be installer.

Are you sure you are not booting with the Intel driver. Usually system is configured to boot with Intel & only use nVidia for heavy demand of video. Not sure if automatic with Ubuntu.

If you get to terminal login:
       #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root
xrandr -q
xrandr --q1

---

### Post by banceu_sergiu_ione on 2016-06-25
I would disable all suspend option set, the fast startup and switch all to max performance.. all settings inside windows. 

Now make sure you have a good bootable [USB installed OS]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows"). 

I would also try to get a 14.04 USB bootable OS to see if that work or it is only the 16.04.

Try again with no changes in grub but with all suspend ( switch on never suspend with or with not plugged )/fast startup set off and set all to max performance from Windows. 
Keep your pc plugged and don't run on battery.
Shut down plug the USB and see if work. I would also leave the secure boot on. Since the ubuntu key must work with it.

---

### Post by banceu_sergiu_ione on 2016-06-25
> **oldfred said:**
> Are all these from installer or after you have installed?
Try option should be installer.

Are you sure you are not booting with the Intel driver. Usually system is configured to boot with Intel & only use nVidia for heavy demand of video. Not sure if automatic with Ubuntu.

If you get to terminal login:
       #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root
xrandr -q
xrandr --q1

if i understand it good, he can not log using the ' Try without install ' option since its get stuck to load screen.

---

### Post by Sankalp_Mittal on 2016-06-26
I can't login into terminal. I am dealing with "try without installing" because I can't edit the grub for already installed ubuntu. Yeah, I get stuck on load screen. sudo sth I can only type if I login successfully but I can't. Ubuntu gets stuck on load screen be it installed or without installed. Does it have to do with resolution. Auto resolution is [B]3840 pixels × [B]2160.

"[/B][/B][COLOR=#000000]Try again with no changes in grub but with all suspend".. What do you mean by this? [/COLOR]

---

### Post by oldfred on 2016-06-26
So you have installed and now can not boot either install on hard drive nor installer flash drive?

Can you get into UEFI/BIOS to change settings?

---

### Post by Sankalp_Mittal on 2016-06-27
Yes I can get into BIOS. What what should I do in that? I have tried disabling "fast boot", "secure boot" and "intel VT".

---

### Post by banceu_sergiu_ione on 2016-06-27
Have you try to boot on the live USB with any advance option selected? 

as acpi=off / select noapic / select nolapic / select nomodeset  ---- dont select all at once

try 1st 1 at time... same,time this 3 go together acpi=off / noapi /nolapic  -this will disable all the acpi system

nomodeset - will make your pc loud with generic graphic driver

Use it with a LiveCD..[here is how to activate the advance welcome page and to config boot.]("https://help.ubuntu.com/community/BootOptions")

---

### Post by oldfred on 2016-06-27
It seems that the pci=nomsi works to get to booting, but still gui issue which then is the video driver.
And if really booting with Intel, not nVidia you may need one of these in addition to the pci=nomsi

 # Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size
 i915.preliminary_hw_support=1 #Skylake some versions of Ubuntu

---

### Post by Sankalp_Mittal on 2016-06-27
I have intel HD graphics 530 skylake.

Shall I edit grub.cfg like this:

"nomodeset pci=nomsi *one of the above lines*" ?

---

### Post by banceu_sergiu_ione on 2016-06-27
try with acpi=off or noacpi

---

### Post by oldfred on 2016-06-27
Intel should not need nomodeset.

I also have Intel Skylake 530 graphics, but on a z170 motherboard Desktop system. I had no issues at all with 16.04 in UEFI mode. I have just defaults of quiet splash. But many laptops need additional parameters. 
```
    linux    /boot/vmlinuz-4.4.0-24-generic.efi.signed root=UUID=5c1e1a3f-261f-4da5-a0c2-8f479b3039de ro  quiet splash $vt_handoff
```

Do not include quotes or comments in grub's linux line like mine above. Just replace quiet splash.

---

### Post by Sankalp_Mittal on 2016-07-05
I have tried all the possible options:


1. menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper i915.preliminary_hw_support=1 pci=nomsi ---
	initrd	/casper/initrd.lz
}
menuentry

2. menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper i915.modeset=0 pci=nomsi ---
	initrd	/casper/initrd.lz
}
menuentry

3. menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper i915.i915_enable_rc6=1 pci=nomsi ---
	initrd	/casper/initrd.lz
}
menuentry

4. menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper video=3840x2160-24@60 pci=nomsi ---
	initrd	/casper/initrd.lz
}
menuentry

5. menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper video=VGA-1:3840x2160-24@60 pci=nomsi ---
	initrd	/casper/initrd.lz
}
menuentry

And every time when I click on "try without installing" I get the black screen showing :-

Ubuntu 16.04 LTS Ubuntu tty1

Login:

------------------------


Now what to do?

---

### Post by Sankalp_Mittal on 2016-07-05
Ok..Ignore the above post. I got it working by the following grub command:

[COLOR=#000000] menuentry "Try Ubuntu without installing" {[/COLOR]
[COLOR=#000000]set gfxpayload=keep[/COLOR]
[COLOR=#000000]linux    /casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper **nouveau.modeset=0** pci=nomsi ---[/COLOR]
[COLOR=#000000]initrd    /casper/initrd.lz[/COLOR]
[COLOR=#000000]}[/COLOR]
[COLOR=#000000]menuentry

I don't know why?

Now I have to reinstall ubuntu by the following changes. Inorder to uninstall, I have to format the partition and repair the boot menu. How to repair the boot menu ?

Thanks.[/COLOR]

---

### Post by oldfred on 2016-07-05
You do not have to uninstall.
If just reinstalling, use Something Else and choose(change button) the same partition that is now / (root) as new / and reformat. It will find an existing swap automatically.

You probably need the same boot option(s) [COLOR=#000000]**nouveau.modeset=0** **pci=nomsi on **first boot or until you install the nVidia proprietary driver from system settings. You may need the pci=nomsi as a permanent setting and have to modify grub to always include that, so you do not have to manually add it on every reboot.

Once installed you can edit grub:
[/COLOR] sudo nano /etc/default/grub
[https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29](https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29)
GRUB_CMD_LINUX


[LIST]
[*]Entries on this  are added to the end of the 'linux' command  (GRUB legacy's "kernel" ) for both normal and recovery modes. It is used to pass options to the kernel.
[/LIST]
 GRUB_CMD_LINUX_DEFAULT="quiet splash"

[LIST]
[*]This  imports any entries to the end of the 'linux'  (GRUB legacy's "kernel" ). The entries are appended to the end of the normal mode only.
[/LIST]
 	   o To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash".[COLOR=#000000][/COLOR]

---

### Post by Sankalp_Mittal on 2016-07-05
Ok. I messed it up. I uninstalled ubuntu as follows:

1. Formatted and deleted the partition of ubuntu from within windows. Worked well so far.
2. I restarted my PC, but then I got an error of grub 2.02. Like this: [http://i.stack.imgur.com/zzjNx.jpg](http://i.stack.imgur.com/zzjNx.jpg)
    I had to type exit to bypass this.
3. Then how should I remove this? For that I thought that I need to repair my boot menu. So I installed a software called "EasyBCD". Then I clicked on "repair boot". But nothing happened. Then I started playing around this software until I encountered this error: [http://www.prime-expert.com/articles/b18/fix-0xC0000098-windows-bcd-does-not-contain-valid-os-entry.php](http://www.prime-expert.com/articles/b18/fix-0xC0000098-windows-bcd-does-not-contain-valid-os-entry.php)


I tried all this before I could come to your above post. Now how to remove this error? My guess is that I will have to insert windows installation disc and click on "repair". But will that require product key? Because I can't find that on the back of my battery.

Thanks..

---

### Post by oldfred on 2016-07-05
UEFI has product key built in.

Do not use Windows to add or delete Linux partitions. It creates more issues than it solves.
Also restore a boot loader before deleting partitions.

With UEFI you should just be able to use UEFI boot menu or one time boot key often f10 or f12 check manual and choose the Windows entry.

---

### Post by Sankalp_Mittal on 2016-07-05
Product Key...You mean "Serial Number" under "System Information" in BIOS ?

---

### Post by oldfred on 2016-07-05
No idea what your UEFI may call it, serial number may be something different and again do not confuse UEFI Secure boot Keys with product key.

 Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)

---

### Post by Sankalp_Mittal on 2016-07-05
Can't find the key in BIOS. Maybe if I use any software. 

How can I remove this error : [http://www.prime-expert.com/articles/b18/images/boot_error_status_0xC0000098.png](http://www.prime-expert.com/articles/b18/images/boot_error_status_0xC0000098.png)

---

### Post by X-RED_Tech on 2016-07-05
You don't need to find it. It's there so you can reinstall/recover Windows whenever needed. You don't need to know the exact Windows key because you won't be asked for it during the installation/recovery. And, yes, maybe there is some (Windows) software that can retrieve it. What's the point if you can't boot Windows anyway?

You need to boot the Windows installation or recovery media and follow instructions that surely are available in the net (don't know where because I don't use Windows).

---

### Post by oldfred on 2016-07-05
I posted the link above. It says this amount other details:

> So if you need to reset or reinstall Windows 8, you don't need to hunt  for the product key. It's automatically applied and activated.

---

### Post by Sankalp_Mittal on 2016-07-06
And this has to be true for windows 10 as well, I guess?

---

### Post by Sankalp_Mittal on 2016-07-06
Ok. So I successfully repaired my boot menu by recovery usb.
Now the last problem. It's still showing ubuntu entry in bios.
I tried removing it by efibootmgr, but it seems that bios is always recreating it.
Any idea?

---

### Post by oldfred on 2016-07-06
I thought you want dual boot with Ubuntu & Windows.
If you just wanted to delete Ubuntu and install Windows, it would have been easier for use to help you in the beginning. 
You need to remove /EFI/ubuntu folder from ESP. Many better UEFI find .efi boot files in ESP and add them to menu. Then remove entries in UEFI NVRAM.

[http://askubuntu.com/questions/794725/can-i-remove-windows-boot-manager-from-dedicated-ubuntu-computer/795341#795341](http://askubuntu.com/questions/794725/can-i-remove-windows-boot-manager-from-dedicated-ubuntu-computer/795341#795341)        

Uninstall Ubuntu from menu, Really UEFI boot menu 
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu)

---

### Post by Sankalp_Mittal on 2016-07-13
Ok. Thanks. Got it. Then I will install ubuntu using nouveau.modeset=0..

---

### Post by Sankalp_Mittal on 2016-07-16
I can't edit my OP. I want to make it [SOLVED]. It says you don't have permission to edit that post ?

---

### Post by oldfred on 2016-07-16
Use Thread Tools at top above first post.

---

### Post by Sankalp_Mittal on 2016-07-16
Thanks.

---

