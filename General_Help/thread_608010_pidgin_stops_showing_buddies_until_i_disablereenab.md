---
title: "pidgin stops showing buddies until i disable/reenable account"
date: 2007-11-09
forum: General Help
---

### Post by mykmelez on 2007-11-09
Since upgrading to Gutsy (and thus from Gaim to Pidgin), my buddy list sometimes goes blank and stays that way until I first disable and then reenable my accounts (AIM and Jabber).  Afterwards, everything works fine for a while, and then the list goes blank again.

I think the blanking happens when I change locations, putting my laptop to sleep at the old location (which also drops network connections) and then waking it up at the new one.  So perhaps this is network-related.

I tried disabling all plugins and restarting, but that didn't help.  I'm using Pidgin 2,2,1, which came with Gutsy, and before that I was using the version of Gaim that came with Feisty.

I did have to copy a file from ~/.gaim to ~/.purple when I first upgraded to get my buddy list working at all.  I think it was blist.xml, the file that stores the buddy list.  But it worked after that, and ~/.purple/blist.xml looks like a valid (and updated) Purple buddy list file.  And of course everything works fine after I disable/reenable the accounts, so this doesn't seem related to that earlier problem.

Does anyone know what the problem is and how to fix/work around it?

---

