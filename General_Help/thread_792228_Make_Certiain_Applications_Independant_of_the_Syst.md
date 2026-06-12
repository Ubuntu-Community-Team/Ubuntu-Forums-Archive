---
title: "Make Certiain Applications Independant of the System Theme"
date: 2008-05-12
forum: General Help
---

### Post by SnakeByte29 on 2008-05-12
I was wondering if there is any way to make certain applications independant of the system theme (in Gnome). The application I'm referring to specifically is OpenOffice, which is rendered very difficult to read/use by the dark theme I am currently using (Overglossed). I otherwise quite like this theme and don't want to change it. Any insight would be greatly appreciated.

---

### Post by Brucevdk on 2008-05-18
See the following thread (and more precisely [the reply by alvinistic](http://ubuntuforums.org/showpost.php?p=4513676&postcount=6)):
[LIST]
[*][*PLEASE HELP* Override GTK theme - Ubuntu Forums](http://ubuntuforums.org/showthread.php?t=688098)
[/LIST]
So in your case try something like:
```
GTK2_RC_FILES=/usr/share/themes/Human/gtk-2.0/gtkrc ooffice
```
Or in a launcher:
```
bash -c 'GTK2_RC_FILES=/usr/share/themes/Human/gtk-2.0/gtkrc ooffice'
```

If you're using the OpenOffice.org Quickstarter you'll want to change the command in System -> Preferences -> Session from *ooffice -quickstart -nologo -nodefault* to something similar (I haven't tried this out myself).

---

### Post by valadil on 2008-08-16
I just did this with gnome-do.  The problem is that any applications it launches retain gnome-do's $GTK2_RC_FILES.  Any ideas for how I could configure gnome-do to launch apps with my default settings and/or any other ways to set a custom skin for a single app that won't propagate to other apps it launches?

---

