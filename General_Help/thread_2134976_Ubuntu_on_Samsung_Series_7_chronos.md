---
title: "Ubuntu on Samsung Series 7 chronos"
date: 2013-04-12
forum: General Help
---

### Post by cpu2007 on 2013-04-12
Hello everyone,
I hope someone can guide me through a set of things that I want to do on the mentioned model.

I have already installed ubuntu on it but because I'm a total beginner, I don't know how to configure it properly in order to take advantage of all the features.
I have read a few articles but none of them is clear enough about what I should do.

First of all
One article mentions installing nvidia drivers(instead of the default ones) on ubuntu as this will increase the battery life. How can I do this?
and is it there any program that I can go to, to see what are the names of hardware installed on my laptop?(similar to device manager of w7)

Thank you

---

### Post by oldfred on 2013-04-13
If you just have nVidia
# You may need headers first - meta package for 12.10 version:
sudo apt-get install linux-headers-generic

   Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

But if you have the dual video you need Bumblebee.
      
 nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Switchable Graphics is killing my Ubuntu Experience - see post #9
[http://ubuntuforums.org/showthread.php?t=1927317](http://ubuntuforums.org/showthread.php?t=1927317)
Optimus
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
12.10 with bumblebee
[http://ubuntuforums.org/showthread.php?t=2077451](http://ubuntuforums.org/showthread.php?t=2077451)
NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)
Released 319.12 Beta April 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM0NzE](http://www.phoronix.com/scan.php?page=news_item&px=MTM0NzE)

    
There is not an equivalent to device manager, but you can dump tons of internal data to text files if really interested.
      
 If using sudo, run any sudo command like ls first. Sometimes sudo & redirect have issues.
sudo ls
Files saved in your home folder
To save it as a file use
sudo lshw > hw.txt

   HTML version of info
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html

   udevadm info --export-db > file.txt
udevinfo -a -p $(udevinfo -q path -n /dev/sdd)

   Similarly, if you run
sudo dmidecode > bios.txt
The last one (dmidecode) lists the machine's DMI or SMBIOS table contents in a friendly format. This DMI or SMBIOS contains a description of the system's hardware components and other useful information such as serial numbers and BIOS revision. This is a really powerful command.

   Internal efi details
ls /sys/firmware/efi/vars

---

### Post by cpu2007 on 2013-04-13
Hi

Thank you for the reply. I will look at the links that you have provided.

Talking of dual graphic cards, I don't know whether I have dual or single. My samsung model is series 7 chronos 700Z5C-S03 ? can you please tell me if this model has dual graphic cards? I believe is only one.

---

### Post by oldfred on 2013-04-13
It looks like you have AMD Radeon 6750M. Many i-series Intel chips also have graphics but I do not know about AMD nor how your system may be configured.

But if you have AMD, you do not install nVidia drivers. There are AMD drivers.

 [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)
[http://ubuntuforums.org/showthread.php?t=1558406](http://ubuntuforums.org/showthread.php?t=1558406)

---

### Post by cpu2007 on 2013-04-13
but checking the model on google it says
NVIDIA® GeForce® GT 640M

---

### Post by oldfred on 2013-04-13
There must be different model Samsungs. Because I got the AMD info from a spec sheet on your Samsung series 7.
But you have to know for sure before installing drivers.

Can you boot in low graphics mode?
       uname -ar
lspci -nnk | grep -iA3 vga 

 #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root

---

### Post by cpu2007 on 2013-04-14
This is what I get after using the command lines that you have suggested in the last post.

> 700Z5C:~$ lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c0d5]
    Kernel driver in use: i915
    Kernel modules: i915
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK107 [GeForce GT 640M] [10de:0fd2] (rev a1)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c0d5]
    Kernel modules: nouveau, nvidiafb
02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6235 [8086:088e] (rev 24)



and

