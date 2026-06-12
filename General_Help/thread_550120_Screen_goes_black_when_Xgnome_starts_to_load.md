---
title: "Screen goes black when X/gnome starts to load"
date: 2007-09-13
forum: General Help
---

### Post by LukeScott on 2007-09-13
Ok now this is just driving me crazy.... :mad:

I have a Dell Otiplex GX260 and I'm running the 845G onboard video. I have the memory cache set to 8MB, and the BIOS is version A06. The sound is also onboard "82801db".

When I first installed ubuntu on the machine (7.04) it was using the "i810" driver for my video. I didn't have hardware acceleration like I needed, so I installed the "intel" driver with apt-get and it gave me hardware acceleration. It worked great, no problems, all configured...

I turn it off for the night and come back the next morning and it goes through GRUB, the ubuntu boot screen shows and loads (with the orange bar), and then X starts to load with GNOME. I get the mouse over a black screen and then the whole display goes black. I try hitting Ctrl-Alt-Backspace and Ctrl-Alt-Backspace to get out of X, but that doesn't do anything.

I've had this happen to me a few times and reconfiguring X worked in recovery mode (Xorg -configure, rm /etc/X11/xorg.conf, mv xorg.conf.new /etc/X11/xorg.conf, Xorg, reboot)... But now nothing seems to be working.

It seems to be happening randomly. I haven't changed anything. The display is the same... the hardware is the same.

This is all becoming very frustrating because I don't know what to expect.

What I'm trying to do is turn this machine into a StepMania (DDR) box for the kids. But I keep having problems... I just want to turn it on and be ready to go...

:confused:

-Luke

---

