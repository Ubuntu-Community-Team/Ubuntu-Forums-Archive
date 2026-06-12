---
title: "True terminal transparency in dapper with AIGLX?"
date: 2007-03-03
forum: General Help
---

### Post by JRevell on 2007-03-03
Okay... I have been trying to do this for hours? Anyone have any ideas? I've tried urxvt, aterm, Eterm and the like and it just shows the desktop image. I *am* running beryl, but this seems to make no difference, all the transparencies are fake.

Thanks.
:(

---

### Post by po0f on 2007-03-03
JRevell,

How are you trying it with urxvt?  The following works for me:

```
$ urxvt --depth 32 --foreground white --background rgba:0000/0000/0000/cccc
```

---

### Post by JRevell on 2007-03-03
> **po0f said:**
> JRevell,

How are you trying it with urxvt?  The following works for me:

```
$ urxvt --depth 32 --foreground white --background rgba:0000/0000/0000/cccc
```


When I do that I get this... 
```
jrevell@jrevell-desktop:~$ urxvt --depth 32 --foreground white --background rgba:0000/0000/0000/cccc
urxvt: "depth": unknown or malformed option.
urxvt: "32": malformed option.
rxvt-unicode (urxvt) v7.0 - released: 2006-01-13
options: xft,styles,combining,blink,iso14755,encodings=eu+vn+jp+jp-ext+kr+zh+zh-ext,fade,XPM,transparent,tint,utmp,XIM,scrollbars=plain+rxvt+NeXT+xterm,frills,selectionscrolling,wheel,slipwheel,smart-resize,cursorBlink,pointerBlank,
Usage: urxvt [-help] [--help]
 [-display string] [-tn string] [-geometry geometry] [-C] [-iconic] [-/+rv]
 [-/+ls] [-/+j] [-/+ptab] [-/+sb] [-/+sr] [-/+st] [-sbt number] [-/+si]
 [-/+sk] [-/+sw] [-/+ip] [-tint color] [-fade %] [-fadecolor color] [-sh %]
 [-/+ut] [-/+vb] [-/+tcw] [-/+insecure] [-/+uc] [-/+bc] [-/+pb] [-bg color]
 [-fg color] [-cr color] [-pr color] [-pr2 color] [-bd color]
 [-pixmap file[;geom]] [-fn fontname] [-fb fontname] [-fi fontname]
 [-fbi fontname] [-/+is] [-im name] [-pt style] [-imlocale string]
 [-imfont fontname] [-name string] [-title string] [-n string] [-sl number]
 [-embed windowid] [-pty-fd fileno] [-/+hold] [-w number] [-b number] [-/+bl]
 [-/+sbg] [-lsp number] [-mod modifier] [-/+ssc] [-/+ssr] [-xrm string]
 [-e command arg ...]

jrevell@jrevell-desktop:~$


```

---

### Post by po0f on 2007-03-03
JRevell,

True transparency is only supported in urxvt >=7.7.  I had to custom compile urxvt on Dapper to get the true transparency, that fact totally slipped my mind.

---

### Post by konungursvia on 2007-03-13
> **po0f said:**
> JRevell,

True transparency is only supported in urxvt >=7.7.  I had to custom compile urxvt on Dapper to get the true transparency, that fact totally slipped my mind.

Umm, could you throw together a deb that we could use to do the same? :mrgreen:

---

