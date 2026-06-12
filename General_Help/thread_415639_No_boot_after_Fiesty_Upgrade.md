---
title: "No boot after Fiesty Upgrade"
date: 2007-04-20
forum: General Help
---

### Post by Tenicus on 2007-04-20
Just upgraded from Edgy yesterday via the alternate CD yesterday
First part went fine, then I got the notice saying "to finish upgrade restart computer"
Well I restarted but it wont boot
The logo comes up, the status bar completes, then this shows up:
>  init:/etc/event.d/logd:11: Unknown stanza
 init:/etc/event.d/tty1:13: Unknown stanza
 init:/etc/event.d/tty2:13: Unknown stanza
 init:/etc/event.d/tty3:13: Unknown stanza
 init:/etc/event.d/tty4:13: Unknown stanza
 init:/etc/event.d/tty5:13: Unknown stanza
 init:/etc/event.d/tty6:13: Unknown stanza
*Activating swap.... [OK]
*Checking root file system  [OK]
*Checking file systems... fsck 1.4-WIP    [OK]

I switched to tty1 and it says:
> 
Starting up.....
Loading, please wait...
kinit: trying to resume from /dev/disk/(bunch of characters)
kinit: No resume image, doing normal boot....

Been like that for several hours
Tried 3 different kernals I have on the HD
Tried recovery modes, didnt work
Tried recovery mode from the CD, I was able to get a shell

Whats going on?

---

### Post by shironeko on 2007-04-20
> **Tenicus said:**
> Just upgraded from Edgy yesterday via the alternate CD yesterday
First part went fine, then I got the notice saying "to finish upgrade restart computer"
Well I restarted but it wont boot
The logo comes up, the status bar completes, then this shows up:

I switched to tty1 and it says:

Been like that for several hours
Tried 3 different kernals I have on the HD
Tried recovery modes, didnt work
Tried recovery mode from the CD, I was able to get a shell

Whats going on?

I've got problems too.
I can't manage to load gnome. And got many hardware problems with my laptop.

Actualized via internet.

---

### Post by Tenicus on 2007-04-20
I actually just booted into XP

---

### Post by stooka on 2007-04-21
Count me in too.  my upgrade from 6.10 worked fine when I logged into KDE.  When I tried to log into an xgl session (so I could run Beryl as I have been doing for months), the display was garbled.  Booted back into KDE to check out my ATI driver status (FGLRX), and noticed that it wasn't configured correctly anymore.  I followed the instructions here [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#C](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#C) in an attempt to fix it and now I get this message about kinit not finding a resume image.  I can login to the command line but i can't figure out what to do from here.  When I try to start kde i get the message that DISPLAY is not detected (sorry I can't remember the exact message right now, I'm on another machine).  The only thing I know how to do to fix this is to re-install 7.04 over the whole thing, but I really don't want to.  Any ideas?  Thank You!

---

