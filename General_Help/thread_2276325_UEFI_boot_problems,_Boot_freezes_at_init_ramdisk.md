---
title: "UEFI boot problems, Boot freezes at init ramdisk"
date: 2015-05-01
forum: General Help
---

### Post by chris377 on 2015-05-01
Hello!

As this is my first real problem after years of using Ubuntu, this is subsequently my first post ;)

I bought a new Laptop (Asus Zenbook) which came with Windows 8 and an implementation of the UEFI firmware. I created a bootable medium (usb stick...since it wouldn't recognize my SD card) and installed Ubuntu with secure boot disabled, fastboot disabled and by completely erasing the disk (since I don't want to keep the windows installation around as I simply won't be using it much). 
Anywho, that all went fine/without errors and when I wanted to reboot the system, it simply got stuck after the boot selection defaulted to the newly installed Ubuntu.
I then tried booting in recovery-mode, which seemse to stop right before/after/during (?) the init ramdisk process. It gave me several options of what I want to do and I just selected to continue booting normally...funny thing is that this actually works. My installation seems to have worked and looks intact (since, e.g. my keyboard layout is how I selected it). I tried running the boot-repair tool with the standard options and that gave me the following results (in case this may help us find the problem): [http://paste.ubuntu.com/10964767/](http://paste.ubuntu.com/10964767/)

I'm clueless right now as to what seems to be the problem, since technically I can boot it. But I would like to have everything intact and want to be able to boot normally...perhaps I missed something in the UEFI settings before/after installing Ubuntu?
From the fact that I have a /boot/efi directory I would conclude that this is a UEFI and not a BIOS installation.

I'd appreciate it if you could help me figure out what the problem is!
Cheers!

---

### Post by grahammechanical on 2015-05-01
Just to avoid confusion.

If the machine came with Windows 8 pre-installed then Windows would have been installed in EFI mode as standard. And it does seem as if Ubuntu was installed in EFI. 

When we select Recovery mode the first thing we see is that message about the ram disk because the difference between the boot parameters of normal boot and the Advanced Options boot choices is this expression 

> echo    'Loading initial ramdisk ...'

Also the Recovery Mode option will always bring us to a menu with the options of

resume - resume normal boot
clean - try to make free space
dpkg - repair broken packages
failsafeX - run in failsafe graphic mode
fsck - check file systems
grub - update grub boot loader
network - enable networking
root - drop to root shell

These options can be very useful as you have found out. Now that you can get to a working desktop using recovery>resume you can see if the problem is a video driver conflict. You  do not give much information apart from "got stuck." So, it is impossible to say what is going wrong. Just guesses.

Go to System Settings>Software & Updates>Additional Drivers tab. Allow time for the utility to find the drivers (need to be connect to the internet) and experiment with another video driver. Start with the open source video driver. If that gets a normal boot to a working desktop you can either keep the open source driver or experiment with the proprietary video drivers on offer. 

You may need to tell us about the graphic set up of the Zenbook.

Regards

---

### Post by oldfred on 2015-05-01
If you can get to recovery mode you are past what Boot-Repair can fix, other than perhaps adding a boot parameter to grub's linux line. But you can easily do that yourself if required. But Summary report does show configuration of your system.

It mentions Broadwell also. That is very new Intel chip and may really require newer kernel & video drivers than in 14.04.2. Or you may need 15.04 or use a ppa to update kernel & drives in 14.04.

You do have 3.16, but 15.04 has 3.19 and more improvements.
       Broadwell (future) fix for use with 14.04's 3.13 kernel. Fixes really in 3.15 kernel
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0ODY](http://www.phoronix.com/scan.php?page=news_item&px=MTY0ODY)
      
 Dell XPS13 - New Broadwell, not yet fully supported Feb 2015
[http://major.io/2015/02/03/linux-support-dell-xps-13-9343-2015-model/](http://major.io/2015/02/03/linux-support-dell-xps-13-9343-2015-model/)
[http://askubuntu.com/questions/395743/how-to-install-ubuntu-on-xps-15-platinum-2014-version-properly](http://askubuntu.com/questions/395743/how-to-install-ubuntu-on-xps-15-platinum-2014-version-properly)

But you may just need a boot parameter to get Intel video in correct mode.
These are the older settings, not sure if still valid with Broadwell or not:

 # Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size

You add them like nomodeset, but with Intel nomodeset usually does not work.
      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

     
 
    
And sometimes it is other boot parameters that are required. But do not know about your system.

---

### Post by chris377 on 2015-05-02
Thanks for the help guys! Adding nomodeset to the boot parameters seems to have done the trick. I just quickly went over what exactly this does and I can conduct from this that this won't result in a loss of video quality or anything similar. So the way I see it I can just leave it at that with these settings and should be fine!

---

