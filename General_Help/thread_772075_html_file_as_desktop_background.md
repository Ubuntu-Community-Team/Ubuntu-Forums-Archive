---
title: "html file as desktop background"
date: 2008-04-28
forum: General Help
---

### Post by thefishki345 on 2008-04-28
Hi.
Does anyone have a simple tutorial on how to make a html file your desktop background, especially this one:[http://www.overdrawn.net/mario/example/](http://www.overdrawn.net/mario/example/)

any help would be appreciated,
thanks!:)

---

### Post by thefishki345 on 2008-04-28
anyone???
please??..
I know somebody knows the answer...
:popcorn:

---

### Post by kesman on 2008-04-28
I don't think you can, but you could create that image yourself, just right-click the elements and save them and then merge them together with Gimp.

[http://www.overdrawn.net/mario/example/bottom.jpg](http://www.overdrawn.net/mario/example/bottom.jpg)
That's the background file.

---

### Post by justleen on 2008-04-28
if you dont mind installing kde:  kwebdesktop

---

### Post by thefishki345 on 2008-04-28
justleen, would that still work with gnome even though it is for KDE?

EDIT: at this website:[http://www.fsckin.com/2008/04/14/fun-with-xwinwrap-in-compiz-fusion/](http://www.fsckin.com/2008/04/14/fun-with-xwinwrap-in-compiz-fusion/)

he managed to do it with xwinwrap, but annoyingly, he never tells you how he made the mario desktop work.

---

### Post by justleen on 2008-04-28
conserding he is just starting the whole screensaver (the executable) i can image that you could start your mario thingy whith something like
```

nice -n 15 ./xwinwrap -ni -o 0.20 -fs -s -sp -st -b -nf -- /usr/bin/firefox --fullscreen  http://www.overdrawn.net/mario/example/ 
```

roughly...

---

### Post by thefishki345 on 2008-04-28
thanks for that, but, erm...now I cant install xwinwrap, lol does anyone have a quick tutorial via command line for 64bit?

EDIT: I got xwinwrap working but when I try that command line:
nice -n 15 ./xwinwrap -ni -o 0.20 -fs -s -sp -st -b -nf -- /usr/bin/firefox --fullscreen  [http://www.overdrawn.net/mario/example/](http://www.overdrawn.net/mario/example/)

I get ./xwinwrap permission denied.
I tried sudoing it, any idea?

---

### Post by justleen on 2008-04-28
i'd suggest you try to find some xwinwrap manuals.. i just copied and pasted the  command line of the screensaver...

try running just xwinwrap, or even xwinwrap from an example.
 cmdline options:


xwinwrap [-g] [-ni] [-argb] [-fs] [-s] [-st] [-sp] [-a] [-b] [-nf]
       [-fl] [-o OPACITY] -- COMMAND ARG1...

 -g       geometry
 -ni      no input
 -argb    argb ?? Alpha, Red, Green, Blue ??
 -fs      fullscreen
 -s       sticky
 -st      skip taskbar
 -sp      skip pager
 -a       above
 -b       below
 -nf      noFocus
 -o       opacity=#   Between 0 and 1

---

