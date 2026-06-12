---
title: "Cannot disable auto login"
date: 2013-03-21
forum: General Help
---

### Post by rdh61 on 2013-03-21
During installation of Lubuntu 12.04 I chose to enable auto login.

Now I cannot disable it. In user settings it says password: asked at login. The "don't ask for password" checkbox is not checked. Also, I have commented the autologin line (line 2) in [COLOR=#333333][FONT=inherit]/etc/xdg/lubuntu/lxdm/lxdm.conf.

Yet the system will not ask me for my password at login, but boots straight to my desktop.

How can I fix this?

Many thanks.[/FONT][/COLOR]

---

### Post by rdh61 on 2013-03-22
The solution was to delete my username (leaving username blank) from the line "autologin-user=username" in /etc/lightdm/lightdm.conf.

[http://askubuntu.com/questions/106428/how-to-disable-automatic-login](http://askubuntu.com/questions/106428/how-to-disable-automatic-login)

So why the **** does "System Tools" -> "Users and Groups" -> "Password: Asked on login" not work? 

What a waste of time. Another fail.

---

