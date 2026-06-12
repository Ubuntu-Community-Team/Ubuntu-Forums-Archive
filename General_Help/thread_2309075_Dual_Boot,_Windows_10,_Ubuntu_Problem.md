---
title: "Dual Boot, Windows 10, Ubuntu Problem"
date: 2016-01-07
forum: General Help
---

### Post by grandpavic on 2016-01-07
I have a dual boot system that had been working fine until yesterday.

Now when I go to boot Windows the grub menu shows

"Windows Recovery Environment (loader) (on /dev/sda3)"

This leads to a window splash screen that last for about 10 second and then I get a black screen and the system goes no further.

It would seem that grub information on how to find the windows loader has become corrupted.

Any ideas on how to solve this will be appreciated.

---

### Post by oldfred on 2016-01-07
Did you update Windows or is it Windows 10 and it updated something?

Windows 10 is not in the list grub2's os-prober looks for, yet. So it ends up with the recovery description as that is the last choice in its search of matching descriptions.

Grub will not boot Windows 8 or later that is hibernated, so Windows updates may turn that on, even if  you turned it off before.

       Fast Startup off
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

If UEFI system boot directly into Windows from UEFI boot menu or one time boot key like f10 or f12.
If BIOS, you probably have to temporarily reinstall Windows boot loader to MBR, update Windows settings & then reinstall grub to MBR. Probably easier with Boot-Repair, but you can do with your Windows repairCD and Ubuntu live installer & command line.

You can install Boot-Repair to working Ubuntu or live installer each time you boot live installer.
      
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
    
You can manually create a boot stanza in 40_custom if description must read Windows 10.

---

### Post by grandpavic on 2016-01-07
Thank you for your reply. Unfortunately, much of what you are telling me is beyond my pay grade. I have some more questions.


> Did you update Windows or is it Windows 10 and it updated something?

I have been running the dual boot Windows 10 / Ubuntu system for probably 5 months now with out a problem. When I went to use my machine yesterday the Windows 10 message in grub changed. When I selected the Windows recovery menu, I go the windows 10 splash screen for about 10 seconds and then a black screen and the computer halted.

> Windows 10 is not in the list grub2's os-prober looks for, yet. So it ends up with the recovery description as that is the last choice in its search of matching descriptions.


What should I do about this?

Grub will not boot Windows 8 or later that is hibernated, so Windows updates may turn that on, even if  you turned it off before.

>        Fast Startup off
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)


Well unfortunately I was running Windows 10 in the fast startup mode. So at this point I am not even able to access Ubuntu. 

> If UEFI system boot directly into Windows from UEFI boot menu or one time boot key like f10 or f12.
If BIOS, you probably have to temporarily reinstall Windows boot loader to MBR, update Windows settings & then reinstall grub to MBR. Probably easier with Boot-Repair, but you can do with your Windows repairCD and Ubuntu live installer & command line.

The term UEFI is new to me and I not sure what it means. I don't have a Windows repair cd. What is Boot-Repair and where do I get it. I have a copy of Ubundu live (typing this reply from it).

> You can install Boot-Repair to working Ubuntu or live installer each time you boot live installer.

I will try this tomorrow and see how far I get!

Once again thank you for you help.

      
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
    
You can manually create a boot stanza in 40_custom if description must read Windows 10

---

### Post by oldfred on 2016-01-08
Link is to Boot-Repair with instructions on how to install & use it. It also has its own live repair ISO, but you can just install to Ubuntu's live installer.
Use advanced options and choose Windows and drive to install new boot loader into. You should then be able to boot Windows. Turn off fast start up. Also best to make a Windows repairCD or flash drive.
Then use Boot-Repair to restore grub to MBR.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
    
 Copy the  entries from this:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gedit /boot/grub/grub.cfg
Copy them to and edit to have only entries you want:
gksudo gedit /etc/grub.d/40_custom
sudo nano /etc/grub.d/40_custom
Then do:
sudo update-grub

Once you know your new entry works, you can turn off os-prober so remove the old entry.
      
 gksudo gedit /etc/default/grub
#Add this line:
GRUB_DISABLE_OS_PROBER=true
sudo update-grub

Same as above:
 One way to fix the descriptions is to move the windows entries to 40_custom and edit at will.
