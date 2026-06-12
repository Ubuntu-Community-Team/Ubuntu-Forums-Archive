---
title: "fluxbox question"
date: 2005-04-23
forum: General Help
---

### Post by ghettobanana on 2005-04-23
for the people using fluxbox...

I am getting a red bar at the top left corner on shutdown...I never got this while using gentoo...any thoughts?

I am using GeForce4 MX 440 all is install and working fine but this issue drives my crazy.

---

### Post by artio on 2005-05-20
How do you shut down? Choosing "Exit" from the Fluxbox menu and then Shutdown from the gdm screen - or using ```
sudo init 0
``` from a terminal? And at what point does the red bar appear?

---

### Post by darkaudit on 2005-05-20
I see this when I logout from Fluxbox via Exit on the menu. It appears during the transition from exiting Fluxbox to the GDM login screen. I think it's harmless. I'm going to check and see if it happens when I exit any other WM's.

[EDIT]This happens on exit from every WM I'm using, be it Fluxbox, Blackbox, KDE, or XFCE. The WM exits, the monitor goes black, then comes back up with the small bar at the top left, and sometimes part of the previous WM's wallpaper. Then the screen goes black again and the GDM login page comes up.[/EDIT]

---

