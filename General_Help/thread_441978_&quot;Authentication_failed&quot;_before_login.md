---
title: "&quot;Authentication failed&quot; before login"
date: 2007-05-13
forum: General Help
---

### Post by Zece on 2007-05-13
Hi all,

I have autologin enabled for a user, but on startup, before the login screen appears, I see a black screen and a popup with the text "Authentication failed". When I click "Ok", I get to the login prompt but cannot edit the username to login. It looks like it is filled with 3 dots (...). The "Authentication failed" popup keeps popping up about 5 seconds every time I click "Ok" in it.

Though, I am able to login via ftp, so there seems to be no problem with the users as such.

I am also able to restart into safe console mode and act as root. Is there some way that I can disable the autologin function from the prompt, or are there any other solution?

---

### Post by Zece on 2007-05-13
Update: I've uninstalled GDM as well as xorg (don't really need them anyway, since it's on a server).

Still can't login though. Getting "Login failed" four times after I've entered my user name, but I can't even enter the password. Then it says: "Maximum number of tries exceeded (5)".

Any ideas?

---

### Post by zvacet on 2007-05-13
```
man -k login
```

That is all I can think of

---

### Post by Zece on 2007-05-15
Couldn't find a solution for this, so I reinstalled Ubuntu from scratch. backed up the conf files and I was back on track within an hour.

If anyone has an idea about what might has been going on, let me know.

---

