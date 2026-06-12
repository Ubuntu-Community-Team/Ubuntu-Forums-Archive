---
title: "Font configuration"
date: 2016-02-01
forum: General Help
---

### Post by bokiscout on 2016-02-01
Hi,

I'm using lubuntu 15.10. and few days ago I installed i3 and it's ok except the fonts are a bit ugly.

So when I'm using lxde fonts are OK, but when I'm using i3 the fonts are ugly. 

First I tried to change anti aliasing settings, sub pixel rendering, hinting style in lxappearance but there isn't any kind of change. No change after restarting the OS. Ok, let's try manually editing font configuration.

Second  to edited ~/.gtkrc-2.0 and ~/.config/gtk-3.0/settings.ini but also no changes. Ok let's try editing fonts.config

Next I creating and editing /.config/fontconfig/fonts.conf (local config should be there, right? This is XDG's default config directory) but also, no visible changes. Then I edited global fonts.config at /etc/fonts/fonts.conf but also no visible changes.

Now I'm asking my self what else can affect fonts appearance? They do not follow any rules under i3, but they do when using lxde.


Note:
 I'm talking about the fonts inside GTK apps like leafpad, audacious etc... not fonts of i3 itself.


Thank You.

---

