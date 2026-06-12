---
title: "Simulate left click without actually pressing mouse button."
date: 2015-04-26
forum: General Help
---

### Post by Rytron on 2015-04-26
Hi.

I have a few soundboard .swf files. I can play these with a web browser (offline). How can I auto click one of the sounds on the soundboard without left clicking the mouse as I don't want the mouse click sound. Is there a way for example to auto simulate a left click if I hover the mouse cursor over a part of the sound board and it 'clicks' on it after let's say 1.5 or 2 seconds?

Thanks.

---

### Post by dragonfly41 on 2015-04-26
I thought of AutoKey (like AutoHotKey in Windows) .. but perhaps this does it  ..

System Settings > Universal Access > Hover Click

[https://help.gnome.org/users/gnome-help/stable/a11y-dwellclick.html.en](https://help.gnome.org/users/gnome-help/stable/a11y-dwellclick.html.en)

---

### Post by Rytron on 2015-04-27
> **dragonfly41 said:**
> I thought of AutoKey (like AutoHotKey in Windows) .. but perhaps this does it  ..

System Settings > Universal Access > Hover Click

[https://help.gnome.org/users/gnome-help/stable/a11y-dwellclick.html.en](https://help.gnome.org/users/gnome-help/stable/a11y-dwellclick.html.en)

Hi dragonfly41. I don't use Gnome - I use MATE. How can I get this feature in AutoKey? I use AutoKey all the time to input common things like email addresses etc.

---

### Post by dragonfly41 on 2015-04-27
I believe that AutoHotKey (Windows) can do this but probably not AutoKey.

 .. but some ideas from the top of my head ..

(a) could you run AutoHotKey in wine (but a lot of setting up to achieve this)

or ..

(b) could you create a hidden iframe in your web browser containing soundboard swf files and embed a hidden swf with actionscript running to monitor hover over an object or x,y position in soundboard? [http://flash.bigresource.com/ActionScript-3-0-How-to-Detect-Mouse-Position-or-Event-VeuYp9q78.html](http://flash.bigresource.com/ActionScript-3-0-How-to-Detect-Mouse-Position-or-Event-VeuYp9q78.html)

or ..

(c) could Selenium (desktop automation) meet this? Or Sikuli Slides is similar to selenium. You would just need  screenshot image of your soundboard which Sikuli Slides would target.  [http://slides.sikuli.org/](http://slides.sikuli.org/)

---

### Post by dragonfly41 on 2015-04-28
On reflection probably placing an object on your web site would be the easiest approach.

Raphael.js is another possible approach instead of actionscript (although an added swf object should work too).

[http://stackoverflow.com/questions/8942338/raphael-js-2-hover-event](http://stackoverflow.com/questions/8942338/raphael-js-2-hover-event)

Then the javascript can call the api of your embedded soundboard swf files.

Just create a hover area which triggers calls to your soundboard.

If you follow the swf object route then look at free haxe.org to compile actionscript.

---

### Post by Rytron on 2015-04-28
I was thinking something simple like a web browser addon.

---

