---
title: "instances crash .. but processes remain in background"
date: 2013-01-19
forum: General Help
---

### Post by dragonfly41 on 2013-01-19
I have an annoying quirk on Ubuntu 12.04 where I'm running firefox and komodo editor .. with quite a few tabs open in firefox .. but suddenly on some event both firefox and komodo windows disappear .. but are still shown as background processes.

If I run 
[COLOR=Navy]pidof firefox
11971 4225[/COLOR]

this shows the firefox id's
 
and then
[COLOR=Navy]sudo kill -9 11971 4225[/COLOR]
kills both firefox instances (one firefox instance is a komodo editor previewing localhost apps under development)

same applies with komodo editor
[COLOR=Navy]pidof komodo
5082
sudo kill -9 5082
[/COLOR]
I then have to restart
 firefox (which shows as a crashed session to restore) 
and komodo editor.

How can I pin down the root cause to avoid restarting these crashed apps?

---

### Post by dragonfly41 on 2013-01-21
Does this clue seen in command terminal point to any error?

> QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.

---

