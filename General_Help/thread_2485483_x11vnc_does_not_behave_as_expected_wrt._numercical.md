---
title: "x11vnc does not behave as expected wrt. numercical keypad"
date: 2023-03-30
forum: General Help
---

### Post by 3246251196 on 2023-03-30
This is all on my local network.

I have a wirelessly connected laptop running Ubuntu 22.04.2
I have x11vnc 0.9.16

That is the server.

When I connect machine, let's call it X to that server, I am able to open up a shell and when I type a number on the numerical keyboard that number displays as expected.

I also have a desktop machine connected via wire running Ubuntu 22.04.2
On it, I have x11vnc 0.9.16

Another server.

When I connect to that with machine X, I am able to open up a shell and when I type a number on the numerical keyboard I **do not **see the number. The key registers, but as if it is performing the *function *of that key; e.g. Home, Pg Up etc.

I have compared the settings of both the wireless laptop and the desktop machine and I cannot see any differences. UK keyboard, etc, etc.

Why, for the same exact client software and machine (X) am I getting different results for the same server version on the same operating system version?

---

### Post by 3246251196 on 2023-03-30
Update:
[https://bugs.launchpad.net/ubuntu/+source/x11vnc/+bug/1852743](https://bugs.launchpad.net/ubuntu/+source/x11vnc/+bug/1852743)

See the comments in that ticket. This does not seem to be an x11vnc issue. I can see that both servers (laptop versus desktop) show different results when using the "xev" tool, used to detect events.

Does anyone know how to configure this properly. From "settings" on both servers, they appear to be the same.


Values of 
**gsettings get org.gnome.desktop.a11y.keyboard mousekeys-enable** is [B]FALSE

[/B]===

The desktop server machine is just a machine sitting there. It only has power and an ethernet cable. (well, a display port) too, but no keyboard or usb device attached at all. Could it be that during the startup of the machine ubuntu detects no keyboard and just assumes there is no numerical keypad versus the laptop which does have one. I cannot imagine this to be the case, but I cannot see why there is a difference here!

---

### Post by 3246251196 on 2023-03-31
So, plugging in a keyboard (which will have been the first time doing so since a fresh install of Ubu) solves this problem. It must have changed something and saved whatever state persistently. Now, I can VNC and use the numerical keyboard.

---

### Post by ActionParsnip on 2023-03-31
Why connect then open a shell? Why not just use SSH?

---

