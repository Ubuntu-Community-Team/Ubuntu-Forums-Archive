---
title: "Boot Up Issues"
date: 2013-08-18
forum: General Help
---

### Post by orioles_fan on 2013-08-18
Hey everyone,

I recently installed Ubuntu 13.04 on my Lenovo U310 and absolutely love it. I removed Windows 8 so currently, Ubuntu is the only operating system on this computer.

I was never having issues booting into Ubuntu until a few days ago. Normally, my screen would turn on, the purple/magenta color would fill the screen, the screen would turn off, and then come back on with the normal Ubuntu loading screen (this is all within a span of maybe 5 seconds). Lately, I've had instances where the screen just turns on but never goes anywhere. This morning was the first time that it just loaded to a single flashing underscore.

Every time this happens, I can simply turn off the computer and restart it. Then it will load up in GRUB (something I normally don't see) and select Ubuntu. Then from there, the issue will go away for a while. 

It's not a deal breaker by any means but it is an weird quirk that I'd like to fix, especially since I'm paranoid that one day, restarting won't fix the issue.

Just some background info, my Lenovo U310 has two drives, a 24GB SSD and a 500 HD. I installed the root directory onto the SSD and everything else is on the 500GB HD. Booting in under 5 seconds is nice. :)

---

### Post by oldfred on 2013-08-18
Not sure if in UEFI mode or BIOS mode. Best to see details. Since it is not every time it may be difficult to resolve. Does system shutdown correctly? As that can cause grub to boot differently.

You can run from your working system, or from your Ubuntu install flash driver, or download a full repairCD or DVD/flash version that also is an installer.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by orioles_fan on 2013-08-18
Thanks for the reply!

I am currently in UEFI mode (I installed Ubuntu in UEFI mode as well).

Here's my boot info: [http://paste.ubuntu.com/6001035/](http://paste.ubuntu.com/6001035/)

Also, here's a picture on my boot menu:
[IMG]https://dl.dropboxusercontent.com/u/83302623/Photo%20Aug%2018%2C%206%2024%2039%20PM.jpg[/IMG]

Please disregard the USB 3.0 Toshiba drive. That's an external I ran a backup on and forgot to unplug prior to this test.

---

### Post by oldfred on 2013-08-18
Not sure if this is an issue or not. But UEFI spec says the efi partition is to be first. But Windows makes it second or even third but only tiny recovery partitions are before it. 
Not sure why spec says first but I assumed the UEFI FAT driver may not read far into new large drives, so easier just to say first.
I also prefer to have an efi partition on every drive, and since you are booting from sda or the SSD it may make more sense to have the efi partition on the 24GB drive.

I do not like moving the start of partitions, but that would be the only way to create an efi partition at the beginning of a drive. Be sure to have good backups.

Your efi partition still has the Windows efi files. You may want to back up and delete those. You may also have to use UEFI shell to delete entries in UEFI menu as it also saves entries. Some UEFI have the shell as a menu entry directly.

       Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

### Post by orioles_fan on 2013-08-18
Could you walk me through these different steps? Would it just be easier for me to run Deja-Dup, make a backup, and then reinstall Ubuntu with the root and EFI partitions on the SSD and the home and swap partitions on the HD?

Thanks for your help!

---

### Post by oldfred on 2013-08-18
If you have not made any system configuration changes which are in /etc, then you can just repartition the SSD and reinstall using Something Else. When you choose to mount the /home just DO NOT reformat it and all your existing data from /home and user settings will be the same.
If you did some system wide changes in /etc and are installing the same version you may restore the files you changed. I do not like to reinstall all of /etc as new install may not need new settings, but if same version it should be ok.

I have never used Deja-Dup as I just use rsync.
       Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)


 Some files to exclude from /home backup - post by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

      
 More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

---

### Post by orioles_fan on 2013-08-19
I really haven't changed much of anything, which is why I was so surprised when things started getting kinda wonky. I almost wish it was a consistent problem so it was easier to diagnose. I find it strange that I was booting to a flashing underscore only yesterday but have not had a single issue since then. I've installed a few programs but nothing out of the ordinary at all.

So, you're saying to basically put everything on the SSD, and put only the /home and maybe /swap on the HD? I honestly don't have a lot on here so I'm not really nervous of completely wiping the computer clean and starting fresh. The Lenovo came with SO many partitions and Windows data scattered everywhere that I'd rather do a "scorched earth" reinstall and now that everything is completely clean.

Is this something that a simple Boot-Repair would fix (ie: running the actual fix rather than the report)?

---

### Post by oldfred on 2013-08-19
Another thread, not sure if user discussed anything that would help.
  lenovo u310  - install to SSD
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)

