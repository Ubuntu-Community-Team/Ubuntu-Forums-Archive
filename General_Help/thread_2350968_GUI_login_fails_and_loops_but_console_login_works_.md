---
title: "GUI login fails and loops but console login works fine"
date: 2017-01-29
forum: General Help
---

### Post by jf-moniquelevi on 2017-01-29
[COLOR=#000000]Upgraded from 14.04 to 16.04.
Some problems, resolved,** one not resolved.**

Trying to login the GUI (Gnome), when I enter my password, screen goes dark, flickers and loops back to password entry  screen.  Therefore I cannot login.

If I go to command line (Ctrl Alt F1) I can login without a problem;  then I enter** reboot ** , and after a while , I am directly in the GUI without having to login  !!!

Checked .*Authority files, I am the owner.

I read that using** sudo Nautilus** was a no-no and could create this kind of problem ?   Well, I didn know and did that a few times.
> if you must run GUI apps as root use [/COLOR]> **gksudo instead, or even [B]sudo -H, both of which are safe to use.**[/B]

Any ideas ?  Been trying to find a fix for the whole week-end, getting close to divorce  :D.

Thanks in advance.

---

### Post by Bashing-om on 2017-01-29
jf-moniquelevi; Hello;

A couple of thoughts.
1) Do you have the authority to access your desktop ?
```

ls -al .ICEauthority .Xauthority

```
2) a broken proprietary graphic's driver ?
```

sudo lshw -C display

```

else, right now
[INDENT][INDENT][INDENT]who knows
[/INDENT][/INDENT][/INDENT]

---

### Post by efflandt on 2017-01-29
That sometimes happens if you have wrong graphics drivers or not configured or removed properly. What graphics hardware to you have, typically related to VGA section (or possibly also 3D section with laptop) in output of **sudo lspci -v** [which may also show graphics driver(s) in use]. Or it might even be that your graphics is not supported by default graphics driver, or you may need **nomodeset** boot parameter.

---

