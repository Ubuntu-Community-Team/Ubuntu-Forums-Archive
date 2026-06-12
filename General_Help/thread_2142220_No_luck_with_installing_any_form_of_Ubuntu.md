---
title: "No luck with installing any form of Ubuntu"
date: 2013-05-05
forum: General Help
---

### Post by chadv0 on 2013-05-05
I've spent the last 2 days trying to get an older PC of mine to become a simpler, faster machine capable of being an HTPC for another room of the house. I've come across a plethora of different errors and issues throughout my installation failure adventure. The PC is manufactured by Everex, and I'm not sure of the release year, but the specs are as follows:

Everex IMPACT GA3400
-AMD Athlon 64 3400+ / 2.2 GHz (referred to as "mobile")
-1.5GB of DDR PC3200 RAM: The 512 stick packaged with the system and an additional 1GB stick
-120GB IDE 7200RPM HDD
-NVIDIA GeForce 6100 (Integrated in the Mobo)

-Claims to support 64-bit computing
-Originally ran Windows XP Home Edition

Here is the full list of events, which may provide helpful information, but you can skip this if you really want.

----------------------------------------------------------
I originally intended to get the PC running on a Linux OS so I could try and become familiar with the potential and benefits it says to provide and probably does for most users. I have had no such luck. I've not been attempting anything of perceivable difficulty, as I'm not performing any partitioning or anything, I just want to install the OS. I began by burning a live CD of Ubuntu 12.04 and tested the "Try Ubuntu" function. I followed through and decided to install the program. My PC was not connected to the internet before installing, but allowed me to install the core components anyway. The installation completed in a short while, and I couldn't wait to try Ubuntu for the first time. In starting up my computer, I was told "hd0 out of disk" and "grub rescue>". I searched these terms and followed instructions on the internet to follow in the prompt. Nothing was accomplished.

Second in line, and the _OS I would like to have most to work_ for my stubborn PC, I attempted to install Lubuntu 13.04, 32-bit, yada yada. The live trial from the CD amazed me, and I connected to the internet and realized how blazing fast Lubuntu can be. everything loaded immediately, as if it were a pre-rendered single application. I was eager to install, and got to the "Preparing to Install" step of the installation process. Upon clicking "Continue" after filling all the necessary requirements, such as internet, I received the loading circle and never got to the next step. It hung forever. I was disappointed. I looked at other viable options to install Lubuntu, and I saw that my computer claimed to support 64-bit computing, boasting the AMD64 sticker on the front of the case. I also checked numerous support topics which noted that the alternate installer did not have this such problem. I loaded Lubuntu 12.04 alternate for 64bit onto another CD and attempted to install. I certainly passed the initial "Preparing to Install" section, but it would always flunk out on the step of actually installing Lubuntu. It'd get to a certain file or something and just quit working. I tried this many times but encountered a consistent repeat of the same kind of errors at the point of installing the actual components of the software. Finally, as my last attempt for Linux, I tried installing "mini.iso" of Ubuntu and going from there to get Lubuntu installed, but I would have settled for anything at this point. Installation of the Ubuntu components took hours, and the iso was only a few megabytes. It never completed, as it hung on 83%.

Finally, although unrelated to Linux OSes, I attempted to install TinyXP as an alternative to the standard Windows, but found no version to work for me at all.


The computer was running a full version of Windows XP Home Edition, albeit at an extremely slow pace, just a few days ago, and is likely to have no issue installing an official version of windows, as it has been formatted back to factory settings a multitude of times.
----------------------------------------------------------

