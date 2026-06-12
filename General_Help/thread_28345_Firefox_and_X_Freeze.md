---
title: "Firefox and X Freeze"
date: 2005-04-19
forum: General Help
---

### Post by tommy04 on 2005-04-19
Okay, I've been browsing the web lately, and randomly Firefox and X freeze, causing me to do a hard-reboot.

The URL behind this is here:
[http://www.arch0wl.com/phpBB2/viewtopic.php?t=1697&start=6600](http://www.arch0wl.com/phpBB2/viewtopic.php?t=1697&start=6600)
It might be the next page over (332)

Other URLs do the same thing. Can someone tell me if they are having the same problem? This has happened on that page 4 times.

---

### Post by Gandalf on 2005-04-19
[QUOTE=tommy04]Okay, I've been browsing the web lately, and randomly Firefox and X freeze, causing me to do a hard-reboot.

The URL behind this is here:
[http://www.arch0wl.com/phpBB2/viewtopic.php?t=1697&start=6600](http://www.arch0wl.com/phpBB2/viewtopic.php?t=1697&start=6600)
It might be the next page over (332)

Other URLs do the same thing. Can someone tell me if they are having the same problem? This has happened on that page 4 times.[/QUOTE]
 no it never quit i tried with 10 pages on that thread and nothing wrong!!

---

### Post by Fab on 2005-04-20
[QUOTE=tommy04]Okay, I've been browsing the web lately, and randomly Firefox and X freeze, causing me to do a hard-reboot.

The URL behind this is here:
[http://www.arch0wl.com/phpBB2/viewtopic.php?t=1697&start=6600](http://www.arch0wl.com/phpBB2/viewtopic.php?t=1697&start=6600)
It might be the next page over (332)

Other URLs do the same thing. Can someone tell me if they are having the same problem? This has happened on that page 4 times.[/QUOTE]
 i got exactly the same problem with all gecko based browsers (mozilla, firefox, galeon, epiphany)
for example, i can only access backports.ubuntuforums.org with lynx, lol sometimes specific threads in phpbb forums give me lockups, when i wget them and view the source i see nothing special
and the problem is reproducable
ive tried to create a new profile for firefox and test, its still the same
i dont have any extensions installed

---

### Post by Gustav on 2005-04-20
I had the same problem a while ago.

It seems to be related to the video acceleration. If you have a NVIDIA card you should change a line in /etc/X11/xorg.conf:

RenderAccel "true"

to:

RenderAccel "false"

The freezes have not occured since I did that.

---

