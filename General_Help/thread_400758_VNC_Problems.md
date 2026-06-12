---
title: "VNC Problems"
date: 2007-04-03
forum: General Help
---

### Post by marcus16 on 2007-04-03
I had Ubuntu 6.10 running on an old Athlon with a Radeon 8500 card, and VNC worked fine.
But I replace that computer with a Pentium D, with a Radeon X600 card, and now VNC works poorly.
Things remain partially on the screen.
Things won't load until you move your mouse over them, and sometimes they don't at all.
I don't even really know how to describe it.
So I'll post some screen shots.

[IMG]http://im.noveis.net/ubuntu-vnc/1.jpg[/IMG]
After creating a new folder.

[IMG]http://im.noveis.net/ubuntu-vnc/2.jpg[/IMG]
Password dialog when doing an admin function.

[IMG]http://im.noveis.net/ubuntu-vnc/3.jpg[/IMG]
User settings.

[IMG]http://im.noveis.net/ubuntu-vnc/4.jpg[/IMG]
User settings. I had to scroll over to see these buttons.

[IMG]http://im.noveis.net/ubuntu-vnc/5.jpg[/IMG]
I can see these icons, but normally I'd have to select them first to see them.

[IMG]http://im.noveis.net/ubuntu-vnc/6.jpg[/IMG]

I doubt it's an issue of bandwidth, because it's over LAN, and it doesn't matter what bandwidth setting I set it too.
And because it worked on the old computer.

I'm using UltraVNC client on a Windows XP machine. Other VNC clients have no more success.

This is quite annoying, so if anyone can help me it would be very appreciated!
If you need any more info, just ask!

Thanks,
Marcus

---

### Post by UncleB on 2007-05-10
It may be stupid to suggest but did you try checking your /etc/X11/xorg.conf file?

Make sure the driver is on ati and not vesa.

Does the system look ok when running Gnome locally?

Also if you are using your own setup VNC (rather than the wino one in the default System-Preferences-Remote Desktop menu) it may be worth experimenting with the vnc arguments- specifically geometry and depth.

Best of luck...

---

### Post by Dillius on 2008-03-18
I am having the same problem and it is very irritating. I'm using the built in remote desktop in Gnome, and on the client side I have tried both RealVNC and TightVNC on my windows machine. Both have the same result.

---

### Post by GregBlen on 2008-03-24
I have been running Ubuntu on an HP nc6000 Laptop for some time now, starting with v6.0. It has worked flawlessly with various VNC clients including TightVNC.
Now after upgrading to 7.10 I got the same problem as described here by marcus16.

The way to solve it for me was to remove the Restricted Driver for the built in ATI Mobile graphics card...

---

