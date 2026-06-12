---
title: "alacarte (Main Menu) image/icon problem..."
date: 2013-10-27
forum: General Help
---

### Post by Baldrick_NZ on 2013-10-27
It used to be that when you set up an app using alacarte, you could choose either a .svg or .png image for the icon, but all I can seem to use is a .jpg - which is fine if you want the image to have a white (not transparent) background.

Is there anyway to change the config settings to allow either/both .png & .svg images as icons?

Cheers.

Currently using Ubuntu Gnome 13.10/GS3.8

---

### Post by Baldrick_NZ on 2013-10-27
Whilst i couldn't find an answer regarding alacarte, I did find the answer by using this...
[http://www.smdavis.us/projects/menulibre/](http://www.smdavis.us/projects/menulibre/)

Great job Sean! Alacarte has just been dumped. Pity Menulibre isn't in the repos.

---

### Post by NeoEcoS on 2014-03-07
Hi, i was having the same issue, the problem is very simple to solve using alacarte.

The bug is this [https://bugzilla.redhat.com/show_bug.cgi?id=1015506](https://bugzilla.redhat.com/show_bug.cgi?id=1015506) and my way to solve was..

find . -name "*.desktop"
vim ./.local/share/applications/alacarte-made.desktop

And the  edit the file adding the extension to the icon.

Icon=/home/sebas/sw/firefox/browser/icons/mozicon128.png  ### Add the .png or what ever your extension is.

---