>  sudo lshw -c display

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: GK107 [GeForce GT 640M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller cap_list
       configuration: latency=0
       resources: memory:f0000000-f0ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:3000(size=128)
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
       resources: irq:46 memory:f1000000-f13fffff memory:e0000000-efffffff ioport:4000(size=64)



> 
 sudo lshw -c display

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: GK107 [GeForce GT 640M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller cap_list
       configuration: latency=0
       resources: memory:f0000000-f0ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:3000(size=128)
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
       resources: irq:46 memory:f1000000-f13fffff memory:e0000000-efffffff ioport:4000(size=64)



>  sudo lshw -c display

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: GK107 [GeForce GT 640M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller cap_list
       configuration: latency=0
       resources: memory:f0000000-f0ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:3000(size=128)
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
       resources: irq:46 memory:f1000000-f13fffff memory:e0000000-efffffff ioport:4000(size=64)



>  sudo lshw -c display

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: GK107 [GeForce GT 640M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller cap_list
       configuration: latency=0
       resources: memory:f0000000-f0ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:3000(size=128)
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
       resources: irq:46 memory:f1000000-f13fffff memory:e0000000-efffffff ioport:4000(size=64)



---

### Post by oldfred on 2013-04-14
So you have dual video and need bumblebee?

---

### Post by cpu2007 on 2013-04-14
I'm not sure how to interpret the outputs of the commands that you have suggested.

However it seems like that I have dual video, one of the link you've provided talks about nvidia optimus (which is basically two graphic cards) and on my laptop, one of the logo on next to the touchpad says Nvidia optimum, so I assume it is optimus.

Let's say it is, having read some of the articles,it seems like there's no actual solution to effectively update the drivers, as is being suggested not to install any restricted driver.

---

### Post by oldfred on 2013-04-14
Post #2 I have links to some info on Bumblebee and how to install it. I do not have that so I have no experience with it.

---

### Post by cpu2007 on 2013-04-14
ok now I have installed bublebee on my system, however not sure how to check whether this is working or not. Any way to test this? 
I can use and run applications using "optirun" eg. optirun firefox and they get executed but I know don't know whether the drivers are installed correctly and whether the power management works.


One of the reasons I wanted to install the drivers was because apparently this was a step to be taken in order to get full control of the function keys of my laptop. However I still can't use the following keys:
increase/decrease backlight keyboard
fan lock/unlock
f1 settings key

I have followed some articles and installed some packages

sudo apt-get install samsung-tools
sudo apt-get install samsung-backlight 


but even after this nothing works yet.

---

### Post by oldfred on 2013-04-14
Cannot help. These threads are more on boot issues, but someone may have discussed your other issues?

 Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)
 SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)
Samsung series 5 UltraBook, erase Windows & install to SSD
[http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/](http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/)

---

### Post by cpu2007 on 2013-04-15
Thanks, they don't really have details about backlight; however,I've noticed in some posts that in the latest versions the packages I've mentioned before are not working. Not sure whether this is still the case; I've created a topic on the voria forum a few days ago but never received a reply.
I'll keep looking around to see whether I find anything.

I have followed the bumblebee guide you've posted and everything was executed smoothly without errors but there was no hint on how to check whether what I've installed is correctly installed. How can I check whether my graphic cards drivers are working and switching appropriately?

I might update my bios as I read this might solve some problems, is it possible to execute exe files in ubuntu? if I run an exe file on ubuntu to update the BIOS using "wine", will this work or I have to have a MS OS?

---

### Post by oldfred on 2013-04-15
I have not paid attention to the way to update BIOS.

My system has 3 ways, a Windows .exe, a bootable DOS flash or floppy or just read the file directly from a FAT32 flash drive which is what I have used.

---

### Post by cpu2007 on 2013-04-15
would you please explain your last method.

When you say fat32, you mean you insert the usb with the exe file in it  and run it from ubuntu?

---

### Post by oldfred on 2013-04-15
With my system there is no .exe, just an update file on flash drive. BIOS is smart enough to read flash drive directly. I do have to extract the update file from a download. This is for a Gigabyte motherboard from 2009, so I assume many others may have that kind of capability by now. 
But most vendors do make it easy or more automatic from Windows.

---

### Post by cpu2007 on 2013-04-16
Thank for you all the great help and explanations.
I'll try the last method and see whether it works, if not I'll just go to w8(which is still installed ) and update the bios by running the exe file from there.

Thanks

---

### Post by cpu2007 on 2013-05-03
The wireless of my laptop works fine and didn't even need to install any driver but what I've noticed is that the signals are low.
Sometime I'm sitting next to the router (10 metres away) and yet the signals are like just half of full.

Can this be because of out of date drivers? if so, is it possible to update drivers or install proprietary drivers and is this recommended?

---

### Post by oldfred on 2013-05-03
I do not know about WiFi.

You can see what chip you are using and search forum for others with similar chip issues. It should be based on chip not vendor of your system.

If you cannot find anything, start a new thread with wifi and your chip model in title.
Those that know about wifi, will want details. Some suggest this:

lspci > ~/abs-network.txt
lsusb >> ~/abs-network.txt
ifconfig >> ~/abs-network.txt
iwconfig >> ~/abs-network.txt
Attach (via the paperclip in advanced edit menu) the abs-network.txt file which will be in your home folder.

---

### Post by cpu2007 on 2013-05-05
Thank you i'll try that out.

---

