---
title: "Blank screen booting from CD"
date: 2008-07-01
forum: General Help
---

### Post by RTDeko on 2008-07-01
I have been trying to boot Ubuntu from the CD.

Everything appears to be going well, then the screen goes black.

I hear the typical startup music, but nothing appears on the screen.

I have a ATI Radeon HD2900 card, and a Westinghouse 24" monitor set to 1920X1200.

Thanks in advance, Artie

:guitar:

---

### Post by quibbler on 2008-07-01
> **RTDeko said:**
> I have been trying to boot Ubuntu from the CD.

Everything appears to be going well, then the screen goes black.

I hear the typical startup music, but nothing appears on the screen.

I have a ATI Radeon HD2900 card, and a Westinghouse 24" monitor set to 1920X1200.

Thanks in advance, Artie

:guitar:

Hello Artie,

When you hear the startup music and still have a black screen,
try pressing Ctrl - Alt - Backspace all at once (3 finger salute),
this will restart  x-windows and you should see the login screen.
Do not try to login, just wait 10 seconds and it should open to the
Desktop. 

This has worked for me in the past.

Good luck quibbler

---

### Post by kriukov on 2008-07-01
That always happened to one of the computers where I had to install Ubuntu. Somehow the monitor switches off when X starts. Try Ctrl+Alt+Backspace to shut down X and see if the CLI appears (or Ctrl+Alt+F2 to switch to a different terminal). The workaround that I used was to install the video driver from the command line and then edit /etc/X11/xorg.conf by putting the corresponding driver in the "driver" string, then restart X.

In your case get CLI and do

sudo apt-get install xorg-driver-fglrx
sudo nano /etc/X11/xorg.conf

Put "fglrx" (with quotes) in the section "Device" string "Driver"

Save the file. 


startx

EDIT: just recalled that gdm restarts automatically by default, so get the command line by Ctrl+Alt+F2, and when you save xorg.conf, press Alt+F7 and Ctrl+Alt+Backspace, and see if it works.

---

### Post by RTDeko on 2008-07-03
Hmmmmmmmmmm..This isn't working.

It makes a coconut noise and then the music plays again.

But the screen stays black.

Any other advice? :)

Artie

---

### Post by RTDeko on 2008-07-06
Ok, it has to be something in my comp. I have tried Mint, OpenSUSE, and Fedora and they all do it. What a bummer eh?

---

