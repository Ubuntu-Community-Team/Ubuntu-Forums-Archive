---
title: "GNOME FreeBSD vs Ubuntu"
date: 2005-10-05
forum: General Help
---

### Post by darius_underhill on 2005-10-05
Hi I'm a user of ubuntu for around 6 months now and I really find it great.  However,  I am wonderin' if which would be faster a Freebsd system with GNOME or Ubuntu?

Anybody tried it yet?

---

### Post by pinoyskull on 2005-10-05
i was using freebsd desktop before but, i use KDE instead of Gnome, i was having a hard time configuring freebsd desktop, but i did it anyway and was using it for like, 6 months before i switch to Ubuntu, my recommendation use Freebsd for servers, its a pain in the arse for desktop usage, well, IMO only :)

---

### Post by ow50 on 2005-10-05
I agree that the FreeBSD installation is not quite designed for desktop use, but at least documentation (the handbook) is great.

I tried a FreeBSD 6.0 beta version about a month ago. Pretty much everything I tried in Gnome was broken. Epiphany's menus and toolbars didn't work. Changing the theme crashed the panels, and so on. Because of the major problems, I didn't get to test FreeBSD on the long run, but it didn't seem significantly faster.

The way I see it is that any possible minor performance increase is not even close to as important as all the work Ubuntu puts into providing a stable and complete Gnome desktop.

---

### Post by abhaysahai on 2005-10-05
FreeBSD is much faster.
I have used both KDE as well as Gnome on FreeBSD and it is simply a breeze. The reason I shifted to Ununtu was extreme difficulty in installing arla ( Openafs ) in FreeBD and lack of hibernate feature in FreeBSD.

---

### Post by skoal on 2005-10-05
Such comparisons are really subjective, IMSO (S = statistical).  I use freeBSD as well. If you honestly can tell me it's faster (_either_ way), then you'll probably try to convince me turning on AGPFastwrites and Sideband addressing in your video card driver shows a substantial difference too.  I've run various benchmarks showing (in that driver case), at best <2% - and that doesn't even translate to anything perceptible by the human eye.  It's just sugar placebo pillarefic! Same case here with platform/DE comparisons...

What should be of importance in your decision, IMHO, is how freeBSD grants you access to all the applications running on Gnome.  apt-get repos shine over ports, IMO, especially when trying to update a huge package set like Gnome (which I've done on freeBSD).

\\//_

---

### Post by darius_underhill on 2005-10-05
[QUOTE=skoal]Such comparisons are really subjective, IMSO (S = statistical).  I use freeBSD as well. If you honestly can tell me it's faster (_either_ way), then you'll probably try to convince me turning on AGPFastwrites and Sideband addressing in your video card driver shows a substantial difference too.  I've run various benchmarks showing (in that driver case), at best <2% - and that doesn't even translate to anything perceptible by the human eye.  It's just sugar placebo pillarefic! Same case here with platform/DE comparisons...
What should be of importance in your decision, IMHO, is how freeBSD grants you access to all the applications running on Gnome.  apt-get repos shine over ports, IMO, especially when trying to update a huge package set like Gnome (which I've done on freeBSD).
\\//_[/QUOTE]
Thanks for the info.  but I have a question, Isn't a matter of running portupgrade in updating? The main reason am asking this is because im trying to squeeze every last bit of performance from my NEO m350 laptop (1.5 GHz Celeron 384MB RAM).  I already have a lot of experience in managing a FreeBSD server.
Another question, does apt-get provide a way to compile from sources? just like Ports??  And does compiling from scratch provide better overall performance?  This is the main reason why I want to use FreeBSD.

---

### Post by 23meg on 2005-10-05
[QUOTE=darius_underhill]Thanks for the info.  but I have a question, Isn't a matter of running portupgrade in updating? The main reason am asking this is because im trying to squeeze every last bit of performance from my NEO m350 laptop (1.5 GHz Celeron 384MB RAM).  I already have a lot of experience in managing a FreeBSD server.
Another question, does apt-get provide a way to compile from sources? just like Ports??  And does compiling from scratch provide better overall performance?  This is the main reason why I want to use FreeBSD.[/QUOTE]
sure, just add deb-src lines to your sources.list and you get the sources beside the binaries as well. compiling from your source is likely to result in better performance only if you have the knowledge to optimize the compilation process to make the apps work the best with your cpu. and whether or not you'll feel that difference in practical use is another matter. ubuntu supports only three cpu architechtures (i386, amd64, ppc) and recompiles every debian package from source to optimize for general use on these architechtures, so the packaged binaries themselves are quite optimized as well. 

if you know your way around compilation, and you want linux instead of freebsd, you may want to look at a source based linux distro such as gentoo.

---

### Post by IcemanV9 on 2005-10-06
I have dual-boot with fbsd 6.0BETA4 & hoary on hp laptop. Freebsd with Gnome responds faster than Hoary. I agreed with others that FreeBSD is the best for servers AND Hoary for the desktop use.

On FreeBSD, compiling apps, such as OOo2, Gnome, java, Firefox and so on, from the ports collection took forever! On Ubuntu, it's ready to be use once you use 'apt-get install' command (and it leaves more hair on my head ;)).

---

### Post by unc0nn3ct3d on 2008-07-11
Does FreeBSD offer automatic system-wide updates the same way that Ubuntu does?  That is another nice big feature that should be taken into consideration IMUO (U = Useless)

---

