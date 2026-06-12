---
title: "[SOLVED] Glib &amp;amp; White boxes Everywhere"
date: 2008-04-14
forum: General Help
---

### Post by nowshining on 2008-04-14
SOLVED: RAN (u need to be root in terminal either sudo /bin/bash or open up a root terminal)

```
pango-querymodules > '/usr/local/etc/pango/pango.modules' 
```EDIT: okay it seems to be a bug in PANGO not Glib so all is fine there except for the sqare box problems for letters..

"http://developer.imendio.com/node/182" & "http://lists.opensuse.org/opensuse-factory/2007-12/msg00254.html"

i'm trying to install jpilot from source (asked to install it from source from a jpilot dev. as I submitted a bug and he said he fixed it and try it out on the updated source) - had to update pango, glib, etc before trying to update gtk, etc....

all was well except for one last thing, I found out that I had to run ldconfig to get the new libraries setup as default, ran that and Now everything that depends on glib has white boxes and no text. If I go to remove the ol' glib it wants to remove everything that depends on it such as openoffice, pidgin, wireshark, etc..

Also did all of that and gtk won't still install. :/

anyway... here is a sample from synaptic.

The Q is how do I fix this?

[[IMG]http://img224.imageshack.us/img224/6128/charissuemf6.png[/IMG]]("http://imageshack.us")
By [nowshining]("http://profile.imageshack.us/user/nowshining")


Other Than that no major problems.

edit: and yes I did try a soft reboot.

---

