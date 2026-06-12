---
title: "Freezing after login"
date: 2023-04-27
forum: General Help
---

### Post by plkoij on 2023-04-27
I'm running 22.04 on a Framework laptop. It's been working perfectly fine for a few weeks until this morning.

After logging in, it freezes before showing the desktop. If I press ctrl+alt+f1 it goes back to the login prompt, but if I try to log in it freezes again.

Already tried:
-entering recovery mode and sudo-apt updating
-using an older version of the kernel from the boot menu (has same issue)

Possibly relevant context: right before this started, I was having an issue connecting to wifi where it wasn't even bringing up the prompt to enter my wifi password. I restarted hoping to fix that and then couldn't log in. Wifi seems to be fine now though.

---

### Post by plkoij on 2023-04-28
I figured out the cause - some xrandr commands in my .profile. If I remove them, it boots fine.

I tried the instructions here ([https://fostips.com/switch-back-xorg-ubuntu-21-04/](https://fostips.com/switch-back-xorg-ubuntu-21-04/)) to force xorg, but even when I do that I can't boot with the xrandr commands in .profile. Is there somewhere better to put them?

The commands are xrandr --newmode and --addmode to add a custom screen resolution, and they work fine if I run them in terminal, just not if I put them in .profile to run on startup.

---

