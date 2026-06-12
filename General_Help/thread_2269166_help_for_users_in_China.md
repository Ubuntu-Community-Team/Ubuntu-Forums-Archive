---
title: "help for users in China"
date: 2015-03-13
forum: General Help
---

### Post by Pedroski55 on 2015-03-13
Many many web pages have google links. If you access the web in China, these links will slow, sometimes to a stop, the load speed because China doesn't like google. To get around this:

sudo gedit

open /etc/hosts

  add this in there (don't get rid of what is already there)

127.0.0.1 [www.googlesyndication.com]("http://www.googlesyndication.com")
127.0.0.1 [www.google.com]("http://www.google.com")
127.0.0.1 [www.gstatic.com]("http://www.gstatic.com")
127.0.0.1 [www.google-analytics.com]("http://www.google-analytics.com")
127.0.0.1 gstatic.com
127.0.0.1 google.com
127.0.0.1 ajax.googleapis.com
127.0.0.1 apis.google.com
127.0.0.1 google-analytics.com
127.0.0.1 googlesyndication.com
127.0.0.1 fonts.googleapis.com
127.0.0.1 pagead2.googlesyndication.com
127.0.0.1 googleads.g.doubleclick.net
127.0.0.1 accounts.google.com

Just a tip! I added the last line today, because mdbg.net was either not loading, or loading extremely slowly. Now it loads great!

---

### Post by TheFu on 2015-03-14
Please read this: [http://ubuntuforums.org/showthread.php?t=2269093](http://ubuntuforums.org/showthread.php?t=2269093) - why you shouldn't recommend **sudo gedit**.

---