Does anyone have any insight regarding my issues? I really want to try Linux, love it immediately, and use it in several future computers of mine, but this unforgiving installation process is making it extremely hard to do so. :(

I thank everyone in advance for providing a forum for me to post my issue with the hope of resolution. An even greater thanks goes out to anyone who can help.

---

### Post by Locus Kiesselbachi on 2013-05-05
> ...[COLOR=#000000] I received the loading circle and never got to the next step. It hung forever.[/COLOR]
Hello!
I had similar problem with Pentium 1, when trying to install later version of ubuntu. Live cd worked, but didnt install, just hung. So I tried older version, like lubuntu 11.10 and it worked. Afterward you can upgrade it to 12.10, if you like, through "Update Manager".

---

### Post by romain.astie on 2013-05-05
Older verions of lubuntu may work, but maybe your problem lies in the the 64-bit architecture. Even though the AMD64 trademark is 64-bit, maybe your system really isn't 64-bit. Look up your processor on google; that should provide some insight into what your problem may be. Maybe a 32-bit installer will work better, even if your system really is 64 bit.I'm no expert though, so take it with a grain of salt :). Maybe it's just lubuntu, could xubuntu work any better? Your system could definitely do it, by the looks of your specs.

---

### Post by chadv0 on 2013-05-05
Alright, I'll try it out!

---

### Post by CatKiller on 2013-05-05
As a sanity check, have you checked the cd for errors and run the hard drive manufacturer's diagnostic utility on the drive? A badly burned disk image can have unpredictable results, and your specified problems all occur during reads from or writes to your elderly hard drive. Might be worth checking out before you tear your hair out with configuration options and the like. Memtest is probably a sensible precaution too, although it doesn't smell like a RAM issue to me.

---

### Post by seppalta on 2013-05-06
First, I am of the view that 64-bit is only valuable if you have at least 3 GB of Ram, which you don't.  So stick with 32-bit, where everything is easier - no multi-arch, etc to have to fool with after installation.  Second, don't give up or limit yourself to one or two installation disks.  I have installed many LXDE Linux systems and when I finish configuring them, they are all essentially the same.  See [http://lxlinux.com/](http://lxlinux.com/) for a guide.  There have been  occassions when an install attempt failed and displayed some of the characteristics mentioned by you.  I never figured out the reason, but I always overcame the difficulty by successfully installing another system and then configuring it to my usual system.

---

### Post by tubbygweilo on 2013-05-06
Would a 12.04 lts [https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop) > System Requirements

The minimum memory requirement for Ubuntu 12.04 is 384 MB of memory for Ubuntu Desktop. Note that some of your system's memory may be unavailable due to being used by the graphics card. If your computer has only the minimum amount of memory, the installation process will take longer than normal; however, it will complete successfully, and the system will perform adequately once installed.

Systems with less memory may be able to select "Install Ubuntu" from the boot menu to run just the installer, rather than the whole desktop, or may be able to use the alternate install CD. 
via [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) be of any use?

Or if this gives problems then a 12.04 Lubuntu [http://lubuntu.net/](http://lubuntu.net/) might just be what is needed.

---

### Post by poltiser on 2013-05-09
Toshiba 1410-310 no DVD 512 RAM - from new U13.04 only Lubuntu alternate instalation worked - it has only problem with suspend/hibernate finctions - otherwise ok!
All others U13.04 - no screen...

---

### Post by Lightning Dragon on 2013-05-09
Hi,

I had a similiar problem with trying to install Ubuntu 13.10 on an older model. I decided to try Lubuntu 11.10 (or any other older version) and it worked. Since your computer is pretty weak, I would suggest Lubuntu or something similar. Linux Mint's requirement is 1GB of RAM, so maybe you could try that, assuming I understood your reply to have meant you have at least 1GB of RAM.

---

### Post by VanillaMozilla on 2013-05-09
Search Google for
hd0 out of disk
The first four hits in particular seem to be helpful.  Here's also one possible solution:  [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write)
Possibly a Grub problem or maybe even a hard drive problem.

---

### Post by oldfred on 2013-05-09
If your system supports 64bit, it would still be better.
 32-bit vs. 64-bit Ubuntu 13.04 Linux Performance with only 1GB of RAM & most tests better with 64bit
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_x86_1304&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_x86_1304&num=1)

Some older BIOS only let you boot from first 100GB of a hard drive. You have to have either the entire / (root) or a separate /boot fully inside the first 100GB of a drive. If using a smaller 10 to 25GB / partition you then can use rest of drive as /home or as data partition(s).

You have an older nVidia card. You will still need nomodeset. I am somewhat surprised you even got liveCD/DVD/Flash to boot as I have a bit newer 9600GT and have to use nomodeset on every live boot and on first boot after install. 
      
 How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
BIOS live installer Boot Options
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place

I think you can only install the older nVidia driver, but Ubuntu should let you install it as it is in repository.

 Versions:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

### Post by VanillaMozilla on 2013-05-09
Oldfred, just a gentle query.  All very knowledgeable, but is that advice potentially helpful?  Would it be better to narrow in on the implications of the error message than to try to sell the OP on a 64-bit system?  And does it have anything to do with his video driver?  Sounds like you may have it it with the hard drive limitations, though.

---

### Post by oldfred on 2013-05-09
Just wanted to point out possibility of 64 bit. 

Looks like I did not mention BIOS settings. Some default to the old IDE and that contributes or is the issue. Best to check how drive is used by BIOS, should be AHCI (but I do not think older systems or AMD have that), LBA or large, not RAID nor IDE.

---

