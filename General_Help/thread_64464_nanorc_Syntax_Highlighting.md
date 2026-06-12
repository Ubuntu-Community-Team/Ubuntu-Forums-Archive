---
title: "nanorc Syntax Highlighting"
date: 2005-09-11
forum: General Help
---

### Post by duminas on 2005-09-11
OK, so I'm in nano editing /etc/nanorc, but as my regex memory is pretty poor, I'm having trouble figuring out how to do what I want to, here.

Namely, what I want is to color all the text in a "value" for an attribute like so:
```
[color=Blue]<body bgcolor=[color=Red]"#000000"[/color] alink=[color=Red]"#ff0000"[/color]>[/color]
```Yet, I can't seem to get it right.

My current HTML syntax section of nanorc is as follows:
```
[size=2]syntax "HTML" "\.(html|tm)$"
color blue start="<" end=">"
color red "&[^; ]*;"
color brightyellow "(<!--.*|//.-->)$"
color brightred "(\".*|//.\")$"[/size]
```What it's doing is```
[color=Blue]<body bgcolor=[color=Red]"#000000" alink="#ff0000">[/color][/color]
```which is, obviously, not right.

Thanks for any help.

---

