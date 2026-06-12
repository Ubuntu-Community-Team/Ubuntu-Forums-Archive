---
title: "screensavers work once or so,  then only blank"
date: 2006-11-07
forum: General Help
---

### Post by brian g on 2006-11-07
yeah i know screen savers are fairly trivial.


upon booting and gnome starting my screensaver works. it' GLidescope and it runs and tests fine as do all my gl screensavers (i guess my driver is working right, since i see the nvidia logo when i boot my computer and followed the directions in the wiki [BinaryDriverHowto/Nvidia]

then later in the day or after sleeping and waking up the next day the screensaver no longer seems to appear. it just goes right to a blank screen, (not the sleep screen, it goes to that eventually) they test fine in the preview box and such, but no matter what saver it's set to when they turn on after the set time they are just blank. this is no fun. 

i thought that there was something wrong with my video driver, but i don't think it is because the previews work fine and it works on occasion.i tried a non gl screensaver to make sure it wasn't my video driver. blank screen as well.

i have a geforce 3
generic kernal
nvidia video driver from the repository (have also tried legacy drivers)
added ```
Section "Extensions"
        Option  "Composite" "Disable"
EndSection
``` to /etc/X11/xorg.conf

is this happening to anyone else?

---

### Post by jimbob on 2006-11-07
This problem has been around for the last couple of releases as far as I am concerned and I still have yet to discover the cause.

I can't even discern a pattern for it to try to narrow it down a bit.  At least now I know there is one other person out there sharing the experience.

Sorry I can't be more help but let's hope someone who has it figured out will see your post.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by brian g on 2006-11-20
reinstalling gnome-screensaver seemed to fix this.
(so far)

---

### Post by szim90 on 2006-11-21
This sounds like the problem discussed in this thread:
[http://ubuntuforums.org/showthread.php?t=288651&page=3&highlight=screensaver](http://ubuntuforums.org/showthread.php?t=288651&page=3&highlight=screensaver)

I think this was found to be a problem in the gnome power manager. Someone posted a patch in gnome's bugzilla system, but I am not sure if it was patched in ubuntu or not. Here is the link to the gnome's bugzilla entry:
[http://bugzilla.gnome.org/show_bug.cgi?id=355279](http://bugzilla.gnome.org/show_bug.cgi?id=355279)

---

