---
title: "Starting services after bootup"
date: 2008-03-22
forum: General Help
---

### Post by randyrick on 2008-03-22
It seems I have to manually start services like SSH & networking after boot, not all the time but often.   Why aren't they being started during boot?  Has anyone else experienced this?

---

### Post by tvtech on 2008-03-22
yup you've got to set them to start on boot. you can do this graphically or... pop open a terminal 

username@localhost:~$gksu gedit /etc/rc.local

this is your boot script loader so you can manually set up boot scripts to start programs automatically it's quick easy and makes people happy.

---

### Post by kaivalagi on 2008-03-22
As tvtech rightly says, rc.local will do the job, and that's probably all you'll need to mess with. 

But there are alternative run levels you may want to pursue, take a look at this page on linux.com for more info:[ http://www.linux.com/feature/114107]("http://www.linux.com/feature/114107")

If nothing else, it will give you an insight into the workings of Linux run levels

Cheers

---

### Post by randyrick on 2008-03-22
Thanks!:)

I have "rcconf" installed but don't see all the services listed (like SSH).  How do I update it to see all the services in init.d, so I can select which to start?

---

