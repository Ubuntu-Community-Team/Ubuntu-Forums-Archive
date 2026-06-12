---
title: "[SOLVED] Resetting video driver in Kub-Gutsy"
date: 2008-02-18
forum: General Help
---

### Post by FleetAdmiral74 on 2008-02-18
Hi people! Once again I proved how stupid I am. I am trying to get Starcraft to go fullscreen under Wine, and after trying a few things decided to change the screen resolution to 640x480, just for the gaming sessions. But nothing was happening when i pressed accept on the new settings (even in admin mode), so i thought the driver might be weird.

I changed the driver from the fglrx (the Radeonnnn 9200, i think those are the right letters) one that comes in the repos) to the fglrx (vesa) one. Mistake! Screen is completely unreadable. Now, how would I go about changing the driver back to the correct one? I currently just have the Kub w/ kde4.0 cd, but i could get the 3.5x if needed. Im on the LiveCD now.

edit: could i have been using the kde4 system manager, instead of the 3.5 one? (the one i usually use is 3.5, but both programs are there side by side..) And another note...my HD is not showing up under /media..should it now auto show-up?

---

### Post by FleetAdmiral74 on 2008-02-18
Bumpity bump

---

### Post by Yellow Pasque on 2008-02-18
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Choose the radeon driver :)

---

### Post by FleetAdmiral74 on 2008-02-19
So just by doing this, it will fix the install on the hd partition? 

```
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080219051147
```

Since I'm currently on a LiveCD, i would have guessed I would have to select the root or home dir first, or something like that...And I am a bit unclear of how to select the right driver. If I rebooted, would it just give me options now?

Or if I drop to a CLI (since i can boot and enter pwd ok, just cant make out anything) will that depend on video driver or not? (how do i drop to the cli anyway, i only know ctrl alt back)

---

### Post by Yellow Pasque on 2008-02-19
Don't use the LiveCD. Boot into recovery mode (you may need to hit 'Esc' to access the boot menu when you start your PC). If that doesn't work, try booting as normal and then pressing Ctrl+Alt+F1 to get to a terminal.

---

### Post by FleetAdmiral74 on 2008-02-19
Thats the ticket. Now, if I can only find out why my screen is not responding to resolution changes...

System Settings > Monitor and Display > resolution...but screen does not change, which is what made me try the other driver in the first place.

nvm, got it to work. system > kRandRtray. it only worked if i right clicked the taskbar icon, not going through the windows, but it works. Good night fellow linux zealots!

And a special thanks to Temüjin

---

### Post by Yellow Pasque on 2008-02-19
What does your etc/X11/xorg.conf look like?

---

