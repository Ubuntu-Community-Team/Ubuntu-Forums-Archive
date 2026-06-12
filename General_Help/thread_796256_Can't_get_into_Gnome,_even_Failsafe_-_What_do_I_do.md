---
title: "Can't get into Gnome, even Failsafe - What do I do now?"
date: 2008-05-16
forum: General Help
---

### Post by OzzyFrank on 2008-05-16
I can't get past the Gnome splash after login, not even if I log into Failsafe Gnome. I have KDE installed as well, and that boots to the desktop fine, so it is definitely a Gnome problem. I deleted everything from ~/.gnome2/session, which has worked for me in the past, to no avail. What else can I try? Is there a log file I could post here to try and shed some light on this?

The only thing I did recently was install Virtualbox, and this situation began after rebooting. But since Virtualbox works fine in KDE, I can't say it is really an issue (but thought I better mention it). I even installed some Gnome updates while in KDE and still no change. So any ideas?

---

### Post by OzzyFrank on 2008-05-17
No clever people online now who can possibly help with this?

---

### Post by pietjanjaap on 2008-05-17
sudo aptitude install ubuntu-desktop
or
sudo apt-get -reinstall ubuntu-desktop

Or first remove and then reinstall.




Or see envy website, here you can remove video driver and reinstall the video driver in textmode.

---

### Post by Rinzwind on 2008-05-17
> **OzzyFrank said:**
> I can't get past the Gnome splash after login, not even if I log into Failsafe Gnome. I have KDE installed as well, and that boots to the desktop fine, so it is definitely a Gnome problem. I deleted everything from ~/.gnome2/session, which has worked for me in the past, to no avail. What else can I try? Is there a log file I could post here to try and shed some light on this?

The only thing I did recently was install Virtualbox, and this situation began after rebooting. But since Virtualbox works fine in KDE, I can't say it is really an issue (but thought I better mention it). I even installed some Gnome updates while in KDE and still no change. So any ideas?

Check the errors file in your home dir.

more .xsession-errors

If there's an error in it relating to this post it here or try to google it ;)

It might also be a corrupted
 .Xauthority
I THINK you can delete this file. Mind you: THINK. 
This files has to do with ssecurity and X.
But you might wait for someone with more knowledge than me :)

---

### Post by OzzyFrank on 2008-05-17
OK, didn't think I needed to reinstall **ubuntu-desktop**, and sure enough I get this when I try:

[COLOR="Blue"]No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.[/COLOR]

If others agree removing this and then reinstalling it will make a difference, please let me know, and I will try it. Otherwise, I'd rather not touch something that appears to be fine.

