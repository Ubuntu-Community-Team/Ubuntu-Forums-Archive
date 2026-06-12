---
title: "FreeCAD window resizes causes freeze/crash"
date: 2015-05-27
forum: General Help
---

### Post by NertSkull on 2015-05-27
I installed the ppa for the most recent freeCad version (0.15).  I'm running Kubuntu 12.04.

It installs and opens fine.  But if I try to resize the freecad program window, it freezes and crashes.

I've turned off desktop effects, still the same issue.

I've gone back to the 0.12 version and it works fine for now.

Is there any way to get the newer version to work?

Is there anyway to troubleshoot this more to get better information on why its crashing.

---

### Post by DuckHook on 2015-05-27
A good habit for chasing down crashes of any kind is to look in your logs, especially syslog, kern and apport.

I don't use FreeCAD myself (LibreCAD here), so you are being led by the blind, but even for another more knowledgeable forum member to help, please post:

HW specs, especially graphics card (give details like chipset, vram, etc)
Driver (are you using proprietary or community?)
Have you tried it in 14.04?
And, of course, anything unusual in aforesaid logs.

**ADDENDUM**

Also try invoking FreeCAD from command line in a terminal rather than through the dash. Errors might show up in terminal that are just funnelled off to null in a graphical invocation.

Also, what do you mean by freeze and crash? The app only or the whole window environment? Is X still responsive (can you kill X)? Or does the freeze extend to the kernel (Cannot even <Ctrl>+<Alt>+<Fn> or ssh in)?

---

### Post by NertSkull on 2015-05-27
My hardware is Nvidia card in a desktop. GTX 460, 16Mb Ram.

I tried running FreeCAD from the command line, while having tail -f going on syslog, apport and Xorg.0.log and kdm.log.

None of the logs, nor the command prompt show up with any sort of error or message when I resize the window causing the program to crash.  

The crash is the program window only. X server is fine, I don't have to restart the computer. I just click the X, wait a few seconds and then click the 'terminate' button when the non-responding app message box comes up.

The program appears to be working fine before window resize, but I can't be 100% sure because the window is so small I can't really see or do much.  But once I resize the window, it freezes up and all the buttons in the app become unresponsive.

On the bright side, I've discovered that if I close the 'start page' tab that is open on program start, I can then resize, and things seem to work fine.  So its just something with the 'start page' that is causing it to crash.  Once I X that out, I can resize the program.

I'm happy to help someone troubleshoot that more. I'm happy that it works for me for now. Hopefully that can help someone else.

---

### Post by DuckHook on 2015-05-27
Good to know that you solved it on your own, or almost, at least. You do not mention what driver you are using. You may wish to try a different one if it is important to get that last little bit of functionality, but it may be wiser to leave well enough alone and just work around the small irritation of the initial splash screen rather than risk destabilizing your whole system with a new driver.

As a passing note, I doubt that you only have 16MB of VRAM, as your card is quite decent and relatively new. At any rate, it is unlikely to be the source of the issue. It is more likely either the oldish kernel (12.04 is ages ago in computer years) or the driver.

If not yet done, please mark thread "solved" so that your workaround gets noticed by those looking for a similar solution.

Good Luck and Happy Kubuntuing.

---

### Post by Gemnoc on 2015-06-01
I recommend posting your problem on the FreeCAD forum. That's where you'll get the most relevant help.

---

