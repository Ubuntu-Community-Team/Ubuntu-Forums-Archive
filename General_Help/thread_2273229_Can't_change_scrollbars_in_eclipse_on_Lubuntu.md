---
title: "Can't change scrollbars in eclipse on Lubuntu"
date: 2015-04-11
forum: General Help
---

### Post by Matthew_Bird on 2015-04-11
Hey all!

I'm trying to set up eclipse properly on my tiny netbook so I can get work done on the go. Everything is fine, but I can't remove the white scroll bars (which show even if the page isn't large enough to need them, and cut my already-small screen size down).

Here's a screenshot to give an insight into my visual pain: [http://imgur.com/fDcHpQG](http://imgur.com/fDcHpQG)

I want the white scroll bars replaced with the sleek orange-line scroll bars I use on my desktop version of eclipse. Failing that, I'd rather have no scroll bar at all, or a thin dark one.

I had the same problem on my desktop version of eclipse, on ubuntu, and I added **LIBOVERLAY_SCROLLBAR=1** to the eclipse launch (originally added it on the terminal, then added it to the .application file). But doing this for my lubuntu version of eclipse doesn't work. Does anyone know whether this is a specific difference between ubuntu and Lubuntu? 

The eclipse version on Lubuntu is 32 bit. I guess that won't make a difference?

Really appreciate your help!

---

### Post by Matthew_Bird on 2015-04-11
OK, so I've been researching into this. Overlay scroll-bars aren't a lubuntu thing. You can install a package which gives you them ([http://www.techques.com/question/24-141150/Is-it-possible-to-use-Overlay-Scrollbars-in-Lubuntu](http://www.techques.com/question/24-141150/Is-it-possible-to-use-Overlay-Scrollbars-in-Lubuntu)) but it only works in some programs, and I've no idea how to get it to work in eclipse.

So my new question: can I remove the lubuntu scroll bar for a specific program, or failing that, how can I customise the lubuntu scroll bar, preferably only for a specific program?

Thanks!

---

### Post by Holger_Gehrke on 2015-04-11
The overlay-scrollbars use/manipulate GTK. Eclipse is a java program written with SWT, which uses GTK in a *slightly* different way than a native application would. With overlay scrollbars, it tends to become unstable or produce broken visuals. For that reason it's blacklisted from using overlay-scrollbars. According to a [thread on the LXDE Forum]("http://forum.lxde.org/viewtopic.php?f=8&t=31638"), it should be possible to change the width of the scrollbars in a GTK-Theme. Whether Eclipse will honour these settings is anybody's guess.

---

### Post by Matthew_Bird on 2015-04-11
Thanks for your reply, Holger_Gehrke! 

I've tracked down how I can modify the width of the scrollbars in the GTK2 theme that eclipse uses. And it does kinda work - setting the width to 0 converts them into a quite a lot thinner white line. But the downside is that I then have 0-width scrollbars for every GTK2 application! Is there any way to make the width different *just for eclipse*? 

Thanks again!

---

