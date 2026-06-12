---
title: "Working replacement for mysql-admin?"
date: 2013-04-15
forum: General Help
---

### Post by The Cog on 2013-04-15
Is there a working replacement for mysql-admin available for Ubuntu? 

I just wasted 3-4 hours with mysql-workbench which seems incapable of granting schema priviledges to users (although it shows that it has). I finally got a windows user to do it for me with mysql-admin, but mysql-admin doesn't seem to be available in the Ubuntu repos any more.

If I have to I'll use mysql-admin in windows in a VM, but it seems rather strange that  such a solution should be necessary.

---

### Post by slickymaster on 2013-04-15
Have you tried [DBSchema]("http://www.dbschema.com/download.html")?

It's an integrated universal database tool, featuring graphical layouts, Relational Data Browse, Query Builder, SQL Editor, schema deployment and synchronization. It has a downside as the free edition is limited to 12 tables and only some of the features will be active.

---

### Post by The Cog on 2013-04-16
> **slickymaster said:**
> Have you tried [DBSchema]("http://www.dbschema.com/download.html")?
I'll give it a try, thanks. 
But I would prefer an open-source piece of software if I could find one.

---

### Post by slickymaster on 2013-04-16
One other option could be [Navicat]("http://www.navicat.com/") for MySQL. It provides database administration and a development tool for MySQL. It works with any MySQL Database Server from version 3.21 or above, and supports most of the latest MySQL features including trigger, dtored procedure, gunction, event, view, and manage eser, etc. It's commercial, but there's a lite version available for free. Maybe worth a look at.

---

