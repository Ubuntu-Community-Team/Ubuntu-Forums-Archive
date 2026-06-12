---
title: "Screen Resolution"
date: 2007-08-29
forum: General Help
---

### Post by dwilliams07 on 2007-08-29
Hello,

I successfully installed Ubuntu 7.04 on my Dell Optiplex GX520.  My screen resolution defaulted to 1024*768 and everything appeared to be fine.  The system then notified me that there were updates which I downloaded and installed.  After rebooting the system my screen resolution now defaults to 640*480 which is the only option in my list of resolutions to choose from.  I could not figure out how to restore my machine prior to installing the updates.  Please help.  I have reloaded Ubuntu twice (to make sure that I was not going crazy) with the same results.

---

### Post by tszanon on 2007-08-29
> **dwilliams07 said:**
> Hello,

I successfully installed Ubuntu 7.04 on my Dell Optiplex GX520.  My screen resolution defaulted to 1024*768 and everything appeared to be fine.  The system then notified me that there were updates which I downloaded and installed.  After rebooting the system my screen resolution now defaults to 640*480 which is the only option in my list of resolutions to choose from.  I could not figure out how to restore my machine prior to installing the updates.  Please help.  I have reloaded Ubuntu twice (to make sure that I was not going crazy) with the same results.
1. Backup /etc/X11/xorg.conf:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
2. Edit the file. Press ALT + F2 and type:
```
gksudo gedit /etc/X11/xorg.conf
```
3. Find a section like this:
```
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24   
    Option         "AddARGBGLXVisuals" "True"
    Option         "TwinView" "1"  
    Option         "metamodes" "CRT: 1440x900 +0+0, TV: 800x600 +1440+0; CRT: 1024x768 +0+0; CRT: 832x624 +0+0; CRT: 800x600 +0+0; CRT: 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        **Modes      "1024x768" "800x600" "640x480"**
    EndSubSection
EndSection
```
4. Edit the line named "Modes", including the desired resolution at the beginning:
```
Modes      **"1152x864" **"1024x768" "800x600" "640x480"
```
5. Save. Restart the X server pressing CTRL + ALT + Backspace.

That should solve the problem.

---

### Post by dwilliams07 on 2007-08-29
It sure did.  Thank you very much!

---

### Post by tszanon on 2007-08-29
> **dwilliams07 said:**
> It sure did.  Thank you very much!
You're welcome. Good to know your problem is solved. :)

---

