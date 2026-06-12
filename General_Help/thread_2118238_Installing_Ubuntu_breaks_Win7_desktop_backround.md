---
title: "Installing Ubuntu breaks Win7 desktop backround?"
date: 2013-02-20
forum: General Help
---

### Post by Deliphin on 2013-02-20
I installed Ubuntu via burning the iso onto a disc, and installing that way, installed alongside Win7. Because I host a minecraft server, (everyone was offline before I installed, it was almost midnight.) so I couldn't play with Ubuntu yet, but this morning when I went to finish the installation, I immediately went to Win7 to load up my server as usual, then I noticed my desktop backround wasn't working. I changed it to a few others and still no change, it's black. I'd like to know how to fix this, and why it does this.

OS's: Windows 7, Ubuntu 12.10 (Install method: Disc)
RAM: 4GB
Processor: Intel Core 2 Quad Processor.
Video Card: Radeon HD5450.
If any other information is required, just ask.

---

### Post by thermion on 2013-02-20
This is a bit confusing.
You installed ubuntu on a partition or using wubi? And what do you mean by "...when I went to finish the installation, I immediately went to Win7...". Was the installation somehow canceled of incomplete?

---

### Post by Deliphin on 2013-02-20
> **thermion said:**
> This is a bit confusing.
You installed ubuntu on a partition or using wubi? And what do you mean by "...when I went to finish the installation, I immediately went to Win7...". Was the installation somehow canceled of incomplete?
Sorry, I didn't proofread it. I meant to say, "When I finished the installation, I immediately switched to Win7...".
I installed Ubuntu via [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) choosing Ubuntu 12.10. Not sure, I just followed the main installation, my partition was set around 500 gigs to left and 400 to right. (No images or words were said on either side for partitions, so I guessed left was Win7 like on the instructions for installation. (I read them just to be sure I wouldn't screw anything up.)

---

### Post by Mark Phelps on 2013-02-20
Presuming that you did not choose the "Windows Installer" option on that page, you must have shrunk Win7 to create an unallocated area of disk space in which to install Ubuntu.

So, HOW did you do that?  Did you go into Win7 Disk Management and do the shrinkage from there? Or, did you use the "slider" in the Ubuntu installer to do the shrinkage?

Asking because, if you did the latter (slider), you most likely corrupted some stuff in the Win7 filesystem -- as that happens sometimes when you shrink the Win7 OS partition from "outside" Windows.

When that happens, any number of functions can suddenly be broken.

---

### Post by tartalo on 2013-02-20
Windows 7 background goes to black when there is an activation problem. Did you also get a message saying that your windows copy might not be legitimate?

As far as I know, a wildly used Windows crack hijacks the Windows bootloader, so I guess that the legitimate activation check is placed there too. Perhaps something went wrong during installation, the Windows bootloader got messed and Windows replaced it with a vanila bootloader that doesn't know about you activation code yet.

Just call Microsoft and activate Windows.

---

### Post by Deliphin on 2013-02-20
> **Mark Phelps said:**
> Presuming that you did not choose the "Windows Installer" option on that page, you must have shrunk Win7 to create an unallocated area of disk space in which to install Ubuntu.

So, HOW did you do that?  Did you go into Win7 Disk Management and do the shrinkage from there? Or, did you use the "slider" in the Ubuntu installer to do the shrinkage?

Asking because, if you did the latter (slider), you most likely corrupted some stuff in the Win7 filesystem -- as that happens sometimes when you shrink the Win7 OS partition from "outside" Windows.

When that happens, any number of functions can suddenly be broken.

All I did was install ubuntu, giving Win7 about 500 Gb (still have 200GB leftover, checked C: for win7).
hm. you're possibly right about the corruption thing. anyway to fix it?

EDIT: Although I'm not sure about corruption, because I have yet to find ANY other files that are damaged.

---

### Post by Deliphin on 2013-02-20
> **tartalo said:**
> Windows 7 background goes to black when there is an activation problem. Did you also get a message saying that your windows copy might not be legitimate?

As far as I know, a wildly used Windows crack hijacks the Windows bootloader, so I guess that the legitimate activation check is placed there too. Perhaps something went wrong during installation, the Windows bootloader got messed and Windows replaced it with a vanila bootloader that doesn't know about you activation code yet.

Just call Microsoft and activate Windows.
 
My copy of Windows 7 is legitimate. I didn't get any message about the legitimacy of my Win7.

---

### Post by Deliphin on 2013-02-20
Forgot to mention, I haven't turned off my computer since I installed ubuntu, would a restart fix this?

---

### Post by Deliphin on 2013-02-21
Oh! I just thought! Could the ubuntu boot thing be the cause? (As in, when the computer loads up, when you get to the point you choose OS, it a weird color instead of black, and says grub at the top.) If so, how do I uninstall it? And will removing it interfere with Ubuntu?

---

### Post by CloakandPigeon on 2013-02-21
> **Deliphin said:**
> Oh! I just thought! Could the ubuntu boot thing be the cause? (As in, when the computer loads up, when you get to the point you choose OS, it a weird color instead of black, and says grub at the top.) If so, how do I uninstall it? And will removing it interfere with Ubuntu?

You need Grub to dual boot between Ubuntu and Windows.  The grub with Ubuntu is typically purple, when you choose Win 7 it will load your windows.  The background you are talking about is your desktop or the boot screen?

---

### Post by Mark Phelps on 2013-02-21
Don't mean to discourage you, but if you continue to have desktop problems in Win7, the best place to go is a Windows 7 forum (sevenforums.com) -- as they have forum sections and tutorials that deal with this.  IF it is an activation problem, then can tell you how to check that and fix it.

---

### Post by Deliphin on 2013-02-22
No, earlier, I first installed the Windows Installer version, when I got to the menu where you choose the OS, it said Windows 7, and Ubuntu. (I switched to disc because steam didn't work on windows installer version, I uninstalled the windows installer version using the built in uninstall.exe before installing disc version.) When I say the screen is NOW black, I mean my desktop screen, when I say it WAS black, I mean the boot screen.
EDIT: Was talking to cloak and pidgeon, forgot I hit quick reply and not quote.

---

### Post by Deliphin on 2013-02-22
> **Mark Phelps said:**
> Don't mean to discourage you, but if you continue to have desktop problems in Win7, the best place to go is a Windows 7 forum (sevenforums.com) -- as they have forum sections and tutorials that deal with this.  IF it is an activation problem, then can tell you how to check that and fix it.
Alright, I'll try it, it's just I came here first because I've never had this problem before installing Ubuntu.

---

### Post by Mark Phelps on 2013-02-24
And, if you want to resize partitions, do NOT, repeat NOT use Ubuntu or Linux utilities to resize Win7.  Doing so risks corrupting Win7 and rendering it unbootable.  Use the Win7 Disk Management utility to do the resizing.

Then, when you're done, boot into Win7 a couple of times to let it make filesystem adjustments.

THEN, you can boot into the Ubuntu CD and use GParted to resize the Ubuntu partitions.

---

### Post by bijupp on 2013-02-24
windows wallpaper black is normally a problem with the activation issues is your windows 7 is genuine (check it in right click on computer --> system properties) if found not genuine logo then reactivate it... otherwise u just need to restart it if the problem still persists..  

what about your ubuntu installation is it works fine...

---

### Post by Deliphin on 2013-02-24
> **Mark Phelps said:**
> And, if you want to resize partitions, do NOT, repeat NOT use Ubuntu or Linux utilities to resize Win7.  Doing so risks corrupting Win7 and rendering it unbootable.  Use the Win7 Disk Management utility to do the resizing.

Then, when you're done, boot into Win7 a couple of times to let it make filesystem adjustments.

THEN, you can boot into the Ubuntu CD and use GParted to resize the Ubuntu partitions.
I tried Win7 Disk Management, but I couldn't seem to find how to actually change the partitions. All I can figure out how to do is resize them.
EDIT: I might as well say this, to save you time, could you just link me a good tutorial?

---

