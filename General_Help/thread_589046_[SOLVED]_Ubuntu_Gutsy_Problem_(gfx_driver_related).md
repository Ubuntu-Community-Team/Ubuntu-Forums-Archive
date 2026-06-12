---
title: "[SOLVED] Ubuntu Gutsy Problem (gfx driver related?)"
date: 2007-10-23
forum: General Help
---

### Post by LynkDead on 2007-10-23
Today I upgraded to Gutsy, and everything was going great until after I turned my laptop off then tried to turn it back on again later.

Let me describe the problem: When I turn my laptop on, the regular startup process occurs, I see the Ubuntu loading screen, as usual. However, instead of taking me to the regular Ubuntu login screen, I am instead taken to a command-prompt login only. My login works fine, and there was no problems with the Gutsy update whatsoever.

Things that might have caused the problem: the most drastic change today, obviously, was the update to Gutsy. However, I also tried to update my graphics driver with Envy. When that didn't work (Envy isn't supported under Gutsy yet, which I didn't find out until later), I thought that perhaps I couldn't upgrade my driver until I had uninstalled the old driver, which I did, again using Envy. Skip ahead to me using the internet to discover that Envy doesn't work yet with Gutsy. By this time, I had to leave the house, so I shut my laptop down.

Upon returning home, I turned on my laptop and was met with the problem above. Right now I'm using my old Feisty LiveCD to get to the internet, but this is definitely a temporary solution, and I'd like to keep all my old files.

Any advice?

---

### Post by Qwerty_ on 2007-10-23
First off I would either boot into safe mode to see if you can access your restricted drivers.

System>Administration>System Drivers Manager.

See if you can install the restricted drivers for your graphics card.

If that does not work you try to following command to hopefully reconfigure your xserver.

```
dpkg-reconfigure xserver-xorg
```

---

### Post by LynkDead on 2007-10-23
Enabling the restricted driver (within the LiveCD, since I can't/don't know how to do it from the terminal) cause the system to give me an error about the xserver upon restart.

I then tried the reconfigure command you listed and set up (hopefully) correctly my settings. After another reboot things SEEM to be working correctly. I'll post here again if anything else goes wrong, but for now everything appears in working order. Thanks :)

---

