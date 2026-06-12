---
title: "Startup Programs deleting"
date: 2007-10-27
forum: General Help
---

### Post by chroncile on 2007-10-27
Every time I put an entry into the startup programs, it automatically gets erased after I close it and open it back up :confused::(
I have no idea why this is happening, can someone please help me :(

---

### Post by chroncile on 2007-10-27
hello?
Can't anybody help me? :(!!

---

### Post by ctsdownloads on 2007-10-27
I am assuming this was done from system, preferences, sessions on GNOME (Ubuntu)?

First tell us which programs you are auto-starting and then what information you are entering into the sessions new start up program box after choosing 'new'? ;)

---

### Post by thelocust on 2007-10-27
[COLOR=#666666]Permissions problem perhaps?[/COLOR]

---

### Post by chroncile on 2007-10-27
So, how would I fix that?

---

### Post by thelocust on 2007-10-27
No idea budy I use KDE. I was just throwing it out there. I think ctsdownloads got you covered.

---

### Post by aidanr on 2007-10-27
```
sudo chown -R `whoami`:`whoami` ~/.config
sudo chmod -R 755 ~/.config
```

---

### Post by chroncile on 2007-10-27
> **aidanr said:**
> ```
sudo chown -R `whoami`:`whoami` ~/.config
sudo chmod -R 755 ~/.config
```

That didn't do anything :(

---

### Post by aidanr on 2007-10-27
Can you run gnome-session-properties from the terminal and see if it prints out any errors.

---

### Post by ctsdownloads on 2007-10-27
Or....get all the programs you want running, then in sessions, goto session options and choose save this current session - it's never failed me. Again, taking a simple approach, sometimes it helps to know what the heck the person is trying to autostart, before getting too deep into the command line ;)

---

### Post by chroncile on 2007-10-28
Well, other then this, I don't think there are any errors :

```

/home/username/.themes/aero-clone/gtk-2.0/toolbar-custom.rc:21: Unable to locate image file in pixmap_path: "Toolbar/toolbar-black.png"
/home/username/.themes/aero-clone/gtk-2.0/toolbar-custom.rc:24: Background image options specified without filename
/home/username/.themes/aero-clone/gtk-2.0/gtkrc:187: Unable to locate image file in pixmap_path: "Arrows/arrow-up.png"
/home/username/.themes/aero-clone/gtk-2.0/gtkrc:191: Overlay image options specified without filename

```

I already tried saving the session, it didn't work :(

---

### Post by #Reistlehr- on 2007-10-28
you can always add the programs you want to /etc/inittab or w/e, and theyll boot at the end of every multiuser runlevel

---

### Post by chroncile on 2007-10-28
Ok, so how do I do that?

---

