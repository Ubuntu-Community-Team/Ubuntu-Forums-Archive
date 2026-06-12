---
title: "Restore Bootloader + fix windows"
date: 2007-06-23
forum: General Help
---

### Post by Efaustus9 on 2007-06-23
I installed ubuntu on to my machine about a week ago. Ubuntu shared the 200GB maxtor hard drive with an already present installation of windows xp home, with the allocation being 160GB windows and 40GB Ubuntu. For a few days everything was working find untill I wanted to access and update files from my windows instillation in ubuntu.So I installed the NTFS Read and Right support program and tried to mount the windows drive. I was informed that the windows drive requires a drive check which will run on its next boot. So I shut down and try to load windows where I am presented with a BSOD which states [unmountable boot volume]("http://support.microsoft.com/kb/555302"). I run Fixboot in the xp recovery console hoping that this will recover the windows installation instead I am presented with simply NTDLR is missing.So now I can not access either windows or ubuntu, next I run testdisk which is able to restore functional MBR (which does not list my ubuntu installation) but when windows loads I still get the BSOD with the aforementioned message. so i am open to suggestions as to how to enable a bootloader that will restore the ubuntu option and how to fix the boot.ini or what ever it is that is causing windows to die during a bootup. I will note that I have tried to reinstall grub using the methods described in this form to no avail. On the live cd I can still access both drives which I have utilized to salvage most of the important data in case a format is necessary.

---

### Post by merlinus on 2007-06-23
Have you tried SuperGrub?

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

---

### Post by logos34 on 2007-06-23
> I was informed that the windows drive requires a **drive check** which will run on its next boot. So I shut down and try to load windows where I am presented with a BSOD which states unmountable boot volume. I run Fixboot in the xp recovery console hoping that this will recover the windows installation instead I am presented with simply NTDLR is missing.So now I can not access either windows or ubuntu, next I run testdisk which is able to restore functional MBR (which does not list my ubuntu installation) but when windows loads I still get the BSOD with the aforementioned message.

My question: did windows run CHKDSK on restart before erroring out with "unmountable boot volume"?  That's what supposed to happen.  If it didn't run chkdsk you could try doing it manually from the recovery console.

**chkdsk volume:/r**

may or may not do any good though

---

### Post by Efaustus9 on 2007-06-23
thank you both for your quick responses :D

to merlinus: 

In fact I just finished using [UBCD]("http://www.ultimatebootcd.com/download.html") which has supergrub on it. Following directions from another thread, supergrub was able to restore grub bootloader and in doing so restored my Ubuntu installation. I had tried this before employing testkdisk but the MBR was to FUBAR for it to work. 

to logos34:

yes I did actually try chkdsk /r before trying both fixboot and fixbr, but chkdsk /r returned a "unrecoverable problems have been found" 

Im wondering if the problem exists with the boot.ini and if so how do I go about fixing it.

---

### Post by logos34 on 2007-06-23
> supergrub was able to restore grub and in doing so my Ubuntu installation.

ok, at least one problem is solved.  

> So I installed the NTFS Read and Right support program and tried to mount the windows drive. I was informed that the windows drive requires a drive check which will run on its next boot


Now that you can get back into ubuntu, you might try running 'ntfsfix' on windows.  Again, not sure it will solve any problems but can't hurt.

**sudo apt-get install ntfsprogs**

Make sure windows in unmounted

**ntfsfix /dev/yourwindowspartition **


