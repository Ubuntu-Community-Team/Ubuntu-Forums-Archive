---
title: "Change the administration theme?"
date: 2007-03-10
forum: General Help
---

### Post by isecore on 2007-03-10
This is a slightly silly problem but it annoys me none the less.

Whenever I go into the Administration tools I of course have to input my password in the dialog box that appears. Then the sudo-user kicks in and the chosen Admin-tool opens.

However, it's a butt-ugly theme whenever something is run with gksudo. This started happening a few days ago, and I can't figure out how to change the GTK-theme to the same that my "normal" user uses. I want a uniform look and when i manually run gnome-theme-manager with sudo I can't change the theme for the "root user" (or whatever one calls it).

This does not affect function, only looks a bit weird. Any clues to how to change it so that I get a uniform look on the desktop?

---

### Post by cmost on 2007-03-10
I had the same problem.  You need to add whatever theme you're using to the following location:

/usr/share/themes

As root, open a nautilus browse window, go to the above location, and paste the theme tarball for the particular theme you're using.  Then extract it.  Delete the tarball.  Now, when you use administrative tools, they should display with the same theme you're using.  Enjoy!

---

### Post by isecore on 2007-03-10
Awesome! Thanks for the excellent help!

I just did a sudo -s in a terminal and copied the theme I was using from ~/.themes into /usr/share/themes, that did the trick.

---

