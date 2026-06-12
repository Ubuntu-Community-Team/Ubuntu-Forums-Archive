---
title: "Remove gdm &quot;Options&quot; button"
date: 2007-03-01
forum: General Help
---

### Post by Stedwick on 2007-03-01
Is it possible to remove the "Options" button in the Human gdm theme (so it doesn't show up in the login window)?

Thanks!

Stedwick

---

### Post by kpkeerthi on 2007-03-01
As a root, cd to /usr/share/gdm/themes/ and then to the appropriate theme folder. You'll find a XML config file where you can comment out the tags correspoding to Options button (do a search for 'options' and you'll find it). Save and logout to see the changes. Make sure you backup the file just in case.

---

