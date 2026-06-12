---
title: "&quot;åäö&quot; doesn't work in terminal, and the default encoding is weird."
date: 2007-11-17
forum: General Help
---

### Post by minus198 on 2007-11-17
I just noticed that I can't type the Swedish characters 'åäö' in terminal. So when I tried to digg in to the problem, I noticed that I had a really weird encoding: ANSI_X3.4-1968.

So I tried to change it by doing: "dpkg-reconfigure locales" but it just gave me the current locales, and I couldn't choose new locales.

[http://pastebin.ubuntu.com/2056/](http://pastebin.ubuntu.com/2056/)

So the main question is: How do I change my locale?

---

### Post by minus198 on 2007-11-17
Anyone?

---

### Post by jamvegan on 2007-11-17
I think that if you edit /etc/environment, and change the following two lines to this:
```
LANG="en_US.UTF-8"
LANGUAGE="en_US:en"
```
you should be set (after, perhaps, rebooting).  Those are the entries that I have, and I have no problem with those characters in terminal.  (I should think that en_GB.UTF-8, or whatever UTF-8 locale is appropriate to wherever you live would work, as well.)

Caveat: I have not tried changing the default locale this way, but it seems like this should be all you need to do, since you have this locale installed already.

---

### Post by minus198 on 2007-11-17
I'll give it a shot.

I'll bring a report soon. :)

Edit: Nope.. That didn't solve it.

---

### Post by minus198 on 2007-11-18
Anyone? There must be a way to change the locales, right?

---

### Post by googlah on 2007-12-06
I'm also looking for a way to do it. Same issue as you man. :(

---

