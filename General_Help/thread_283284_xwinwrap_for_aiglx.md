---
title: "xwinwrap for aiglx?"
date: 2006-10-24
forum: General Help
---

### Post by jcrnan on 2006-10-24
Ive see ways of doing it with xgl but isnt there any way of using aiglx isntead? When I try the screen goes to hell and flickers violently. (beryl works fine btw)

---

### Post by puccaso on 2006-10-24
yep
i have the same problem
it just flickrs

maybe we need to set something like opengl overlay or something
but i dont know how

---

### Post by jcrnan on 2006-10-25
I have no idea either.. I tried messing around with the xwinwrap paramters but didnt get any effect out of that. Anyone that know?

---

### Post by poofyhairguy on 2006-10-26
I have been looking into it recently.

It has always seemed like Xwinwrap is a very hackish program from since it was released. David made it just for his XGL presentation, and he made no how tos or any real documentation for it. He did make quite a few tags of action for it, and always I wonder how quickly he banged it out....I bet it would shock me.

Anyway...I think its trick is to take advantage of the fact that many screensavers rely on OpenGL and direct rendering and somehow Xwinwrap puts together the two direct rendered images (XGL and the screensaver) in mixed layers. With Aiglx (or heck, just plain Xorg now right?) the indirectly rendered desktop does not play along with the hack and so the directly rendered screensaver takes up the whole screen- blackness and all.

What the correct (and kinda unfortunate) solution to the problem is a true moving desktop program designed to take that job away from nautilus (in a way where nothing else can tell) and do it better. Such a program could create desktops that could change with mouse movements, the time of day, or  depending on what side of the cube they are on. It could be used for desktop widgets above and beyond what we have now. Such a thing is probably what David was thinking about when he made Xwinwrap, but he didn't want to spend the time making this (or the moving background programs) so he made the Xwinwrap hack. A true program would run smoother theoretically as well.

Closest thing we have to that in the Linux world is e17. The closest thing to what I'm thinking of on any platform is:

[http://www.fourminutemilesoftware.com/quartzdesktop/](http://www.fourminutemilesoftware.com/quartzdesktop/)

For now Xwinwrap is still maybe the best solution- if you need it use XGL. I'm hoping that KDE4 will have a few features that might make Xwinwrap seem like an old hat!

---

### Post by jcrnan on 2006-10-28
well, I cant stand KDE so I have to hope for Gnome 3 I guess :P

But is there any way then to use XGL instead of Aiglx on a intel card?

---

### Post by dondolo on 2007-02-07
hi, 


i've been able to install beryl and xwinwrap with aiglx, i would like to create an optical effect in my pc but i don't know hot to....
is it possible to set the matrix screensaver as beryl's cube background???? using this code 

> xwinwrap -ni -fs -s -st -sp -b -nf -- /usr/lib/xscreensaver/glmatrix -window-id WID -delay 50000 -density 60 

i'm able to strat in in full screen, but i like to set it for beryl's cube background too, is it possilbe???? let me know best regards

---

### Post by mcduck on 2007-02-07
> **dondolo said:**
> hi, 


i've been able to install beryl and xwinwrap with aiglx, i would like to create an optical effect in my pc but i don't know hot to....
is it possible to set the matrix screensaver as beryl's cube background???? using this code 

 

i'm able to strat in in full screen, but i like to set it for beryl's cube background too, is it possilbe???? let me know best regards
That command should run it as background.

If you mean skydome picture that's not possible as far as I know.

---

### Post by dondolo on 2007-02-07
i know it works in background but in the desktop but it doesen't work for me with beryl actived simultanely, i am interested to know if it can works too for beryl's cube background

---

### Post by ethana2 on 2007-06-29
The guy who made this needs to port it into a simple compiz fusion plugin, and it needs to be distributed with all copies of compiz that are downloaded, in place of the draw fire plugin, which I honestly found to be rather worthless.

Video skydomes would be freaking sweet, too.

And 3d animations inside the cube, like, say, a dancing tux or perhaps a bug with a simple AI trying to find its way out ;)

---

### Post by Qu4k3R on 2007-06-29
I am using AIGLX drivers (nvidia go 6800) and it is running fine.
There are two topics (how-to) in the tutorial's forum..
Qu4k3r

I've got this (working):
> 
xwinwrap -ni -argb -fs -s -st -sp -b -nf -o 0.25 -- /usr/lib/xscreensaver/glmatrix -window-id WID


---

