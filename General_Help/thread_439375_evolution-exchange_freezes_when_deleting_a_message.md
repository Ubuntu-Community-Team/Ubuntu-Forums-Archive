---
title: "evolution-exchange freezes when deleting a message"
date: 2007-05-10
forum: General Help
---

### Post by elofland on 2007-05-10
Ok, environment:
Feisty (all patches), evolution 2.10.1, evolution-exchange, (with and without) beryl, exchange 2003 sp2

I can start evolution, it connects to the owa server, scans and downloads headers.  I can even read, reply, create, etc messages - but when I delete a message the application freezes and I can't do anything but kill it.

I'm curious if anyone else is experiencing this problem or if anyone may have a solution.  

TIA,
Eric

---

### Post by dwinter3 on 2007-05-14
This happens to me as well, but if I wait for like 10 minutes it eventually comes back and has all the messages deleted. It does not seem to matter if I am deleting one or 100 messages, it pretty much takes almost 10 minutes. After I have gone through that initial delete and waiting period, I can operate normally until I close and re-open evolution. Then the first time I try to delete, I have to wait. 

I am not familiar with evolution enough to know how to turn on any debugging so if someone is I would appreciate it.

---

### Post by elofland on 2007-05-14
Thanks for the heads up, the first delete took over an hour and afterwards everything looked normal.  Now when I restart evolution the initial delete takes a couple of minutes and then back to normal.  Weird.  

I was hoping to get some debugging info too, I don't know where else to report this.

/me <-- ubuntu newbie

---

### Post by dwinter3 on 2007-05-14
I am trying some of this stuff to debug, but I am not getting anything useful.

[http://www.gnome.org/projects/evolution/bugs.shtml](http://www.gnome.org/projects/evolution/bugs.shtml)

---

### Post by lfjewett on 2007-10-21
I have noticed this exact same problem and it's been around since Fiesty.  I was hoping it would go away when I upgraded to Gutsy but alas no love.  Does anybody have a fix for this, or is there any information we could provide to help along a fix?

---

### Post by ari on 2008-02-13
This actually seems to happen because Evolution is waiting to get the entire list of messages in Deleted Items before it deletes any messages. Before you delete anything, if you click on Deleted Items and make sure it's up to date first (which may freeze evolution for a few seconds while it syncs up), deleting messages seems to work normally. It helps if your Deleted Items folder is not enormous.

---

