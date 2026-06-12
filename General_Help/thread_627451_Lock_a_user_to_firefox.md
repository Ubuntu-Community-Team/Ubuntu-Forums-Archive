---
title: "Lock a user to firefox"
date: 2007-11-30
forum: General Help
---

### Post by xirian on 2007-11-30
I've been searching for hours and I believe this has probably been covered but I must just be bad with search terms.

I'm trying to make a user that basicly when they log in, it launches firefox and only firefox. Then I'd like it so if they exit firefox, it automaticly logs the user out and goes back to the login screen.

---

### Post by geirha on 2007-11-30
> **xirian said:**
> I've been searching for hours and I believe this has probably been covered but I must just be bad with search terms.

I'm trying to make a user that basicly when they log in, it launches firefox and only firefox. Then I'd like it so if they exit firefox, it automaticly logs the user out and goes back to the login screen.

When you start an X session, you must run an application with it. Usually that application is a desktop environment or window manager (like Gnome or fluxbox). You can run any application, but unless it has window manager features, it won't have window borders and there's no way to resize the window, but otherwise it will behave as you want. If you add /etc/X11/sessions/firefox.desktop with the following content:
```
[Desktop Entry]
Encoding=UTF-8
Name=Firefox
Exec=/usr/bin/firefox
Icon=
Type=Application

```

You will be able to choose firefox as a session on the login screen, which will launch firefox, and only firefox (and close the session when you close firefox). 

I'm just telling you it's somewhat possible, but it's not something I would recommend doing. A proficient user will no doubt be able to run other applications anyway, you have to customize ubuntu quite considerably to have it the way you want.

---

### Post by xirian on 2007-11-30
Thanks for the response, that worked perfectly. I understand its trivial to get a normal desktop as is, but I mainly wanted it for when I let my friend check his email, I'd like to keep him out of his files, but I know he wont think to touch the sessions button.

---

