---
title: "How to specify desktop type using command?"
date: 2024-02-15
forum: General Help
---

### Post by zzzzhhhh on 2024-02-15
We usually specify desktop type like GNOME or Ubuntu listed in `/usr/share/xsessions/` at login GUI by mouse click. If we need to specify it in command line, what command can do it? The OS is Ubuntu 22.04.

---

### Post by TheFu on 2024-02-15
Gnome is tough.  They often don't follow standards. 

ICCCM2 2.0 compliant window managers allow swapping the window manager from inside a running system.  DEs are more complex and not all DEs work with all WMs. In short, there isn't a single command to switch that I know about.  Ghome is tightly coupled to the WM, so even using a different WM isn't supported.

However, if you don't use Gnome and want to change DEs, assuming the DEs involved all work with the same WM, you can just kill the DE process - usually a has "panel" or "de" in the process name, then start the other process.

Swapping DEs can cause problems.  Some settings with the same name have conflicting meanings.  Switching between Qt and GTK+ -based DEs is less dangerous, so LXQt and XFCE is much safer than XFCE and Mate.  Gnome4+ is a different animal.

---

### Post by Yellow Pasque on 2024-02-15
Does this work?:
```
echo $XDG_CURRENT_DESKTOP
```

---

### Post by MAFoElffen on 2024-02-18
If what you mean by "specify desktop" is how do you change desktops on the fly...

There use to be ways to do it... And there are ways shown on the internet to how they "were" done, that just do not work anymore. 

That was before the evolution of the Linux Graphics Layer changed the number of vtty's, where display session 0 used to always start in only one location (no longer defaults to vtty7), and where other other displays are assigned after that (used to be :1 @ vvty8, :2 @ vtty9...), a vttyX limit change set the default to 'NAutoVTs=6'... The addition of the Wayland Graphics Engine (GE), where Xorg used to be the only other player... And more complex Desktop Environments like Gnome & KDE that set many ENV VARS that do not cross over from one to the other.   

I used to be able to just kill the existing current desktop and using a chained command, start the other new. No that longer works, and the limited times when it does, it isn't stable.

I used to be able to increase the number of vttys, and then tell startx to start a session in another display session. No longer "stable".

If you start one GE while another is already running, it kills the other. They can't run (normally) at the same time.

Things just got complicated.

There are currently two accepted answers... 

The first is still if'fy... Install a Xephyr Desktop Development Environment, and run a DE within the current desktop in a virtual sandbox. It's hard and time consuming to setup the DEV environment for that, and even though it used to be cool, it still has limitations on what you can run concurrently... and because of that, and  honestly is not 100% stable.

The only way currently that is 100% stable, is to log out to the DM, and start a new session from the DM.

---

