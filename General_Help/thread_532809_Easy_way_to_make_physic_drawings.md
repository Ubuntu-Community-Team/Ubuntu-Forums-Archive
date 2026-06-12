---
title: "Easy way to make physic drawings?"
date: 2007-08-23
forum: General Help
---

### Post by Azzco on 2007-08-23
Hello, I'm studying physics and my handwritting is the worst ever so I try to rewrite my notes after school on my computer (while I still have most in my head).

The thing is that I've tried to do some of the drawings with different programs but none of them is really good for what I'm trying to do. gimp is good with it's measurement tool but it lacks certain functions like drawing a circle (such as the one in paint on windows).

I've tried Krita and arbo14 (maybe not the best of choice but still had to try). karbon14 was to hard for me and I'm not sure if I might be able to find what I need in it and krita is just hell for making 3 different perfect cricles that start at the exact same place but have different diameters.

On paper it's easy but I tend to screw up anyways so scanning isn't really an option (don't you just like those coffee marks?). Anyways yesterday I tried to do a drawing similar to this:
[IMG]http://superstruny.aspweb.cz/images/fyzika/quantum/quantum_split.png[/IMG]

But after an hour I just gave up, is there a program for drawings like this specificly?

---

### Post by manimal on 2007-08-23
For 2-d drawing, I like [Xfig]("http://www.xfig.org/").  It is pretty old-school, but powerful.  I'm not sure about 3-d drawings like the one you have shown.  [OpenDx]("http://www.opendx.org/") is pretty nice for multi-dimensional visualization (and just a *really* great program), but you can't really "draw" with it.  I believe both of these programs are available in the ubuntu repositories.

---

### Post by yousufinternet on 2007-08-23
to draw a circle in the gimp 
1- draw a circular sellection using the oval sellection tool 
2- keep the sellection active and choose fill with fg color from the edit menu

---

### Post by Azzco on 2007-08-23
Thanks for the fast replies, I tried some script with gimp but it was a dialog in which you entered width and height and doing that multiple times is just not productive.

I guess that your tip will help a bit but it'd be just plain easier if you could just draw a elipse and hold down Ctrl to make a perfect circle, I'd have to make 2 selections for one circle and if I'm to make, say like 5 it'll be some work... I'll try it though ;)

---

### Post by christhemonkey on 2007-08-23
I use Open Office Drawing.
Its installed by default (i think) but hidden in the menus for some reason.

I use it to do physics drawings for my physics work.

---

### Post by Azzco on 2007-08-23
I've tried Open office before but it's still a lot of work getting them aligned right and such.

I did another trip through adept and found something useful today, namely kig.

This app seems really nice, :) I haven't learned to much about it yet though and I'm trying to do a part of a circle ( 90 degrees of it) but I just can't seem to do it. =/
Except for that I think that it'll work just perfectly :D

---

### Post by manimal on 2007-08-24
Xfig is what you're after.

```
sudo apt-get install xfig
```

---

### Post by tpg on 2007-08-24
Just to go off on a tangent, I also typed up my school physics notes. For that, I used TeXmacs, a WYSIWYGish LaTeX frontend. It has fairly basic drawing capabilities, but it was very useful from the equation point of view.

Otherwise, XFig is good, although it has somewhat of a steep learning curve, and I believe the lead developer has stopped work on it (correct me if I'm wrong). Also I'd recommend something vector-based rather than bitmaps (i.e. not gimp), as then the drawings will scale much better. Inkscape, Karbon-14, and OpenOffice.org Draw are all good options.

3D drawings are going to be a lot harder - I suppose a compromise is to do complicated diagrams by hand, scan them in, and use them that way.

Although you said "easy" I thought I'd give metapost a mention. It's a scripting language, which you can then process to make an image (postscript, pdf, etc...). It's complicated to learn, but very powerful, especially for more mathematical diagrams.

---

### Post by Azzco on 2007-08-24
I'm very happy with kig it's really simple but powerful and I got some help from a maintainer on IRC. :)

I export the images as SVG, the only proble is that I have to open them with karbon14 and resave to be able to use them in a koffice document but I'm truly happy with this app! :D

---

