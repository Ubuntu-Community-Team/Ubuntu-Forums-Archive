---
title: "Ubuntu Beginner, installer wont run and/or detect current OS"
date: 2017-04-30
forum: General Help
---

### Post by a1j3b6 on 2017-04-30
Hello All,

I'm attempting to install Ubuntu 16.04.2 LTS via bootable USB on my PC (which is currently running windows 10) and having a few issues. I have gone through the step by step setup and configured the USB correctly and am able to boot from the USB into the initial Ubuntu screen. At this point, I click on the installer and attempt to go through that process, but I am noticing that 1 of 2 things happens...depending on which way I boot from USB initially the installer either detects no OS or it detects windows boot manager. It never detects Windows 10. In my PC's boot menu, my USB is split into 2 categories (one with a 'UEFI' prefix). I have tried to boot into Ubuntu with both, and I am not sure which one to use. In the situation where I tried to boot with USB (non UEFI) i followed directions to boot via nomodeset (followed directions in this YT video-[https://www.youtube.com/watch?v=OTmZYzaxR_k](https://www.youtube.com/watch?v=OTmZYzaxR_k)) and got all the way to the installer (i chose the option to try ubuntu before installing btw). In this scenario, I went through the installer and it detected no OS at all. 

In the 2nd scenario, I attempted to boot from my USB via the 'UEFI' version of my USB drive and the only way I could get it to work was to go into the edit settings and add a string of commands to the LINUX line (which im not even sure if I did it correctly). I did some version of this 4 or 5 times and only got it to work once. When i did get it to work, I went through the installer and it was recognizing the Windows Boot Manager (but still not Windows 10). I find most directions pretty confusing and not exactly specified to my needs, so any help you guys could offer me would be incredibly helpful. I will include a list of my hardware and any steps I've made thus far within the framework of trying to install UBUNTU and hopefully that is helpful. My apologies if i haven't described things well here or left out too much detail. If i can clarify anything further please let me know. Thanks!!!


Motherboard:     [https://www.newegg.com/Product/Product.aspx?Item=N82E16813130892](https://www.newegg.com/Product/Product.aspx?Item=N82E16813130892)
Graphics Card:   [https://www.newegg.com/Product/Product.aspx?Item=N82E16814487248](https://www.newegg.com/Product/Product.aspx?Item=N82E16814487248)
SSD:                [https://www.newegg.com/Product/Product.aspx?Item=N82E16820156124](https://www.newegg.com/Product/Product.aspx?Item=N82E16820156124)


Other steps i've done thus far:

Ran RUFUS and created a bootable USB stick (via UBUNTU website tutorial)--USB stick i have is 4GB
disabled fast startup within Windows 10

---

### Post by yancek on 2017-04-30
Make sure you have anything related to 'fastboot' or 'hibernation' off.  Most computers will have multiple ways to do this.
Did you shrink the windows partitions to create unallocated space on which you could install Ubuntu.  That would be necessary.  Before doing that, run disk defragmenter from windows then use the windows disk management to shrink the windows partition to create unallocated space.  Then reboot windows and run chkdsk.

If your windows 10 was pre-installed, it is almost certainly UEFI so you would need to use the UEFI option with Ubuntu or you will have boot problems.  The Ubuntu documentation on this is at  the site below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by a1j3b6 on 2017-04-30
yancek,

thanks for your response. I did in fact shrink the partition and create an unallocated space of ~50GB (i know ubuntu 16.04 only requires 25 but i had plenty of space so intentionally overshot it in case necessary in the future). I also just ran chkdsk and the following came up in CMD:

C:\WINDOWS\system32>chkdsk
The type of the file system is NTFS.


WARNING!  /F parameter not specified.
Running CHKDSK in read-only mode.


Stage 1: Examining basic file system structure ...
  411648 file records processed.
File verification completed.
  12017 large file records processed.
  0 bad file records processed.


Stage 2: Examining file name linkage ...
  518934 index entries processed.
Index verification completed.
  0 unindexed files scanned.
  0 unindexed files recovered to lost and found.


Stage 3: Examining security descriptors ...
Security descriptor verification completed.
  53644 data files processed.
CHKDSK is verifying Usn Journal...
  36393176 USN bytes processed.
Usn Journal verification completed.


Windows has scanned the file system and found no problems.
No further action is required.


 680793087 KB total disk space.
 339656064 KB in 317757 files.
    190156 KB in 53645 indexes.
         0 KB in bad sectors.
    538939 KB in use by the system.
     65536 KB occupied by the log file.
 340407928 KB available on disk.


      4096 bytes in each allocation unit.
 170198271 total allocation units on disk.
  85101982 allocation units available on disk.


My PC was built by a friend of mine who works in IT, and after speaking with him just now he told me that Windows 10 was installed on my machine using BIOS, not UEFI. Given this new information, can you point me in the best direction going forward? Install Ubuntu in BIOS? I was also told my motherboard might not support UEFI but im not sure how to verify that. If i do in fact need a new/different motherboard would you mind suggesting one? I know this is alot of questions, but I really appreciate your help. Trying to learn alot of this stuff on the fly :)

---

### Post by a1j3b6 on 2017-04-30
actually, i take it back. I have just confirmed my motherboard is running UEFI. my apologies.

---

### Post by oldfred on 2017-04-30
Motherboard is UEFI, but has CSM.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

How you boot install media UEFI or BIOS is then how it installs.

 MSI Z170M Intel i7 6700 GTX 980TI 16.10 does not work, 16.04 does
[https://ubuntuforums.org/showthread.php?t=2357641](https://ubuntuforums.org/showthread.php?t=2357641)

With my Gigabyte Z170 I did not have to make many changes in UEFI, but with Asus Z97 I had many changes.
It depends on vendor and version.
But you need UEFI fast start up off.
You need to know if Windows is installed in UEFI or BIOS boot mode.
And with Windows 8 or 10 you must have Windows fast start up or always on hibernation off.

From live installer post this:
sudo parted -l

If drive is gpt then Windows is UEFI, if drive is MBR(msdos) then Windows is BIOS.

How you boot install media for both Windows & Ubuntu UEFI or BIOS is then how it installs. And you then want to always boot all devices/installs in the one mode to avoid conflicts. Best to use UEFI/gpt.

For more info on UEFI see link below in my signature.

---

### Post by a1j3b6 on 2017-04-30
fred,

thanks for your response. honestly, most of the technical jargon is a little over my head (trying to learn fast though!). I can tell you that i have verified in the BIOS of my MSI Z170-A that fastboot is disabled and also windows fast start up and hibernation are both off/disabled. I also verified that the drive is GPT. I then went ahead in the BIOS and changed the boot sequence order so that the UEFI USB was at the top of the list in the boot sequence. I restarted and was met with the GNU GRUB screen (version 2.02^beta2-36ubuntu3.7). From here, I had the following 4 options:

Try Ubuntu without installing
Install Ubuntu
OEM Install 
Check disc for defects

I tried both the 'try ubuntu without installing' and 'install ubuntu" options. After pressing enter, I was within a few seconds met with a couple lines of code that reads as follows:

0.110238 CPU2: Package temperate above threshold, cpu clock throttled (total events = 1)
0.118023 CPU5: Package temperate above threshold, cpu clock throttled (total events = 1)
0.123135 CPU7: Package temperate above threshold, cpu clock throttled (total events = 1)

I'm pretty lost at this point. Trying to learn about one thing and then get wormholed in another direction and get lost again. Really not sure how to continue from here so hoping you can help. Thanks so much!!

---

### Post by a1j3b6 on 2017-04-30
it may also be worth mentioning that i noticed the following in my motherboards BIOS.

1) MSI Fast boot and Fast Boot are both disabled in the BIOS.

2) boot mode select has 2 options:
-UEFI
-LEGACY+UEFI

currently it is set to LEGACY+UEFI

---

### Post by a1j3b6 on 2017-04-30
update:

I changed the book mode select to 'UEFI' instead of 'legacy+uefi'. I do not notice if this has made a single bit of difference other than in the BIOS there are now less available options in the boot sequence. With that said, I have went back to the GNU GRUB screen and edited the boot options under 'try ubuntu without installing' where is says "quiet splash". I changed this to read "quiet splash nomodeset" and hit enter to run it. The same lines of code showed up regarding the "package temperature above threshold" still showed up, but it bypassed them anyway and ubuntu loaded to the main screen. I got to the main screen and tried to go through the installer, but it did not detect the copy of windows 10 that is on my PC. Instead, it detected "windows boot manager". Not sure where to proceed from here...

---

### Post by oldfred on 2017-04-30
Right after you see the package temperature waring, go into UEFI and see what it says about cpu temps.
This to make sure not software mis-reporting issue.

If high possibly fan not working, check connections. 

Or cpu not installed correctly. They all now come with very thin layer of heat transfer compound. If your "friend" was old school he may have added more and you have too much. But if you redo it, you have to remove  cpu & then must remove old compound, and apply very thin layer yourself.

Are these the settings you changed in Windows to turn off fast start up?
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by a1j3b6 on 2017-05-01
Fred,

Within windows 10 'Turn on Fast startup' and 'hibernate' are both disabled. Per an earlier youtube video i watched, i did download the .bat file and turn it off by this route. As i said earlier, fast boot in the BIOS is also disabled (idk if this is relevant or not). 

In regards to the temperature issues, motherboard temp was showing a stable 33`C, but the CPU temp when i first accessed the BIOS was almost 70`C and just a few min later by the time i exited, spiked to nearly 100`C. As far as I can tell, all 4 of the fans I have in my machine are operational (though they are whisper quiet and idk how effective they really are?). There are 3 fans stacked vertically on the front end of my tower just inside the outside shell and another one on the back panel. My BIOS is showing 2 CPU fans and 3 System Fans. I dont know if that means I actually have 5 fans or just this machine has the capability to run 5. If there is a specific way to check this let me know. As I said, all the fans I see are clearly "on" and running in some capacity. Looks like online the average temp for intel i7 is 50-65`C so obv i may have be having an issue with overheating.

---

### Post by a1j3b6 on 2017-05-01
fred,

here is a link to a screenshot showing temperature data of my PC via CPUID HWMonitor 

[https://ibb.co/egeLWQ](https://ibb.co/egeLWQ)

---

### Post by oldfred on 2017-05-01
CPU fan is probably most important.
That is the large cooling tower/fan on top of CPU. And it is plugged into motherboard which my UEFI mother board shows rpm of fan.

---

### Post by oldfred on 2017-05-01
My Gigabyte Z170 temps right now.

```
fred@Z170N:~$ sudo sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +27.8°C  (crit = +119.0°C)
temp2:        +29.8°C  (crit = +119.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +41.0°C  (high = +84.0°C, crit = +100.0°C)
Core 0:         +35.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:         +36.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:         +35.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:         +34.0°C  (high = +84.0°C, crit = +100.0°C)

```

---

### Post by a1j3b6 on 2017-05-01
seems like your temps are much lower (or in range) compared to my intel i7. do you think this is the main issue? or is it the graphics card? combo of both? idk if the problem i just need a newer/better fan or what exactly the problem is. I've never had a single issue ever with my PC in regards to overheating. Windows 10 has always ran fine and I've never encountered an issue relative to temperature overheating, but now I am having one with ubuntu with just the install? I'm sure many of these questions are super newbish but I'm really having a tough time troubleshooting these issues one by one (especially with very little knowledge of this area in the first place).

---

### Post by oldfred on 2017-05-01
I do not have video card, just i5 with its internal graphics.
I am using 16.04 and did download a new Intel driver for Skylake & Kabylake systems.
Do not know what issue then may be.

 Intel Driver updates
[https://ubuntuforums.org/showthread.php?t=2342137&p=13565767#post13565767](https://ubuntuforums.org/showthread.php?t=2342137&p=13565767#post13565767)
Updates often needed for Skylake or Kabylake
[https://01.org/linuxgraphics/intel-linux-graphics-firmwares](https://01.org/linuxgraphics/intel-linux-graphics-firmwares)

---

