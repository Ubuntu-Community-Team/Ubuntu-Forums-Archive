---
title: "/etc/apt/sources.list help"
date: 2008-05-06
forum: General Help
---

### Post by Twitch6000 on 2008-05-06
well I tried fixing my avant windows navigator problem with a tutorial and I made a few mistakes from me being to fast.
I ended up adding things not needed in the /etc/apt/sources.list.
I removed everything except some random thing that will not remove.
I tried going in it by actually going into it and just backspacing and it said permission denied.So help?
I know if I can fix this I can fix my other problem =[.

---

### Post by alan34 on 2008-05-06
In a terminal to copy to a backup

sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup

to edit

gksudo gedit /etc/apt/sources.list

to restore backup

sudo cp /etc/apt/sources.list.backup /etc/apt/sources.list

---

### Post by aysiu on 2008-05-06
Read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Twitch6000 on 2008-05-06
Problem solved thank you both =].

---

