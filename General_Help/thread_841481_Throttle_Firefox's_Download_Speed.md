---
title: "Throttle Firefox's Download Speed?"
date: 2008-06-26
forum: General Help
---

### Post by dorkdork777 on 2008-06-26
After recently opening a premium account with RapidShare, I have been downloading quite a bit - all the downloads are very quick, at my line speed much of the time. However, I now have the problem that they are too quick - other people using my network are complaining that their Internet connection is much more sluggish than before.

So, does anyone know of a way to throttle Firefox's speed - or perhaps my entire connection's speed - to 350kbps? I'd prefer a graphical app that can easily run in the background, though command-line apps are still fine!

Thanks a lot!

---

### Post by cariboo on 2008-06-26
Here is something that looks like what you are looking for. Unfortunately you will have to compile the program your self, but there is a gui frontend for it.

Source code:

[http://aria2.sourceforge.net/](http://aria2.sourceforge.net/)

Gui frontend:

[http://www.aria2fe.com/](http://www.aria2fe.com/)

Read the documentation for aria2 to compile, aria2fe is alraedy compiled, just copy it to /usr/bin or /usr/local/bin.

Jim

---

### Post by dorkdork777 on 2008-06-26
That's certainly an option - however, I'm very happy with DownThemAll + Firefox to manage my downloads, and it's all working perfectly and easily at the moment. Adding another independant app to manage my downloads would complicate this a lot more (I've got it set up so that I can just highlight the links, right click, select 'DtA OneClick', and it will do everything else automatically, including setting the username and password, putting it into the right directory, etc).

If there is some way to get Aria2 to do this, then I'd have no hesitations in switching to it - but really, all I need is one app to throttle Firefox's bandwidth.

---

### Post by dorkdork777 on 2008-06-30
bump

---

### Post by orawax on 2008-12-31
> **dorkdork777 said:**
> So, does anyone know of a way to throttle Firefox's speed

There's an experimental plugin for this purpose, but it's only available for Windo$€. Perhaps you could consider installing Firefox in Wine until the plugin is also available for Linux (if ever).

[https://addons.mozilla.org/en-US/firefox/addon/5917](https://addons.mozilla.org/en-US/firefox/addon/5917)

---

