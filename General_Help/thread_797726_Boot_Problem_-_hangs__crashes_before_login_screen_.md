---
title: "Boot Problem - hangs / crashes before login screen ( black screen )"
date: 2008-05-17
forum: General Help
---

### Post by jakeofspades on 2008-05-17
Hi - I've just migrated from SuSE to Ubuntu and have to say I think it's brilliant. I'm running Hardy Heron.

However I have one small issue - when I boot, about four times out of five the system will hang just before the login screen. The loading bar will 'fill up' in a healthy fashion but then the screen stays black.

In fact there is a little bit of screen flicker before the login screen:

Working: black - tints lighter - black - login screen
Not working: black - tints lighter - black - Nothing (no keyboard and mouse response, not even for ctr alt del)

I have a G35 intel graphics chipset so, as I understand, I shouldn't be having any graphics problems as it is supported well. 

* I am running a 32-bit Ubuntu installation on a 64-bit processor (hope that doesn't matter)

Any suggestions on how to further pinpoint the problem would be great.

---

### Post by pmelo86 on 2008-05-28
man, i'm having the same problem, i thought it was a problem with my fglrx driver, i've seen a lot of problems with suspend and resume with the fglrx driver, but now I discovered that it is with others drivers too, i don't know what makes the crash, if I find out i'll tell you :)

ps.: sorry my english mistakes.

---

### Post by VMC on 2008-05-28
Have you guys investigated the System Logs?
At the top "System > Administration > System log"

Look around there and see if anything that might indicate your errors.

---

### Post by bpl07 on 2008-05-29
I have this problem too on a dell inspiron 1501 running ubuntu 8.04, AMD64, generic kernel 2.6.24-17, with integrated ati xpress 1150 graphics.  I use the proprietary drivers installed by EnvyNG.  I actually have [another thread]("http://ubuntuforums.org/showthread.php?t=810064") where I described trying to fix various errors in my dmesg, primarily the iommu aperture one.  It apparently didn't work because the crash happened again this morning.

---

### Post by pmelo86 on 2008-05-31
hi again, i've found something that worked for me:

put in your xorg.conf these lines:

Section "DRI"
    Mode 0666
EndSection

and comment the DRI module load line, something like:

Section "Module"
#    Load   "dri"
     Load   "glx"
EndSection

i'm not sure, but i think there is a problem with some drivers and direct rendering. i hope it can help you.

---

### Post by jakeofspades on 2008-06-05
Well - this is a bit of an annoying problem because it basically stopped the day after I made the original thread post ie. Two weeks ago. But then it has suddenly started again, about one in three boots it does this. I have added that section to my xorg.conf file and I will see how that goes (I rebooted and nothing nasty happened so it's all good so far lol)

Cheers

---

### Post by bramnijhof on 2008-06-05
I have added the lines to the xorg file but the problem is not solved. Again I got a black screen between the splash en the login and the black screen freezes. Sometimes I can login and sometimes it hangs. 

Does anyone knows a solution?

---

### Post by bpl07 on 2008-06-17
So I've noticed this happens to me when the boot sequence does the forced disk check, which is about every 32 boots.  This explains the intermittency of the problem, but not why it's happening.

---

### Post by kolibri on 2008-07-10
I'm also having a black screen problem.

Upgraded to Hardy.  Dual monitors no longer worked,  screen resolution was set to lowest setting, NVIDIA console no longer worked.  Tried to reinstall NVIDIA drivers using this guide:  [https://help.ubuntu.com/community/NvidiaMultiMonitors](https://help.ubuntu.com/community/NvidiaMultiMonitors)  and the first troubleshooting step:  uninstall the restricted driver, reset xorg.conf and then reboot

After reboot:  get the HP splash screen, get to loading grub, get the Ubuntu screen and progress bar, then it goes black.  I can't get into the system at all, and I'm clueless as to what to try.  I guess try booting from a live CD?  

Why are video card issues with Ubuntu so hard to fix?

---

