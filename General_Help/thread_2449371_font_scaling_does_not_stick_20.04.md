---
title: "font scaling does not stick 20.04"
date: 2020-08-25
forum: General Help
---

### Post by stevelcb on 2020-08-25
Hi everyone

I just upgraded 18.04 to 20.04.
I set font scaling using gnome tweak to 0.8, but the setting does not remain between sessions.

I've tried:

```
gsettings set org.gnome.desktop.interface text-scaling-factor 0.8
```

But that has no effect either as user or sudo.
Anyone?

Cheers,
Steve

---

### Post by pantazi on 2020-08-28
Try removing and re-installing Gnome-tweaks.  Maybe related to [this]("https://ubuntuforums.org/showthread.php?t=2449249")

---

### Post by stevelcb on 2020-08-29
Hi
Thanks, but that didn't work. I removed gnome-tweak-tool but tweaks is still available in activities. 
No idea...
Anyone?
TIA

---

### Post by norobro on 2020-08-29
No idea either but gnome-tweaks and gsettings both work on my 20.04 box.

Do other changes persist? 

The config file for those settings is ~/.config/dconf/user. Is the file writable?```
~$ ls -lgG .config/dconf/
total 20
-rw-rw-r-- 1 20142 Aug 29 18:06 user

~$ gsettings  writable org.gnome.desktop.interface  text-scaling-factor
true

```

---

### Post by joe129 on 2020-08-30
> **stevelcb said:**
> Hi everyone

I just upgraded 18.04 to 20.04.
I set font scaling using gnome tweak to 0.8, but the setting does not remain between sessions.

I've tried:

```
gsettings set org.gnome.desktop.interface text-scaling-factor 0.8
```

But that has no effect either as user or sudo.
Anyone?

Cheers,
Steve

I have also been having this problem I have been running 20.04 for 2 months now but font problem only started  four days ago , my font size is set  to 1.02 in tweaks but on each boot it presents with small icons  fonts and small logon password box,  I have to go into tweaks each time and manually alter font sizes for the fonts to scale properly even thought tweaks is still set to 1.02  i have not added or removed any apps so this must be down to something that installed during updates.

---

### Post by stevelcb on 2020-08-30
Hi everyone
I just discovered kubuntu. *Sooo *much easier. 
Totally as you want it to look without having to jump through hoops!
Thanks everyone for their time and effort of course.

---

### Post by Dennis N on 2020-08-30
Instead of changing the Scaling factor, did you try changing the Interface Text size? That might be more persistent.

The size of the font in the top bar is set by the gnome-shell theme for the theme you are using. Look for the file gnome-shell.css in the theme folder.

```
dmn@Sydney-VM:/usr/share/themes/Flat-Remix-Dark/gnome-shell$ tree -L 1
.
&#9500;&#9472;&#9472; assets
&#9492;&#9472;&#9472; gnome-shell.css

```

---

### Post by pantazi on 2020-08-31
Interface text size can easily be changed via Gnome tweaks and it *is* more persistent.

---

### Post by nico16 on 2020-09-06
Been having the same issue, and although I didn't find a solution as such, here is what I ended up doing, which makes things a bit better:
[https://ubuntuforums.org/showthread.php?t=2449512&page=2](https://ubuntuforums.org/showthread.php?t=2449512&page=2)

---

