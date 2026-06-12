---
title: "Problem with Virtualbox"
date: 2008-04-30
forum: General Help
---

### Post by cj1976 on 2008-04-30
I'm fairly new to the whole Linux thing, but I'm quite impressed so far with Ubuntu 8.04. I am having a problem with Virtualbox OSE.
I installed it using the Synaptic manager in order to use Windows XP (only to use a Korean office application). The installation starts fine but when I click inside the virtual "screen" for Windows, the keyboard and mouse simply do not respond and I cannot even access the System Monitor to force quit.
Any useful tips or advice would be greatly appreciated.

---

### Post by Nunu on 2008-04-30
Try pressing the right CTRL or Shift or ALT buttons, i don't remember which one of them released control back to the host OS

---

### Post by cj1976 on 2008-04-30
The host capture is set by default to be Right Ctrl but this doesn't do anything.

---

### Post by sdennie on 2008-04-30
I had a problem with this not working at one point.  You could try to re-assign the key by using File->Preferences->Input and changing the key for the main VirtualBox window.  Also, I've found turning off "Auto capture keyboard" to be very useful as well.

---

### Post by cj1976 on 2008-04-30
> **vor said:**
> I had a problem with this not working at one point.  You could try to re-assign the key by using File->Preferences->Input and changing the key for the main VirtualBox window.  Also, I've found turning off "Auto capture keyboard" to be very useful as well.

I tried this but it didn't help either. Once I go into the Virtualbox, I can't do anything at all.

---

### Post by rbmorse on 2008-04-30
Are you using a USB keyboard and mouse?  List time I tried Virtual Box it had fits with USB peripherals.

---

### Post by ericy on 2008-05-02
> ... found turning off "Auto capture keyboard" to be very useful as well.

This works for me. Thanks!

(I couldn't type anything in my WinXP guest)

=================
Update:

Keyboard still doesn't work if the guest OS is Linux... (Fedora 8/9, Ubuntu 7.04, Gparted iso disc)

---

