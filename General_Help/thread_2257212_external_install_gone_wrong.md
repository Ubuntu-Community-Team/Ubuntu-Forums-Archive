---
title: "external install gone wrong"
date: 2014-12-17
forum: General Help
---

### Post by Jacob_Jackson on 2014-12-17
alright, so here lies the problem.
initially, I went to install Ubuntu on my external 2TB. after some issues, I decided I would work on it later, and decided to revert to plain old windows (seeing how I paid quite a bit for my laptop) and I didn't want to severely mess anything up. after going through issues with GRUB, and finally getting it to let me use windows, I did a complete format on my laptop. it ran into major errors, wouldn't let me completely format. so I got it to let me just format my C: drive. but its still popping up errors left and right. my installation of windows is installed into my computer, so I don't have a recovery disk (msi uses the F3 reboot). any help on how to completely rid my laptop of Ubuntu, so I can start from scratch at a later date and time?
any other info required, just ask.

---

### Post by nerdtron on 2014-12-17
Well I can't say about windows 7, but I think the error you experience is the GRUB is installed on the internal disk instead of the external drive.
Next time you install it's better to disconnect any internal drive and just install on the external 2TB. Or you should just use the "Something Else" option for choosing where to install the GRUB Bootloader.

Sorry, just passing by... Maybe you can tell the model of your laptop so that other members can get the idea on your situation.
And you should probably say here any Errors that you encountered like what is written on the screen when you boot windows so that we can start troubleshooting.

---

### Post by Jacob_Jackson on 2014-12-17
sorry, my post was a little vague. 

I'm running an MSI gt70.
8gb ddr3
intel i7 processor 2.7Ghz
NVidia GeForce GTX870m 
intel HD graphics 4600
Killer e2200 gigabit Ethernet controller

the problem is no longer the starting up, everything starts up. however, if it did not come stock with the laptop instillation, (ie firefox, chrome, VLC, adobe photoshop) it will not work, or update. even my graphics card is refusing to update. and even then, some of the programs that are installed by default are refusing to work at all, or force close as soon as opened. I does not say any errors when I try to reinstall, just "something went wrong, task can not be completed"
none of these issues occurred until I went to install Linux. and I have never had any of these problems after installing Linux on any of my previous computers.

---

### Post by Jacob_Jackson on 2014-12-17
to add to the issues list, im also getting an error on my rapid storage saying that its at risk of degrading, which did not pop up until I ran into my errors with Ubuntu, although it doesn't tell me th eexact issue.

---

### Post by Jacob_Jackson on 2014-12-26
to bring into more news on this, i made a recovery disk with the same OS on my external HD, but when i go to recovery to install from the external HD, the only thing it brings up options for is ubuntu. i know there is no copy on there for sure because i formatted it, then made the backup, but i still cant get an option to load into windows recovery. any help?

---

### Post by yancek on 2014-12-26
I'm not sure what the problem is.  A Recovery disk of what, your windows?  If you have a windows recovery disk, you should boot from the CD/DVD drive with the disk in the drive.  What are you trying to install "from" the external?  You said you formatted it so there would be nothing there.  What are you able to boot if anything?

---

### Post by Jacob_Jackson on 2014-12-26
im booting Windows 8 from my external, because the recoverty option is normally self installed. i created a startup on my external, but the only thing it will show is ubuntu. windows 8 is installed by itself, including the reovery. i made a copy of the recovery and tried to  run in reovery mode off of my external, but the only option it shows is ubuntu

---

### Post by oldfred on 2014-12-26
Is this an Ultra-Book with the small 16GB to 32GB SSD to make for fast boot.
That usually is Intel SRT or related technology. 

        Intel Smart Response Technology
[http://mjg59.dreamwidth.org/26022.html](http://mjg59.dreamwidth.org/26022.html)
For GPT systems, this needs to have a type GUID of D3BFE2DE-3DAF-11DF-BA-40-E3A556D89593. 
For MBR systems, you need a partition type of 0x84[2].
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
[http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology](http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology)
[http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf](http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

Did you turn off SRT in UEFI before installing Ubuntu? Also fast boot and secure boot settings in UEFI?

Boot-Repair cannot fix most Windows issues as you usually need a Windows 8 repair flash drive and a full image copy or backup of your Windows. But it can show configuration to see if it still looks normal. Beyond that then it is just Windows/UEFI settings and repairs. 

Windows has this, but I do not have Windows so do not know much about it and how well it works with your OEM or vendor installed version.
[http://windows.microsoft.com/en-us/windows-8/restore-refresh-reset-pc](http://windows.microsoft.com/en-us/windows-8/restore-refresh-reset-pc)

      
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Jacob_Jackson on 2014-12-27
i have made a flash drive to make a reinstall for windows. but when i go to select "install from usb/CD/dvd" the only option it gives me is ubuntu. and i know there is no ubuntu on the external hard drive, since i completely formatted it before making an install disk from another computer of mine running windows 8. but i have noticed that i have extra partitions that i dont remember formerly being there. the only problem, i dont know which wasnt there to begin with. could it be possible, since it asked to put in a buffer zone, that its still trying to catch off of it? [ATTACH=CONFIG]258817[/ATTACH]
im showing that i have 2 different recovery partitions (which i should only have 1, if im right?) my D: drive now automatically turns raw after a format, i have an EFI system partition, and my os_install.
would i be correct in assuming that one of these things doesnt belong here??

---

### Post by oldfred on 2014-12-27
You are missing a partition.
Windows normally has a recovery partition which is really just the repair console. Vendors have a recovery partition which is the image of the hard drive as purchased. Then if an UEFI install Windows needs the efi partition which is used by all UEFI installs including Ubuntu. Then with UEFI Windows has its system reserved a small 128MB unformatted partition which you do not seem to have, and the main install.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)

---

### Post by Jacob_Jackson on 2014-12-28
[http://paste.ubuntu.com/9633230/]("https://paste.ubuntu.com/9633230/")

this is what the boot-repair-disk logged.

---

### Post by oldfred on 2014-12-28
Looks like a normal Windows partition plan.
External drive not shown?

Script could not mount sda5. Is that from Intel SRT so is a cache? Then that would be normal that is it not seen. Otherwise is is a corrupted partition, but cannot tell what it is otherwise.

Ubuntu boot files are in efi partition on sda2. 
I prefer to have boot files in efi partition on same drive as install. But even when I was very specific in my system in a second Ubuntu install on hard drive it overwrite my main install's boot on SSD. I had to reinstall grub. Since Windows nothing was overwritten. If you have an efi partition on external you can just copy the ubuntu efi folders from internal drive to external drive. I did that and then reinstalled grub for main working install on my SSD.

---

