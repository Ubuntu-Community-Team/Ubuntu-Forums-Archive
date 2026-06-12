---
title: "Oh crap - changes my hostname and things went to hell."
date: 2008-06-09
forum: General Help
---

### Post by ravenvii on 2008-06-09
I decided to change my hostname to make my GDM look cooler (yeah...), so I went ahead and changed it with the GUI (went into Network preferences, changed the hostname under the General tab, and changed the name also under the Hosts tab. I was aware that after changing the hostname I could not launch any applications, but I didn't know that includes the logout/restart/shut down/etc dialog!

So with no choice, I hit del+alt+backspace to kill X.

And I'm now stuck on the screen, the last line says "running local boot scripts (/etc/rc.local)"

What to do what to do?

---

### Post by fsmithred on 2008-06-09
ctrl-alt-F7 should get you back to your desktop. If that doesn't work, try ctrl-alt-F1 or ctrl-alt-F2, and see if you get a console login screen, log in, and then you can do stuff on command line, such as:

```
less /etc/hosts
less /etc/hostname
```

or, if you see something there that needs to be corrected (like your hostname), edit the files with nano.

or, you might want to restart your x-session with:
```
startx
```
or
```
sudo /etc/init.d/gdm restart
```

or you could even:
```
sudo reboot
```

---

### Post by ravenvii on 2008-06-09
I tried alt-ctrl-f1 to bring up a new console, but no commands registers. Anything I try to put in, nothing happens. The return key acts as a normal return key, not as an enter key.

I ended up just hard rebooting the thing.

---

