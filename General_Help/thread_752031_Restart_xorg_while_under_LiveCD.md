---
title: "Restart xorg while under LiveCD?"
date: 2008-04-11
forum: General Help
---

### Post by Burillo on 2008-04-11
I am a Windoze refugee and am used to switching layouts with Alt+Shift, so i edit my xorg.conf as appropriate during normal installation and then restart xorg and everything works fine.

That's not the case with livecd - if i restart xorg - the computer just reboots. Is there a way to restart the X-server within LiveCD Session?

---

### Post by kesman on 2008-04-11
Maybe run in terminal
```

sudo /etc/init.d/gdm restart

```

---

### Post by ajgreeny on 2008-04-11
Are you sure **Ctrl+Alt+Backspace** doesn't do the trick after you have changed xorg.conf?  That key combination normally just stops x and it restarts, the computer should not reboot.

---

### Post by danwood76 on 2008-04-11
Actually ctrl+alt+backspace logs you out, thats why it will shutdown the live disk.
It does restart X when you log out ;)

You should be able to restart gdm from the command line without it restarting.

---

### Post by ajgreeny on 2008-04-11
OK, I'd never though about it that way.  Thanks for setting me straight.

---

### Post by ajgreeny on 2008-04-11
Actually, I've just tried the Ctrl+Alt+Backspace on a live Ubuntu CD and it does what I originally thought, it stops x and then it restarts again.  I also did try editing xorg.conf before the restart and the changes were retained OK, with the graphics driver changed from ati (good for my card) to vesa (relatively bad for my card).

I don't understand why my setup is acting differently to yours but it could be worth you trying what I did and see if it gets you to where you want to be.  Or, of course, perhaps I've just misunderstood your problem.

---

