---
title: "DVD burner no longer burns .iso image"
date: 2008-06-21
forum: General Help
---

### Post by Dr Bones on 2008-06-21
Hello all,

I recently built a new computer and installed Hardy on it and have not been able to burn a DVD .iso file with it as of yet.  I took the old IDE dvd burner I had been using to do this very task in hardy on my previous machine and so far I can not get it to work.  In my previous machine I had an IDE hard drive in comparison to a SATA drive in my new machine, but I am not sure if that makes any difference or not.  I used this same DVD drive to install ubuntu so I know that it is detected and capable of being accessed. 
 
I have tried using K3b, gnomebaker as well as doing it through the terminal using growisofs -Z and I get the same input/output error every time I try it and the disk just ejects.  I also tried uninstalling and reinstalling the dvd+rw tools package to no avail.

In the debugging output for K3b under the growisofs command it says

Executing 'builtin_dd if=/dev/fd/0 of=/dev/dev/scd0 obs 32k seek0'
:-( write failed: Input/output error.

If someone has any solution it would be greatly appreciated as I am banging my head against the wall here.  Thank you in advance and have a nice night/day.

---

### Post by VMC on 2008-06-21
> **Dr Bones said:**
> Hello all,

I recently built a new computer and installed Hardy on it and have not been able to burn a DVD .iso file with it as of yet.  I took the old IDE dvd burner I had been using to do this very task in hardy on my previous machine and so far I can not get it to work.  In my previous machine I had an IDE hard drive in comparison to a SATA drive in my new machine, but I am not sure if that makes any difference or not.  I used this same DVD drive to install ubuntu so I know that it is detected and capable of being accessed. 
 
I have tried using K3b, gnomebaker as well as doing it through the terminal using growisofs -Z and I get the same input/output error every time I try it and the disk just ejects.  I also tried uninstalling and reinstalling the dvd+rw tools package to no avail.

In the debugging output for K3b under the growisofs command it says

Executing 'builtin_dd if=/dev/fd/0 of=/dev/dev/scd0 obs 32k seek0'
:-( write failed: Input/output error.

If someone has any solution it would be greatly appreciated as I am banging my head against the wall here.  Thank you in advance and have a nice night/day.

The installing ubuntu from the dvd rom comes from BIOS and the ISO from the cd media not ubuntu. After ubuntu is installed it apparently doesn't reconize you dvd drive. 

What's under Places-Computer, Should be Filesystem, then what else?

---

### Post by Dr Bones on 2008-06-21
It does show up under Computer in places and I can read data from the drive in Ubuntu.  Also when I put in a Blank DVD+R it shows up on the desktop.

---

### Post by Dr Bones on 2008-06-21
I forgot to mention I put another IDE dvd burner in this computer and I get the same results, the drive shows up, I can read from it but when it comes to writing it appears to hit a wall.

---

### Post by VMC on 2008-06-21
In Terminal

```
wodim -checkdrive
```

What does it display?

---

### Post by doug1212 on 2008-06-21
Hi,
Sounds similar to the issues I had with sata dvd drives on my gutsy machine where I was unable to burn a disk.

I was advised to change the owner of "/dev/sg0" to root:cdrom by adding a line to "/etc/rc.local" file before the line "exit 0".
```

chown root:cdrom /dev/sg0

```
worked for me.
good luck,
Doug

---

### Post by VMC on 2008-06-21
> **doug1212 said:**
> Hi,
Sounds similar to the issues I had with sata dvd drives on my gutsy machine where I was unable to burn a disk.

I was advised to change the owner of "/dev/sg0" to root:cdrom by adding a line to "/etc/rc.local" file before the line "exit 0".
```

chown root:cdrom /dev/sg0

```
worked for me.
good luck,
Doug

Yes, mine is owned by root:
crw-rw---- 1 root disk 21, 0 2008-06-20 22:28 /dev/sg0

---

### Post by Dr Bones on 2008-06-21
Thank you for the help so far guys, here is the output of ```
wodim -checkdrive

```
```
bebeau@bebeau-desktop:~$ wodim -checkdrive
Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/sr0
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identification : 'DVD-RW  DVR-107D'
Revision       : '1.05'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.

```

I also tried your solution Doug, it was the only line in that file outside of the exit 0 that ended the document and still the drive does not burn anything.

---

### Post by VMC on 2008-06-21
Mine shows below. I wonder about the SCSI info that yours doesn't have. I know my drive is different but how about the driver?

```
Detected CD-R drive: /dev/cdrw
Using /dev/cdrom of unknown capabilities
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVD-RAM GSA-H22N'
Revision       : '1.01'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
```

Also, if you type "lsmod|grep cdrom", does anything show up?

---

### Post by Dr Bones on 2008-06-22
here is the output for lsmod|grep cdrom

```
cdrom                  41512  1 sr_mod

```

As for the driver how do I look to see what driver is being used in linux, as that is not something I have ever needed to do in linux?

---

### Post by Dr Bones on 2008-06-22
I also ran the wodim -checkdrive again and it appears to have changed.  below is the new information.
```
Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/sr0
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identification : 'DVD-RW  DVR-107D'
Revision       : '1.05'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO

```

---

### Post by VMC on 2008-06-22
You mentioned you took this dvd drive from an old system. Have you rechecked the cables. I don't see how they would matter because you can read okay.

If you have Windows installed can it burn on the drive?

---

### Post by Dr Bones on 2008-06-23
I took this drive from my old box which had ubuntu and Windows on it even though I had not used windows in a few months.  Because of this I didn't even bother to reinstall windows on it.  I will try another cable and see if that works.

---

### Post by Dr Bones on 2008-06-23
I changed the cable connected to the dvd-burner and the problem still exists. Any other possible explanations?

---

### Post by VMC on 2008-06-23
> **Dr Bones said:**
> I took this drive from my old box which had ubuntu and Windows on it even though I had not used windows in a few months.  Because of this I didn't even bother to reinstall windows on it.  I will try another cable and see if that works.

It really seems impossible that it could be a cable. I haven't use pin-outs in a long time. I was just trying to get another OS to verify if the dvd drive was able to write. 

If there is a way to clean the optic head of the dvd drive that would be great. DONT use alcohol! I was told by a technician that uses to repair DVD drives that alcohol destroys the "vision" of the head.

---

### Post by Dr Bones on 2008-06-23
I think it would be highly unlikely that the drive no longer functions right after I reinstall Ubuntu and try 2 different drives, obtaining the same results with each of the drives.  I will buy a new drive if I think that all of the software appears to be in working order but would rather not do this quite yet.

---

### Post by MichaelSwengel on 2008-06-23
I had a similar issue for a while until I discovered that the discs I had been using were faulty. Some would work. Some wouldn't. The ones that failed gave me the "input/output" error.

Have you tried burning/reading with another brand/type of disc?

---

### Post by Dr Bones on 2008-06-23
Thank you for the input Michelle but I just tried burning using a different brand and type of disk to no avail.

---

### Post by mc4man on 2008-06-23
If you want to install wine you could try burning with Imgburn which will use a different driver than your linux app, if successful would point to method your presently using as culprit. Fairly easy to set up, let me  know

---

### Post by Dr Bones on 2008-06-23
Ok I reinstalled ubuntu just in case for some reason it was botched from the beginning as this was a new install anyway and I installed imgburn which was also unsuccessful at burning the image.  I did notice that the imgburn program listed no writers detected when I went into the img burning section of the program at the bottom.  

To clarify what I have changed I will rehash everything I have done since my last post.  I have both of the IDE DVD burners I mentioned installed in the computer on the same IDE cable (the one on the end furthest from the MB has it's jumper set to master and the other slave as it should be) and neither of them function.

When I type wodim -checkdrive in the terminal this is what is displayed
```
Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/cdrw
Using /dev/cdrom of unknown capabilities
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identification : 'DVD-RW  DVR-107D'
Revision       : '1.05'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R

```
This did change since I reinstalled ubuntu as you can compare this output with the output from my previous post here.

```
Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/sr0
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identification : 'DVD-RW  DVR-107D'
Revision       : '1.05'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
```

It appears that the device name has changed on the Pioneer drive I have installed from /dev/sr0 to /dev/cdrw and I am not sure why this is or if it important at all.

When I place a blank disk in the drive it successfully displays it in the computer window.  Both drives also show up under Computer but I am not sure if there is supposed to be both drives identified when I enter wodim -checkdrive in the terminal.

When I enter lsmod|grep cdrom into the terminal this is what is exported.
```
cdrom                  41512  1 sr_mod

```

Also I added the line chown root:cdrom /dev/cdrw to the /etc/rc.local file as Doug had suggested and saved the file.  Do I need to execute this file or restart my computer after I update this in order for it to take effect?

Thank you all again so much as you have already helped me a lot and I have a feeling we are getting close.  I will also try to burn another image and report back with any changes as I am not sure if the image is good or not.

---

### Post by mc4man on 2008-06-23
> It appears that the device name has changed on the Pioneer drive I have installed from /dev/sr0 to /dev/cdrw Those changes are due to running wodim with no media in drive, put a blank dvd in drive and the output would be like earlier post. In regards to Imgburn - in winecfg the windows ver. should Windows nt 4.0 and under drives tab select autodetect
If imgburn opens detecting drives and your using latest ver. 2.4.1 then under the mode tab choose write (more verbose than ez mode picker )

Edit; people seem to have ok success using brasero or cd/dvd creator vs. k3b, ect.

Personally while the linux burning apps work here I don't like how the gui apps have virtually no settings, means to adjust and tell you nothing about what they're doing, what file ext.'s are being used, ect. Your left to trust them and then see after the burn is finished if your disk will play on standalones, pc's, various Os's. This forum is littered with threads about failed burns, slow burning speeds, incompatibilities with other Os's, even gutsy <-> hardy, boot disks being burned as data and on and on.

I've never had imgburn fail to burn a disk properly with proper ext.'s that work on _everything_ else with the default settings. (except in the rare case of bad media). Even then your free to change the settings, options, in a ton of different ways. My burning speeds are whatever I want within the limits of the media and burner.
While your issue may be outside of what burning app, drivers are being used, it's well worth learning how to use and adjust Imgburn if you do more than occasional dvd/cd burning.

---

### Post by Dr Bones on 2008-06-23
Ok I went into Wine and changed the version of Windows from XP to NT 4.0 and also went to the drives page then hit the auto detect button and then apply.  Wine picked up a cdrom drive although imgburn still does not detect any writers.  I went back into the wine config page and I noticed that after I had closed the window the writer was no longer listed until I pushed the auto detect button again and this appears to happen every time that I close the configuration window.   What do you suggest I do next.

---

### Post by mc4man on 2008-06-23
i was writing my 'rant' didn't see your post, and sorry about the rant to some extent
What version of wine are you using and did you click apply after making changes in winecfg?

---

### Post by Dr Bones on 2008-06-23
I am using Wine 0.9.59 as it was in the repositories and didn't feel like compiling it to install.  Also to your other question I did click apply.  Changing the windows version to NT 4.0 stayed but as I was saying the addition of the drom drive did not.

---

### Post by Dr Bones on 2008-06-23
Ok I went in and manually added the drive and it did show up in imgburn and it appears to be burning correctly right now.  I will get back to you if it works correctly.  Thanks again for the help and is there any ideas you have as to why it does not work in linux but works through wine.  Also I am not aware if you knew that I had tried to burn the disk through the terminal using growisofs command and had similar a fate.

---

### Post by VMC on 2008-06-23
> **Dr Bones said:**
> ....  I did notice that the imgburn program listed no writers detected when I went into the img burning section of the program at the bottom.  
...

The reason ImgBurn shows no devices is because it needs further setup in Wine configuration. Look at my screen shots and make sure you setup ImgBurn for Windows NT:

---

### Post by Dr Bones on 2008-06-23
OK, imgburn succesfully burned the image to disc and I tried brasero and it also worked.  This is very confusing as I retried using Gnomebaker again and got the same error.  Do you think uninstalling and reinstalling gnomebaker will do the trick?

---

### Post by mc4man on 2008-06-23
> Do you think uninstalling and reinstalling gnomebaker will do the trick? You could try, gnomebaker may have some bug that's manifesting itself for you. 
I know there is this widespread philosophy that one should only use native apps in linux. I just don't get that, to me an app or prog is just a tool, where it comes from I don't care, i prefer to use the best tool for the task at hand.
If you decide to keep wine, imgburn
 
Wine ver. ...59  has some bugs specific to ubuntu, if you keep it i'd upgrade to latest ver.
To upgrade and keep the app menu.
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
```
```
sudo apt-get update
```
then ck. in package manager and let it install update
for reading on imgburn and settings, if you choose to keep
[http://forum.imgburn.com/index.php?showforum=4](http://forum.imgburn.com/index.php?showforum=4)

---

### Post by Dr Bones on 2008-06-23
I know what you are saying and for that reason I was using utorrent for a long time as it is very easy to use, I was familiar it coming from the windows platform and overall it had the best layout I had used up until that point.  I don't use torrents that often any more so I have just been using transmission which has always done what I needed it to do.  I guess the main thing to take away with this is what do I prefer and the answer is something that works and is not overly complicated or poorly designed.  I will just stick to using brasero for everything and hopefully some time in the future this bug will work itself out over the course of updating as I really did like gnomebaker but hey who knows I may take a liking to brasero in the long run and want to use that in the future.  Thank you again all.

---

