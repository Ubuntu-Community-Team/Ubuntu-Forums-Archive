---
title: "Everything ok but no boot"
date: 2018-04-29
forum: General Help
---

### Post by edwisosa on 2018-04-29
Hi, Im new to ubuntu, today i installed ubuntu, installed everything i though i need

i change login screen and the system dont boot up, it shows some info but i dont get it

The last thing i remember was

try to configure touchegg, didnt work so i erased the .xprofile&#8217;s file data
try to change the login screen with a wallpaper with this guide
[http://ubuntuhandbook.org/index.php/2017/10/change-login-screen-background-ubuntu-17-10/](http://ubuntuhandbook.org/index.php/2017/10/change-login-screen-background-ubuntu-17-10/)


i dont know what to do, of course i can install all over again, but i was almost ready when this happen

please help me

---

### Post by ank2 on 2018-04-29
> **edwisosa said:**
> Hi, Im new to ubuntu, today i installed ubuntu, installed everything i though i need

i change login screen and the system dont boot up, it shows some info but i dont get it

The last thing i remember was

try to configure touchegg, didnt work so i erased the .xprofile’s file data
try to change the login screen with a wallpaper with this guide
[http://ubuntuhandbook.org/index.php/2017/10/change-login-screen-background-ubuntu-17-10/](http://ubuntuhandbook.org/index.php/2017/10/change-login-screen-background-ubuntu-17-10/)


i dont know what to do, of course i can install all over again, but i was almost ready when this happen

please help me

I am not sure what causes the problem.

I suggest hitting CRTL-ALT-F4 and see if you get a login shell. Log in as user (you need the name of the user and a password you provided). Then issue

startx

to see if the GUI comes up.

---

### Post by oldfred on 2018-04-29
In testing something, I could only remember startx, and did not get full gui.
I believe this is now preferred:
 sudo /etc/init.d/lightdm restart 


What video card/chip?
UEFI or BIOS install?
What brand/model system?

      
 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by edwisosa on 2018-04-30
My laptop is a dell xps 9370, 16gb ram, ssd 512, video intel hd 620, i installed over UEFI, i just deleted windows 10 and deleted all the partitions, i create:

1 efi partition 100 MB
1 / partition 80000 MB
1 /home partition 420000 MB

I don&#8217;t know if there&#8217;s a partition missing because I just follow instruction in the internet, Im not tech savy

sorry for my bad english, I&#8217;m spanish speaker

Thanks

---

### Post by oldfred on 2018-04-30
That should be fine as long as you are installing in UEFI boot mode.
Dell often have drive set to RAID or Intel SRT. You need to change to AHCI in UEFI on drive settings.
You also probably need UEFI update from Dell.

       Dell Inspiron 3567 Review i3 7100u (Works well)
[https://ubuntuforums.org/showthread.php?t=2364642](https://ubuntuforums.org/showthread.php?t=2364642)
Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en)
Dell with NVMe needs AHCI & boot option nvme_load=YES
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en)
Dell XPS 13 9360 
[URL="https://ubuntuforums.org/showthread.php?t=2353288"]https://ubuntuforums.org/showthread.php?t=2353288
[/URL]
 Dell XPS 13 9360 16.04 worked after nvme firmware & BIOS update, 16.10 did not, new rEFInd for NVMe
[http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install](http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install) 


Edit:
Just saw this where a Dell user had to manually add an entry.
 Dell Latitude, Missing UEFI boot entry for 18.04
[https://askubuntu.com/questions/1029889/ubuntu-18-04-uefi-boot-fails-moklistrt-out-of-resources](https://askubuntu.com/questions/1029889/ubuntu-18-04-uefi-boot-fails-moklistrt-out-of-resources)

---

