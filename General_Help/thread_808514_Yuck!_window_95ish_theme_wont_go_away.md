---
title: "Yuck! window 95ish theme wont go away"
date: 2008-05-26
forum: General Help
---

### Post by thwoom on 2008-05-26
hey, i cant seem to keep this theme from popping up, if i go to appearance and pick a new theme, it will only change the panels and whatever window is open. but then after restart it all goes back to this ugly boxy grey theme. any help would be much appreciated

---

### Post by p_quarles on 2008-05-26
So, what are you using? Gnome? KDE? Openbox? Windows 95? :D

Assuming that you're using the default Ubuntu setup, this may well be a Compiz problem -- but the "ugly boxy grey" theme doesn't sound familiar. If you could post a screenshot, that might help people see what you mean.

---

### Post by thwoom on 2008-05-26
oops, sorry yeah im using gnome, here is the screen shot

[IMG]http://i37.photobucket.com/albums/e75/thwoom/Screenshot.png[/IMG]

---

### Post by Genius314 on 2008-05-26
What theme are you trying to use? If the theme has an error in it (maybe even something minor, like a typo), the theme you want to use will revert to that theme.
Try to use a different theme, other than the one you want, and other than the "Windows 95" one. If it works, it's probably the theme. If not, it could be a bigger problem.

---

### Post by Forlong on 2008-05-27
Run this (first in the terminal to look for error messages, if there are none, then via [Alt]+[F2]): ```
gnome-settings-daemon
```

Did you by any chance install Xgl on your machine?

---

### Post by Dan_Dranath999 on 2008-05-27
Aaaaah my eyes! My blocked 95' Memories!

That's an UGLY Son of a Bi... Bill Gates!

---

### Post by sayakb on 2008-05-27
Do you gave the theme tarball (the tar.gz file?). If yes, then do this:
```
gksudo nautilus
```
Extract the theme and copy the theme's folder to /usr/share/themes
Then re-apply the theme

---

### Post by Arthur Archnix on 2008-05-27
That looks like the default gnome theme to me. But the transparency around the window borders suggests that you're running compiz. Maybe you want to blur your real name out of the screenshot?

Anyway, the first thing to do is locate the source of the problem. You can rule out compiz by hitting Alt+F2 then typing
```
metacity --replace
```
Now try changing your themes. Does it work? If so, you've messed up the default compiz install, or some other compiz related problem is failing to apply your theme.

---

### Post by stueng on 2008-05-27
looks to me like you enabled transparency in the advanced compiz settings... that happens to my themes when I turn on that setting.

Also, if you are using emerald try pressing alt+f2 and entering emerald --replace

---

### Post by thwoom on 2008-05-28
** (gnome-settings-daemon:25457): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:25457): WARNING **: Could not acquire name

this is what i get when i type that in, ill check the other thigns shortly, thanks for all of your help

---

### Post by smartboyathome on 2008-05-28
I have seen somoene else get this, they were trying to start gnome-settings-daemon on E17, and failed. Seems like there is a bug. Mind reporting on launchpad.net?

---

### Post by thwoom on 2008-05-28
metacity --replace does not fix the problem..
instersting new thing i noticed is that in  the system monitor gnome-appearance-properties is open several times, infact whenever i open appearance, a new one pops up in here and never goes away..

---

### Post by smartboyathome on 2008-05-28
That, I think, is because of gnome-settings-daemon having a bug. Have you upgraded gnome-settings-daemon recently?

---

### Post by thwoom on 2008-05-28
yes i believe so, i will do it now just incase 

edit: yes its up to date

---

### Post by smartboyathome on 2008-05-28
Ok, I got the same error, but the daemon was already running so that may be why. Try opening up the System Monitor (alt+f2 then type gnome-system-monitor), and killing it. It should restart itself. If not, run it again. If so, then see if it gives you your theme. Try other themes as well.

---

### Post by thwoom on 2008-05-29
that seems to have fixed the problem for now. ill report in if it ends up popping up again.

---

### Post by yen223 on 2008-05-29
Same windows 95 problem is happening to me too, only that it only affects Synaptic Package Manager:confused:

---

### Post by Forlong on 2008-05-29
That's because you are using a theme that is only installed for the current user.

Synaptic is run by root, thus you have to install the theme system-wide (just copy the theme's folder to /usr/share/themes) to make it used by root as well.

---

### Post by yen223 on 2008-05-29
> **Forlong said:**
> That's because you are using a theme that is only installed for the current user.

Synaptic is run by root, thus you have to install the theme system-wide (just copy the theme's folder to /usr/share/themes) to make it used by root as well.
Hey it works! Thanks man! And screw Ubuntu's separate main user/root user system!

---

