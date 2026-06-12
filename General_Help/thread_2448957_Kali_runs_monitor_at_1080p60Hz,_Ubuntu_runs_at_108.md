---
title: "Kali runs monitor at 1080p60Hz, Ubuntu runs at 1080p24Hz"
date: 2020-08-17
forum: General Help
---

### Post by dreamxr on 2020-08-17
I am using Ubuntu Budgie and I have used Ubuntu regular many times and for some really odd reason, Kali Linux is the only distro that I have found that can actually run my monitor at 1080p 60Hz. I have tried replacing the monitors.xml file to try and get it to change however I keep having to downscale my resolution to 1024x720 to get 60Hz refresh rate or suffer with 1080p24hz - 1024x720 is havoc when trying to use virtualbox or any other application because the "done" or "continue"  button is always off screen. 

Someone please help!

---

### Post by TheFu on 2020-08-17
Kali isn't a general purpose distro and should never be used as a standard desktop, unless you want to be completely pwn'd.

Anything happening inside a virtualbox VM is subject to the virtual HW settings for that VM.  Anything graphical, will be dependent on the "Guest Additions" being loaded.  Every time there is a new kernel or a new version of Vbox is upgraded/installed, the guest additions need to be re-linked with the kernel. In theory, DKMS should make that automatic.  It almost always works, unless it doesn't work.  

I saw yesterday, while helping someone else, that vbox has 3 methods to show the GUI of a guest VM.  The default mode is pretty bad.  Full-screen and "scaled" are better, but only if you also set the resolution using the GuestVM tools - Settings --> Display.  That's from memory of Ubuntu-Mate, which is what he just installed.  Don't know about Budgie, but basically, all the Ubuntu Desktop versions have a "control panel" with a "Display" applet. Look in there.

I don't use vbox anymore as a hypervisor, so cannot check settings. Sorry.

---

### Post by dreamxr on 2020-08-17
I don't even think you read my post. Virtualbox was an example of an application I could not use because of the resolution issue, that isn't the actual source or cause of the problem. The problem exists on my own actual Desktop environment on my SSD. As for kali being my desktop environment, I am aware of the implications hence why I don't actually use it very often. If this was going on inside a VM, why would I try and copy over a monitors.xml file?

Edit: I have checked every single nook and cranny for Display options that let me run 1080p60. None work. I tried xrandr, I tried Display in control panel and as mentioned, replacing monitors.xml. I even tried switching display manager/environment to lightdm on XFCE4 (what Kali uses), no results.

---

### Post by TheFu on 2020-08-17
Sorry that I wasn't able to understand your post. Good luck.

---

