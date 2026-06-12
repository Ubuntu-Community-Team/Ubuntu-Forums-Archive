---
title: "Grub dual boot on separate drives, wont boot into windows 10"
date: 2016-08-03
forum: General Help
---

### Post by acdcman200 on 2016-08-03
So last night I wiped my entire system due to the anniversary update for windows 10 getting stuck at 83 percent for several hours. I decided just to do a clean install of everything since I hadent done it in a while and decided with this major update I may as well. I decided to also reinstall Linux while I was it. (Yes I backed up my data to a separate drive and unplugged it so I wouldn't loose my data). 

I installed windows 10 1 of my  ssds and then installed Ubuntu to my other ssd. I set my first boot option to the Ubuntu ssd so that grub would come up so I could choose my os. 

Ubuntu works fine and boots normally. (I got GNOME and other settings set up along with mounting my drives properly) 

When I select windows 10 boot loader from grub I get this error

Error: No such device
Error: Cannot get C/H/S values.

I went into my bios and did a boot override to my windows ssd. It booted up fine. 

I thought that Grub might need to be updated so I ran [sudo update-grub] It said that it found my Windows 10 drive. Upon a restart it still gave me the same error when I selected windows 10.

---

### Post by ajgreeny on 2016-08-03
See Boot-Repair in my signature and from that run the boot-info-script.

Do not accept the default repair at the moment; just run the script and post back here with the pastebin link you are sgown for the report.

---

### Post by acdcman200 on 2016-08-03
> **ajgreeny said:**
> See Boot-Repair in my signature and from that run the boot-info-script.

Do not accept the default repair at the moment; just run the script and post back here with the pastebin link you are sgown for the report.

Here is the boot report
[http://paste2.org/skcY2xfd](http://paste2.org/skcY2xfd)

---

### Post by oldfred on 2016-08-03
You have a new UEFI based system, but have both Ubuntu & Windows installed in the 35 year old BIOS/MBR configuration. That will work, just old configuration on new hardware.

With Windows 10 you must make sure UEFI Secure boot is off. Boot-REpair was booted in UEFI mode and indicated that was off.

And you must have Windows fast start up off which really  is always on hibernation. Grub will not boot a Windows system that is hibernated nor if it needs chkdsk. Best to have Windows repair flash drive for Windows repairs.
       Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[URL="http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html"]http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html

[https://support.microsoft.com/en-us/help/12415/windows-10-recovery-options](https://support.microsoft.com/en-us/help/12415/windows-10-recovery-options)
[http://answers.microsoft.com/en-us/windows/wiki/windows_10/how-to-create-a-recovery-drive-for-reinstalling/58df9c7d-84de-4652-9952-8bac34abc6c5](http://answers.microsoft.com/en-us/windows/wiki/windows_10/how-to-create-a-recovery-drive-for-reinstalling/58df9c7d-84de-4652-9952-8bac34abc6c5)
[/URL]

---

### Post by acdcman200 on 2016-08-04
@oldfred
Yes I disabled that already.(both windows fast startup and uefi secure boot)

For your first thing about a 35 year old config. How would I go about update that for my hardware to the new eufi standard?

Apologies for the reply post in the windows 7 thread, for some reason he reply button posted there.

---

### Post by oldfred on 2016-08-04
I do not think it is possible to convert Windows.
And you can only convert Ubuntu from BIOS to UEFI if you installed on gpt partitioned drive.

There are ways to convert from MBR to gpt, supposedly without losing data, backup still required, but then you do not have standard UEFI partitions.

How you boot install media for both Windows & Ubuntu is then how it installs. In UEFI you have two entries for a flash drive installer. One is UEFI:flash drive and other (BIOS) is just flash drive or name, label of flash drive. 

So if you want to convert it is just about backup all data and configurations you have done. And reinstall. Good practice on backup procedures & install processes. They say you do not know if you have a good backup unless you know you can restore from it. But you will not be able to use any image backups as those are the BIOS/MBR.

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

In link below I have a lot more info on UEFI/gpt, it is a lot especially if you follow links to even more info, but best at least to review.

---

### Post by acdcman200 on 2016-08-04
> **oldfred said:**
> I do not think it is possible to convert Windows.
And you can only convert Ubuntu from BIOS to UEFI if you installed on gpt partitioned drive.

There are ways to convert from MBR to gpt, supposedly without losing data, backup still required, but then you do not have standard UEFI partitions.

How you boot install media for both Windows & Ubuntu is then how it installs. In UEFI you have two entries for a flash drive installer. One is UEFI:flash drive and other (BIOS) is just flash drive or name, label of flash drive. 

So if you want to convert it is just about backup all data and configurations you have done. And reinstall. Good practice on backup procedures & install processes. They say you do not know if you have a good backup unless you know you can restore from it. But you will not be able to use any image backups as those are the BIOS/MBR.

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

In link below I have a lot more info on UEFI/gpt, it is a lot especially if you follow links to even more info, but best at least to review.

So just wipe my drives and reinstall windows 10 first and then Ubuntu? In the boot select screen I need to select the flash drive that says uefi on it correct? I already have backups of both systems(files and folders, not the core os) on my d drive as I store everything of importance there. (Plus I just installed these operating systems a few days ago, not like there is anything of importance on them)

---

### Post by oldfred on 2016-08-04
Converting from MBR to gpt will in effect erase drive, or your D drive is also removed.
You could copy data to other drive, repartition first drive and then copy data back to first drive after converted to gpt.
Is your d: drive the sdc drive? That already is gpt, so changes to sda & sdb will not change that unless you select it by mistake.

But best to have backups on external device. While I do do "backups" from one drive to another, I do not really consider them as my real backup. Only an full copy to another device. I regularly copy most critical data to DVDs and/or flash drives.

---

### Post by acdcman200 on 2016-08-04
> **oldfred said:**
> Converting from MBR to gpt will in effect erase drive, or your D drive is also removed.
You could copy data to other drive, repartition first drive and then copy data back to first drive after converted to gpt.
Is your d: drive the sdc drive? That already is gpt, so changes to sda & sdb will not change that unless you select it by mistake.

But best to have backups on external device. While I do do "backups" from one drive to another, I do not really consider them as my real backup. Only an full copy to another device. I regularly copy most critical data to DVDs and/or flash drives.

I just unplugged the drives sata power cable and formatted both ssds. I just installed windows 10 via uefi onto one of the ssds. I am about to install Ubuntu onto the other one. Is it necessary for me to back up my d (backup and mass storage drive) and format it or can I just leave it alone and just mount it how I had it before?

If I need to back it up and format it that is no problem, it will just take a little bit of time.

Thanks for your help this far I really appreciate it.

---

### Post by oldfred on 2016-08-04
On what drive is D:?
If on SSD, yes you need to back it up. 
If on sdc and unplugged then it will not matter.

Also note that with UEFI, grub only installs boot loader into the ESP - efi system partition on drive seen as sda. I still put an ESP on sdb, but it normally is not used. I manually copy boot files back from sda to sdb, just in case sda has issues. But ESP on sda is used for both Windows & Ubuntu/grubs boot files.

If you disconnect Windows SSD, UEFI may lose its NVRAM entries for Windows. Most UEFI will refind the Windows entries with a couple of cold boots. Only UEFI cold boot checks system for changes, a warm reboot does not check for any system reconfiguration or changes. Makes boot faster, but when reconfiguring, you are not sure if changes are there or not.

---

### Post by acdcman200 on 2016-08-04
Install went smoothly, however upon boot I'm greater with a CLI grub interface. How do I make it go to the graphical one with the operating systems listed properly?

Edit- Figured out that I needed to type exit in CLI to get to a GUI interface. 

Would it be ok if i do that boot log agian so you can verify I set it up properly this time?

Thanks

---

### Post by oldfred on 2016-08-04
What brand/model system? 
Some need work arounds to let you directly boot ubuntu/grub as default.

Post new link to summary report.

---

### Post by acdcman200 on 2016-08-04
> **oldfred said:**
> What brand/model system? 
Some need work arounds to let you directly boot ubuntu/grub as default.

Post new link to summary report.
It is a custom computer I built. The motherboard is a gigabyte z97 x sli.


Also you wouldn't happen to know how to get the Nvidia x server settings for screen resolution to save would you? I run 2 144hz monitors so I need the proprietary Nvidia drivers to set the refresh rates. the issue is the resolution and therefore the refresh rate set to auto after every system restart so I have to set it up so that Nvidia x server settings boots up so I can change the settings and restart.

Boot report 

[http://paste2.org/7gFMVVh9](http://paste2.org/7gFMVVh9)

---

### Post by oldfred on 2016-08-04
I have an Asus z97 and a Gigabyte Z170. With both I had to change a lot of UEFI settings. And keep track as UEFI updates from vendor reset back to default and I have had to redo settings.

Did grub install ok to sdb?
I did see a new update to grub and have not tried installing grub to sdb, since. Everytime I try to install grub to anything other than sda it still defaults to sda. And users without ESP on sda could not get grub to install at all.

How did you install nVidia drivers? From ppa?
Can you boot with nomodset?

I just on Asus system have an older nVidia 620GT, and that only because I misplanned and motherboard had one set of ports & monitor had nothing that matched.
I am still running Nouveau.

         # list drivers available, same list as system settings,  software updates,  additional drivers or last tab
ubuntu-drivers devices
# or
ubuntu-drivers devices | grep recommended 


 #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA

---

### Post by acdcman200 on 2016-08-04
> **oldfred said:**
> I have an Asus z97 and a Gigabyte Z170. With both I had to change a lot of UEFI settings. And keep track as UEFI updates from vendor reset back to default and I have had to redo settings.

Did grub install ok to sdb?
I did see a new update to grub and have not tried installing grub to sdb, since. Everytime I try to install grub to anything other than sda it still defaults to sda. And users without ESP on sda could not get grub to install at all.

How did you install nVidia drivers? From ppa?
Can you boot with nomodset?

I just on Asus system have an older nVidia 620GT, and that only because I misplanned and motherboard had one set of ports & monitor had nothing that matched.
I am still running Nouveau.

         # list drivers available, same list as system settings,  software updates,  additional drivers or last tab
ubuntu-drivers devices
# or
ubuntu-drivers devices | grep recommended 


 #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA

I installed my Nvidia drivers via the additional drivers tab changing the drivers from the open source ones over to the Nvida one listed there. Am I supost to get it from a different place if so how would I go about installing them?

---

### Post by oldfred on 2016-08-04
Depending on version of Ubuntu and version of nVidia cards, the repository may be ok.
If new 1070 or 1080, you need the very newest drivers from nVidia. Then you add a ppa.

       Ubuntu Launches Its "Fresh" Proprietary Driver PPA - August 2015
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa) 
   # Shows standard repository versions
ubuntu-drivers devices
sudo apt-add-repository ppa:graphics-drivers/ppa
# should show newest versions available in addition
ubuntu-drivers devices 

But if you have installed one version of nVidia driver, you must purge that before installing any other, or else you get major conflicts.

 Lists installed version, in/with your kernel:
dkms status
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*
Do not know if a xorg.conf is still created or not. If not found that is ok.
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 

Did you install nvidia-settings?
      sudo apt-get install nvidia-settings 
    The nvidia-settings utility is a tool for configuring the NVIDIA
Linux graphics driver.

---

### Post by acdcman200 on 2016-08-04
> **oldfred said:**
> Depending on version of Ubuntu and version of nVidia cards, the repository may be ok.
If new 1070 or 1080, you need the very newest drivers from nVidia. Then you add a ppa.

       Ubuntu Launches Its "Fresh" Proprietary Driver PPA - August 2015
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa) 
   # Shows standard repository versions
ubuntu-drivers devices
sudo apt-add-repository ppa:graphics-drivers/ppa
# should show newest versions available in addition
ubuntu-drivers devices 

But if you have installed one version of nVidia driver, you must purge that before installing any other, or else you get major conflicts.

 Lists installed version, in/with your kernel:
dkms status
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*
Do not know if a xorg.conf is still created or not. If not found that is ok.
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 

Did you install nvidia-settings?
      sudo apt-get install nvidia-settings 
    The nvidia-settings utility is a tool for configuring the NVIDIA
Linux graphics driver.

So to be clear I should run the following commands for a 970
Removing the old driver
1) Change drivers to the open source drivers then restart
2) dkms status
3) sudo apt-get remove --purge < nvidiadriverpackagename>
4) sudo apt-get purge nvidia*
5) Restart




