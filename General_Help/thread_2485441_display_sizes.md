---
title: "display sizes"
date: 2023-03-29
forum: General Help
---

### Post by jgw on 2023-03-29
I have two machines.  One is fine and one is not.  the display is a samsung 24" display.  They are both using the same display (kvm) The one that is not 1680x1050 (16/10) and so is the problem is the same.  I have tried several resolutions - same problem.  The one with the problem has a display which is approximately 25% bigger as the good one.  They should be the same.  I have absolutely no idea how or why.

I think this might have to do with the kvm.  The kvm connector has a cable with one vga connector on both ends.  The one with just the vga connector goes into the kvm distributor and the other, with a male usb and the vga connector which goes into a usb port and the vga connector into the vga port on the pc.  I moved the usb to different usb ports and got different vga results on the monitor (an overall reduction of almost 50%).  I am beginning to think that this may not be workable.  

My current system displays firefox and the display fits within the parameters of the monitor.  The problem is that the headers in firefox remain too big.  but, at least, I have help myself a bit on this one. 

Thank you..............

---

### Post by jgw on 2023-03-31
Figured it out.  Got rid of wayland and went to x11 - fixed the problem!

---

### Post by jgw on 2023-04-01
It worked last night but, today, it doesn't even thought I am not using X11 rather than wayland

---

### Post by MAFoElffen on 2023-04-01
Please run the UbuntuForums 'system-info' Script, either by downloading from the Forum's [GitHub Page]("https://github.com/UbuntuForums/system-info") or installed via [the PPA]("https://launchpad.net/~mafoelffen/+archive/ubuntu/system-info"). Post the URL of where the report uploads it to a Pastebin.

---

### Post by jgw on 2023-04-05
Should mention that I have fixed the problem.  The system was a bit confused but kinda fixed itself!

[https://termbin.com/wa9i](https://termbin.com/wa9i)

---

### Post by MAFoElffen on 2023-04-05
> **jgw said:**
> Should mention that I have fixed the problem.  The system was a bit confused but kinda fixed itself!

[https://termbin.com/wa9i](https://termbin.com/wa9i)
I am glad that it is working for you!

Pray tell... How was it confused?  And how did it fix itself?

---

### Post by jgw on 2023-04-05
I am really not sure but its all working now.  I remember I was messing with a variety of zoom/not zoom.  Same with fonts and, suddenly everything just started snapping into place.  It was very strange.  I am old, been doing computer stuff for a very long time but my mind is slowly but surely going to hell in a handbasket.  I tend to blame a lot of my problems on ME!  I can remember the good old days when I could sit down and code stuff with no problem.  I don't even try anymore.  

There is a phrase which is my favorite - **** Happens! (wasn't intended, stuff just happens, no sense in blame as its a waste of time)

---

