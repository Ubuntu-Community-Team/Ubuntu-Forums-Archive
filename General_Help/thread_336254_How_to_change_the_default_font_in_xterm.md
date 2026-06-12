---
title: "How to change the default font in xterm?"
date: 2007-01-11
forum: General Help
---

### Post by tsg1zzn on 2007-01-11
How can I set the default font in xterm to the default monospace font, so that xterm uses the same font as gnome-terminal when use the system terminal font is checked in gnome-terminal.

I do NOT want to set the font in xterm to a font name, I want it to be the default font.

---

### Post by IcemanV9 on 2007-01-11
"[COLOR="Orange"]man xterm[/COLOR]" has lots of good information. :)

```
xterm -fa [font name]
```

To make it default for xterm, just add this line, alias xterm='xterm -fa monospace', to the file .bash_aliases. OR/AND, add it to the 'xterm' launcher properties - command.

---

### Post by tsg1zzn on 2007-01-12
> **IcemanV9 said:**
> "[COLOR="Orange"]man xterm[/COLOR]" has lots of good information. :)

```
xterm -fa [font name]
```

To make it default for xterm, just add this line, alias xterm='xterm -fa monospace', to the file .bash_aliases. OR/AND, add it to the 'xterm' launcher properties - command.

Well, as I said, I don't want to set the default font to a font name, I want to set it to the system default monospace font. Will the monospace font map to the system default monospace font? I thought it was the name of a real font?

---

### Post by tsg1zzn on 2007-02-17
Ok, it turns out that monospace maps to the system default monospace font. However, when I set the font in xterm to monospace, xterm ignores my hinting settings. Why is this?

---

### Post by kerry_s on 2007-02-17
You can setup xterm using a .Xresources file. Here's mine->

```
! this are Xresources to make xterm look good
! put into ~/.Xresources
! after changing contents, run xrdb -merge .Xresources
! gentoo has a bug so that it doesnt read it when X starts, so add above
! command to /etc/xfce4/xinitrc (top) and be happy.

!xterm*background:	Black
!xterm*foreground:	Grey
xterm*font:		-misc-dejavu sans mono-medium-r-normal-*-*-120-*-*-m-*-iso8859-1
!xterm*font:		-misc-dejavu sans mono-medium-r-normal-*-*-120-*-*-m-*-iso8859-1
!xterm*iconPixmap: ...
!XTerm*iconName: terminal
!Mwm*xterm*iconImage: /home/a/a1111aa/xterm.icon
XTerm*loginShell: true
XTerm*foreground: gray90
XTerm*background: black
XTerm*cursorColor: rgb:00/80/00
XTerm*borderColor: white
XTerm*scrollColor: black
XTerm*visualBell: true
XTerm*saveLines: 1000
!! XTerm.VT100.allowSendEvents: True
XTerm*allowSendEvents: True
XTerm*sessionMgt: false
!XTerm*eightBitInput:  false
!XTerm*metaSendsEscape: true
!XTerm*internalBorder:  10
!XTerm*highlightSelection:  true
!XTerm*VT100*colorBDMode:  on
!XTerm*VT100*colorBD:  blue
!XTerm.VT100.eightBitOutput:  true
!XTerm.VT100.titeInhibit:  false
XTerm*color0: black
XTerm*color1: red3
XTerm*color2: green3
XTerm*color3: yellow3
XTerm*color4: DodgerBlue1
XTerm*color5: magenta3
XTerm*color6: cyan3
XTerm*color7: gray90
XTerm*color8: gray50
XTerm*color9: red
XTerm*color10: green
XTerm*color11: yellow
XTerm*color12: blue
XTerm*color13: magenta
XTerm*color14: cyan
XTerm*color15: white
XTerm*colorUL: yellow
XTerm*colorBD: white
!XTerm*mainMenu*backgroundPixmap:     gradient:vertical?dimension=400&start=gray10&end=gray40
!XTerm*mainMenu*foreground:          white 
!XTerm*vtMenu*backgroundPixmap:       gradient:vertical?dimension=550&start=gray10&end=gray40
!XTerm*vtMenu*foreground:             white
!XTerm*fontMenu*backgroundPixmap:     gradient:vertical?dimension=300&start=gray10&end=gray40
!XTerm*fontMenu*foreground:           white
!XTerm*tekMenu*backgroundPixmap:      gradient:vertical?dimension=300&start=gray10&end=gray40
!XTerm*tekMenu*foreground:            white
!XTerm Profiles (idea from dag wieers)
XTerm*rightScrollBar: true

```

---

