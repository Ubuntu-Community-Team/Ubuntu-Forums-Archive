---
title: "Sudden GUI display issues"
date: 2013-06-03
forum: General Help
---

### Post by cyanide911 on 2013-06-03
[Ubuntu 12.04 64bit)

I'm having some sudden rendering issues.

As you can see, chrome looks very ugly (notice the thick border around the URL bar and beneath the tab bar and the buttons), and Gnome 3 'overview' looks ugly as well, with no backgrounds at all for some reason.
[IMG]http://i.imgur.com/mwCph09.png[/IMG]

[IMG]http://i.imgur.com/gILuPpf.png[/IMG]

PS: Because of a dependency of something I was working on, I *did* have to upgrade [COLOR=#444444][FONT=Consolas]gtk+-3[/FONT][/COLOR] forcefully to version 3.6.2, from some PPA because officially 12.04 had updates till 3.4.x only. Not sure if this might be cause by that.

---

### Post by Hekabe on 2013-06-03
It's probably related to the fact that you're using a slightly incompatible package for GTK. Any specific reason you can't upgrade to 12.10?

---

### Post by 25tom on 2013-06-03
I get a non-transparent black dash in Unity a bit like your 'overview' screen if compositing has been turned off for Metacity...

Hope this tidbit of info helps with that particular aspect of the problem :)

---