Installing the new driver
1) [COLOR=#333333]sudo add-apt-repository [/COLOR][COLOR=#333333][FONT=inherit !important]ppa:graphics-drivers/ppa
2) sudo apt-get update
3) [/FONT][/COLOR][COLOR=#333333]sudo apt-get update && sudo apt-get install nvidia-355
4 Restart
5) In the additional drivers tab change to Nviida 
6) restart

If these are not right could you please tell me where I went wrong and list the proper order/commands for me to run?

Thanks[/COLOR]

---

### Post by oldfred on 2016-08-04
With your 970, the version in the repository should be ok. 
The ppa shows 367 as the newest.

What was the newest in the standard Ubuntu repository that you get, I would think it is this:?
fred@Asusz97:~$ ubuntu-drivers devices | grep recommended 
driver   : nvidia-361 - distro non-free recommended

Then if you want or need a driver newer than 361 you add the ppa and install that after totally purging the current driver you have.

---

### Post by acdcman200 on 2016-08-05
> **oldfred said:**
> With your 970, the version in the repository should be ok. 
The ppa shows 367 as the newest.

What was the newest in the standard Ubuntu repository that you get, I would think it is this:?
fred@Asusz97:~$ ubuntu-drivers devices | grep recommended 
driver   : nvidia-361 - distro non-free recommended

