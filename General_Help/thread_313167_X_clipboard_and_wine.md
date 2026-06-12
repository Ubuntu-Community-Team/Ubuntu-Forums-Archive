---
title: "X clipboard and wine"
date: 2006-12-05
forum: General Help
---

### Post by jpolanco on 2006-12-05
I've been trying to run a windows application through wine, but my problem is that this application is supposed to read the clipboard, since it runs with a clipboard manager. Well that's not working. When I copy any text the clipboard manager says "The Clipboard does not contain recognizable information at the moment.". So I'd like to know if it's possible to integrate the X clipboard with wine.

Just if you want to know, I'm talking about Utopia Angel, a formatter for the online game Utopia. It's supposed to format the info that I copy into the clipboard. Angel can be downloaded at [www.utopiatemple.com](www.utopiatemple.com), but it's only avaiable for windows... :( 

Anyway, I hope I can get some help, thanks in advance, and sorry for my bad English :)

---

### Post by jpolanco on 2006-12-07
I could still use some help... :neutral:

---

### Post by bodhi.zazen on 2006-12-07
I have integration on my set-up but that does not help you much does it.

I did not do anything "special" to get integration.

Perhaps downgrade you version of wine.

[How to downgrade wine](http://doc.gwos.org/index.php/HowToWine#Downgrade_wine)

---

### Post by jpolanco on 2006-12-07
It's still not working... I downgraded wine to version 0.9.24 and then 0.9.12 for Dapper, but I still have the same problem.

When I start this program I get:

```
err:systray:delete_icon invalid tray icon ID specified: 0d
err:systray:delete_icon invalid tray icon ID specified: 0d

```

I don't think that has to do with my problem though. Angel runs fine excepting the clipboard integration problem.

---

### Post by bodhi.zazen on 2006-12-07
See if this helps:

[http://appdb.winehq.org/appview.php?iAppId=531](http://appdb.winehq.org/appview.php?iAppId=531)

---

### Post by jpolanco on 2006-12-07
Nope, that's still not working. Actually I had tried that before but it doesn't work, at least on the most recent versions of angel. Anyway, thanks for helping...

---

### Post by bodhi.zazen on 2006-12-07
Sorry M8 :(

---

