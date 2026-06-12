---
title: "Why is my Partial Distro upgrade not working?"
date: 2007-07-09
forum: General Help
---

### Post by Protagonistics on 2007-07-09
I'm getting an error when I use Update Manager. I'm trying to do a partial Upgrade which I'm assuming a lot of people are doing right now because it's a distribution upgrade. I DID just reinstall Ubuntu 7.04 so who knows. Regardless, I'm getting an error stating that I cannot update some very basic  and well-repositoried packages (like Pidgin) because there may be "transient network problems." Do I have to do something here or should I do what it says and try again later? Automatix isn't working quite right either. it says it can't download some packages...

thanks

---

### Post by loserboy on 2007-07-09
you should look at the automatix forums on info about that, I know that you're suppose to uninstall automatix before doing the version upgrade and also remove the sources that it added otherwise it could cause problems with the upgrade (there is instructions on the AX site)

---

### Post by Protagonistics on 2007-07-10
Ok, for the love of mike. can someone explain this to me? every time I try to do my "partial upgrade" through Update manager, ALL of these package downloads fail. here is the text of the window I get.



Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.

compiz
compiz-core
compiz-gnome
compiz-plugins
gaim
libtotem-plparser7
pidgin
pidgin-data
rhythmbox
totem
totem-gstreamer
totem-mozilla


I don't get it. is there some way I can get a terminal output of this to see what specifically is blocking these upgrades?

---

