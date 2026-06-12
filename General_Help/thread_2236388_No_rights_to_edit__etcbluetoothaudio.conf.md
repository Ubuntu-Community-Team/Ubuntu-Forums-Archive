---
title: "No rights to edit  /etc/bluetooth/audio.conf"
date: 2014-07-26
forum: General Help
---

### Post by rob70hoeben on 2014-07-26
Hi..

I want to edit /etc/bluetooth/audio.conf but i get the message that it is read only and I don't have rights.  How can I edit the file neverthelss?

Greets,  Rob

14.04

---

### Post by rob70hoeben on 2014-07-26
Sudo

---

### Post by coldcritter64 on 2014-07-26
> **rob70hoeben said:**
> Sudo

Note linux is case sensitive ... "sudo". If using a graphical text editor use gksudo or gksu. See the link in my sig "Rootsudo documentation" in the "Graphical sudo" section for the reasons why.

@ OP put gksudo before your command, if using gedit the command would be ...

```
gksudo gedit [COLOR=#333333][FONT=UbuntuRegular]/etc/bluetooth/audio.conf[/FONT][/COLOR] 
```

Edit: just noted the OP was replying to his own post, LOL. Others reading should note the graphical sudo practice of using gksudo or gksu.

---

