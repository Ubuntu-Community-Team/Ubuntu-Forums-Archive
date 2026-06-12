---
title: "azureus hangs when adding torrent"
date: 2007-11-05
forum: General Help
---

### Post by roythomas on 2007-11-05
Whenever Azureus is run all is OK until I try to add a torrent either using the menus or drag & drop. Azureus has been sucessfully updated (using auto update) and this problem did not happen until I upgraded to Ubuntu to 7.10.

I believe this is an established bug associated with Java (which is installed) or some software library version - but, sorry, I can't find how to fix it.

Thanks for your time, Rgds. Roy

---

### Post by por100pre1 on 2007-11-06
This is a common issue with Azureus. Sometimes to use the latest Sun Java fixes the issue, sometimes renaming your settings fixes the issue:

```
mv .azureus .azureus_backup
```

I just use Deluge. If using Gutsy do this:

```
sudo aptitude install deluge-torrent
```

If using Feisty check [this]("http://deluge-torrent.org/downloads-ubuntu").

---

