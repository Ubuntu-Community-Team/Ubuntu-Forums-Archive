---
title: "Thunderbird eMail client issue"
date: 2006-08-27
forum: General Help
---

### Post by dbonline on 2006-08-27
I'm hoping someone here can help me. I'm sure it's just a minor adjustment that's required, but for some reason when I receive eMail in Thunderbird, go to click a link in that eMail, absolutely nothing happens? does anyone here know why that would be? for example, if I have a confirmation link I have to copy and paste the URL in my browser which makes absolutely no sense at all.

---

### Post by GadgetsGuy on 2006-08-27
Hmmmm .... I know the fix for windows - involves deleting a registry entry - but have not encountered this issue in Ubuntu.

You might want to delete Thunderbird via Synaptic and then re-install it using Automatix. Cant hurt any .. ;)

(be sure to backup/export your mailbox before doing this)

 

GG

---

### Post by yopnono on 2006-08-27
> **dbonline said:**
> I'm hoping someone here can help me. I'm sure it's just a minor adjustment that's required, but for some reason when I receive eMail in Thunderbird, go to click a link in that eMail, absolutely nothing happens? does anyone here know why that would be? for example, if I have a confirmation link I have to copy and paste the URL in my browser which makes absolutely no sense at all.

Make sure that your browser is setup as default in preferred applications.

System - Preferences - preferred applications

---

### Post by arnieboy on 2006-08-27
do this:
in thunderbird go to edit--> preferences-->Advanced-->Config Editor
and change the Value of the following options to "firefox" minus quotes:
> network.protocol-handler.app.https
network.protocol-handler.app.http

---

