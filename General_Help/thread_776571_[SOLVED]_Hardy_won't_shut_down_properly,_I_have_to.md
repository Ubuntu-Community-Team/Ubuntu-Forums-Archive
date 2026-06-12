---
title: "[SOLVED] Hardy won't shut down properly, I have to kill X before it will turn off"
date: 2008-04-30
forum: General Help
---

### Post by rainwalker on 2008-04-30
Hardy always hangs when I try to shut down, either pressing my laptop's power button or going to System > Quit and choosing "Shut Down". The panels, windows, Compiz, etc will all disappear, but my wallpaper will still show, and it won't shut down unless I kill X with Ctrl + Alt + Backspace. ```
sudo shutdown -h now
``` works, though.
How can I check what errors go on when shutting down?

Just FYI, I haven't tried restarting/suspending/hibernating yet to see if this happens with those.

---

### Post by garyedwardjohnston on 2008-04-30
hmmm

---

### Post by rainwalker on 2008-04-30
> **garyedwardjohnston said:**
> hmmm

Erm...no offense, but that was no help at all

---

### Post by buradleix on 2008-04-30
I'm having a similar (if not the same) issue.

When I hit the power button, I don't get the usual confirmation for shutdown, restart, etc. Everything freezes and in at least one case, I wasn't even able to go to text mode (cntrl+alt+F5).

I had installed from scratch, and until seeing this post, I was planning on starting over (thinking something may have gone wrong during the first installation.) Anyone have any ideas? I don't know where to begin looking.

---

### Post by warp99 on 2008-04-30
> **rainwalker said:**
> Hardy always hangs when I try to shut down, either pressing my laptop's power button or going to System > Quit and choosing "Shut Down". The panels, windows, Compiz, etc will all disappear, but my wallpaper will still show, and it won't shut down unless I kill X with Ctrl + Alt + Backspace. ```
sudo shutdown -h now
``` works, though.
How can I check what errors go on when shutting down?

Just FYI, I haven't tried restarting/suspending/hibernating yet to see if this happens with those.
Check you ~/.xsession-errors log to see if something is hanging the system as you shutdown. To make it easier delete the file first, then crtl+alt+backspace and login again to generate a new file. Attempt to shutdown and that way anything hanging and not unloading will be easy to spot in the log file.

---

### Post by rainwalker on 2008-04-30
> **warp99 said:**
> Check you ~/.xsession-errors log to see if something is hanging the system as you shutdown. To make it easier delete the file first, then crtl+alt+backspace and login again to generate a new file. Attempt to shutdown and that way anything hanging and not unloading will be easy to spot in the log file.

Here's what it says:
> 

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
SESSION_MANAGER=local/riley-laptop:/tmp/.ICE-unix/5553
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
Shutdown failed or nothing to shut down.
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192
Checking for Xgl: not present. 
Found laptop using ati driver. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1920x1200) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
11
seahorse nautilus module initialized
evolution-alarm-notify-Message: Setting timeout for 78951 1209686400 1209607449
evolution-alarm-notify-Message:  Thu May  1 19:00:00 2008

evolution-alarm-notify-Message:  Wed Apr 30 21:04:09 2008

The middle part is the "SKIP_CHECKS=yes compiz" command I added to the startup stuff, just FYI.

---

### Post by xyverz on 2008-05-02
This happens to me when I'm *not* running X.  Just doing 'sudo reboot' ends with the message [rebooting system] and it freezes right there.  The only thing that works is 'sudo shutdown -h now'

So it'll turn off, but it won't reboot.

---

### Post by mridkash on 2008-05-02
When I press the shutdown button, the screen goes blank with cursor blinking, and when I press ctrl-alt-f7 it says, shutting down gdm, which takes over 2 minutes! I had installed the RC version of Ubuntu Hardy

---

### Post by aebenmx on 2008-09-04
I'm having exactly the same problem as rainwalker. After pressing the shutdown button, the wallpaper stays on screen. I have to press ctrl+alt+backspace before my system shuts down. I have tried booting the latest and the older kernel, but it makes no difference. A minute ago I disabled compiz and it solved the problem, but I'm not sure it always works.

Any idea?

---

### Post by Peter09 on 2008-09-04
And Me, and also a friend who I support. Had this issue for over a month. I have been waiting for a resolution, I think (hope) its an identified bug.

---

### Post by trappleye on 2008-09-04
My system is doing the same thing. I haven't tried disabling compiz, but I'll give that a try.

---

### Post by rainwalker on 2008-09-04
Ack! I forgot I still had this thread going...
I found out what was causing the problem for me: KeyTouch
If you use it, check out [https://bugs.launchpad.net/ubuntu/+bug/186713](https://bugs.launchpad.net/ubuntu/+bug/186713)

---

