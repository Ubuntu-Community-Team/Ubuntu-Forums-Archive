---
title: "Some daemons won't autostart... help"
date: 2005-07-24
forum: General Help
---

### Post by garion on 2005-07-24
Hi, I am having trouble to get two programs start at boot-up, one is emifreq-applet (cpu scaling applet), and the other one is ddclient (dynamic dns update applet).  Both of them are in /etc/init.d/ and have S20 symlink in run-level 2 to 5... I tried Boot-Up Manager (bum) and update-rc.d... both show that they are configured properly for autostart.  Other daemons like ssh and firestarter boot properly, with exactly the same setting.  Anyone knows why and how to solve this?

With ddclient, it seems to be the script that's the problem, since using "sudo /etc/init.d/ddclient start" gives some error too.  However, with emifreq-applet, it works perfectly well with "sudo /etc/init.d/emifreq-applet start", but just won't auto-start.  Since I have this applet on my gnome panel, it always complains the daemon is not started everytime I login, until I manually start it.

The functionality of emifreq is not compromised, because it seems to control the cpu using powernowd anyway... but i'd like to see cpu temp too, so i am kind of stuck with emifreq.

These sound like pretty trivial questions... but I am new to this OS... any tip or help is greatly appreciated.  Thanks.

---

### Post by charlieg on 2005-07-24
On bootup, do the daemon loaders appear as Ubuntu inits each daemon?  Try 'ctrl-alt-f1' and reading what's shown (although might not show everything) or reading on boot (If you're using Upower or Splashy, hit F2 as soon as the boot-up spash screen appears).

---

### Post by garion on 2005-07-25
Yah, thanks... I should have thought of that earlier.  So as I have expected, the ddclient script is not right, there is a line before the start block that reads a default config file /etc/default/ddclient, in which the daemon option is disabled.

As of emifreqd, by looking at the startup message I found it's complaining cpufreq not supported... and then I realize that it got started before powernowd because both are by default priority 20... so I changed emifreqd to 21, then everything works fine.

Thanks for the help!

---

