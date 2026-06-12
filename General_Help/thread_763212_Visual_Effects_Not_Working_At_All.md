---
title: "Visual Effects Not Working At All"
date: 2008-04-22
forum: General Help
---

### Post by amtur_poet on 2008-04-22
No matter what visual settings option I select, it always gives me the error message, "Desktop effects could not be enabled." How do I fix this? [I have an 82G965 Integrated Graphics Controller, but no graphics card.]

---

### Post by pytheas22 on 2008-04-22
I have the same graphics adapter and desktop effects work fine.  Did the effects work at some point and suddenly break (and if so did you make any changes to the system before they broke), or is this a fresh install on which desktop effects never worked?

Open a terminal and type "compiz --replace"  What is the output that gets dumped to the terminal?

Also, type "glxgears" in a terminal.  Do you see the gears?

EDIT: actually I have an Intel 945 card, but it's close to yours, so I would think yours would work too.

---

### Post by irunwithknives on 2008-04-22
try seeing if there are any drivers you can enable in system=>administration=>restricted drivers manager.  
If there are, I suggest you print this then enable the driver[s].  If there aren't, im not sure I can help you.  The best thing you can do now is buy a new graphics card.

Reboot normally.  If you get to your normal desktop, you are in a good situation.  If not, turn off your computer manually, and reboot, pressing Esc on the GRUB loading screen.  go to recovery mode, and type

```
dpkg-reconfigure xserver-xorg
```

Go through the steps to set your system settings, then when you are done, type

```
shutdown -r now
```

---

### Post by Carl Hamlin on 2008-04-22
If you don't have Xgl installed, you could try that and see if you can enable the effects thereafter.

---

### Post by pytheas22 on 2008-04-22
> try seeing if there are any drivers you can enable in system=>administration=>restricted drivers manager.
If there are, I suggest you print this then enable the driver[s]. If there aren't, im not sure I can help you. The best thing you can do now is buy a new graphics card.

Unlike ATI and nvidia, Intel cards have open-source drivers, so the restricted driver manager shouldn't have anything to do with this.  Please do not go out and buy a new video card; the effects should definitely work with this one; you just need to figure out what's wrong.  Please post the information I asked for above and hopefully it will allow us to find a solution.  In addition, it would be useful if you posted the output of the command:
```

cat /etc/X11/xorg.conf
```

Also, you might want to take a look at this thread: [http://ubuntuforums.org/showthread.php?t=506744&highlight=965+compiz](http://ubuntuforums.org/showthread.php?t=506744&highlight=965+compiz) .  It's for Feisty and is outdated, but it could be useful.

---

### Post by Yellow Pasque on 2008-04-23
See this:
[http://ubuntuforums.org/showpost.php?p=4202892&postcount=6](http://ubuntuforums.org/showpost.php?p=4202892&postcount=6)

---

