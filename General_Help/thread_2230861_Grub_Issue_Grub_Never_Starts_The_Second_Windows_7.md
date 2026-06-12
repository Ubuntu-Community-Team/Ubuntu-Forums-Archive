---
title: "Grub Issue: Grub Never Starts The Second Windows 7"
date: 2014-06-21
forum: General Help
---

### Post by JessWLStuart on 2014-06-21
Howdy!  Thanks for reading this.  I searched the forums and didn't find this issue listed.

I have an Ubuntu 12.04 installation.

**My goal:**
[LIST]
[*]Use Grub to tripple-boot between Ubuntu 12.04, Windows 7 (gaming), Windows 7 (productivity) 
[/LIST]

**Technical Facts:**
[LIST]
[*]Each OS is on separate 500 Gb hard drive. 
[*]The Windows 7 (gaming) instance was installed from scratch.  The Windows 7 (productivity) instance is a restores of Acronis True Image gaming images. 
[/LIST]
[INDENT=2]Note: I'm looking into changing the license on the Windows 7 (productivity) instance, but right now they have the same license.

[/INDENT]

[LIST]
[*]When I start grub, I see the Ubuntu selections, and two Windows 7 selections (/dev/sdb1, /dev/sdc1). 
[/LIST]

**Problem:**[INDENT]Selecting either Windows 7 results in running the Windows 7 (gaming) instance.  The Windows 7 (productivity) instance is ignored.[/INDENT]

**What I've Tried So Far:**
[INDENT][B]
I compared grub.cfg files generated when only one Windows 7 instance was available.  The files were identical.[/B]

[/INDENT]

[LIST]
[*=1]I alternately disconnected the each one of the Windows hard drive (disconnected the SADA and power cables) so only one Windows 7 instance was available
[LIST]
[*=1]I ran sudo update-grub 
[*=1]I made a copy of the grub.cfg file 
[*=1]Note: Selecting either Windows in grub successfully started the Windows 7 instance (i.e. productivity and gaming both run independently). 
[/LIST]
  
[/LIST]

[INDENT]**I compared the Windows 7 selections in the grub.cfg files generated when both Windows 7 instance was available.**
[/INDENT]

[LIST]
[*=1]The only difference was the drive letter (sdb1 vs sdc1). 
[/LIST]

Please let me know if putting the grub.cfg files into this thread would help (I don't want to bloat my posts if it isn't necessary).

Thanks!

Jess

---

### Post by oldfred on 2014-06-21
Grub is not the issue if you have Windows on two separate drives. But if one is the image of another the BCD and internal data are the same. So it is like in Ubuntu where you have duplicate UUIDs which are not allowed. You have duplicate internal data.
Not sure if editing BCD alone would work. But I do not think you are allowed to run two copies anyway.

---

### Post by JessWLStuart on 2014-06-21
I thought it might be that.

So:
Any images made from the gaming drive will only be used on the gaming drive.
Install another instance of Windows7 on the productivity drive with a different license.

Thanks!

---

