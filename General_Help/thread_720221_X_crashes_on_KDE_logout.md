---
title: "X crashes on KDE logout"
date: 2008-03-10
forum: General Help
---

### Post by KeyserSoze93 on 2008-03-10
I'm using Kubuntu 7.10 and it has been fine up until recently, however every few times I log (including on the way to shutting down),

I either get a black screen with just a cursor (though that can be fixed with ctrl-alt-bkspace).

Or, more recently a black terminal screen with only a (bios like) underscore cursor which doesn't respond to anything... (and none of my ttys work either)

I have discovered I can get control back via Alt+SysRq+R + Alt+SysRq+E + Alt+SysRq+I (the first part of REISUB to do an emergency reboot) and then log into the terminal and shut down normally. But it is pretty annoying.

This may or may not be related, but I recently turned of the splash screen in GRUB so I can see a list of whats going on and not that stays on tty1 all the time (meaning I can use 2 / 6 with 7 as my x server).

---

### Post by kesman on 2008-03-10
Do you have an ati graphics card? Their newest catalyst fixes quite similar problems.

---

### Post by KeyserSoze93 on 2008-03-10
Nah, I've got an Nvidia Gefore MX 440 using the restricted drivers...

---

