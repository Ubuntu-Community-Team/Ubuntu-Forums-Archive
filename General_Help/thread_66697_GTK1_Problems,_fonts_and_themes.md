---
title: "GTK1 Problems, fonts and themes"
date: 2005-09-18
forum: General Help
---

### Post by Kimm on 2005-09-18
ok,

I'm having some trubble with GTK1 apps. First of all, I cant change the theme of them, not using gtk-theme-switch atleast. It acctually works in XFCE4 but when I switch to gnome the theme is gone and I still cant change it. The other problem is that the fonts are large and uggly, I cant explain why but I would like that fixed to....

I think this screenshot will describe the problem fairly well:

[img]http://i.domaindlx.com/MrKimm/Screenshot.png[/img]

Can anyone help?

---

### Post by Kimm on 2005-09-18
Well, I fixed the problem.

I had to do some slight tweeking in .gtkrc.mine to get the fonts right... and I had to copy the contents if the themes gtkrc and place it in .gtkrc.mine to get that to work...

I lost the link for that, but this fixes the fonts:

> style "user-font"
{
   fontset="-*-bitstream vera sans-medium-r-normal-*-11-*-*-*-*-*-iso8859-1"
}

widget_class "*" style "user-font"


It was an ubuntu page...

---

### Post by flaming_monkey on 2005-10-06
Thank you for posting your reply. That fix did the trick and now I have small GTK1 fonts. Yay.

---

### Post by sprucio on 2006-04-03
I'm trying to change the font for all GTK1 apps (XMMS, Mplayer).

Currently, I'm using gtk-theme-switch do achieve this goal but it doens't seem like it's working.

Upon checking my files (.gtkrc and .gtkrc-1.2-gnome2), it looks like the font settings are correct but nontheless, it hasn't changed the appearance in any GTK1 apps.
```
[bpark@spruce ~]$ cat .gtkrc
# -- THEME AUTO-WRITTEN DO NOT EDIT
include "/usr/share/themes/Default/gtk/gtkrc"

style "user-font"
{
  font="-misc-fixed-medium-r-semicondensed-*-*-100-*-*-c-*-iso8859-1"
}
widget_class "*" style "user-font"

include "/home/bpark/.gtkrc.mine"
```
I also don't have the file called .gtkrc.mine.

Does anyone have a clue as to how to solve this? I remember resolving this problem when I used to use Debian and it's a shame that Ubuntu suffers from this problem as well.

---

