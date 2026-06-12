---
title: "&quot;System program problem detected&quot; message on startup"
date: 2016-10-30
forum: General Help
---

### Post by Tom_Carr on 2016-10-30
When I start my computer running ubuntu 16.04 I get several message  boxes saying "System program problem detected".
When I then click the "report problem" button I get another box that lets me show the details.
The problem is always something about an executable path, but  to lots of different places, such  as 
apport-gtk
something in genome
other things I can't remember or get to come up now.

What is going on?  How can I fix it.

The system seems to be running fine.

---

### Post by asgard2 on 2016-10-30
To get rid of the apport messages:

Remove crash logs:
```
sudo rm /var/crash/*
```

Reappear these messages after a reboot?

You can deactivate apport, change the value to **enabled=0 **in:
```
sudo nano /etc/default/apport
```

But these errors maybe need fixing, you should provide more information.

---

### Post by Tom_Carr on 2016-10-30
> [COLOR=#000000]But these errors maybe need fixing, you should provide more information.[/COLOR]

I gave all the information that the boxes gave me.  How do I get more information?

---

