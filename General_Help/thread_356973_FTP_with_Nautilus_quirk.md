---
title: "FTP with Nautilus quirk"
date: 2007-02-09
forum: General Help
---

### Post by Pigsflew on 2007-02-09
I've been using Ubuntu for two semesters now and am incredibly pleased, but I've noticed a quirk in Edgy that I can't figure out how to fix.

I have a few FTP sites that I use Nautilus to connect to, and the Gnome panel helpfully lists them under "Places", but when I click on them, Nautilus doesn't open. Instead it tries to access the FTP site with Firefox.

How does gnome-panel choose default programs, and is there something I can do about this?

---

### Post by asdfsaefrtaghafred on 2007-03-01
I had the same problem. You need to execute "gconf-editor" and navigate to /desktop/gnome/url-handlers/ftp.

There you'll see a name value pair "command" which probably has a value pointing to firefox.
Change that command path to /usr/bin/nautilus or wherever else nautilus may be. To be sure where it is, you should run "which nautilus" to get your path. Hope this helps

Cheers.

---

### Post by Pigsflew on 2007-05-07
Perfect, thank you so much!

---

### Post by CocoAUS on 2007-05-07
This actually answered a question I had, as well.  In fact, I asked last night why, even after my default browser and HTML filetype association were both set to Epiphany, Firefox kept opening links instead of Epiphany, and no one answered!

This does it, though.  Now Epiphany handles everything.  Thanks.

---

