---
title: "HP specter x360 Palm Rejection"
date: 2015-07-13
forum: General Help
---

### Post by mlsbeta on 2015-07-13
Hi,

I am running Ubuntu 14.04 on the HP specter x360, which has a huge touchpad. Its so huge that while typing my hand covers about a third of the surface, causing the cursor to jump all over the place. I have tried to enable palm detection with synclient like this ([http://ubuntuforums.org/showthread.php?t=2212010&highlight=touchpad+palm+detection](http://ubuntuforums.org/showthread.php?t=2212010&highlight=touchpad+palm+detection)) post suggests, but no combination of the parameters makes the slightest difference. What more can I do? I know proper palm detection is possible because it works fine in windows.

Thanks.

---

### Post by Geoffrey_Arndt on 2015-07-14
Many laptops have a key combination (like Fn+F1 (System 76) or Fn+F7 (Acer) that "turns-off" the touchpad, then doing the key combo again toggles it back on.   Have you checked the users manual (or just scanned the keyboard) for info on that?   There may also be 3rd party apps that do the same (did you research/google?).

PS:  Correction:   pls check post #9 in this thread for a possible command line fix:  [http://ubuntuforums.org/showthread.php?t=2192864](http://ubuntuforums.org/showthread.php?t=2192864)

---

### Post by mlsbeta on 2015-07-14
I already have a key combination that disables the touchpad. That is how I am currently avoiding moving the cursor while typeing. The solution is annoying though. What I want is a driver that will automatically reject input from the touchpad if it detects a palm rather than a finger is in contact with it. I know this is possible because the windows drivers already do this

---

### Post by Geoffrey_Arndt on 2015-07-14
Hmm interesting.   Talk about "esoteric" software.   

How confident are you that you entered the commands correctly?   I wonder if the "one-time"  command shown in your link needs to be preceded with sudo (seems it would but I'm not sure).   IF results are positive, it seems worth doing the script so a restart won't revert back to original settings.  Adding the script seems to have made a big difference to the OP (original poster) in the linked thread.

---

### Post by Geoffrey_Arndt on 2015-07-14
OK, here is something worth trying, especially if one is not used to working in a linux terminal (CLI) interface.

It seems there is an app in the USC (Ubuntu Software Center) to handle palm detection and disable while typing . . . 

The app is "Pointing devices" . . just search for it and try installing it.   The developers web site shows more info and it seems at least the program is designed to do what you are requesting.   Let us know if it works (and mark thread as solved) in case other users with similar laptops run into the same issue.   Thanks.

---

### Post by mlsbeta on 2015-07-14
I executed the synclient commands as sudo and as a normal user. I did to same with the gui you suggested. Neither of which changed the behavior of the trackpad. Using both synclient and the gui I was able to edit other settings such as enable/disable trackpad and pointer speed. It is only the palm detection setting that does not change behavior. I tried enableing it with many different combinations of range and pressure values to no avail.

 I suspect the problem lies at the driver level. Is there any way to view debug output from the trouchpad driver?

---

### Post by Geoffrey_Arndt on 2015-07-15
At this point, it may be worth building the app from source.  See GitHub for source files and instructions . . I'm not familiar with debug location for this, but perhaps a new thread just dealing with compiling the source for just your machine will help attract some more experienced users than I.

[http://osdn.jp/projects/gsynaptics/downloads/45812/gpointing-device-settings-1.5.1.tar.gz/](http://osdn.jp/projects/gsynaptics/downloads/45812/gpointing-device-settings-1.5.1.tar.gz/)

[URL="http://osdn.jp/projects/gsynaptics/downloads/45812/gpointing-device-settings-1.5.1.tar.gz/"]

[/URL]

---

