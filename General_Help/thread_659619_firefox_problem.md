---
title: "firefox problem"
date: 2008-01-05
forum: General Help
---

### Post by stumped on 2008-01-05
I am running ubuntu edgy eft  and firefox version 2.0.0.11
Whenever I right click on a picture and click save image as, firefox closes.
This also happens when I try to download something and click on the save to button.
If I open firefox as the root user, this does not happen, and it all works fine.
I am not %100 positive, but I believe this started happening after I installed wine.
What could be causing this and how do I fix it ?

---

### Post by Joe Jarvis on 2008-01-05
> **stumped said:**
> What could be causing this and how do I fix it ?

When you look in Firefox's preferences, what is the default location to save files?

---

### Post by stumped on 2008-01-06
It is set on always ask me where to save files.

---

### Post by Joe Jarvis on 2008-01-06
Sorry I'm stumped.

---

### Post by stumped on 2008-01-06
LOL !    So am I.

---

### Post by stumped on 2008-01-06
I have just discovered that my sources.list also won't open. It will flash on for a split second and then close. The only way I can get it to stay open is to right click on it and select open with text editor. It used to open just by clicking on it.
Could this problem and the forefox problem be related some how?

---

### Post by ~LoKe on 2008-01-06
> **stumped said:**
> I have just discovered that my sources.list also won't open. It will flash on for a split second and then close. The only way I can get it to stay open is to right click on it and select open with text editor. It used to open just by clicking on it.
Could this problem and the forefox problem be related some how?

Try opening both applications through the terminal.  When they crash, you should get some output.

---

### Post by stumped on 2008-01-06
If I do the command   less sources.list
it will let me see it.
When I open firefox through the terminal it opens as it should. 
Opening firefox isn't the problem. The problem is right clicking and clicking on save picture as, or clicking on a download link and clicking on the save to button.

---

### Post by ~LoKe on 2008-01-06
> **stumped said:**
> If I do the command   less sources.list
it will let me see it.
When I open firefox through the terminal it opens as it should. 
Opening firefox isn't the problem. The problem is right clicking and clicking on save picture as, or clicking on a download link and clicking on the save to button.

Open firefox through the download then do what makes it crash.  It'll output some information in the terminal that could help us solve the problem.  Same with gedit:
```
gksu gedit /etc/apt/sources.list
```
And paste here what the printout is once gedit crashes.

---

### Post by stumped on 2008-01-07
> **~LoKe said:**
> Open firefox through the download then do what makes it crash.  It'll output some information in the terminal that could help us solve the problem.  Same with gedit:
```
gksu gedit /etc/apt/sources.list
```
And paste here what the printout is once gedit crashes.

I ran  firefox through the terminal and did what makes it crash twice.
The first time the terminal said:
Segmentation fault (core dumped)

The second time the terminal said:
(Gecko:5371): Gdk-CRITICAL **: gdk_colormap_get_screen: assertion `GDK_IS_COLORMAP (cmap)' failed

(Gecko:5371): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(Gecko:5371): Gdk-CRITICAL **: gdk_colormap_get_visual: assertion `GDK_IS_COLORMAP (colormap)' failed
Segmentation fault (core dumped)


Running gksu gedit /etc/apt/sources.list I get:
(gedit:5712): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Gedit does open and show me the sources.list but I get the error above as it opens.

---

### Post by stumped on 2008-01-08
Does anyone have some idea?

---

### Post by stumped on 2008-01-12
bump

---

