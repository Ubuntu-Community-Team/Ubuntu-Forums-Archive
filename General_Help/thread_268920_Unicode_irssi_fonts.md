---
title: "Unicode irssi fonts?"
date: 2006-09-30
forum: General Help
---

### Post by zergberg on 2006-09-30
I just downloaded rxvt-unicode, and to my delight, international characters are no longer rendered as gobbledegook. However, the default font is ugly and tiny; my eyes are burning.

So, I need some suggestions as to good unicode fonts to use for IRC'ing. Also, how do I tell rxvt to use them?

---

### Post by po0f on 2006-10-01
zergberg,

Yay, my favorite terminal!  Glad you like it so far.

I don't have any good font suggestions (haven't got around to ripping my Korean CDs, so plain ASCII is fine for now), but I can tell you how to use them.  You will need to edit ~/.Xresources.  Open up that file in gedit (if it doesn't exist, no worries).  Add a line that looks like this:
```
URxvt*font: -bitstream-bitstream vera sans mono-medium-r-normal-12-120-*-*-*-*-iso8859-1
```
To get that font setting, use xfontsel.  Open up a terminal and run xfontsel.  Go through the various menus, and when you get all the settings the way you like it, click Select.  In gedit, just middle-click to paste it in, then save.

Alternatively, you could use Xft to render your fonts, in which case, add a line like this:
```
URxvt*font:  xft:Bitstream Vera Sans Mono:pixelsize=12
```

You can specify more than one font on the font line.  I don't know the exact syntax, as I don't have a use for this feature, but it sounds like you do (if you want to view those "gobbledegook" characters  ;) ).  Look at [this](http://cvs.schmorp.de/rxvt-unicode/doc/rxvt.1.html), which is the man page, just online.  Click on the resources link, and look for the font setting.

Open up urxvt.  If the font didn't change run this command:
```
$ xrdb ~/.Xresources
```

Close that terminal and open up another one.  Your font changes should have taken effect.

There are a bunch of other settings that you can change, urxvt is pretty customizable.  I usually keep a terminal open all the time.  A lot of lines go by in that time, so I added this to my .Xresources file also:
```
URxvt*saveLines:  3000
```

There are other settings, but I'll let you play with it for now.  Have fun!  :)

---

