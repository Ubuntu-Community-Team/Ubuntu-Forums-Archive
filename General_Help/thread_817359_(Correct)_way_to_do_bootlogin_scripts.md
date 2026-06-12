---
title: "(Correct) way to do boot/login scripts?"
date: 2008-06-03
forum: General Help
---

### Post by TagUrIt on 2008-06-03
Is there a relatively painless way in Ubuntu 7.10?

For more details, I'm working with an old P3 system trying to get dual monitors to work off of the old ATI Radeon 7000/VE card.  I've finally gotten it to work, though in a very roundabout fashion.  In order to get into the system so that the graphics work, I need to boot into recovery mode, startx, then kill x (Ctrl+Alt+F1 or Ctrl+Alt+Bkspc).  After that, I change the runlevel to 2, which starts X.  After logging in, I simply run 'xrandr --output DVI-0 --left-of DVI-1', and then I have my dual screens working.

If I boot straight into "normal" mode, then the system seems to boot fine until it finishes with the splashscreen, but then turns black and both monitors turn off.  It doesn't make any sense to me, but I found something that works, and I'm pretty content staying with my convoluted method if I can find a decent way to automate it.

So, in short:
1. How can I make a small snippet of shellcode run as the "recovery mode" finishes booting?  (This would be something like 'startx ; /etc/init.d/gdm stop ; init 2', I think.)
2. How can I make it so that the xrandr stuff happens at login after X gets started?

((I thought about playing with the /etc/rc1.d/ and /etc/init.d/gdm things, so that we have the start/kill X as priority 99 in the former directory, and the xrandr as the end of the latter file.  I don't want to break it too badly, though.))

---

