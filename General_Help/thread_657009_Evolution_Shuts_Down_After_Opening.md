---
title: "Evolution Shuts Down After Opening"
date: 2008-01-03
forum: General Help
---

### Post by Maupertus on 2008-01-03
Hi everybody,

I really hope you can help me with this problem as it's driving me mad and I have no idea why it is happening.

When I open Evolution by clicking on it, it opens for about three seconds, and then shuts down again.
I have no idea why and I don't get any message telling me why.

Please, if anybody has any idea why this is happening, help me, because after a day of this and a couple of reboots, I'm a little bit frustrated. I haven't done anything to Evolution in the past weeks, so sorry for the meager information, but if I can do anything to get more info, please tell me.

Thanks,

---

### Post by kpkeerthi on 2008-01-03
Launch evolution for terminal. You should see some messages printed to the console when it crashes. Might provide you some clue.

---

### Post by Maupertus on 2008-01-03
> **kpkeerthi said:**
> Launch evolution for terminal. You should see some messages printed to the console when it crashes. Might provide you some clue.

[QUOTE=Console]CalDAV Eplugin starting up ...
evolution-shell-Message: Killing old version of evolution-data-server...
RSS Plugin enabled
RSS Plugin enabled
Loading Bogofilter as the default junk plugin
** (evolution:6257): DEBUG: mailto URL command: evolution %s
** (evolution:6257): DEBUG: mailto URL program: evolution
Reading RSS articles...
Segmentation fault (core dumped)[/QUOTE]

This is what console gives me.
Is there something wrong with the RSS feeds?

I noticed that there is no problem when I have no internet connection.

---

### Post by kpkeerthi on 2008-01-03
May be. Is there a **.evolution** folder or something in your $HOME. Delete it (or rename with **mv .evolution .evolution_backup**) and see if it helps. Restore the folder back if required later.

---

### Post by Maupertus on 2008-01-03
> **kpkeerthi said:**
> May be. Is there a **.evolution** folder or something in your $HOME. Delete it (or rename with **mv .evolution .evolution_backup**) and see if it helps. Restore the folder back if required later.

Did it and the problem still occured.

However, after your "May Be" I shut down all RSSfeeds after disabling my connection.
I re-opened the connection and Evo kept running.
After closing each connection one by one, I came to the conclusion that one feed was causing the problems....for Dutch Evolution users:

[http://feeds.feedburner.com/tweakers/mixed](http://feeds.feedburner.com/tweakers/mixed)

It's the tweakers.net rss feed that gives the problems. (It's a Dutch Tech site)

Thanks Kpkeerthi!

---

