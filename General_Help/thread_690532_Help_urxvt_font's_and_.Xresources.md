---
title: "Help urxvt font's and .Xresources"
date: 2008-02-07
forum: General Help
---

### Post by Breakage on 2008-02-07
I'm having trouble setting font's in urxvt with this command in ~/.Xresources

> URxvt*font: xft:DejaVu Sans Mono:pixelsize=10

Urxvt or rxvt wont start, I get this error...

> urxvt: unable to load base fontset, please specify a valid one using -fn, aborting.

Everything works fine without that line like the colours, background and no scrollbar etc, here is my normal .Xresources

> URxvt*background: #242424
URxvt*cutchars: BACKSLASH '"'&()*,;<=>?@[]{|}
URxvt*colorUL: #86a2be
URxvt*foreground: #ffffff
URxvt*geometry: 80x25
URxvt.cursorColor: #86a2be
URxvt*internalBorder: 0
URxvt*jumpScroll: true
URxvt*loginShell: true
URxvt*perl-ext-common: default,matcher,searchable-scrollback
URxvt*pointerBlank: true
URxvt*saveLines: 4000
URxvt*secondaryScroll: true
URxvt*scrollBar: false
URxvt*scrollTtyKeypress: true
URxvt*scrollWithBuffer: true
URxvt*termName: rxvt-unicode
URxvt*underlineColor: #86a2be
URxvt*urlLauncher: /usr/bin/swiftfox
URxvt*color0: #242424
URxvt*color1: #bf7979
URxvt*color2: #97b26b
URxvt*color3: #cdcda1
URxvt*color4: #86a2be
URxvt*color5: #d9b798
URxvt*color6: #a1b5cd
URxvt*color7: #ffffff
URxvt*color8: #cdb5cd
URxvt*color9: #f4a45f
URxvt*color10: #c5f779
URxvt*color11: #ffffaf
URxvt*color12: #98afd9
URxvt*color13: #d7d998
URxvt*color14: #a1b5cd
URxvt*color15: #dedede


I've tried it with different font's other that the one I would like to use like sans etc and still get the same error, what am I doing wrong? 

Help please, Cheers :)

Edit: Fixed! It was rxvt-unicode-lite that was messed up even though it said it can support xft fonts, switched to rxvt-unicode and all's good.

---

### Post by xyblor on 2008-03-10
~/.Xresources doesn't seem to affect urxvt for me. I installed the "rxvt-unicode-ml" package but it doesn't seem to come with support for .Xresources; not sure why. I'm trying to figure out the best way to change the font, it looks like setting up an alias for urxvt with the -fn option is the way to go.

---

### Post by RedSquirrel on 2008-03-10
> **xyblor said:**
> ~/.Xresources doesn't seem to affect urxvt for me. I installed the "rxvt-unicode-ml" package but it doesn't seem to come with support for .Xresources; not sure why. I'm trying to figure out the best way to change the font, it looks like setting up an alias for urxvt with the -fn option is the way to go.
If you use gdm, ~/.Xresources should be loaded for you automatically.

You can also load it manually on the command line:

```
xrdb -merge ~/.Xresources
```

Confirm that your settings were loaded with:

```
xrdb -query
```

See the man page:

```
man xrdb
```

---

