---
title: "Tracker can't search in the Psi chat history files"
date: 2008-06-09
forum: General Help
---

### Post by descentspb on 2008-06-09
Is there a way to make tracker search inside the Psi history files? They are located here:

**/home/user/.psi/profiles/default/history**

as text files with names like: **40****93_at_icq.jabber.org.ru.history**

But even if i provide the direct link to this folder inside the tracker configuration as the place, where it should always index, it doesn't help, and i can't see these files listed if i enter their contents.

---

### Post by descentspb on 2008-06-11
bump

---

### Post by berteh on 2008-06-25
I think tracker does not know about this file format, so you need to either ask to the dev mailing list or hack tracker (fairly easy for this particular point).

It should be possible by telling to tracker how to index these files (eg: as html, pdf or any other of the already indexed format: [http://live.gnome.org/Tracker/SupportedFormats](http://live.gnome.org/Tracker/SupportedFormats)) in the tracker mime-types associations settings (see sources and development documentation)

If you want to make a particular extractor for this file format (eg to get rid of all chat times & dates) have a look at the plugins.

I won't be of more help, so better ask the developpers directly if you go that way:
[http://www.gnome.org/projects/tracker/development.html](http://www.gnome.org/projects/tracker/development.html)
[http://mail.gnome.org/mailman/listinfo/tracker-list](http://mail.gnome.org/mailman/listinfo/tracker-list)

---

