---
title: "Multi-boot System and GRUB 1.14  Problem?? (SOLVED)"
date: 2017-09-18
forum: General Help
---

### Post by ken0069 on 2017-09-18
I have a multi-boot system which consists of 6 DIFFERENT Windows operating systems with each on it's own hard drive and 2 Linux systems which are also on their own drive.  For reasons I won't get into now, when I installed both versions of Linux, ie, Ubuntu 14.04 and Mint 17.3 I ran the "purge os-prober" command from terminal to keep either Linux system from trying to control my boot drive selection.  Since Ubuntu 9 I have choosen my boot drive from BIOS so there is no reason to have the GRUB boot loader do that.

Well, in the past I have unchecked the GRUB updates that come specifically to keep os-prober from possibly being reinstalled.  Fast forward to this morning when I booted up on Ubuntu 14.04 and the GRUB update to 1.14 appeared along with a kernel update so I unchecked the GRUB update and clicked installed the kernel.  

I sat and watched as the install started and the next thing I see is a list of all the other hard drives on my system go by in terminal???  A WTF moment to say the least so I hit the reset button to stop it and reboot but it appears that I was too late as I have a couple of problems showing up now.  

So on reboot I get the GRUB boot menu, which I've NEVER seen on this system before?  Click enter to boot Ubuntu and and when the desktop comes up my 24" monitor has been turned into a 22" monitor and after going into the Control Center - Monitor I found that I'm not offered any way to change the resolution at all to try to get the full screen back?  

The kernel update was from 4.4.0-93.116 to 4.4.0-96.119 and IIRC the GRUB update was from 1.12 BETA to 1.14 BETA?  Which begs the question of why BETA software was installed on my system without my permission?  

Anyway, can someone tell me how to get my Ubuntu 14.04 system back to where it was BEFORE the update screwed it up?

Thanks

Ken

---

### Post by oldfred on 2017-09-18
Default install always installs grub to drive seen as sda. Whether newer UEFI or older BIOS.
If UEFI you just have to change UEFI boot order.
If BIOS you generally have to boot install and install grub to that drive. And then reinstall boot loader (usually Windows) to drive seen as sda.

If you have multiple installs best to know what is where and document details. This report with multiple drives will be long, so only post link to pastebin site. If it does not post report, manually copy to pastebin site. (Some are having issues getting it to auto post.)

DO NOT run auto fix. That installs one grub to all MBRs, which you do not want. If using Boot-Repair to update MBR only use Advanced mode and choose operating system and drive to update boot loader.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by ken0069 on 2017-09-18
Hardware is ASUS P5Q Pro socket 775 motherboard purchased back around 2007 and does NOT have UEFI.  Has Xeon x5460 Quad core CPU and 8GB DDR2 RAM.  Ubuntu is installed on a 30GB Toshiba mSATA SSD.

Default install of Ubuntu 14.04 and all other versions of Linux has always been done with ALL other drives disconnected from the motherboard since version 9.04.  Once the install was completed and updated and BEFORE any other drives are reconnected to the motherboard I then purge os-prober so GRUB cannot be installed on any other drive.  

After this update today I went in and tried to uninstall os-prober but it is NOT installed?  That and the GRUB 1.14 update STILL appears in the Software Update screen so GRUB v1.14 was NOT installed.    

FYI, NONE of the 6 Windows drives mention anything about GRUB when I  boot to them so I'm guessing that nothing was installed on them with the  update and only the GRUB boot screen appears at boot and something is causing my monitor not to go full screen?  GRUB??  

So having said all that it "appears" that the kernel update is what caused this problem.  Would it be simpler just to uninstall the kernel update and see if everything goes back to normal?  I just want the GRUB boot screen to go away and my monitor to go full screen again and removing this kernel may be the simplest way to do that??  And can't I do that from that GRUB boot screen??  

Thanks

Ken

---

### Post by ken0069 on 2017-09-18
UPDATE:  I fixed it!  

I disconnected ALL the other hard drives except Ubuntu.  Booted up and at the GRUB boot screen I booted in the old 4.4.0-93 kernel and when it came up the monitor was full screen again!!  YAHOO!!  Rebooted it and the GRUB screen was still there so I edited the grub config file and changed the delay time from 10 to 1 second.  Saved it then opened terminal and updated grub and now it's back where it was BEFORE that kernel update.  

Thanks for your help oldfred.  I'm old Ken and 72 years old and sometimes I just have to have my mind jolted a bit to get it in gear and working correctly!

Ennywho, there WILL NOT be any more kernel upgrades on this system!!  

Thanks again........

Ken

---

### Post by oldfred on 2017-09-18
Kernel updates should not be a problem. But who knows.

I turn os-prober off in grub:
 [http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this line for os-prober:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
sudo nano /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or 
sudo sed -i '$a GRUB_DISABLE_OS_PROBER=true' /etc/default/grub
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub 

And I have 16.04LTS as main working install so use its grub as boot and add my other installs boot  into 40_custom to boot them.
      
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

---

