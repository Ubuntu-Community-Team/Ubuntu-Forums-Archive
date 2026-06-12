---
title: "Tracker to search Evolution Contacts?"
date: 2008-05-19
forum: General Help
---

### Post by Jfrench on 2008-05-19
Is there a way I can get tracker to index the contacts I have in Evolution. I used it to store my phone numbers, it would be really awesome if I could just use Tracker to find the numbers. Anyone know of a way to do this?

---

### Post by berteh on 2008-06-25
I think tracker does not know about this file format (yet), so you need to either ask to the dev mailing list or hack tracker (fairly easy for this particular point I guess).

It should be possible by telling to tracker how to index these files (eg: as text, html or any other of the already indexed format: [http://live.gnome.org/Tracker/SupportedFormats](http://live.gnome.org/Tracker/SupportedFormats)) in the tracker mime-types associations settings (see sources and development documentation)

If you want to make a particular extractor for this file format (eg to get rid of some details, or provide meta-data besides the full text) have a look at the extractors and plugins.

I won't be of more help, so better ask the developpers directly if you go that way:
[http://www.gnome.org/projects/tracker/development.html](http://www.gnome.org/projects/tracker/development.html)
[http://mail.gnome.org/mailman/listinfo/tracker-list](http://mail.gnome.org/mailman/listinfo/tracker-list)

---

