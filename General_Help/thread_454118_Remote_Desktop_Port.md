---
title: "Remote Desktop Port?"
date: 2007-05-25
forum: General Help
---

### Post by Znupi on 2007-05-25
How can I change the Remote Desktop port? I get lots of attacks on 5900, just the other night I had it set to 'Ask for my permission' and suddenly I got 10 or so dialogs saying 'someone is trying to view your desktop'. So I turned off, and a couple of days later turned it back on, this time with a password set. The thing is, I left it like that for a while and when I came back, my desktop was moving in steps, just the way it happens when someone is connected to my remote desktop. The thing is, there was no icon in the tray to indicate that. So I turned off Remote Desktop and everything was back to normal in a minute.

Conclusion: to get rid of these attacks, I want to change my RD port. How can I do it?

---

### Post by Znupi on 2007-05-25
bump. No one? :|

---

### Post by Znupi on 2007-05-26
bump. There must be a way :(

---

### Post by robbiewalter on 2007-05-28
Within gconf-editor,

look for keys *alternative_port* and *use_alternative_port* in 

**/desktop/gnome/remote_access**.

I've been looking for this same option for some time. I discovered that the desktop sharing process is called "vino", which led me to this page.

[http://www.bani.com.br/2007/04/25/hidden-features-of-vino-remote-desktop-access/]("http://www.bani.com.br/2007/04/25/hidden-features-of-vino-remote-desktop-access/")

---

### Post by Znupi on 2007-05-28
Thanks a lot! :)

---