Then if you want or need a driver newer than 361 you add the ppa and install that after totally purging the current driver you have.

Okay thank you install went smoothly and I now have Nvidia version 367 installed and running. However I still have the problem with my settings not saving after a restart 

I have already tried [sudo nvidia-settings], I am able to change the settings and apply them but then upon restart I loose them. Any ideas what I am doing wrong? (I am trying to get it to save my 144hz screen settings and the prefer maximum performance in the power mixer settings.)

---

### Post by oldfred on 2016-08-05
Did you purge previous version of nVidia?
Installing a new one does not correctly overwrite/replace old one. 
You must purge all traces of old nVidia driver before installing new one.

       Lists installed version, in/with your kernel:
dkms status
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*
# This may not exist, so if not found that is ok.
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

---

### Post by acdcman200 on 2016-08-05
> **oldfred said:**
> Did you purge previous version of nVidia?
Installing a new one does not correctly overwrite/replace old one. 
You must purge all traces of old nVidia driver before installing new one.

       Lists installed version, in/with your kernel:
dkms status
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*
# This may not exist, so if not found that is ok.
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup


Yes I purged the old copy complexly and then installed a clean copy as you said to do. The driver is now up to date and cleaned out but It still wont save the settings after a restart.

---

### Post by oldfred on 2016-08-05
I have seen a variety of older threads with 970 or 980 nVidia.
And almost all were resolved with install of newest available nVidia driver.

