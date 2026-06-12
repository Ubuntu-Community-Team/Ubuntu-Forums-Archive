---
title: "Enable Ctrl-Alt-F1 for new login prompt"
date: 2012-12-30
forum: General Help
---

### Post by tornadof3 on 2012-12-30
Hello

Ctrl-Alt-F{1-5} always used to work to give a new login prompt for a terminal session. This seems not to be the case anymore! Is there a particular package I need to install or setting to make this work again?

Ubuntu 12.10 with the 'classic' Gnome desktop.

Thanks

---

### Post by steeldriver on 2012-12-30
What exactly happens when you hit Ctrl-Alt-Fx? if it's just a blank screen then in my experience that's usually a graphics driver issue - for example on my NVIDIA based laptop with 12.04 it was trying to use a blacklisted framebuffer device

---

### Post by tornadof3 on 2012-12-30
Nothing whatsoever happens - it just stays on the standard graphical desktop, with no indication it even registered...

---

### Post by steeldriver on 2012-12-30
Oh... in that case I have no clue, sorry

---

### Post by ibjsb4 on 2012-12-30
Odd ..

Console (tty) is built in and should work without needing any extra packages.

Will "Ctrl + Alt + t" work?

Also check that function key work with some other command.

---

### Post by tornadof3 on 2012-12-30
Ctrl-Alt-t opens a terminal emulator window on my desktop

---

### Post by ibjsb4 on 2012-12-30
Found this

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1001183](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1001183)

Got a few more hits here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=cannot+switch+to+console+tty&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=cannot+switch+to+console+tty&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by father_ted on 2012-12-30
I got this too. Its not related to nvidia as im on ati video. Its very annoying and i hope they fix it soon - or give a workaround.

---

### Post by tornadof3 on 2012-12-30
Ah, that is annoying. Thanks for the link.

---

### Post by ibjsb4 on 2012-12-30
> **father_ted said:**
> I got this too. Its not related to nvidia as im on ati video. Its very annoying and i hope they fix it soon - or give a workaround.

Maybe you should file a bug report

---

### Post by rnerwein on 2012-12-30
> **tornadof3 said:**
> Hello

Ctrl-Alt-F{1-5} always used to work to give a new login prompt for a terminal session. This seems not to be the case anymore! Is there a particular package I need to install or setting to make this work again?

Ubuntu 12.10 with the 'classic' Gnome desktop.

Thanks
just a question: if you run in a terminal: "ps -ef | grep getty" can you see then 6 getty processes ?
if not have a look at /etc/default/console-setup and there at
ACTIVE_CONSOLES="/dev/tty[1-6]"
sorry no more ideas.
cheers

---

### Post by craigchambers on 2013-03-06
I too have this problem.  I've found that if I kill my current X session, then login again from the login manager, the TTYs are all available.
I'm not sure what is wrong on first login (autologin), or how to fix it.  Anyone have any ideas?

/Craig

---

