---
title: "No Option To Change Window Theme in Gnome-Tweak-Tool"
date: 2013-10-27
forum: General Help
---

### Post by mvjt-dobson on 2013-10-27
So I have just done a fresh install of Ubuntu Gnome Edition 13.10 and I have no options to change the Current Theme for the title bar or change the fonts for the same section, here are a couple of screenies to show:

[[img]http://en.zimagez.com/miniature/selection002.jpg[/img]](http://en.zimagez.com/zimage/selection002.php)

[[img]http://en.zimagez.com/miniature/selection0010.jpg[/img]](http://en.zimagez.com/zimage/selection0010.php)

I managed to change them in dconf but I still want the option back in Tweak to be able to change it easier, anyone else have this problem or find a solution?

Cheers

---

### Post by Baldrick_NZ on 2013-10-27
If you go to "Shell Extensions", there should be a switch to enable "User Themes". Switch this on, and you should have the ability to change the Gnome Shell theme, which controls the panel at the top. While you're there, check out some of the other preinstalled extensions, or download new ones to help personalise your desktop more the way you want it.

If you are trying to change the font of the top panel, there is an app that comes with the theme you currently have (Elegance Colors), which will pretty much configure the entire shell theme the way you want it. You can find the app on the dash. Personally, I find Elegance Colors the best theme of them all for that reason alone. Other themes you have to get into the .css code to change fonts, enable icons, etc... 

Hope that helps!

---

### Post by mvjt-dobson on 2013-10-27
Thanks Baldrick. That wasn't quite what I was after :D  I may not have explained myself clearly, the options to change the titlebar theme and titlebar fonts are missing from Gnome-Tweak-Tool.  I know how to change them via Dconf but I am wondering why these options have vanished.

---

### Post by mvjt-dobson on 2013-10-28
Anyone?

---

### Post by qetuR on 2014-01-15
> **mvjt-dobson said:**
> Anyone?

I have installed a new Ubuntu Gnome desktop (13.10) and I also miss this option. I'm running another machine where this option is still there.

Strange, help?

---

### Post by qwazix on 2014-02-01
Try opening dconf-editor, searching for metacity and changing the theme there.

---

