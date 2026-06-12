---
title: "panels..."
date: 2006-10-10
forum: General Help
---

### Post by qiemem on 2006-10-10
My panels got all screwed up... anyone know a way to restore the default panel set up? (I'm using the edgy beta)

---

### Post by srt4play on 2006-10-10
How are they screwed up? Could you post a screenshot? I think a quick and dirty way would be to delete the '.gnome2' folder in your home directory and log out and back in, which would set GNOME to defaults. But hesitate before doing that since it will affect more than panels.

---

### Post by qiemem on 2006-10-10
Oh, actually they got all fixed up with a restart (which was kinda weird). I had a bottom custom panel showing up (I've removed the orginal bottom panel to create a dock like thing), but the top bar wasn't showing up at all (which I'd also customized, putting the window selector and the like up there). Still, I was curious about a way to reset it to default. I guess I'm also curious if there is a way to save certain set ups so one might try out different layouts (via backing up text files and the like). Thanks though!

---

### Post by komputes on 2007-12-13
I would like to share this, since I had the same frustrating issue with panels. They are way too easy to remove and change since they can't be locked. This command + rebooting will bring back the default panels. 

You will first need to get a terminal up. Since you don't have a menu bar/panel, that is quite tricky, but there is a keyboard shortcut for this:

Alt+F2 (This is equivalent to a run command)

from here you have a choice of which terminal you want to use, the default is **gnome-terminal** (which is a bash terminal) or you can also use **xterm** as well.

Once you have a terminal window open it is pretty simple to restore the default panels (as they were when you first installed Ubuntu). In the terminal type:

```
sudo debconf gnome-panel
```

Close the terminal, reboot, et voila!

:popcorn:

---

### Post by magnat2 on 2008-01-21
I have a problem with the notification area in gnome panels, some icons i cant open or close them, like they werent there, like the network icon or the sound icon sometimes, ive formated the computer but the problem still comes again, sometimes it is solved with control-alt-backspace and restart X but another times it just stays the same... Can you help me? My laptop is an Acer 5720 and my distro Ubuntu 7.10...
Thank you!

---

