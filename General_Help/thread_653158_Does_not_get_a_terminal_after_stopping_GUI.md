---
title: "Does not get a terminal after stopping GUI?"
date: 2007-12-29
forum: General Help
---

### Post by iox42 on 2007-12-29
I got the book "Beginning Ubuntu Linux" by Keir Thomas (Second edition)  this christmas, and I really like the new stuff the terminal lets me configure and do.

In the book, there is a chapter about optimizing my harddrive's settings, by using the command *hdparm*. To do this, however, the book tells me that it is most effective if the GUI is stopped, and this is achieved by typing
```
sudo /etc/init.d/gdm stop
```
and enter my password etcetera.

However, when I do this, my GUI indeed stops, but i do not get a terminal to fiddel with - my screen is just black. What am I doing wrong? I tried CTRL+ALT+F (as i read in some other thread) to start a terminal, but this did not work. The only way I can get out of the Black Void is to do a hard reset of my laptop, by the button.

I have up to date Ubuntu 7.10 on my Acer Aspire 5102WLMI laptop, and I dual boot with windows XP, if that would have any impact.

Please help!

PS. I hope I choose the right forum, just relocate my thread if it fits somewhere else. Thanks! DS.

---

### Post by psycho78 on 2007-12-29
check your /boot/grub/menu.lst file for any entry that looks similar to 
"vga=791" (search for vga=)... you will find something like this:
# defoptions=vga=791
just delete vga=791 so that there is only 
# defoptions=
left. Afterwards type:
sudo update-grub  
in an xterminal (e.g. gnome-terminal)... this will set your screen resolution for the console back to default AFTER REBOOT and you will be able to see the console after stopping gdm (i have the same problem).. i don't know if there is another way to fix this...
Regards,
Psycho

---

### Post by iox42 on 2007-12-29
I fixed it, the problem was solved using the trick presented in this thread:
[http://ubuntuforums.org/showthread.php?t=582962&page=4](http://ubuntuforums.org/showthread.php?t=582962&page=4)

Namely, doing this:

> **fwhr said:**
> My Ctrl+Alt+F did'nt worked, too
So, I opened a terminal and typed
```

sudo modprobe vga16fb
sudo modprobe fbcon
```
Checking... After that commands I can use Ctrl+Alt+Fx to open a virtual terminals again...
I just added this lines :
```

vga16fb
fbcon
```
into /etc/modules
and Ctrl+Alt+Fx works for me after reboots, too.

Sorry for not checking this out before posting.

EDIT: Alas, this did not solve stuff in a good way - when I rebooted after doing this tweak, I never arrived at the login-screen and was stopped in the tracks when the system tried to start up. I think it coughed by the time it read my new additions to the modules-file, so I switched to a virtual terminal, undid my changes, rebooted, and everything worked as earlier (thank god.)
My temporal solution is to run these commands in a terminal;
```

sudo modprobe vga16fb
sudo modprobe fbcon
```
whenever i wish to use the virtual terminals, although this is rather cumbersome, and avoid the latter part of the trick quoted above. Anyone have any ideas why stuff went wrong?
I added
```

vga16fb
fbcon
```
just after the code already present in my /etc/modules , making it contain the following commands to be used at boot time::
```

fuse
lp
vga16fb
fbcon

```
and this, as said, caused problems. Should I try putting the new commands before the old ones already present?
(This would make modules:
```

vga16fb
fbcon
fuse
lp

```)

---