Not sure if any were sli. And then what extra issues that may cause.

These are old, so not sure if anything now applies:
 [http://askubuntu.com/questions/778670/ubuntu-16-trying-to-set-up-3-different-monitors](http://askubuntu.com/questions/778670/ubuntu-16-trying-to-set-up-3-different-monitors)
With xorg.conf - older 
[https://help.ubuntu.com/community/NvidiaMultiMonitors](https://help.ubuntu.com/community/NvidiaMultiMonitors)
ARandR Screen Layout Editor 0.1.4 - Dual screens
[http://christian.amsuess.com/tools/arandr/](http://christian.amsuess.com/tools/arandr/)
Dual nVidia cards - 2013
[http://ubuntuforums.org/showthread.php?t=2129190](http://ubuntuforums.org/showthread.php?t=2129190)

---

### Post by acdcman200 on 2016-08-05
> **oldfred said:**
> I have seen a variety of older threads with 970 or 980 nVidia.
And almost all were resolved with install of newest available nVidia driver.

Not sure if any were sli. And then what extra issues that may cause.

These are old, so not sure if anything now applies:
 [http://askubuntu.com/questions/778670/ubuntu-16-trying-to-set-up-3-different-monitors](http://askubuntu.com/questions/778670/ubuntu-16-trying-to-set-up-3-different-monitors)
With xorg.conf - older 
[https://help.ubuntu.com/community/NvidiaMultiMonitors](https://help.ubuntu.com/community/NvidiaMultiMonitors)
ARandR Screen Layout Editor 0.1.4 - Dual screens
[http://christian.amsuess.com/tools/arandr/](http://christian.amsuess.com/tools/arandr/)
Dual nVidia cards - 2013
[http://ubuntuforums.org/showthread.php?t=2129190](http://ubuntuforums.org/showthread.php?t=2129190)

That did not fix it, but I will open a new thread and mark this one as solved since we fixed the thread issue

---

