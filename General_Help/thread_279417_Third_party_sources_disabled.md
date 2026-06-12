---
title: "Third party sources disabled"
date: 2006-10-17
forum: General Help
---

### Post by Jordan Meeter on 2006-10-17
I got this error while upgrading to Edgy Eft:

[[IMG]http://aycu09.webshots.com/image/4608/2003331604041925670_th.jpg[/IMG]](http://allyoucanupload.webshots.com/v/2003331604041925670)

How can this be resolved?

---

### Post by mssever on 2006-10-18
I haven't switched to Edgy yet, but i'm guessing that you should open your sources.list (gksudo gedit /etc/apt/sources.list) and uncomment any lines that you think you still need. change any occurances of "dapper" to "edgy".

---

### Post by DarkN00b on 2006-10-18
That's not an error. It is just telling you that it had to temporarily disable some non-official repositories that you have in your sources.list. You can re-enable them after the upgrade by editing sources.list (they should be commented out) or checking them in Synaptic.

---

