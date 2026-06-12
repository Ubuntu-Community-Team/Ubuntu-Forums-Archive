---
title: "x11/Gnome Problem - Window Titlebar Icons (Minimize/Maximize/Close) not working"
date: 2007-07-24
forum: General Help
---

### Post by Mark England on 2007-07-24
Hello everybody :)

Here's my problem... sometimes (Depending on what I do with a window) I will lose the ability to click on the icons displayed to the top right hand side of a window (Minimize, Maximize, Close).

My problem is **_NOT_** that they are invisible like I found other people have had (Thank you 'Similar Threads' function... very nice).

The problem is that the buttons are there, however when I mouse-over them they do not change like usual and when I click in that space, the click event triggers whatever is actually behind the button... so If I go to close a window, I may end up closing the window behind it.


Some things I have done to my Ubuntu (Feisty Fawn) install may have caused this :(

I had problems with Compiz where I tried to uninstall it and the restricted NVidia drivers but I uninstalled the drivers before uninstalling Compiz so had to manually change some files to stop them pointing at the restricted drivers back to the old drivers... it was a mess, I'm a nub so I don't know exactly what I'm doing...

hopefully I havn't messed things up too much, has anyone got any ideas what I can do to fix this? I'd really love to get it working properly without a reinstall :(


At the moment I have Compiz uninstalled and the Restricted NVidia Drivers installed.


Thanks everyone :)
Mark

---

### Post by ScarletSpider on 2008-07-05
metacity is crashing : try this because it worked for me:type this into the terminal :

```

metacity --replace &
```

It should work..cheers :D

---

