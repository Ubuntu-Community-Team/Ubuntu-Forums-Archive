---
title: "E17 customize menu"
date: 2007-02-20
forum: General Help
---

### Post by bestial on 2007-02-20
Have been foolin' around with this awesome windowmanager for about three weeks now and I'm starting to get somewhat of a clue how things works. Some modulethingies e.t.c. are still a mystery. But this thread will be about another subject.

On screenshots you'll see peoples nice customized menu's (not only the application menu's cause that I know how to do). I mean the first one you see when you leftclick on the screen. Originally it has submenus as "Configuration, Enlightenment, Windows e.t.c." and startes for example "Run Command". That's the menu I want to personalize, so, how do I do it?

Examples.

Here's some customized menu's,
[http://chneukirchen.org/blog/graphics/enlightenment.png](http://chneukirchen.org/blog/graphics/enlightenment.png)
[http://enlightenment.sourceforge.net/Enlightenment/Screenshots/DR17_User_Screenshots/_images/screenshot2.png](http://enlightenment.sourceforge.net/Enlightenment/Screenshots/DR17_User_Screenshots/_images/screenshot2.png)

PS: I just remembered another little problem I have, and that's that the "Print Screen"-button isn't working, in Gnome "gnome-screenshot" opened up by pressing it, but now, nothing. And I can't find out how to bind it.

Thanks!

---

### Post by bestial on 2007-02-20
Ah, my questions where to hard for you all! \\:D/

---

### Post by Rui Pais on 2007-02-21
> **bestial said:**
> Ah, my questions where to hard for you all! \\:D/

that's a weird thing to say... looks like you would be happy if people wouldn't answer your question then the other way...


The first of your links is to an e16, a different version of enlightenment that you mention on your thread title. It has nothing in common, except that you can use e17 winter theme on e17 to get a close color/animation/decoration scheme of that picture.

The second is a menu out-of the box with a home made theme or an out-of-date theme and personal font. 
Fonts are set with: Right Click on desktop, Configuration -> Appearance -> Fonts.
Menus are generated with: Configuration -> Menus -> Application menus ->Regenerate/update  "Application" menus.
Themes can be download from [here]("http://www3.get-e.org/Themes/E17/"). Since there are frequent api changes in e17 that is a alpha work-in-progress (and maybe not recommended for beginners, by the way), there are always themes that stop to work and the authors stop to update them or take some time to do it.

You can do/change a theme of your own by "decompile" it with:
```
edje_decc <theme_file.edj>
```
and change icons, edit code files, etc. and run the build script to produce a new edj file.
Maybe it sounds a little hard but it's very simple. If you cannot managed to understand the code, you can only change icons to something you like more. In short, it gives a lot of power, but came with a price, you need to learn a little... ;)

---

### Post by bestial on 2007-02-21
Hehe, it was just my way to say "come, help me", but yeah, maybe a little bit harsh.

Also, the things you mention I have figured out by my own, I have some skills at least. But the things that I mentioned like the "config-menu" and "run command"-tool etc. you can't (at least by what I see) remove from the menu>application-menu, cause only the programs shows there, favourites etc. and those things have I already found out.

But thanks anyway for your time, the e-sites have I, also, already visited many times, don't you think that those themes are a little bit boring? Anyway I'm sticking to Milky's right no, some nice OSX-stylish thing.

EDIT: But maybe you hade some answers to my questions on a second look, though they seem to be a little bit of troubble, but it might be fun to fix ém sometimes. I'm thinking about the decompile-thing. But you would think that there should be some easier way to do things as I want them to be. :D

---

