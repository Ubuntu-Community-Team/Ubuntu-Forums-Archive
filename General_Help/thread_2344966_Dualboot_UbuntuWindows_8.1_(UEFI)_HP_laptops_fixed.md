---
title: "Dualboot Ubuntu/Windows 8.1 (UEFI) HP laptops fixed now?"
date: 2016-11-29
forum: General Help
---

### Post by t0p on 2016-11-29
I have a HP laptop, model hp15-g261sa.  I tried installing Ubuntu in, I think, 2014,. as a dual-boot with the Windows 8.1.  I followed various "tutorials", but none came to anything, and last I heard was HPs with UEFI were notoriously difficult/impossible to dual-install with Ubuntu.  I gave up after that, resigning myself to Win8.1 and the extra malware probs etc associated with that brand.

Now I'm back, hoping maybe a newer version of Ubuntu might work.  Can anyone point me in the right direction please?  Remember, this is a HP15 laptop  I'm writing about here - tutorials which apparently work with other model laptops never worked with HP laptops in the past.  Has the Free Software society found out how to get around Windows' UEFI trap?

Or are there other decent Linux distros that I'd be able to install?  I've always liked Ubuntu, but a shift in distro may be acceptable... so long as it doesn't presuppose much knowledge of Windows OSes (I have none).

Please can anyone help?

Thanks.

---

### Post by Frogs Hair on 2016-11-29
My HP is a bit older and required the removal of the HP tools before dual booting. It was the four partitions that were the problem for me not UEFI. I don't know if this is applicable in your case. I did not use the HP tools to create a bios password which can't be removed once the tools are removed thus making it almost impossible to dual boot without reinstalling the HP tools.

---

### Post by oldfred on 2016-11-29
UEFI makes it more complicated.
And with HP, it  is more difficult but not impossible. Many have installed and done a work around to make it work

If Windows is UEFI, and Windows 8 would be, then better to install Ubuntu in UEFI boot mode.

From link below in my signature:
**Summary UEFI install instructions:**
Back up Windows, your data, and make a Windows repair flash drive.
Download and create Ubuntu 64 bit  installer, flash drive or DVD.
Only use Windows own Disk Management tools to shrink Windows & reboot so it can run chkdsk.
Turn off Windows fast startup in Windows.
In UEFI turn off fast boot (different than fast start up) and often  better but not required to turn off Secure boot (may be called "other"  vs. "Windows"), some may need CSM mode on, but still select UEFI
Some UEFI may need you to turn on or allow USB/DVD boot, especially if Secure boot is on.
Boot Ubuntu installing in UEFI live mode, and verify your system works ok.
Install Ubuntu.
Create backup procedure for your data and configuration files.
If Issue with install, more info needed, or terms not understood, see info & links below:

And HP specific installs:
       HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216)

Most HP use the fallback or hard drive boot entry. Some HP have that UEFI entry which boots /EFI/Boot/bootx64.efi. Some may have that folder in the ESP, but not have entry in UEFI. And some need both entry in UEFI & files.
Boot-Repair using its advanced mode will now copy shimx64.efi to bootx64.efi so you have files, but will not create UEFI boot entry.

 Boot-Repair now creates  bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI. 
     'Use the standard EFI file' in advanced options.       
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Older HP UEFI installs manually copied files which you can do, if you do not want to run Boot-Repair.
       HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by t0p on 2016-11-29
**oldfred **thanks a lot for all that info.  I shall take some time to ensure I understand what I need to check and do, then I'll give it a go and report back to let other HP15 users know what I did and how it worked out.

It's a shame the past couple of Ubuntu releases haven't returned us to the BIOS days when you could just create/edit partitions and tell the installer to install Ubuntu next to the pre-existing Windows OS on the hard drive.  I hope a/some Ubuntu developer/s can some day return us to those days of simplicity.  I've used Ubuntu on and (sometimes) off since Breezy, and have witnessed installation go from a bit complex to not so complex to easy and now to rather complex again.  I prefer simplicity.  And Win 8.1 just isn't simple to me.  Very sad.  :(

---

### Post by oldfred on 2016-11-29
Well I do not have Windows.
I create multiple / (root) partitions. And just install. And new install works & I can also boot older installs.

And even with UEFI just select a partition, change it to /, ext4 and install.
The only thing with installing another Ubuntu in UEFI mode is that it overwrites my LTS version in the ESP which I really want as default boot. But I quickly learned to back the entire ESP up. But new install really only changes /EFI/Ubuntu/grub.cfg with new partition & UUID, so I copy old one back.

---

