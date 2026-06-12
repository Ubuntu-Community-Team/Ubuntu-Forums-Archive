---
title: "Can no longer change icons"
date: 2018-03-05
forum: General Help
---

### Post by col48 on 2018-03-05
I have a number of files which I gave given their own home-made icons.

Hitherto I could change the icon within nemo or nautilus by right-clicking on the file, choosing Properties, clicking on the icon then displayed alongside the other properties then navigating down to the desired icon file (a png built as an icon in gimp), and then clicking 'Open'.

After taking the latest kernel (or it may be the one before) these icons are no longer associated with the files in the file manager (either nemo or nautilus).  Furthermore, the above procedure no longer works.  It looks OK up to the last step (click 'Open'), which has no effect.

After trying with nautilus initiated in a terminal, I find the following in syslog (username redacted)```

gnome-session[1725]: (nautilus:1807): GVFS-WARNING **: can't init metadata tree /home/[[username]]/.local/share/gvfs-metadata/home: open: Permission denied
```

What's up?
How can I get round this?

---

### Post by col48 on 2018-03-06
Maybe it's obvious from the log message.....

The file called 'home' and its companion 'home-75bc14e4.log' were the only files in that folder which were owned by root rather than me.

I changed their ownership using chown to myself and **_(without any further action on my part)_** the files showed the desired icons in nemo.
Also I could set icons as before.

Presumably this will persist over a restart....

Something must have changed the ownership of the 'home' file and its log.... Very cheeky!

---

### Post by col48 on 2018-03-06
My solution (post 2) may shed some light for anyone with a similar question to that in this Closed thread:

[HTML]https://ubuntuforums.org/showthread.php?t=2115384[/HTML]

which is entitled
*How can I find the current icon for a file on my desktop?*

---

