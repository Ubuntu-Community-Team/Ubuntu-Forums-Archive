---
title: "Installed Ubuntu but now having problems with WinXP"
date: 2008-06-03
forum: General Help
---

### Post by ERAUman on 2008-06-03
I have 3 hard drives (40,80,500GB) with winXP on the 80gb. I've run into a pretty big problem. I decided to install ubuntu onto my 40gb hdd and it works fine (still trying to get the dual monitors up though). But now winXP will not boot.  During the install I used the "use entire hdd feature" for installing ubuntu so it shouldn't have affected other hdds. If it helps at all, i have my 40gb as the first master hdd and the 80gb is the slave and the 500gb one is the second master. When I try to boot XP it gives me an "Operating system error".

---

### Post by Aearenda on 2008-06-03
Windows XP really, really wants to be on drive C:, which is the master drive on the first IDE channel, even if you tell it different. 

When you installed XP, was its drive the master? 
If so, as the first test, I would change it back and see if it works then. 
If not, was XPs drive the first in the boot order? 
If so, try changing that back as well.

Please tell us what happens.

There is magic stuff you can do in Grub to make XP think it is on the first drive when it isn't, but let's not try that until we know XP itself is bootable still.

EDIT: In case I'm not around when you get to try this, and assuming you have proved you still have a working XP installation, here's a link to a post that tells you how to do the Grub magic:
[http://ubuntuforums.org/showpost.php?p=87591&postcount=7](http://ubuntuforums.org/showpost.php?p=87591&postcount=7)
For this to work you should return things to the state you described in your first post, with Ubuntu on the master drive on the first IDE controller and XP on the slave. If it doesn't work, try changing the 'root (hd1,0)' statement in these instructions to 'rootnoverify (hd1,0)'.
It would also be possible to leave XP as the master drive and get it to boot Ubuntu from the NTLoader menu, but that's a little more fiddly.

---

### Post by ERAUman on 2008-06-03
> **Aearenda said:**
> Windows XP really, really wants to be on drive C:, which is the master drive on the first IDE channel, even if you tell it different. 

When you installed XP, was its drive the master? 
If so, as the first test, I would change it back and see if it works then. 
If not, was XPs drive the first in the boot order? 
If so, try changing that back as well.

Please tell us what happens.

There is magic stuff you can do in Grub to make XP think it is on the first drive when it isn't, but let's not try that until we know XP itself is bootable still.

EDIT: In case I'm not around when you get to try this, here's a link to a post that tells you how to do the Grub magic:
[http://ubuntuforums.org/showpost.php?p=87591&postcount=7](http://ubuntuforums.org/showpost.php?p=87591&postcount=7)
This assumes you have returned things to the state you described in your first post, with Ubuntu on the master drive on the first IDE controller. 
It would also be possible to leave XP as the master drive and get it to boot Ubuntu from the NTLoader menu.

XP was previously on the slave drive like it is now, however, I had an older, corrupted version that I was too lazy to get rid of before on the master drive (40gb).  I installed Ubuntu on the 40gb drive wiping that clean and Ubuntu now works fine. I changed the boot order so that the 80gb drive with winXP was first, but I got the same error, I'll try and switch the jumpers to change the 80gb hdd  to the master.  Thanks for the quick response.

---

### Post by Aearenda on 2008-06-03
If you can't get XP to start, try creating a boot floppy (assuming you have a floppy drive!) as explained in [http://support.microsoft.com/kb/305595](http://support.microsoft.com/kb/305595). But note that for your system, assuming the XP drive is back to being a slave, you will need to put 
```
[boot loader]
timeout=30
Default= multi(0)disk(0)rdisk(1)partition(1)\windows
[operating systems]
multi(0)disk(0)rdisk(1)partition(1)\windows="Windows XP"

``` in boot.ini, since you need to start from drive 1, not drive 0 (the two 'rdisk' numbers are changed).

---

### Post by ERAUman on 2008-06-03
alright, i'm going to try that.

---

### Post by Aearenda on 2008-06-03
I suspect this is what has happened:
1. You installed the old XP in C: on the 40Gb drive. This created all the XP boot files etc on C:.
2. Later, you installed XP again on the 80Gb drive, which I will call D:. This added itself in to the boot config on C:, but needs to run on D:.
3. Later still, you wiped C: and installed Ubuntu. This deleted the XP boot configuration, but added an entry for Windows XP in the Grub menu to chainload to first partition on the second drive D:, which it calls (hd1,0). Unfortunately, there is no boot code for XP in that partition, since it was using C:.

If I'm right, the boot floppy idea should work for now.
What to do about it: I have a variety of ideas, but nothing certain. It may be that all you need is to add ntdetect.com, ntldr and boot.ini on D:. It may be that D: needs the volume boot record added (see [http://en.wikipedia.org/wiki/NTLDR](http://en.wikipedia.org/wiki/NTLDR)). 
The XP CD has a recovery mode, which may be able to repair things. In doing so, it may prevent Ubuntu from loading, and it may need C: to be re-established with FAT or NTFS. I don't know for sure, as it is now a very long time since I had to do this, and so I'm going to suggest we wait and see if anyone else who has done this kind of repair pops up with a reply. It may be necessary for a new thread to be started with a title like 'Repairing XP on D:' or something like that to attract attention.

Sorry to slow things down like this, but if we rush in we may end up with the loss of both XP and Ubuntu installations.

OTOH, if you're prepared to reinstall from scratch, we can get you running quickly by making the 80Gb drive the master, installing XP first, then installing Ubuntu on the 40Gb as slave. That should 'just work' :)

---

### Post by ERAUman on 2008-06-03
I really appreciate the help, I'm still working on the floppy disk solution.

edit: the floppy disk worked (i actually created a bootable cd, since i couldn't quite format my floppy disk in ubuntu). I'm going to take a look at the wiki link. I guess I'll look for where to add the ntdetect.com, ntldr and boot.ini files.

edit2:I also just loaded "settings" from the "startup and recovery" in my computer's advance tab and found out that windows could not find boot.ini, so that seems to def be the problem, where is normally supposed to be found?

---

### Post by Aearenda on 2008-06-03
All those files should be at the root of the drive (c:\ if drive c:, d:\ for d: - presumably the latter). You should be able to copy the working ones off your CD. After doing that, I'd try a boot via the Ubuntu Grub menu again next - it shouldn't need any of the changes referred to in that link I gave you, since XP knew it was being installed on the second drive.

---

### Post by Aearenda on 2008-06-03
More googling: if the previous failed, after making a backup of any data you wish to be sure you have preserved, which you now have access to thanks to the CD you made, you could boot the recovery console using an XP installation CD and then run ```
fixboot d:
```(assuming d: is the system drive where windows is - check that!)

This is supposed to put the boot sector back on that partition. This is where the Grub chainloader command links to, I think. You still need the boot.ini, ntdetect.com and ntldr files to be there too. After this is done, see if you can boot via the Ubuntu Grub menu.

Note: this is not the same as fixmbr. Don't try that one.

---

### Post by ERAUman on 2008-06-04
> **Aearenda said:**
> More googling: if the previous failed, after making a backup of any data you wish to be sure you have preserved, which you now have access to thanks to the CD you made, you could boot the recovery console using an XP installation CD and then run ```
fixboot d:
```(assuming d: is the system drive where windows is - check that!)

This is supposed to put the boot sector back on that partition. This is where the Grub chainloader command links to, I think. You still need the boot.ini, ntdetect.com and ntldr files to be there too. After this is done, see if you can boot via the Ubuntu Grub menu.

Note: this is not the same as fixmbr. Don't try that one.

Ok, thanks again for your help, copying the files off of the cd didn't work so I'm going to have to obtain a copy of the xp recovery disk.  I'll try that as soon as i get the chance.

---

### Post by ERAUman on 2008-06-04
I inserted an XP cd and my two options are to install windows or repair windows. When I choose the repair option, it tells me which windows i want to repair and only lists c:/windows...?

---

### Post by Aearenda on 2008-06-04
I think it is ignoring the Ubuntu disk, since it can't understand the filesystem there. I would disconnect the Ubuntu disk, make the Windows disk the master, and then let fixboot do its work on 'c:'.
Then put the Ubuntu drive connector back and see what happens.

---

### Post by ERAUman on 2008-06-04
> **Aearenda said:**
> I think it is ignoring the Ubuntu disk, since it can't understand the filesystem there. I would disconnect the Ubuntu disk, make the Windows disk the master, and then let fixboot do its work on 'c:'.
Then put the Ubuntu drive connector back and see what happens.
Ok, going to try that.

---

### Post by ERAUman on 2008-06-04
I tried disconnecting the C drive (ubuntu) to no avail, should I try to rename my drives since windows seems to have an affinity towards the C drive?

---

### Post by Aearenda on 2008-06-04
That's not easy to do with Windows already installed. There are too many places in the registry where the drive letter is used. 

So the situation now is that you can't boot XP via the Grub menu, even though you have tried fixboot and have copied the boot.ini, ntdetect.com and ntldr files into the root of the XP drive; but Ubuntu still boots correctly, right?

Does the boot CD you made still work to start Windows?

From Ubuntu, please post the part of /boot/grub/menu.lst that contains the XP startup section - starting with 'title' and probably containing 'chainloader +1'.

EDIT: I'm going to install XP in a virtual machine to see if I can recreate your situation. This is why I want to check up on where things stand now.

EDIT2: I've been out for a bit, but now I'm back. I have my VM, and have observed the same outcome as you. I have then reinstalled XP on C:, and proven that after editing boot.ini on C: the system on D: can be started. The downside to this is that it means Ubuntu has to be moved, so now I'm going to work on how to avoid having to do this!

---

### Post by Aearenda on 2008-06-05
Here is what I have found:
1. FixMBR simply doesn't work under these circumstances.
2. Copying the boot sector from a bootable XP drive to the slave drive makes that drive bootable when master - but in my test the two drives were the same size, so we need to take care to preserve your partition table. Also, this test changed the driver letter of the system drive, which is not desirable.
3. The partition on the slave drive was not marked bootable.
4. When all of these things are fixed, and boot.ini, ntdetect.com and ntldr are present on the slave, the following Grub segment will boot XP off the slave drive:
```
title Windows XP from Slave Drive
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1
```

I will experiment further to deal with the differing sizes and avoiding the drive letter change - watch this space.

---

### Post by Aearenda on 2008-06-05
OK, here is what I think you should do, with the Ubuntu drive as master and the XP drive as slave. It seems to leave the XP system's drive letter alone - it should end up the same as it began.

1. Using your existing boot CD, make sure you have a backup of any valuable files on XP - just in case!

2. Reboot and do the same for Ubuntu.

3. In Ubuntu, do this in a terminal:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.old
```
That takes a backup of the Grub config.

4. Now do this in a terminal:
```
gksudo gedit /boot/grub/menu.lst
```
Find the section that refers to your XP installation, which will have a chainloader entry. It probably looks something like this:
```
title         Windows XP
root          (hd1,0)
makeactive
chainloader   +1

```
Make it look like this:
```

title          Windows XP
rootnoverify   (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader --force +1
```

If it doesn't exist, create it either at the very end of the file, or just before the line ```
### BEGIN AUTOMAGIC KERNELS LIST
```Take care not to alter anything else.

5. Now we need to make the NT partition bootable. Do this in a terminal:
```
sudo fdisk /dev/sdb
```
Press 'p' first to make sure there is one partition on the drive, with its type set to HPFS/NTFS. If it is wrong, press 'q' and stop here!
Next press 'a' and then '1' and then 'p' again; this time the partition should have a '*' below the 'boot' column. If so, press 'w'; if not, press 'q' and stop here!

6. Now reboot using the Windows XP installation CD, and get into a recovery session. It does not seem to matter that this calls the Windows partition C:. 

7. First, let's check that the drive is where we think it is:
```
map
```
This should produce a list of drives, including the Ubuntu ones. Find the one that is marked as NTFS, which is probably C:. Notice it's device path, which is probably \device\harddisk1\partition1. If it isn't, stop here!

8. Now we have to put the essential boot files on the drive. I'm assuming here that the CD drive is D:.```

copy d:\i386\ntdetect.com c:\
copy d:\i386\ntldr c:\

```
It seems that we can omit boot.ini! These are the paths to the two files on my installation CD - if yours is different, you might need to hunt for them.

9. Next we need to add the MBR and boot sector. This appears to work only if the partition is set bootable, which we did in step 5. ```
fixmbr \device\harddisk1
fixboot c:
```
Note that the fixmbr device path omits the partition name, since we are working on the boot sector of the drive.

10. Type ```
exit
``` to reboot, and take the CD out. The machine should boot to Grub, and from there to Ubuntu.

11. Assuming all is well, reboot again, and this time press 'ESC' to enter the Grub menu, select your XP entry, and try that. Hopefully, it will work!

Good luck!

---

### Post by ERAUman on 2008-06-05
Thanks again for your help, I was able to get "Windows XP" displayed in the Grub Menu but when I would try to boot it from the menu I would get an error that said I needed a valid pathname or blocklist.  The only glitches I ran into were that while in the terminal while checking to see if the partition was labeled as a boot sector, it already was (I'll check again to make sure that I was for sure dealing with the right drive and partition but I think I was). So I made sure that it was still labeled as a boot sector before I closed the terminal. And while in the recovery console, my 80gb hdd with windows was labeled as \device\harddisk**0**\partition1 instead of \device\harddisk**1**\partition1.  I still went ahead and copied the files to \device\harddisk0\partition1 instead of \device\harddisk1\partition1.  The recovery console successfully fixed the master boot record and and add the boot sector. It seems as though the problem may lie in the Grub menu. Thanks again for all of your help!!!

---

### Post by Aearenda on 2008-06-05
Hmm - when you saw the windows drive as harddisk0 in the recovery console, was it in fact the master drive? I don't see how it could be drive 0 while still being slave. Anyway, from Ubuntu, please post the output of ```
sudo fdisk -l
```which should help getting the Grub menu fixed.

---

### Post by ERAUman on 2008-06-05
Oh, sorry, I changed the jumpers on my hdd so that the windows drive was the master and ubuntu is on the slave.

---

### Post by Aearenda on 2008-06-05
Ah, that would account for it. In that case, the Grub entry for XP needs to have 'rootnoverify (hd0,0)'. BUT, you will need to change all the entries for Ubuntu to say 'root (hd1,0)' -  in fact, I'm surprised you have managed to boot Ubuntu without coming across this!

---

### Post by ERAUman on 2008-06-05
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x471ad2cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      969018   488385040+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f350b3e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ffb1ffa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4660    37431418+  83  Linux
/dev/sdc2            4661        4865     1646662+   5  Extended
/dev/sdc5            4661        4865     1646631   82  Linux swap / Solaris

```

edit: Ok, I'll proceed to go to my terminal

---

### Post by Aearenda on 2008-06-05
Hang on a minute - your Ubuntu drive is /dev/sdc here - don't rush in yet!

Please tell me how the drives are cabled now - it sounds like the 80Gb XP should be primary master, Ubuntu the primary slave, and the big drive secondary master - but is it? 
Please post /boot/grub/device.map.

Also, the XP drive is NOT showing the bootable flag. But since my idea of where the drives were didn't match reality, that's hardly surprising.

---

### Post by ERAUman on 2008-06-05
> **Aearenda said:**
> Hang on a minute - your Ubuntu drive is /dev/sdc here - don't rush in yet!

Please tell me how the drives are cabled now - it sounds like the 80Gb XP should be primary master, Ubuntu the primary slave, and the big drive secondary master - but is it? 
Please post /boot/grub/device.map.

Also, the XP drive is NOT showing the bootable flag. But since my idea of where the drives were didn't match reality, that's hardly surprising.
OK, I haven't edited anything, and I'm sure that when I was in the recovery console I restored the master boot record and fixboot'd the the 80gb winXP drive, so even though I previously mistook the master and slave drives would simply enabling the "boot" option for the 80gb drive in the grub menu fix the problem?

edit: and I just checked the cabling and jumpers and i'm sure that the 80gb winXP drive is primary master with the 40gb ubuntu drive the primary slave.

---

### Post by Aearenda on 2008-06-05
Yes, I think the recovery console part was right - but without the bootable flag being set it may not have worked. 

For XP to boot I think we need to get that boot flag set. If the layout is still as you posted it, the XP drive IS now /dev/sdb, so ```
sudo fdisk /dev/sdb
``` followed by 'a' and '1' and then 'w' should work for this.

Do this and then post the output of ```
sudo fdisk -l
``` again, and the contents of /boot/grub/device.map please.

I'm uncertain how it is that your system boots at all at the moment - which drive is the BIOS set to boot from? It may be that the BIOS is swapping the drives internally as well, depending on the boot order.

---

### Post by ERAUman on 2008-06-05
Apparently my installation of Ubuntu heard you and decided not to boot now. The weird part is that it hangs after it loads (right before the login screen)...

Hmm...if it swaps the drives depending on the boot order that could be an issue.  I change the boot order depending on which OS I want to run.

---

### Post by Aearenda on 2008-06-05
Stranger and stranger!

Can you switch to a console using CTRL ALT and F1?

BTW, the point of getting the Grub menu right is so that you don't need to change the boot order - you just choose from a menu.

---

### Post by ERAUman on 2008-06-05
Yep, just logged on.

---

### Post by Aearenda on 2008-06-05
Changing the drive order should not have caused the hang - have you done any updates to Ubuntu along the way? I had to reinstall the restricted modules on one of my machines because the nvidia driver failed to load. You could try ```
/etc/init.d/gdm stop
startx
``` from the console to try to debug the hang.

How are you connecting to the internet - another machine? 

Anyway, on with grubbing about in GRUB. If you can only get into a console, I won't ask you to post loads of stuff. From the console, you should be able to do ```
sudo fdisk -l
``` as before. Check that the 80Gb drive is /dev/sdb - and if it isn't, use the correct /dev/sd? in the next command.

Then do ```
sudo fdisk /dev/sdb
``` followed by 'a' and '1' and then 'w' to make the XP partition active.

Then do ```
cat /boot/grub/device.map
``` and post that so I can see it, please - it's only short.

---

### Post by ERAUman on 2008-06-05
It's definitely no problem for me to post this, thanks for continuing to help!

(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc

edit:to answer your other questions
-I'm using my laptop to go online right now.
-I may have installed one of the suggested updates before I last logged of Ubuntu. 
-the 80gb drive was indeed sdb like you assumed.

Thanks for taking the time to help today, I'll check your response tomorrow!

---

### Post by Aearenda on 2008-06-06
No problem!

Step 1: I assume you have done the fdisk bit, and that the 80Gb drive /dev/sdb is showing the '*' under the boot column now  - so that the output of ```
sudo fdisk -l
``` looks like this:
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x471ad2cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      969018   488385040+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f350b3e

   Device Boot      Start         End      Blocks   Id  System
**/dev/sdb1   *           1        9729    78148161    7  HPFS/NTFS**

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ffb1ffa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4660    37431418+  83  Linux
/dev/sdc2            4661        4865     1646662+   5  Extended
/dev/sdc5            4661        4865     1646631   82  Linux swap / Solaris
```
Please tell me that this matches!

Step 2: do ```
more < /boot/grub/menu.lst
```and check the contents of the line that starts "# groot=" and also the contents of the first line that starts "root=" **after** "## ## End Default Options ##". I think they will both say "(hd0,0)". Please tell me what they say. If they ARE set to (hd0,0) then your BIOS must be changing the order when booting off the slave drive; if set to (hd1,0) then not, and step 5 below needs changing.

Step 3: I'm assuming that you have Windows on the primary master, Ubuntu on the primary slave, and the big disk on the secondary master; and I'm assuming that the BIOS is set to boot from the primary slave drive (Ubuntu).
Please reboot into the BIOS setup screen and tell me if any of these don't match what you see on your BIOS screen.

Step 4: Now that the XP partition is set bootable, please reboot into recovery mode off the XP installation CD and repeat the "fixmbr \device\harddisk0" and "fixboot c:" steps. I'm not convinced they work if the partition is not bootable.


Step 5: If all the assumptions given above are true, you should be able to boot XP from the GRUB menu so long as the BIOS is set to boot off the Ubuntu drive, and you press ESC to get into the Grub menu and choose the entry that you created earlier - like this:
```
title          Windows XP
rootnoverify   (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader --force +1
```

(You should also be able to boot directly off the XP drive, by changing the BIOS boot order.)


Finally, to address the black screen before login: Reboot into Ubuntu, press ESC to get into the Grub menu, and choose the second Ubuntu entry down, if there is one - this might start the user interface properly. Tell me what happens.

BTW, you can change the following settings in /boot/grub/menu.lst if you want to avoid pressing ESC to see the boot menu:
1. Change 'hiddenmenu' to '#hiddenmenu'
2. Change the 'Timeout' value to the number of seconds you want to see the menu.
These are best changed after you have the login screen fixed, with 'gksudo gedit /boot/grub/menu.lst'.



As you've realised we have a significant time difference! It's early afternoon here :)

---

### Post by ERAUman on 2008-06-06
The 80gb is properly showing as a boot device.  Also, whenever I change the hdd boot priority the winXP 80gb hdd still stays as the primary master. However, I cannot boot any of the Ubuntu options from the Grub menu, and for some reason, whenever I copy the ntdetect.com and ntldr to my windows D:/ windows XP has a hard time booting.  If there isn't a quick fix towards rebooting ubuntu in it's gui mode than the best option might just be to reinstall as I haven't really done much to it anyway. What I'm more worried about is having to reinstall windows now.:(

---

### Post by Aearenda on 2008-06-06
> whenever I copy the ntdetect.com and ntldr to my windows D:/ windows XP has a hard time booting
I'm not sure how you're booting when this happens - from the CD, from Grub, or off its own hard drive?

Please confirm: 
1. Can you still boot into XP off your recovery CD?
2. What happens when you try to boot directly from the XP drive?

With Ubuntu, does it fail at the very beginning, or just before the login screen as before, so that you can get a command-line login? If it fails at the beginning, you can use Grub to alter the startup on the fly, like this:
1. Power the machine off so that the BIOS forgets any maps from earlier boots.
2. Power on again after 30 seconds or so.
3. Press ESC to enter the Grub menu at boot time
4. Highlight the second Ubuntu entry down - recovery mode
5. Press Enter

If this starts up (lots of text will go past, and it will stop asking whether you want to go into a root command prompt), that's good - please let me know. If it does not start up, but rather fails quickly, repeat steps 1-4 but then continue as follows:

5. Press 'e' to edit that entry
6. Select the 'root' line
7. Press 'e' to edit that line
8. If this line says (hd1,0) make it say (hd0,0); and if it says (hd0,0) make it say (hd1,0); then press enter
9. Press 'b' to boot with the modified settings

Again, please let me know if this lets you enter the root command line.

I'd rather we not lose the Grub setup by reinstalling Ubuntu until we have XP booting properly.

---

### Post by Aearenda on 2008-06-06
Another thought - how much free space is there on your 500Gb drive? Maybe you could make that one the primary master, do a conventional XP installation on it, and then add the 'real' XP installation on the 80Gb drive (now on the primary slave again) in to its boot menu. Then we can reinstall Ubuntu on the 40Gb as secondary master drive.

---

### Post by ERAUman on 2008-06-06
> **Aearenda said:**
> Another thought - how much free space is there on your 500Gb drive? Maybe you could make that one the primary master, do a conventional XP installation on it, and then add the 'real' XP installation on the 80Gb drive (now on the primary slave again) in to its boot menu. Then we can reinstall Ubuntu on the 40Gb as secondary master drive. 
The only thing i'm scared of happening is that windows try to install boot files onto the C:\ again... And I don't want to put windows on my c:\ since it's an older hdd and more prone to be corrupted. :confused:

---

### Post by Aearenda on 2008-06-06
That's why we would make the big drive the primary master - it becomes C:, not the old drive - and to make sure, the old drive could be disconnected during the installation.

---

### Post by ERAUman on 2008-06-06
> **Aearenda said:**
> That's why we would make the big drive the primary master - it becomes C:, not the old drive - and to make sure, the old drive could be disconnected during the installation.
Ok, I wasn't sure exactly how drives were designated their letters.   Disconnecting the old c:\ during installation sounds like the best option.  I think I might reinstall both windows and linux this weekend!  Thanks for your help man, even though we couldn't completely fix the problems, I learned a lot.:popcorn:

---

### Post by Aearenda on 2008-06-06
If you are going to reinstall, I would do XP first with the big drive as the only one connected - so it must be primary master, and you must use the existing partition to avoid losing any data on that drive. It may keep the drive letter that partition previously had, but it won't matter.

Then I would add the 80Gb drive as primary slave, and modify boot.ini (see first listing in next post) on the big drive to add this as the default option, so that your existing XP is recovered.

EDIT: See new post... [Finally I would connect the Ubuntu drive as secondary master, and reinstall that. Then copy it's boot sector into a file and add it into the XP boot menu - there are 'howto's around on that, I'll find one and give you the link.]

I'm sorry it didn't all work, and I'm not sure why. It DID work in my virtual machine simulation. Maybe the BIOS is just confusing things too much when changing boot order. This is why there is no change to the BIOS boot order in my suggestion in this post.

Good luck!

---

### Post by Aearenda on 2008-06-06
Here is how to set up the boot.ini file on the 500Gb drive, prior to turning off to reconnect the 80Gb drive as its slave. Start Windows XP from the 500Gb drive, and right-click on 'My Computer'; choose 'properties'. Click on the 'advanced' tab, and choose 'start up and recovery'; then click on the 'edit' button to see the contents of boot.ini. Add the line in bold, and optionally change the default as shown here:
```

[boot loader]

timeout=30

default=multi(0)disk(0)**rdisk(1)**partition(1)\WINDOWS

[operating systems]

[B]multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="XP on 80Gb drive" /fastdetect
[/B]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="XP on 500Gb drive" /fastdetect

```
Save the file and close all the windows. Reboot - you should now be able to boot your existing Windows XP system on the 80 Gb drive (assuming it is also still bootable from the CD - you never told me :) ), from the menu of the 500Gb drive.

[From now on, this is version 2 of this post!]
Reinstall Ubuntu with its drive now connected as the secondary master; it should automatically add Windows XP into the Grub menu, for both installations. But be aware, you are going to end up with a computer that relies on the old drive working to be able to boot XP, which is too risky by my thinking. 

Therefore, when the installation is complete, I would do this:

1. Use 'sudo fdisk -l' to discover the drive name of the 500Gb drive - such as /dev/sda, assumed below.

2. Make a copy of that drive's mbr:
```
sudo dd if=/dev/sda of=~/ubuntu.bin count=1
```

3. Copy the file 'ubuntu.bin' onto a flash drive using the file browser (Nautilus).

4. Now reboot to the new XP system from the Grub menu.

5. Copy the 'ubuntu.bin' file from the flash drive to the root of the 500Gb drive.

6. Modify 'boot.ini' again, and add the bolded line below:
```

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="XP on 80Gb drive" /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="XP on 500Gb drive" /fastdetect
**C:\ubuntu.bin="Ubuntu"**

```
If your 500Gb drive is not C:, change it to match.

7. Now shutdown and boot from the XP recovery CD.

8. Run fixmbr (no parameters needed). Say yes to the warning that pops up.

That should be it! Now you can choose the old XP, the new XP, or the new Ubuntu from the XP menu, all without changing the BIOS boot order; and XP will boot even if the old drive with Ubuntu on it fails.

I have successfully tested this process too in my virtual machine - good luck!

---

### Post by CHawker on 2008-08-16
[FONT="Verdana"]A repair installation of windows should help.

Insert your Windows XP Disk into your CD drive. When it comes to the first window press enter to proceed. It will scan all your hard drives for any existing Windows XP installations. it will bring up the installation on the 80gb HDD. Press R to start a repair installation of Windows. From there, simply follow all the prompts as you normally would. It should not delete any programs or files that you might have on that hard drive.[/FONT]

---

