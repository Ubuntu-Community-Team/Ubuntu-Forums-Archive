---
title: "Persistent remapping of keys with setxkbmap or Xorg configuration"
date: 2020-02-16
forum: General Help
---

### Post by matthew-bluteau on 2020-02-16
I have been wracking my brain over the past week or so with what should be a straight forward problem. I want to *permanently* swap the CapsLock and Ctrl keys on my laptop. I emphasise the permanently because I know how to do this on an ad hoc basis easily from the command line with a minor tweak to the keyboard map:

```
setxkbmap -option ctrl:swapcaps
```

The problem with this is I have to execute it every time I boot up, wake from sleep/hibernate, or connect a USB keyboard. This quickly gets annoying, and this really feels like something that should be persistently set on a per user basis.

 After extensive Google searching and on this forum, I have drawn up the following dead ends:

[LIST=1]
[*]Setting a "Startup Application" with the appropriate command works for initial login, but then the keyboard gets reset upon sleep/hibernate and USB keyboard connection. This is the solution I see posted everywhere, but its not really a solution. Example: [https://ubuntuforums.org/showthread.php?t=2375159&highlight=keyboard+map](https://ubuntuforums.org/showthread.php?t=2375159&highlight=keyboard+map)
[*]I dove into X11/Xorg configuration. Creating any version of [FONT=courier new].x<something>[/FONT] in my home directory has no efffect (e.g.  [FONT=courier new]~/.xinitrc, ~/.Xkbmap, ~/.Xmodmap, ~/.profile)[/FONT]
[*]Tried placing a script in [FONT=courier new]/etc/X11/xorg.conf.d/[/FONT] but that has no effect either.
[*]I don't have a [FONT=courier new]/etc/X11/xorg.conf[/FONT] file present and I don't particularly want to generate one. Also, I would rather not make a setting that is universal across users and not portable across devices.
[*]It seems like the above doesn't work because of gdm3 taking over the Xsession generation and possibly some involvement of Wayland (although I have confirmed my user session is X11 and not Wayland). I looked at the file [FONT=courier new]/etc/gdm3/Xsession[/FONT] and confirmed that it does source the [FONT=courier new]~/.x<something>[/FONT] files, but then those settings must get overwritten at some point.
[/LIST]

Does anyone have any insight through this swamp? It seems like the desktop/display manager situation for Ubuntu is an absolute mess with no definitive documentation.

My system: ```
5.3.0-28-generic #30~18.04.1-Ubuntu SMP Fri Jan 17 06:14:09 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by matthew-bluteau on 2020-02-18
Could this be moved to the General Help subforum? I tried posting again there but my duplicate there got removed.

---

### Post by slickymaster on 2020-02-19
*Thread moved to **General Help**.*

---

