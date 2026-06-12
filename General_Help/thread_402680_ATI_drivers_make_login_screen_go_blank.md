---
title: "ATI drivers make login screen go blank"
date: 2007-04-06
forum: General Help
---

### Post by anemon on 2007-04-06
Since I switched  to the ATI graphics drivers, my login screen doesn't display right: whatever settings I choose in System > Administration > Login screen, the monitor goes blank and says the signal does not comply with its recommended resolution (1680x1050, if I remember right).

Any ideas on this? Where can I change the display resolution for the login screen? It doesn't seem to have anything to xorg.conf, 'cause everything looks all right there. The weird thing is that it's *only* the login screen that is affected: the boot splash looks good, and once I log in (i.e. enter my user name and password without seeing what I write) the Gnome logo and desktop pop up just like usual. 

I don't know if it's a bug, but it sure bugs me. ;-)

---

### Post by adam.tropics on 2007-04-06
Have a read [through this page.]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/16472") I don't have a specific answer for you but that page has a couple suggestions if you look through it.

---

### Post by anemon on 2007-04-06
I've taken a look at the page you recommended, and there is one workaround that seems promising: the "aticonfig" command. But when I try

```
aticonfig --resolution=0,1680x1050
```

in terminal, I get the following error message:

```
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.
```

What's up, doc?

---

### Post by anemon on 2007-04-06
Sorry, it's just me being stupid. I forgot to "sudo"...

---

### Post by anemon on 2007-04-06
Anyhow, it still doesn't work: on logout, the screen just goes black again. And I tried all the other workarounds on the bug report page (except the one for Kubuntu users), and none of them seems to work.

Sooo ... any more ideas, anyone?

---

### Post by anemon on 2007-04-07
OK, problem solved. And it *does* seem that "aticonfig" worked! But you won't notice until you actually reboot your system; just logging out doesn't do the trick (I got that impression from the bug report page)...

Thanks, adam.tropics, for your excellent recommendation!

---

### Post by strabes on 2007-04-07
You don't have to completely reboot. You can just restart the X server (which also logs you out) with Ctrl+Alt+Backspace.

---

