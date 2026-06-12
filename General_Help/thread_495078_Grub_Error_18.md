---
title: "Grub Error 18"
date: 2007-07-07
forum: General Help
---

### Post by hooksie on 2007-07-07
Alright, so Windows XP, in all it's wonderful glory, decided to crash for the second time.  Apparently I used the soft reboot button right before it blue screened, because when I was loading grub, I got:

> Grub Error 18

which is (got this info from another site, and it matches the further error information grub gave me)

> 18 : Selected cylinder exceeds maximum supported by BIOS. This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).

My system is set up as a dual boot between XP Pro and Ubuntu 7.04.  Anyways...

First I tried commenting out the Windows entry in Grub.  No success.  They I tried inverting that, uncommenting the XP entry and commenting out all the Ubuntu ones.  Same error.

The one thing I noticed was that when I commented out the windows entry, it at least would show me the list of Ubuntu Kernals I could boot.  Selecting anything though got me the same error.

I think I should try reinstalling grub, but I really have no clue where to install to.  I know I should use grub-install, but thats it...

Aside: Ugh windows.

---

### Post by phidia on 2007-07-07
From the live or install cd you should be able to chose "Recover broken system" and then from the rescue environment select "Reinstall GRUB bootloader"

---

### Post by hooksie on 2007-07-07
> **phidia said:**
> From the live or install cd you should be able to chose "Recover broken system" and then from the rescue environment select "Reinstall GRUB bootloader"

Where specifically is this option?

And now, for some reason, after waiting a few minutes with the system off (I think it's overheating) I'm getting Grub Error *17*

> 17 : Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

(This is, by the way, with only the Windows option uncommented in menu.lst).

---

### Post by hooksie on 2007-07-07
Anyone?

---

### Post by hooksie on 2007-07-07
Sorry for the triple post but,

I've done a bunch of searching on this "Recover Broken System" option and I've come up empty handed.  Are you sure it exists on the 7.04 feisty live CD?

---

### Post by phidia on 2007-07-08
Yes I just ran the cd and it's there. Are you sure that you are booting from the cd? I'm asking that because in post #3 you said something about menu.lst. You won't be getting a grub menu from the live or install cd.
The option from the live or install cd is "Recover broken system".

If you can't get that to work for some reason try booting from the livecd and open a terminal and type > grub-install /dev/hd? where I typed "?" put in the appropriate letter designation of your 1st hard drive. If that doesn't work there are other things to try, but try that and let the thread know how that goes.

---

### Post by hooksie on 2007-07-08
> **phidia said:**
> Yes I just ran the cd and it's there. Are you sure that you are booting from the cd? I'm asking that because in post #3 you said something about menu.lst. You won't be getting a grub menu from the live or install cd.
The option from the live or install cd is "Recover broken system".

If you can't get that to work for some reason try booting from the livecd and open a terminal and type  where I typed "?" put in the appropriate letter designation of your 1st hard drive. If that doesn't work there are other things to try, but try that and let the thread know how that goes.

Dont worry, I'm just alternating from booting into the LiveCD and booting from the HDD.  I edited menu.lst from the LiveCD by going into the filesystem of my Ubuntu install.

Anyways, I think I'm just looking in the wrong place for this option.  Is it in the Ubuntu startup screen, right after booting to CD, with the "Start or Install Ubuntu," "Start Ubuntu in Safe Graphics Mode," and "Install with Driver Update CD" options?  Or is it somewhere within the OS itself?

Thanks.

---

### Post by logos34 on 2007-07-08
It's "Rescue a broken system" and it's only on the startup menu screen of the text-mode Alternate install CD...the 1024 cylinder limit error is strange unless this is an older system, and maybe your getting the error 17 because whatever is wrong with windows in preventing it from recognized properly.  I don't think reinstalling grub will help but here is the easy method:
**[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)**

I'd run CHKDSK on windows from the XP install cd recovery console.  You could also do a filesystem check of linux from the live cd:

**sudo fsck /dev/hda2**  (replace 'hda2' with your root partition)

---

### Post by phidia on 2007-07-08
On my cd it's definately "Recover a broken system" and it's available at the first screen you see when the cd loads. 
I mostly use the alternate cd because I multi-boot but the Ubuntu Hacks book from O'Reilly says it's also available from the install cd.
I'm not sure if they're calling the alternate cd the install cd so I'd have to check if that menu option is on the live cd- I'll do that and post back.

Added: So logos34 is right. At least it isn't available on the feisty livecd. It is on the alternate install cd.

---

### Post by hooksie on 2007-07-08
Thanks for all the help.

However, now I'm really starting to come to the conclusion that I have some sort of problem with my HDD.  Every attempt at installing Windows XP again has resulted in a Blue Screen, and booting Ubuntu shows I/O errors when quiet boot is disabled.

Ughh

---

### Post by logos34 on 2007-07-09
try running S.M.A.R.T. diagnostic if you think it's the drive

[B]sudo apt-get install smartmontools

sudo smartctl -a /dev/<yourdrive>[/B]

---

### Post by hooksie on 2007-07-09
> **logos34 said:**
> try running S.M.A.R.T. diagnostic if you think it's the drive

[B]sudo apt-get install smartmontools

sudo smartctl -a /dev/<yourdrive>[/B]

"Device does not support Self Test logging"

:confused:

---

### Post by GerryB on 2007-07-09
This also might give you some idea about the problem.
[http://ubuntuforums.org/showthread.php?t=377674](http://ubuntuforums.org/showthread.php?t=377674)

---

### Post by hooksie on 2007-07-09
Used the alternate CD to run the rescue option.  I only sometimes used to get this, now I'm getting it each time (sometimes I would get the ntldr missing message).

> A disk read error has occurred
Press Ctrl+Alt+Del to restart

Also, I did another memtest last night.  I had to stop it after 2.3 passes, but there were still no errors at that point.  ( I read somewhere that error may be caused by bad Ram)

:(

---

### Post by hooksie on 2007-07-10
I completely reinstalled Ubuntu (keeping the old partition system intact) and the problem persists.  Should I format the entire drive?

---

### Post by hooksie on 2007-07-10
Last resort time.  I've decided to just format the *entire* drive, making new partitions and everything.

Wish me luck. :P

---

### Post by atlfalcons866 on 2007-07-10
try using the diagnostics disc from the manufacture of the hard disk

---

### Post by hooksie on 2007-07-10
> **atlfalcons866 said:**
> try using the diagnostics disc from the manufacture of the hard disk

Well, I did my full format, and everything is fixed.  Now for the pain in the *** of restoring all my files...

---

