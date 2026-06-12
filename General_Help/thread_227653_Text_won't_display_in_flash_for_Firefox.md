---
title: "Text won't display in flash for Firefox"
date: 2006-08-02
forum: General Help
---

### Post by jeff_ on 2006-08-02
I'm running firefox 1.5.0.5 and just installed flash. It seems to work fine except any regular text in the animations won't display. All other parts of the flash animations seem to work correctly. Any idea on how to fix this??

Some examples are tvguide.com/listings or [http://www.federalreserveeducation.org/fed101/policy/money.htm](http://www.federalreserveeducation.org/fed101/policy/money.htm)

Thanks -- Jeff

---

### Post by hw-tph on 2006-08-02
Did you install it manually (downloadied from Macromedia) or from the Ubuntu package system? The reason I ask is that the Flash player requires the gsfonts-x11 package to display fonts properly, and if you install it "by hand" it is easy to forget about it. The Ubuntu package (flashplugin-nonfree) depends on gsfonts-x11 so it should be installed automatically.

For me that page you linked to displays well, although making flash-only sites is completely braindead and should be severely punished... :o


Håkan

---

### Post by easyease on 2006-08-02
If you are viewing a Flash video and you do not see any text, install the gsfonts and gsfonts-x11 packages.

---

### Post by jeff_ on 2006-08-02
Thanks guys, this worked like a charm. I'm having another problem with fonts though and I'm not sure if it's related or not. It seems firefox is having trouble displaying certain apostrophes, for example in news headlines on googles personalized homepage or in rss feeds. Instead of the apostrophe it displays a square box with what looks like 0 0 on top and 9 2 on the bottom. I'll post a screen shot if need be. Thanks again, ubuntu ftw!

---

### Post by Mr Frosti on 2006-10-04
I installed Flash from inside Firefox by clicking on the plugin, and the gsfonts-x11 package was not installed. Should this be in Ubuntu by default as everyone uses Flash, and most people will probably install through the method I used?

---