> Im wondering if the problem exists with the boot.ini and if so how do I go about fixing it.
doubt it.  but here's mine if you want to compare (windows on hda1; I added the grldr bit):
> 
[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect /usepmtimer
c:\grldr="Ubuntu Linux"

---

### Post by Efaustus9 on 2007-06-24
thanks for the follow up logos34. Now that I am back into ubuntu the windows drives strangely seems mount by default (as "dsk1_vol1") and the only way to unmount it is to toggle the NTFS read/right program off and on (where it claims it cant mount the drive that was just mounted). Im not sure as to weather or not this floating NTFS drive  with out an OS designation is the cause, but ubuntu has been a bit buggy at times, with windows refusing to close, and applications refusing to open. I attempted your suggestion logos, but to no avail, for after downloading and running ntfsfix I am presented with various forms of "can not find or mount drive" and it suggests I run chkdsk. also I while i am on a role I was trying to set up some "launchers" for the desktop but in my home folder I can not see any folder except desktop. How to I get to my program files folder or rather make these files and folders visible? Once again I appreciate all your help :D.

---

### Post by logos34 on 2007-06-24
gconf-editor

apps>gnome>nautilus>desktop

As for ntfsfix, i guess the old way was to run it on unmounted htfs volume, but that's apparently changed (?)...In any event it just marks the volume as 'dirty' and schedules a check on next boot into windows.  but you've already done all that.

ntfs-3g automounts windows by default. You don't want that, or was that related to unmounting them for ntfsfix?

---

### Post by Efaustus9 on 2007-06-24
> **logos34 said:**
> gconf-editor

apps>gnome>nautilus>desktop

thats neat, so is nautilus analogous to the control panel in windows? yet I still cant navigate to certain folders (well pretty much any folder) for example I want to see z:\home\user\.wine\c_programfiles\ect ect... . I can get as far as Z:\home\user\ but the only file that shows up under my user name is desktop.  also I installed gdesklets recently and I was wondering if Its at all possible to get the program to load when the system starts? 


> **logos34 said:**
> 
As for ntfsfix, i guess the old way was to run it on unmounted htfs volume, but that's apparently changed (?)...In any event it just marks the volume as 'dirty' and schedules a check on next boot into windows.  but you've already done all that.

ntfs-3g automounts windows by default. You don't want that, or was that related to unmounting them for ntfsfix?

Im going on a number of tangents huh? there is just so much new to learn and yet I still haven't resolved my main issue, that being restore windows. anyways, it appears, according to you analysis that the auto mount is not a mishap but a behavior of ntfs-3g. Im wondering since the problem seems to have originated from this apps instillation that if I uninstall it I might be headed in the right direction towards a resolution. so how do I uninstall ntfs-3g and where do you think I should go from there?   thanks yet again.

---

### Post by logos34 on 2007-06-24
> **z:\home\user\[B].wine**...

it's a 'hidden' folder (they start with a '.' -- like /home/user/.Trash)

Sneaky,[B] eh?

View>Show hidden folders[/B]

> also I installed gdesklets recently and I was wondering if Its at all possible to get the program to load when the system starts?

**admin>sessions>startup programs tab**
<program command>

> Im wondering since the problem seems to have originated from this apps instillation that if I uninstall it I might be headed in the right direction towards a resolution. so how do I uninstall ntfs-3g and where do you think I should go from there? thanks yet again.

You can uninstall it from Synaptics (complete removal)

[B]Or
sudo apt-get --purge --remove ntfs-3g ntfs-config[/B]

Not sure where's the next stop.  let me think.

---

### Post by AndyCinDallas on 2007-06-24
Something I found:   

1.  Insert the Windows XP bootable CD into the computer.
2. When prompted to press any key to boot from the CD, press any key.
3. Once in the Windows XP setup menu press the "R" key to repair Windows.
4. Log into your Windows installation by pressing the "1" key and pressing enter.
5. You will then be prompted for your administrator password, enter that password.
6. Copy the below two files to the root directory of the primary hard disk. In the below example we are copying these files from the CD-ROM drive letter "E". This letter may be different on your computer.

[b]copy e:\i386\ntldr c:\
copy e:\i386\ntdetect.com c:\[/b]

7. Once both of these files have been successfully copied, remove the CD from the computer and reboot.

Once all that is done, bear in mind that Windows is a jealous mistress and will pretty much wipe out Grub, so you'll then have boot up from your Ubuntu CD and reinstall that.

---

### Post by Efaustus9 on 2007-06-25
> **logos34 said:**
> it's a 'hidden' folder (they start with a '.' -- like /home/user/.Trash)

Sneaky,[B] eh?

View>Show hidden folders[/B]

**admin>sessions>startup programs tab**
<program command>



You can uninstall it from Synaptics (complete removal)

[B]Or
sudo apt-get --purge --remove ntfs-3g ntfs-config[/B]

Not sure where's the next stop.  let me think.

why thank very much.

> **AndyCinDallas said:**
> Something I found:   

1.  Insert the Windows XP bootable CD into the computer.
2. When prompted to press any key to boot from the CD, press any key.
3. Once in the Windows XP setup menu press the "R" key to repair Windows.
4. Log into your Windows installation by pressing the "1" key and pressing enter.
5. You will then be prompted for your administrator password, enter that password.
6. Copy the below two files to the root directory of the primary hard disk. In the below example we are copying these files from the CD-ROM drive letter "E". This letter may be different on your computer.

[b]copy e:\i386\ntldr c:\
copy e:\i386\ntdetect.com c:\[/b]

7. Once both of these files have been successfully copied, remove the CD from the computer and reboot.

Once all that is done, bear in mind that Windows is a jealous mistress and will pretty much wipe out Grub, so you'll then have boot up from your Ubuntu CD and reinstall that.

thanks for contributing I was contemplating copying the core system files from the start up disk back into windows.  I usually do this to help some one, who's system is debilitated, access their must have files before I format.

---

### Post by logos34 on 2007-06-25
> **Efaustus9 said:**
> why thank very much.



thanks for contributing I was contemplating copying the core system files from the start up disk back into windows.  I usually do this to help some one, who's system is debilitated, access their must have files before I format.

At this point it might just be easier to backup all your personal files and settings, and reinstall windows (if the last poster's suggestion doesn't work).  Then, if you have a floppy drive, use the live cd to write grub from root to a [grub boot floppy]("https://help.ubuntu.com/community/GrubHowto/BootFloppy") and use that to get into ubuntu, leaving your windows bootloader untouched.  Then at least you'll have access to both OS's. The floppy will allow you to experiment with different windows entries and maybe you will happen upon one that will get you into windows.  When you are sure it works, reinstall grub to the mbr.  

Or use SuperGrub CD to boot ubuntu.

edit: and your boot.ini looks ok.

---

