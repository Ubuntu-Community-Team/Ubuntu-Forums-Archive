---
title: "Problem in Configuring Grub Menu using Easy BCD"
date: 2014-11-11
forum: General Help
---

### Post by 22990atineshgmail on 2014-11-11
I've installed Windows 8.1 and Ubuntu 14.04 in dual boot. As In Grub menu Ubuntu was default entry, So I used a tool called Easy BCD in windows to configure boot menu. I followed the steps from this webpage


[http://www.maketecheasier.com/configure-the-boot-menu-windows-8/](http://www.maketecheasier.com/configure-the-boot-menu-windows-8/)


There is paragraph in the above article where they have showed how writre mbr and set windows to defalut


> 
Edit Master Boot Record


We’re nearly done, but not quite. If you now restart your computer, you will be presented with the familiar GRUB menu from which you can choose Windows or Ubuntu. If you select Ubuntu, this operating system will load as expected.


However, if you select Windows, a second menu will appear, again asking you to choose between Ubuntu and Windows. This extra step can be eliminated by using EasyBCD to replace the MBR – this is handy if you think you’re going to be using Windows more than Ubuntu.In the program, click the BCD Deployment button to the left and then select the partition containing your C: drive from the Partition menu. Select the Install the Windows Vista/7 bootloader to the MBR and click Write MBR.


But after following the above paragraph i'm getting another problem. While selecting Windows option its fine, But when I select ubuntu option then again the old Grub menu comes and then I'v to choose Ubuntu and Windows.

---

### Post by oldfred on 2014-11-11
Are systems installed in UEFI or BIOS boot mode. If UEFI you do not need EasyBCD.

Post this:
sudo parted -l

You can turn off os-prober in grub configuration, so it does not find other systems.
Add this line:
       gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
Then run this.
 sudo update-grub

If in BIOS mode we generally do not suggest EasyBCD, but some do use it.
It forces grub to be installed to the partition boot sector where it does not fit. So it converts to blocklists or hard coded addresses. Updates to grub or even fsck may move boot files on drive and booting will fail. So be sure to have a working live installer of the current version of grub to reinstall if need be.

 [http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