[http://askubuntu.com/questions/659528/grub-menu-with-windows-10-and-ubuntu-14-04/659910#659910](http://askubuntu.com/questions/659528/grub-menu-with-windows-10-and-ubuntu-14-04/659910#659910)

---

### Post by Swagman on 2016-01-08
You told him how to do that stuff but not where !!

When Ubuntu has booted (assuming it can) then press ctrl and t together to get a terminal and then copy & paste in one line at a time what OldFred has posted

---

### Post by grandpavic on 2016-01-08
> **oldfred said:**
> Did you update Windows or is it Windows 10 and it updated something?

Windows 10 is not in the list grub2's os-prober looks for, yet. So it ends up with the recovery description as that is the last choice in its search of matching descriptions.

Grub will not boot Windows 8 or later that is hibernated, so Windows updates may turn that on, even if  you turned it off before.

       Fast Startup off
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

If UEFI system boot directly into Windows from UEFI boot menu or one time boot key like f10 or f12.
If BIOS, you probably have to temporarily reinstall Windows boot loader to MBR, update Windows settings & then reinstall grub to MBR. Probably easier with Boot-Repair, but you can do with your Windows repairCD and Ubuntu live installer & command line.

You can install Boot-Repair to working Ubuntu or live installer each time you boot live installer.
      
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
    
You can manually create a boot stanza in 40_custom if description must read Windows 10.

I have installed and run Boot-Repair. The output of the boot diagnostics is found at:

[http://paste.ubuntu.com/14438913/](http://paste.ubuntu.com/14438913/)

Do you think that I can now go ahead and run the automated repair as is suggested at the end of the diagnostic dump?

Thank you for your continuing support.

---

### Post by oldfred on 2016-01-08
Boot-Repair's auto-fix just reinstalls grub to MBR.
Boot-Repair cannot fix most Windows issues, so best to have a Windows repairCD or flash drive and understand Windows fixes.
But Boot-Repair's advanced mode has a choice to install a Windows "like" boot loader to MBR that will boot Windows, so you can turn off fast start & make repair disk.

I think Windows 10 would be the same.
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
found this:
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)

---

### Post by grandpavic on 2016-01-08
> **oldfred said:**
> Boot-Repair's auto-fix just reinstalls grub to MBR.
Boot-Repair cannot fix most Windows issues, so best to have a Windows repairCD or flash drive and understand Windows fixes.
But Boot-Repair's advanced mode has a choice to install a Windows "like" boot loader to MBR that will boot Windows, so you can turn off fast start & make repair disk.

I think Windows 10 would be the same.
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
found this:
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)

Please remember  that much of this stuff is beyond my pay grade!

Here is the latest from Boot-Repair

[http://paste.ubuntu.com/14439471/](http://paste.ubuntu.com/14439471/)
 
The next thing I will try is to "install a Windows "like" boot loader to MBR." I will then see if I can boot windows.

Thank you for your help

Latest dump from boot-repair

[http://paste.ubuntu.com/14440454/](http://paste.ubuntu.com/14440454/)

I will see if I can now boot into Windows 10

In my last iteration I thought that I had changed the advanced options in the boot repair menu to load the windows loader into the MBR. 

So when I boot my machine, I no longer get the grub menu but I get:

BOOTMGR is missing

Ctrl+Alt+Delete to restart

Maybe I need some coaching to get the right parameters checked in the Advanced settings of the Boot-Repair

Thank you for your help

---

### Post by oldfred on 2016-01-08
Boot flag was moved from sda3 to sda2, use gparted and move boot flag back to sda3.

---

### Post by grandpavic on 2016-01-09
> **oldfred said:**
> Boot flag was moved from sda3 to sda2, use gparted and move boot flag back to sda3.

Thank you for this. I am back to the place where windows *should* boot.

Two more points, First, how do I mark this thread as solved with thanks to those who helped along the way.

The second point. Gparted tells me that the window partition (OS) is some how corrupted. I can see now that this is how I got into this mess in the first place. Windows boots and gets hung at the point where the login screen should appear. So I guess there must be one or more files that are corrupted. I can do a "safe" boot. So at this point I will ask questions in the Windows 10 forum.

Thanks to everyone who helped along the way.

---

### Post by oldfred on 2016-01-09
Often that is why you need a Windows repairCD or flash drive.
You may be able to use f8 if Windows just barely starts to get into its internal repair console.
Often chkdsk or other repairs are then required.

Above first post is [Solved] in thread tools.

---