With the SSD, it is an Ultrabook which has dual video. Did you install Bumblebee? Info in link in my signature on Ultrabooks.

---

### Post by orioles_fan on 2013-08-19
> **oldfred said:**
> Another thread, not sure if user discussed anything that would help.
  lenovo u310  - install to SSD
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)

With the SSD, it is an Ultrabook which has dual video. Did you install Bumblebee? Info in link in my signature on Ultrabooks.

I have not. I thought the only video I had in my U310 Touch is the Intel HD 4000 Integrated Graphics.

In regards to that thread, those are actually the instructions that I followed the first time before I decided to be rid of Windows completely. If I reformat the current EFI partition on the HD and make a new one on the SSD during the Ubuntu install process, will that cause any issues?

Basically, what I'm planning on doing now, is reformatting everything and reinstalling. So, I would reformat the entire SSD and HD. Then I would put / (root), /etc, and /efi on the SSD and put /home and /swap on the HD. Would this be a much better setup than what I currently have? Is putting the /swap partition on the SSD worthwhile? I have 24GB to work with on that SSD. Also, I would install in UEFI mode (or should I change it now that I don't need/have Windows)?

I already felt that my install of 13.04 wasn't entirely clean, just because of the partitions and things that were left from Lenovo and Windows. I have zero desire to retain any of that information or put Windows on this computer again. I'm hoping that just wiping the slate clean and reinstalling Ubuntu will leave me with a pure Ubuntu Lenovo.

---

### Post by oldfred on 2013-08-19
I do not have UEFI, but have a 60GB SSD, which I partitioned into two / partitions of 28GB for two installs current and a test. I install / including /home but have swap and data partitions (and more installs) on my hard drive. I then link data partitions back into /home. My root is 9GB including my /home. My /home is 2GB but 3/4 of that is .wine with Picasa.

If not using Windows and you have UEFI, I would make sure both drives are gpt partitioned. Whether you use UEFI or BIOS then is your choice. Ubuntu works from gpt with either BIOS or UEFI but Windows only boots from gpt drives with UEFI.

I put both a efi partition (for future) and bios_grub (BIOS boot) partition on all my new drives as I have been planning a new system for a while. The efi partition is supposed to be first and adding that later is difficult.

If you have 4GB or more of RAM you probably will not use swap unless you like to load every app at once or edit videos. And with new SSD where swap is does not really matter from a life standpoint.

---

### Post by orioles_fan on 2013-08-19
Alright, that definitely makes sense. Again, seriously, thanks for your help.

So here's what I'm thinking.

1. Copy all of my personal files onto my Toshiba external drive as well as create a backup for good measure.
2. Boot from my LiveUSB.
3. Loaded up gparted and format both drives (SSD and HD) to start completely fresh.
4. Run the Ubuntu installer.
5. Install as "Something Else".
5a. SSD = /efi, /boot, / (root), /swap, /etc
5b. HD = /efi, /boot, /home
5c. Partitions are in that order.

Does that make sense/look perfect?

---

### Post by oldfred on 2013-08-19
You do not need /boot as a separate partition for most desktop installs. Servers or desktops with server type configurations of RAID or LVM, or other specific requirements may need them. Also some old systems and a few with certain BIOS and USB installs.

You do not have to make all of the remaining space /home if you want to do anything else. I was not sure if I might want more data space or more / partitions when  I got my new drive 3 years ago. Just about all that remaining space has been used by 25GB installs of something or the other. I really should houseclean and did not need all of them as I could have reused some.

I find my own optimal partitioning plan is not so good a year or two later. But after another year I add a new drive and start over as I do not trust main working drive for more than about 3 years.

---

### Post by orioles_fan on 2013-08-19
Ok, I'll disregard the /boot partitions. I still should have two /efi partitions at the start of each drive, right? How big should those be?

---

### Post by oldfred on 2013-08-19
I typically suggest about 250MB which for most drives is not much. I think the default for Windows or maybe Ubuntu is 100MB. But efi partitions can have more than just the basic boot loader and later you may want some more space.

You will only use one efi but I prefer to make space on every drive. My goal is reliability first. So I want every drive to have all the necessary partitions to fully boot even if I get fstab errors about not mounting a partition on another drive.  And hopefully I have backups of any data on the other drives that then may not be working.
So I would not just have an efi partition on every drive but a / (root) on every drive.

 
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

### Post by orioles_fan on 2013-08-19
Welp, I reinstalled Ubuntu 13.04 and the second time booting into the new installation, I was greeted with the same exact issue as before (boot up, flashes the magenta/purple screen, and then the screen goes back to black, and stays there). Forced the shut down, turned back on, went to the GRUB, picked Ubuntu, and here we are.

