---
title: "Ubuntu 21.04: Wayland + Gnome session bugs..."
date: 2021-04-24
forum: General Help
---

### Post by edwardecl on 2021-04-24
When I first run Gnome + Wayland session (which is the default now) the Gnome dock updates really slowly, once every 10 seconds or so, I disabled the disk mounts on the dock so it's not that. After a couple of hours gnome-shell starts using increasingly more amount of CPU time until the mouse pointer starts becoming unresponsive, the longer you leave it the worse it gets. If you enable and disable any shell extension the problem goes away for a few hours like starting a new session does.

I have reset the gnome settings to defaults, even tried making a new user just to be sure, disabled all user extensions, still have the same problem. The X11 Gnome session works fine, what is the problem here?

Hardware: AMD Ryzen 2700 CPU, AMD Radeon RX580 GPU, 16GB 3200mhz ram, 5.11.0-16-generic kernel, amdgpu glx_mesa 21.0.1 renderer.

I have the exact same dock bug on a Intel/Nvidia laptop, with a new install of 21.04...

Edit: OK the fix for the dock is to disable mounts showing...
gsettings set org.gnome.shell.extensions.dash-to-dock show-mounts false

Then rebooting or restarting wayland/gnome, just disabling is not enough.

---

### Post by kneutron on 2021-04-26
[COLOR=#000000][FONT=Arial]I did the install to ZFS boot/root and wayland/gdm3 is buggy in virtualbox 6.1.20 even with the guest additions installed.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Switching to tty1 gives you a blank terminal, you need tty3 to login as root. Switch to tty2 and it tanks X resolution back to 800x600.  You need to pull up Settings and re-set the Display resolution.

After pressing the Activities button at the top left (show all open windows) there is no way out of it short of restarting the gdm3 service, clicking on any open window or pressing ESC does nothing. 

All latest package upgrades are installed.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Right now it's too buggy to use.

[/FONT][/COLOR]

---

### Post by ipv2 on 2021-04-26
> **kneutron said:**
> [COLOR=#000000][FONT=Arial]Right now it's too buggy to use.[/FONT][/COLOR]

thus far i have not encountered any hiccups with the hippo.

my only grievance yet being that there are only 4 wallpapers.

---

### Post by edwardecl on 2021-04-26
I just did a full reinstall, and it's broken exactly like before... I only have one gnome extension installed "cpu freq".

I don't understand what is making gnome-shell use more CPU over time until you can't move the mouse pointer anymore, I never had this problem with 20.10.

The other bug with the gnome dock updating slowly is as soon as I add NFS shares, then not only do you have to disable the mounts on the dock you have to log out and into the Xorg session, then back out into the Wayland session for it to stop being slow. Even rebooting and going straight back into Wayland it's still broken. I don't really understand what logging into Xorg does to fix the Wayland session.

The gnome-shell thing slowing using more CPU is weird, because I have other PCs and a virtual machine and they don't have the same bug. It does it with Xorg and Wayland. Reading the Syslog does not help me at all, other than it saying my keyboard and mouse are unresponsive and my system is too slow.

The only thing I can do is periodically disable and enable a random extension, so I'm thinking one of the built in extensions is buggy or something.

---

### Post by edwardecl on 2021-04-27
I think I may have found the cause of the slow down...

"Ubuntu App Indicators", if i disable it my CPU usage goes back to normal. I guess it's not playing nice with one of the programs I have open... needs a fix.

I only have 3 programs open that use the indicators... element.io, discord and radeon-profile...

---

### Post by edwardecl on 2021-04-28
Does anyone know where I submit a bug report for this?

The problem definitely is with "Ubuntu AppIndicators" gnome-shell extension. Since disabling it I have had no problems with slowdown and mouse stuttering which was caused by high gnome-shell CPU usage over a period of time.

Again this was not a problem with Ubuntu 20.10 with exactly the same programs running, "radeon-profile" + "Discord" + "Element.IO". I'm not sure which of the programs is causing the extension to behave like that, but no program should be causing a shell extension to do that anyway.

---

### Post by ipv2 on 2021-05-01
> **edwardecl said:**
> Does anyone know where I submit a bug report for this?

the last time i reported a bug it was from within ubuntu itself.

this is how :

[https://help.ubuntu.com/stable/ubuntu-help/report-ubuntu-bug.html.en](https://help.ubuntu.com/stable/ubuntu-help/report-ubuntu-bug.html.en)

---

