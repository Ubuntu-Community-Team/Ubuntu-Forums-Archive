---
title: "Tried to Uninstall Current Kernel in Package Manager"
date: 2007-04-11
forum: General Help
---

### Post by odelay on 2007-04-11
I just started a fresh install of Kubuntu and ran the Update Manager.  Since I'm kind of crunched for time now, I was trying to get as many steps done in one restart as possible to speed things up.  The updater installed the newest linux kernel (ending in ".11").  Since I didn't want to restart, and then have to uninstall the ".10" kernel image, I tried uninstalling it before the restart.

This stalled Adept because it prompts you in terminal (which I wasn't using) if you actually want to do something this stupid.  I only saw this by clicking the "Details" button in Adept.  Of course, because it's Adept, there isn't a way to click either the "cancel" or "proceed" button, so I had to force quit.

When I restarted, both .10 and .11 showed up in GRUB, so I selected .11.  It went through 99% of the loading bar and then stalls indefinitely.  Same thing happens with .10.  So I rebooted into recovery mode and entered the correct dpkg command to release the package manager.  Now I'm able to use apt-get, but I still can't actually get past the boot screen.

What should I do?  I'm not sure if I should try to boot in to .10 recovery and reinstall .11 or boot into .11 and remove .10.  I'm also not positive what the actual command (with the proper package name is).  Any ideas?

Thanks a ton.

[COLOR="Red"]Update: Problem Solved[/COLOR]
I was way off on this one.  While the whole kernel situation did get screwed up, it wasn't causing Kubuntu not to start.  The culprit was my xorg.conf file.

To fix the common KDESU bug, I commented out all the lines containing wacom.  It turns out I missed the last 3 important lines (because the post I read forgot to mention them).  This is what you need to comment out:

#Section “InputDevice”
# Driver “wacom”
# Identifier “eraser”
# Option “Device” “/dev/wacom” # Change to
# /dev/input/event
# for USB
# Option “Type” “eraser”
# Option “ForceDevice” “ISDV43 # Tablet PC ONLY
#EndSection

#Section “InputDevice”
# Driver “wacom”
# Identifier “cursor”
# Option “Device” “/dev/wacom” # Change to
# /dev/input/event
# Option “ForceDevice” “ISDV43 # Tablet PC ONLY
#EndSection

#Section “InputDevice”
# Driver “wacom”
# Identifier “cursor”
# Option “Device” “/dev/wacom” # Change to
# /dev/input/event
# for USB
# Option “Type” “cursor”
# Option “ForceDevice” “ISDV43 # Tablet PC ONLY
#EndSection

And finally, the 3 lines I forgot to comment out:

Section “ServerLayout”
Identifier “Default Layout”
Screen “Default Screen”
InputDevice “Generic Keyboard”
InputDevice “Configured Mouse”
# InputDevice “stylus” “SendCoreEvents”
# InputDevice “cursor” “SendCoreEvents”
# InputDevice “eraser” “SendCoreEvents”
InputDevice “Synaptics Touchpad”
EndSection

Once again...only comment the 3 lines *as shown* (not the whole thing).

---

### Post by zvacet on 2007-04-11
Try to reinstall newer version of kernel.After you do that go to the Adept and find linux image(older version)and mark it for complete removal.After that you will have only last version of kernel.

---

### Post by odelay on 2007-04-11
> **zvacet said:**
> Try to reinstall newer version of kernel.After you do that go to the Adept and find linux image(older version)and mark it for complete removal.After that you will have only last version of kernel.

I typed in apt-get upgrade and it found one package listed as "not completely removed or installed."  After executing the command, I thought it would take care of everything, but it didn't.

Do you know the actual name of the kernel package to install/remove?  I don't want to uninstall the wrong thing.

Thanks

---

### Post by odelay on 2007-04-11
I managed to uninstall 2.6.17-10-generic, but I saw a line about a broken link and how I should fix it with lilo.  I still had the same problem...so I decided it's quicker (and probably will cause fewer problems in the long run) to just reinstall.  After all I just started installing, so no big loss.

However...I am getting really sick of not being able to cancel out of a prompt in Adept.  Tons of people got screwed over when they tried to install the Java Runtime Environment in Adept (which asks for a confirmation).  I feel like there's no reason to not fix this...it's caused thousands of people hours of aggravation, and undermines the idea that all the packages in Adept won't cause any problems.

I realize this is a special case, and I shouldn't have tried to remove the old kernel before restarting...but this all could have been avoided if I was able the select the "cancel" prompt.

Thanks for the help though.

---

