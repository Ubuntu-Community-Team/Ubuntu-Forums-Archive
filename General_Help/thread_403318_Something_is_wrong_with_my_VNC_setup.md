---
title: "Something is wrong with my VNC setup"
date: 2007-04-06
forum: General Help
---

### Post by SeanWuzHere on 2007-04-06
I'm using RealVNC viewer on my Windows XP laptop and connecting to my Ubuntu 6.10 desktop. I can connect no problem but I can't seem to click on anything. For instance, I have both computers sitting right next to each other. I connect, and I can see the desktop in Windows once it connects. When I move the mouse around, I can see the cursor moving around on both screens but when I click, it's only working on the Ubuntu side. For instance, on the Windows side, I can see the mouse (with the little black dot) and move it around but when I click nothing happens. But something does happen on the ubuntu side. Does this make sense?

In Ubuntu, under Remote Desktop Preferences, I have the following ticked..
- Allow other users to view your desktop
- Allow other users to control your desktop
- Require the user to enter this password:

---

### Post by crispy_420 on 2007-04-06
This appears to be on the windows side. Maybe a setting in RealVNC?

---

### Post by SeanWuzHere on 2007-04-06
I thought so too at first but I feel like it might be on the Ubuntu side. I've tried DotNetVNC, TightVNC, RealVNC, etc. and get the same results.

Just fyi,.. the ip of the ubuntu box is 192.168.1.54,... so I am just punching in 192.168.1.54:0 in RealVNC and then clicking ok. I also tried x.x.x.x::5900, I have connected with putty using SSH and the tunneling configuration. So all these different ways connect fine but for whatever reason I am not able to make windows react to clicks from the Windows side. I'm just wondering if there is some kind of *.conf file I should edit, or something. Something somewhere is just not right.

---

### Post by crispy_420 on 2007-04-06
How did you allow remote desktop in ubuntu?

What has worked for me is the default app: System -> Preferences -> Remote Desktop

I checked these:

Allow other users to view desktop
Allow other users to control your desktop
Require password (password added of course)

Left unchecked:

Ask you for confirmation

From my win box I open RealVNC and point to the ubuntu box (eg. 192.168.0.12 and not 192.168.0.12:0). Before I connect I decide my connection (eg. colors, more means slower connection). When you connect it will ask for that password you added in ubuntu.

That has worked me and it will allow basic connection. Some may point out a lack of security but I'm behind a firewall router. I figure if someone really wants to attack you, they will.

---