As for Envy and the nVidia drivers, all that was working fine, and I am loathe to touch it since I had such a pain trying to get it all going again after Hardy upgrade (which left me with an almost-unusable display of 640x480). I will leave this as a last resort, especially since my display is perfectly fine in KDE (when I've had actual display/driver problems before, it has affected both the Gnome and KDE desktops).

Any other suggestions guys? Something at startup is obviously halting Gnome, and I have emptied the **session** file, so where else can I look?

---

### Post by OzzyFrank on 2008-05-17
Tried that command, and here is the output (note I am in KDE as I can't get into Gnome, so hopefully that doesn't matter):

**:~$ more .xsession-errors**
[COLOR="Indigo"]/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_AU.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinp
ut.d/default.
startkde: Starting up...
startkde: kpersonalizer not found! Please install to properly configure your u
ser.
kbuildsycoca running...
DCOP Cleaning up dead connections.
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be prel
oaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloa
ded: ignored.
Ignored duplicate item: Printing
Ignored duplicate item: Konqueror
Ignored duplicate item: Firestarter
Ignored duplicate item: Kontact
Ignored duplicate item: Gnumeric Spreadsheet
Ignored duplicate item: Firestarter
Ignored duplicate item: Software Sources
Ignored duplicate item: Printing
Ignored duplicate item: Partition Editor
Ignored duplicate item: NVIDIA X Server Settings
--More--(1%)
[/COLOR]
Does any of this make sense, or rather point to the error and its fix? Or should I be running this command from a command prompt outside of Gnome and KDE?

---

### Post by OzzyFrank on 2008-05-17
OK, so "More" means I have to hit the Enter key to keep the list coming. Since that will be pretty long, I will just post any items with errors:

[COLOR="Indigo"]ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.[/COLOR]
(these 2 repeat a couple more times later)
[COLOR="#4b0082"]Could not find 'restricted-manager-kde' executable.[/COLOR]
[COLOR="#4b0082"]WARNING: modinfo for module nvidia failed: modinfo: could not find module nvidia
WARNING: modinfo for module nvidia_legacy failed: modinfo: could not find module nvidia_legacy
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
libpng warning: Ignoring gAMA chunk with gamma=0
libpng warning: Invalid cHRM white point
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x1c053b6
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x1c053b6
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  12
  Minor opcode:  0
  Resource id:  0x4600005
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  12
  Minor opcode:  0
  Resource id:  0x4600005
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x36060bb
  Resource id:  0x1c053b6
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x1c053b6
[/COLOR]
What next?

---

### Post by Xiong Chiamiov on 2008-05-17
With problems like this, I always start by renaming my (well, usually KDE) folder:
```

mv ~/.gnome2 ~/.gnome2_old

```
When you log in to GNOME without .gnome2 existing, it will regenerate a new one.  If that works, it's something in your config, and you can slowly narrow down (by copying files and folders from the old folder to the new one) what's causing the problem.

---

### Post by OzzyFrank on 2008-05-17
Unfortunately, that has no effect. Good tip to hang onto though, so thanks.

Next!!

---

### Post by OzzyFrank on 2008-05-18
More info: I installed Xfce the other day, but hadn't bothered to log into it till now. It doesn't get to the desktop either (it doesn't even get to the splash). I assume now it has something to do with GTK, which (as far as I know) Xfce uses as well as Gnome. I originally thought it was a Gnome problem because KDE isn't affected, but now I'd be surprised if it wasn't specifically GTK that's messed up. You guys out there with lots more knowledge about GTK can correct me if I am wrong in that assumption, or advise me on the next step if you think that makes sense.

---

### Post by HandyAndy on 2008-05-19
I've got a similar problem.

I did a clean install of 8.04 and had everything working fine. Then I installed Fluxbox and spent most of my time in that, rather than Gnome. Gnome was still working ok, though, because I dropped back into it now and again to do some things that were easier or I didn't know how to do in Fluxbox. So I know that installing Fluxbox didn't cause the problem.

Then, after about a week of using Fluxbox continually, I tried to get into Gnome and couldn't. After I enter my username and password the login dialogue disappears, but then nothing for about 10 seconds, just the default brown background. Then I get a white rectangle in the top lefthand corner of the screen. Then nothing - it just sits like that.

It's probably something I did while I was in Fluxbox, but I don't know what.

I had hoped that all those Gnome and GDM updates recently might correct whatever it is I've screwed up, but no joy.

I tried zapping ~/.gnome2 as suggested in a previous post, but that didn't make any difference.

In a similar thread I saw **sudo apt-get install gnome** suggested. I'll try that if I'm assured it won't mess with my Fluxbox, which I've spent a lot of time on and I love. I'd rather live without Gnome until my next clean install than risk that.

Any advice?

Any ideas?

---

### Post by OzzyFrank on 2008-05-30
Weird. When I first deleted (or renamed, actually) **.gconf, .gconfd and .gnome2**, it did absolutely nothing, And yes, did reboot a few times in case a simple log-out-log-in wasn't enough. Then after a few days' "rest" while editing vids in Windows it decides to boot up fine! Minus my old Gnome settings, like the panel, etc.

Ever since first starting to get into PCs since the early 90s, I have come across cases (usually in Windows of course) where NOTHING would work to fix a particular problem... but give it a day or two rest, all is fine! God, you have no idea how badly that has messed with my logic-based, causality-believing brain, hehe! "It does not compute, Will Robinson!" comes to mind. Now Ubuntu has done it to me, hehe.

Now I just need to find out if there are things I can restore from previous settings, like the top panel etc. So, can I?

---

### Post by HandyAndy on 2008-06-05
I've been reading in other threads about people having similar problems getting into Gnome, with no obvious cause.
So maybe it wasn't anything I did while I was in Fluxbox.

Nevertheless, the problem remains (see my post above). The recent new kernel and stack of other updates haven't cured it.

Any (safe) suggestions?

---

### Post by OzzyFrank on 2008-06-05
Did you try deleting or renaming all 3 folders mentioned above? It's "safe", though you will lose a few little settings, and your panel launchers. Some tips involve renaming/deleting other folders like **.gnome2_private**, but I found it wasn't necessary.

---

### Post by OzzyFrank on 2008-06-05
And yes, I doubt mucking in Fluxbox did anything to Gnome. I installed Virtualbox, but doubt that killed Gnome, especially since in KDE it worked fine. And works fine in Gnome, now that I can get into it. And one would hope updates would fix things, which they often can, but waiting for Gnome to fix itself wasn't getting anywhere in my case.

---

### Post by HandyAndy on 2008-06-06
Thanks, Ozzy - it worked!

I had tried renaming just **.gnome2** before, but to no effect. But I hadn't tried doing the same with **.gconf** and **.gconfd**.

I have now and I'm back in Gnome.

That's great - I'll remember that :)

---