Following the new install, here's the Boot Repair info:
[http://paste.ubuntu.com/6004523](http://paste.ubuntu.com/6004523)

---

### Post by oldfred on 2013-08-19
Since you only have one install, you will not get grub menu. You normally have to hold shift key from BIOS boot until menu appears. Some with UEFI have had to use escape key.

Do you have control over which video your are booting with as a setting in UEFI/BIOS, either Intel or nVidia. NVidia needs the nomodeset and sometimes the nomodeset will work with Intel.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
Editing the GRUB 2 Menu During Boot
[https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting)

See also info on Ultrabooks in link in my signature. You may want  bumblebee.

---

### Post by orioles_fan on 2013-08-19
I went into the BIOS and didn't see any settings for the graphics card. I've never seen an Nvidia card mentioned in reference to my U310 before so I'm fairly certain I'm stuck with Intel HD 4000 Integrated graphics. In the System Settings, it just comes up as "Intel Ivybridge Mobile". I saw that there is an Intel Linux Installer out now. Is that something I should look into?

One thing I did notice in the BIOS was that the Intel Rapid Storage Technology option was still enabled. It would make sense that that could mess with the boot so I turned it off.

Did a little digging last night. You were definitely on the right track. It sounds like the Intel HD 4000 graphics are the issue. The bug below is the exact issue:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1070150](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1070150)

---

### Post by oldfred on 2013-08-20
Post this:

 #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root

---

### Post by orioles_fan on 2013-08-20
> **oldfred said:**
> Post this:

 #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root

**sudo lshw -c display:**
  *-display               
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:3000(size=64)

**sudo lshw | grep -A 11 display:**
        *-display
             description: VGA compatible controller
             product: 3rd Gen Core processor Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:45 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:3000(size=64)

[B]lspci | grep VGA:
[/B]00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)

**xwininfo -root**
xwininfo: Window id: 0xb3 (the root window) (has no name)


  Absolute upper-left X:  0
  Absolute upper-left Y:  0
  Relative upper-left X:  0
  Relative upper-left Y:  0
  Width: 1366
  Height: 768
  Depth: 24
  Visual: 0x20
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x22 (installed)
  Bit Gravity State: ForgetGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +0+0  -0+0  -0-0  +0-0
  -geometry 1366x768+0+0

---

### Post by oldfred on 2013-08-20
That confirms you have just the Intel video. And Intel only has one Linux open source driver.

 New Intel driver installer (only with 13.04)
[http://www.phoronix.com/scan.php?page=news_item&px=MTQyNTQ](http://www.phoronix.com/scan.php?page=news_item&px=MTQyNTQ)
NVIDIA's Linux Driver On Ubuntu Is Very Competitive With Windows 8
[http://www.phoronix.com/scan.php?page=article&item=nvidia_windows8_geforce&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_windows8_geforce&num=1)
Linux 3.2 To 3.8 Kernels With Intel Ivy Bridge Graphics
[http://www.phoronix.com/scan.php?page=article&item=intel_linux32_38&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_linux32_38&num=1)
Intel HD4000
[http://communities.intel.com/thread/34221](http://communities.intel.com/thread/34221)
[http://ubuntuforums.org/showthread.php?t=2089640](http://ubuntuforums.org/showthread.php?t=2089640)
[http://ubuntuforums.org/showthread.php?t=2126191](http://ubuntuforums.org/showthread.php?t=2126191)
Also one used nolapic.
[http://ubuntuforums.org/showthread.php?t=2133816](http://ubuntuforums.org/showthread.php?t=2133816)
GRUB_CMDLINE_LINUX_DEFAULT="acpi_osi=Linux quiet splash"
Needs Raring & new kernel
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1175029](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1175029)

---

### Post by orioles_fan on 2013-08-21
Ironically enough, after updating 13.04 using the Software Update, I was having a terrible time trying to get ubuntu to boot properly. I ended up finally getting it after the 3rd or 4th attempt but definitely a regression.

I went ahead and installed the Intel Linux Graphics Installer this morning. It ran whatever checks it did and installed what it needed to. Since then, I've had no issues booting up although now, I don't even see the ubuntu load screen anymore. I can live with not seeing the ubuntu logo over staring at a blank screen.

Will update if the issue returns.

UPDATE:
Welp, it came back. After constant boots with a black screen and one wake that resulted in 4 CPU Package power limit notifications, I just decided to install GDM and use that instead of lightdm. Since the switch, haven't had a single issue. Will continue to update.

---

