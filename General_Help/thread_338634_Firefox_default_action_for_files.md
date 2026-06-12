---
title: "Firefox default action for files"
date: 2007-01-14
forum: General Help
---

### Post by Nate53085 on 2007-01-14
I am trying to change the default application for a downloaded file, specifically torrents (.torrent).

Its currently set to ktorrent.

Looking in Edit->Preferences->Content->Manage there is nothing about torrents.

Where else is this information stored?

Thanx ahead of time.

---

### Post by Buck2348 on 2007-01-14
I'm not sure about this for your question, but in general you can right-click on a file's icon, select Properties -> Open With tab, if the app you want is not listed, click Add and find it.

Buck

---

### Post by Nate53085 on 2007-01-15
> **Buck2348 said:**
> I'm not sure about this for your question, but in general you can right-click on a file's icon, select Properties -> Open With tab, if the app you want is not listed, click Add and find it.

Buck

What I'm looking for is where firefox stores its default actions.

---

### Post by andreas64 on 2007-01-16
Hi,

I think, Buck2348 is right. If there is no action defined in Firefox for torrent-files, the gnome-standard-action is used.

Andreas

---

### Post by Nate53085 on 2007-01-17
I don't believe this to be the case.

Right now double clicking on a torrent in gnome opens in it gnome's torrent client while firefox opens in in ktorrent.



*******EDIT*************

Found it.

its mimetypes.rdf found in your .mozilla/firefox/../ folder.

Deleting a bunch of torrent related tags fixed it for me.

I am really surprised that these aren't available to view under preferences.

---

