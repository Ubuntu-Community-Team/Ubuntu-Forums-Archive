---
title: "Beryl Help -- &quot;no composite extension&quot; compatibility error"
date: 2007-02-24
forum: General Help
---

### Post by satchelpig on 2007-02-24
I'm hoping someone here can help me solve the problem I'm having getting beryl going.  I have followed the directions for installation and installed the latest drivers for my video card (256MB ATI mobility Radeon 1400), and on the surface everything seems fine.

I even get the beryl manager in the system tray.

But once it's there, I can't get it going.  When I try to select Beryl as the window manager, my windows all blink but then return to where they were.  No splash screen, no nothing, and when I check the window manager selection it's already back to metacity.

In checking the terminal readout, this is what I get, which I suspect would easily clue a more experienced linux user into an obvious problem, but I don't know what it means:

* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

---

### Post by floke on 2007-02-24
Did you edit your xorg.conf file correctly? 
You have to add a section at the end which looks something like

Section "Extensions"
Composite "true"
EndSection

Its not this (I can't remember it exactly) but its something like this.

Have you got it set up properly? any typos etc.?

---

### Post by lolwhites on 2007-02-28
I'm getting the same error messages, yet Beryl was working fine until today.

---

### Post by ~LoKe on 2007-02-28
You're using Feisty, aren't ya?
> Section "Extensions"
    Option "Composite" "Enable"
EndSection

---

### Post by lolwhites on 2007-03-03
No, Edgy. Like I say, it was fine before, though it stopped working after downloading some updates a few days ago. Not sure what they were; is there any way of finding out?

---

### Post by precinto on 2007-03-12
Same here. Any updates?

---

### Post by lolwhites on 2007-03-13
You might find an answer here:
[http://ubuntuforums.org/showthread.php?t=374879]("http://ubuntuforums.org/showthread.php?t=374879")

---

