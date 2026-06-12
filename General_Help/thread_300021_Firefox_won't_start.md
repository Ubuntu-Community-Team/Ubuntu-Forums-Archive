---
title: "Firefox won't start"
date: 2006-11-15
forum: General Help
---

### Post by RyanGRA on 2006-11-15
I was having trouble getting Firefox 2.0 to install correctly. For whatever reason the new version wouldn't load. It would load the older version. So I got the bright idea that I would uninstall the old version and do a clean install of 2.0. I used the command 'apt-get remove firefox'. Well to my surprise not only was the old firefox uninstalled but a few other packages as well including one that itegrates Firefox with Gnome. So I try to reinstall firefox 'apt-get install firefox'. Only firefox installs, not the other packages. Next I try to install 2.0 with a script from this website [http://everythingelse.wordpress.com/2006/07/15/howto-install-firefox-20-bon-echo-in-ubuntu/]("http://everythingelse.wordpress.com/2006/07/15/howto-install-firefox-20-bon-echo-in-ubuntu/") Now when I start Firefox 2.0 starts. Sounds good right? Well here's the kicker. If I close Firefox and then try to reopen I get an error message telling me that a version of Firefox is already running and it cannot open Firefox. The only way I know of to fix it is to reboot. To make matters worse this is on my drive for school and I really don't want to explain to my teacher what is going on as I was supposed to be paying attention to his lecture when this all happened. Is there any way to resolve this problem short of reinstalling Ubuntu? By the way this is my first post on the forum, I hope I explained my problem enough. Thanks.

---

### Post by Paul41 on 2006-11-15
Try:
```
apt-get -f install
```
This fixes dependency problems.

---

### Post by RyanGRA on 2006-11-15
thanks, but the problem seemed to fix itself when I booted up today.

---

### Post by dweez on 2006-11-15
Wow, sounds like an MS fix.

---

