---
title: "Beryl and screensaver"
date: 2006-12-28
forum: General Help
---

### Post by PatsM on 2006-12-28
Since i'm running Beryl i seem to have lost the screensaver. It is enabled but at time-out the screen just turns black. Any ideas anybody?

---

### Post by SingLee on 2007-01-05
I have the same problem. Are you using Dapper or Breezy?

---

### Post by vaskark on 2007-01-05
Same prob here. I also noticed that VLC turns black too. Very annoying.

---

### Post by Waappu on 2007-01-05
Hi

If you have ATI video card try this
```
gstreamer-properties
```
Go to video tab and select to output: X Window System (No XV)

---

### Post by vaskark on 2007-01-05
Nope. Didn't work :(

---

### Post by Waappu on 2007-01-05
Hi

It seem I having also problems... =)
Screensaver works but if I try to go change it X crash

---

### Post by Waappu on 2007-01-07
Hi

My Screensaver problems seems to related to some how to gnome-power-management.
When I disable ACPID and APMD services I can change screensaver. Try if it works for you problem also. First you can try
```
killall gnome-power-manager
```

---

### Post by mrdeeno on 2007-01-21
don't know if you figured out your problem yet, but I had the same problem but was able to figure it out.

I am running Beryl on Edgy on a Vaio laptop with ATI mobility 9000 r250.

Screensaver was working fine shortly after I installed and set up my Beryl settings.  But after "playing" with some of the settings, my screensaver would just go black.  It came out of screensaver mode fine, but it didn't display anything.

I went through and checked/unchecked some of the settings in Beryl that wasn't exactly clear to me what their functions were.  

The one that did it for me is in the Beryl settings > General Options > Choices tab

I had "Unredirect fullscreen windows" checked (default is unchecked) and wasn't sure what it did, but after returning it to default (unchecked), my screensavers work fine.

---

### Post by AkiraXXX on 2007-02-02
The entire Beryl/Nvidia/Wallpaper/Screensaver issue is a vast mess that I hope is resolved soon.  Beryl is a wonderful application and it bothers me that I only seem to be able to use it to a small fraction of its capabilities.  I've had some minor success with these issues.  I have two units on which I use it: one is a laptop and one is a desktop.  The laptop runs an integrated Intel video chipset and I have no trouble at all with Beryl.  I can run it with all capabilites (that I have tried, at least) and need no special configurations or workarounds. But, with my desktop (which runs an old Nvidia card) I have had issues like black screens when running an app at full-screen, black screen when running a screensaver, black wallpaper, etc. Here is what I've done:

I disabled the gnome-screensaver and replaced it with xscreensaver.  I used  [[COLOR="DarkOrchid"]these instructions[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=195557&highlight=screensaver") for that.

After that I made sure that had the following two lines in my Session startup (System, Preferences, Sessions, Startup Programs):

beryl --use-copy
beryl-manager

Then, I went into Beryl Settings Manager and rechecked the "Unredirect Fullscreen Windows".  I had it unchecked when trying to get the gnome-screensaver to work.  It may work without it, but I've not tried it out.

After that it seems to work.  I still have issues if I switch from Beryl to Metacity and back again.  I try not to touch anything.  :) I don't run with a lot of windows open at one time, so that helps.  In all, it is functional, but I hope the Nvidia driver is fixed soon so I can just run normally.  And, I miss my "Busy Spheres" screensaver in gnome.  I imported it into xscreensaver, but it doesn't run at full speed. :(

Hope this works out for someone.  If anyone else finds another/better workaround, let us know.

---

