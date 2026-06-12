---
title: "Xorg pinning the CPU kdm/gdm hanging"
date: 2007-10-30
forum: General Help
---

### Post by worldDownInFire on 2007-10-30
I have a PC running Kubuntu Fesity which acts as a media PC in the living room.  The other day while watching a movie VLC's video playback froze, but the audio continued.  Neither the mouse nor the keyboard worked to exit VLC and the machine was hard rebooted.  When the computer rebooted the Kubuntu login screen came up but looked odd.  The background was all black and there were two boxes (username/password) in the middle of the screen.  The mouse cursor could be moved around but clicking in the text boxes didn't give a blinking cursor and typing the password and pressing enter did not login.  I poked through my xorg.conf, but nothing appears to have changed.  /var/log/Xorg.0.log does not show any errors either.  I SSHed into the machine and used apt to remove/reinstall kde and kubuntu-desktop to no avail.  Tonight I installed ubuntu-desktop and set gdm as the default window manager.  The computer boots, brings up the ubuntu login screen, and I'm able to interact with that and login.  However, once the desktop loads, after using the system for a few minutes, it becomes unresponsive.  The SSH shell session still works and I can see in top that Xorg is utilizing 99.9% CPU.  Killing the Xorg PID results in the display shutting down and X firing back up.  Trying to log into GNOME at that point usually results in the system freezing during the GNOME startup (usually by the appearance of the 3rd icon in the little progress box) and the machine needs to be rebooted to make it functional again.  As far as I can tell, I haven't changed anything and I'm at a total loss to figure out what to do.  I've tried hunting around various forums using Google, but I don't seem to have any good search keywords to use.

Any ideas?

---

### Post by nowshining on 2007-10-31
in gnome try sudo killall nautilus

:) see if that helps..

---

### Post by worldDownInFire on 2007-10-31
I will give that a try when I get home tonight, but from what I'm seeing the problem is essentially Xorg is running out of control (utilizing almost all of the CPU) and kdm/gdm are suffereing as a result.  I'm much more familiar with KDE then GNOME, but isn't Nautilus just a file browser, somewhat analogous to Konqueror in KDE, and neither of them has the more fundamental under pinnings as say Explorer on a Windows system?

---

### Post by nowshining on 2007-11-02
n/m i was thinking u had Gutsy for some odd reason.. :/ ugh! i misread --- so i'll just bumpy ur thread and have u installed all the updates?

---

### Post by worldDownInFire on 2007-11-02
If I'm not completely up to date, I'm close.  What's weird is that this happened without (as far as I can tell) any configuration changes being made.

---

