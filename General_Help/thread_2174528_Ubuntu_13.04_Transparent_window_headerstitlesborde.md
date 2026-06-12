---
title: "Ubuntu 13.04 Transparent window headers/titles/borders"
date: 2013-09-15
forum: General Help
---

### Post by eru2 on 2013-09-15
Hello everyone,

This will be my first post on these forums and I hope that I have an easy question for the community.

I've recently installed ubuntu 13.04 64-bit on my laptop and have been configuring it over the last 24 hours. So far it has been a breeze since I this is not my first venture into Ubuntu but I think it will be my first permanent installation.

So far I've just been configuring aesthetics and what I'm trying to achieve is to make the black, brown, grey, I don't really know what color it is, bar at the top of each window transparent. I am amazed that there is no simple transparency option for this like there is for the launcher.

 When I've googled how to do this I find a few tutorials that use the gconf-editor however I must insist that there are no options to change the transparency in my window. The closest tutorial that I have found uses the dconf-editor. When I change the metacity-theme-active-opacity and inactive-opacity options, as the tutorial says it, doesn't simply make the bar transparent. It makes the text transparent as well which makes using the window a pain.

Is there anyone that has achieved a satisfying tranparent effect for the bar at the top of their windows in 13.04?

Thank you very much for reading this [IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG]

---

### Post by maestrobwh1 on 2013-09-15
I have not seen the option for the top bar being transparent as of yet on Unity.  You might try "Ubuntu Tweak" and/or Unity Tweak but I have both and I don't see a way with those.  I have done it in LXDE and KDE with no issue.

---

### Post by stinkeye on 2013-09-16
Hi eru2,

Open dconf-editor @ org.compiz.gwd 
for some window decoration options.
[COLOR="#FF0000"]EDIT[/COLOR] I see you already tried this.
You need to set the metacity theme active opacity but keep the Active shade opacity enabled
to see the text.

You could also install the **emerald** window decorator which has more options.
Emerald needs to be installed from a ppa.
[**_[COLOR="#B22222"]How To Install Emerald In Ubuntu 13.04[/COLOR]_**]("http://www.webupd8.org/2013/05/how-to-install-emerald-in-ubuntu-1304.html")
If you do use the ppa I would disable it in **Software and Updates** after installing emerald as the
ppa contains a lot more applications besides emerald.

---

### Post by lveitas956 on 2014-04-18
Hey, do you know any alternative, which would work on ubuntu 14.04 (64bit)? I mean something, that will be able to get transparency, too. Thanks a lot.

---

