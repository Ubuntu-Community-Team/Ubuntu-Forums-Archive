---
title: "Skype tooltips unreadable."
date: 2013-04-12
forum: General Help
---

### Post by ajgreeny on 2013-04-12
On my Xubuntu 12.04 I use skype every so often, and I find it works very well except that the tooltips that appear on both the skype contacts window and on the video window are dark blue background and black font, so they are quite useless and unreadable.  See my screenshot which shows what I am talking about.

Can anyone tell me how to change that to a more useful colour choice?  I have tried all variations of the themes I have, together with many of the options in the window manager, but nothing seems to change those tooltip colours for skype.  No other application uses the same colours for tooltips and I am baffled.

---

### Post by r_avital on 2013-07-04
Similar problem here.  Not in Skype, but in several xubuntu stock applications (xubuntu 12.04, not in xfce), such as Synaptic (many others, this is just the one I remember at the moment) tooltips are dark grey on dark grey, not kidding.

I would love to see a solution to this.

Thanks in advance, and Happy Fourth! :)

---

### Post by fantab on 2013-07-04
Change the theme. Skype is base on Qt, I think. And the issue is perhaps caused by Gtk theme not applying well with Qt applications. Install 'qtconfig' or 'qt4-config' if its not installed and in it change the theme to Gtk. See if it helps.
Editing gtkrc file with appropriate tool tip colors may also help. Sometimes restart is required to apply the theme you want.

A

---

