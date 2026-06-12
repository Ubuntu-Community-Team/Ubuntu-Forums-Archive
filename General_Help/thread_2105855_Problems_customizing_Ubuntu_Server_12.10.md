---
title: "Problems customizing Ubuntu Server 12.10"
date: 2013-01-17
forum: General Help
---

### Post by tech291083 on 2013-01-17
Hi,

After having installed Ubuntu Server 12.10 64-bit on my desktop pc, I tried to customize the system to my liking using this guide at

[http://www.noobslab.com/2012/10/important-thingstweaks-to-do-after.html](http://www.noobslab.com/2012/10/important-thingstweaks-to-do-after.html)

1. I tried to do item no 10 ie putting my username on the space next to Shutdown (gear like icon to the far right, next to time) icon but I do not see that happen. This is what I did as root in a terminal

> 
[COLOR=red]gsettings set com.canonical.indicator.session show-real-name-on-panel true[/COLOR]


2. Item no 21 ie Move Minimize, Maximize, Close Buttons to Right:

> 
[COLOR=red]gconftool-2 --set /apps/metacity/general/button_layout --type string menu:minimize,maximize,close
[/COLOR]

---

### Post by tech291083 on 2013-01-17
Also tried to install Adobe Reader using the instructions give here at

[http://www.noobslab.com/2012/11/install-adobe-acrobat-reader-in-ubuntu.html](http://www.noobslab.com/2012/11/install-adobe-acrobat-reader-in-ubuntu.html)

But failed to do so.

```

[INDENT] 
[LIST]
[*][COLOR=red]sudo add-apt-repository "deb http://archive.canonical.com/ precise partner"[/COLOR]
[*][COLOR=red]sudo apt-get update[/COLOR]
[*][COLOR=red]sudo apt-get install acroread[/COLOR]
[/LIST]
 [/INDENT]
```

Please help me guys, thanks a lot.

---

### Post by tech291083 on 2013-01-20
Dear Friends, please help me with your guidance, thanks a lot.

---

