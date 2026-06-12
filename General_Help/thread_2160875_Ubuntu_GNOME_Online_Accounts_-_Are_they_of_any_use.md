---
title: "Ubuntu GNOME Online Accounts - Are they of any use?"
date: 2013-07-08
forum: General Help
---

### Post by Roasted on 2013-07-08
Am I missing something, or are these online account features useless? I added both my work's Microsoft Exchange as well as my personal ownCloud account. The options for files, contacts, calendar, mail, etc., are all checked. Yet approximately nothing has changed. I'm not seeing what I'm missing?

I've tried this on two installs on the same system.

Ubuntu GNOME 13.04 + Gnome3 PPA
Ubuntu GNOME 13.10 Alpha

---

### Post by Roasted on 2013-07-08
I found out some more information, based on tests of my own as well as discussions in the IRC channel.

13.04 with Exchange integration - currently I get nothing at all when I add my Exchange account. I open Evolution and it's as if I have no accounts activated, despite having it enabled in Gnome's Online Accounts. 
13.10 with Exchange integration - works flawlessly. It syncs over my calendar, email, everything. Granted there's about an 8-10 minute lapse between when calendar items sync over, but it's great having two way edit-ability (finally). It makes Evolution a real treat these days.

In regard to the ownCloud integration, it seems as if (on Fedora 19) all it does is add a shortcut to the webdav login on the left side of your Nautilus bar. It's no secret that ownCloud's webdav port is pretty poor. I thought that the ownCloud integration would be a replacement for their sync client, but it doesn't seem to be that way at all. Ubuntu GNOME's lack of ownCloud integration, despite Gnome Online Accounts having it listed, is due to a missing httpd/apache instance. Evidently there's more work to do to get it working beyond simply installing Apache, but that seems to be the primary reason as to why ownCloud doesn't seem to work on Ubuntu GNOME. That being said, as I mentioned above, the sync client is far superior to ownCloud's webdav port anyway (which is all the integration handles), so it's a relatively moot point.

I'm still exploring why 13.04's exchange integration is, well, seemingly non-existent while 13.10's is a home run.

---

