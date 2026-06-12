---
title: "Internet Connection - Ubuntu vs. Kubuntu"
date: 2005-06-05
forum: General Help
---

### Post by Lorraine on 2005-06-05
For some reason my internet connection using the Ubuntu Live CD is not as good as when I use the Kubuntu Live CD.  Has this been an issue for anyone?  When I'm using the Kubuntu Live CD, I breeze through web sites like nothing (I have a DSL connection).  However, when I load up Ubuntu, I get stalled when trying to load web pages, if they bother to load at all.  Is it due to differences between the Mozilla browser in Ubuntu and the Konqueror browser in Kubuntu?  Although, I'm not sure why that would matter.  I use Firefox under Windows, and it runs just fine.   I would really prefer to do a full install of Ubuntu rather than Kubuntu, but should I be expecting the same internet connection issues from the full install?  Is Ubuntu just generally slower than Kubuntu?

---

### Post by defkewl on 2005-06-05
Ubuntu Live CD is known much slower to load. Perhaps it affected your internet connection.

---

### Post by Lorraine on 2005-06-05
Yeah, I did notice that it took longer to load than Kubuntu.  That must be it.  That doesn't have any bearing on Ubuntu when it is fully installed though, does it?

---

### Post by Joeb on 2005-06-08
[QUOTE=Lorraine]For some reason my internet connection using the Ubuntu Live CD is not as good as when I use the Kubuntu Live CD.  Has this been an issue for anyone?  When I'm using the Kubuntu Live CD, I breeze through web sites like nothing (I have a DSL connection).  However, when I load up Ubuntu, I get stalled when trying to load web pages, if they bother to load at all.  Is it due to differences between the Mozilla browser in Ubuntu and the Konqueror browser in Kubuntu?  Although, I'm not sure why that would matter.  I use Firefox under Windows, and it runs just fine.   I would really prefer to do a full install of Ubuntu rather than Kubuntu, but should I be expecting the same internet connection issues from the full install?  Is Ubuntu just generally slower than Kubuntu?[/QUOTE]


This is a good news bad news thing.  First the good news:  Most likely, it is an IPv6 problem with Firefox.  Firefox defaults to trying to use it and konqueror doesn't.  If you search on the forums for IPv6 or google for firefox and ipv6, you'll get info on the settings to change.  As far as I know, the Windows version of firefox doesn't have the problem.  Now the bad news:  Since you are running the livecd, you can't save the changes and would have to make them each time you booted.

You indicate that you are planning a regular Ubuntu install.  Is your intention then to install the KDE environment (since standard Ubuntu installs gnome)?  If so, then you will still be running konqueror and it won't be a problem.  If not, and you plan or running gnome or at least using firefox, then disabling the IPv6 should do the trick.

---

### Post by Lorraine on 2005-06-11
Oh, wow.  Good to know.  I'll definitely look up that IPv6 issue, and see how it works out reworking the settings using the Live CD.  The plan was just to install Ubuntu (Gnome environment only).  I could always install KDE later should I find that I don't like Gnome, but for right now I'm pretty enamored with the idea of running Ubuntu by itself.  Thanks again for the info. :D

---

### Post by Lorraine on 2005-06-11
Yep, changing those settings in Firefox worked like a charm.  I'm surfing with the Ubuntu Live CD as I type.  Thanks, joeb.  :)

---

