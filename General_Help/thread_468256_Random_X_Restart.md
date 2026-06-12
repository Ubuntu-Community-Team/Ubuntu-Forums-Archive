---
title: "Random X Restart"
date: 2007-06-08
forum: General Help
---

### Post by the_dark_light on 2007-06-08
This seems to be a new problem since I reinstalled Ubuntu Feisty (Only difference between now and my old setup is a new hard drive) - X keeps resetting

This seems to happen when I leave it to install software.  The past few times I've left Synaptic running, I've come back to be greeted by the login screen.  A few minutes ago I managed to catch it in the act.  I was using the add/remove programs tool to install the "ubuntu restricted extras" package.

Is this a common problem and does anyone know what's going on? (I can provide logs etc as needed)

Just when I'm about ready to ditch Windows (Ubuntu was running happily before) this happens :(

(Addendum: It just did it in the middle of watching a movie, so it's not the installer)

---

### Post by jimbob on 2007-06-08
How do you know that X is resetting?  If that was happening you would go to single user text mode like in CTRL-ALT-F1.  It sounds to me like you are being logged out or the machine is being re-booted.

Maybe power supply problem?  Try booting with these two switches added to the kernel line in /boot/grub/menu.lst:  acpi=off noapic
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

