---
title: "Clipboard manager with unlimited storage"
date: 2012-12-22
forum: General Help
---

### Post by Inoki on 2012-12-22
Hi lads,

I was wondering, since spending countless hours (one could say) on the internet searching for a clipboard manager, that allows one to store unlimited units of either text, image, links, whatever similar to the only one I found, but unfortunately **Ditto** only works on Windows and I couldn't get it to sync over Wine with X11's clipboard, I'm turning to these forums for help.

For the past few months I've been using ClipIt, which I found the only perfect alternative for Linux so far, but what I'm looking for is a highly configurable clipboard manager similar to the above mentioned, so far working only on Windows, Ditto, which allows, among other features:

[LIST]
[*]grouping of entries
[*]save unlimited entries
[/LIST]

---

### Post by raja.genupula on 2012-12-22
Ok look at there , there is some information which can help you . 

[http://www.webupd8.org/2010/08/best-linux-clipboard-manager.html](http://www.webupd8.org/2010/08/best-linux-clipboard-manager.html)

---

### Post by Inoki on 2012-12-22
> **raja.genupula said:**
> Ok look at there , there is some information which can help you . 

[http://www.webupd8.org/2010/08/best-linux-clipboard-manager.html](http://www.webupd8.org/2010/08/best-linux-clipboard-manager.html)
Thanks, but I've already had a look at those and they didn't meet my requirements. If you'll give Ditto a try you'll understand.

---

### Post by raja.genupula on 2012-12-22
Ok how about having it through WINE ?

---

### Post by Inoki on 2012-12-22
> **raja.genupula said:**
> Ok how about having it through WINE ?
As I said, I've tried, it worked, except for two vital things:[LIST]
[*]I couldn't get it to sync with XFCE's shortcuts, i.e. I wanted to use <Super>X for the popup, which didn't work of course, as Wine only recognizes the WIN key, not SUPER key
[*]It didn't sync data between clipboards at all
[/LIST]

---

### Post by Bucky Ball on 2012-12-22
I use Clipman in Xubuntu. Not sure if you can install on Ubuntu but don't see any reason why not. It saves a history of everything copied to the clipboard, including images or anything else. You might try looking for it in Software Centre of Synaptics. 

You can set how many things it will keep ...

PS: There are *many* users (including forum staff) who are _not_ lads ...

---

### Post by Inoki on 2012-12-22
> **Bucky Ball said:**
> I use Clipman in Xubuntu. Not sure if you can install on Ubuntu but don't see any reason why not. It saves a history of everything copied to the clipboard, including images or anything else. You might try looking for it in Software Centre of Synaptics. 

You can set how many things it will keep ...

PS: There are *many* users (including forum staff) who are _not_ lads ...
Nope, tried, doesn't suffice. It's very very basic. I'm looking for something more advanced.

E.g. with Ditto you can not only **_store unlimited clips_**, but also **_create groups_** in which you store them and **_search through history_**. You can also configure a period of days e.g. when old, unused entries are removed automatically.

I haven't encountered such a feature-rich clipboard manager for Linux so far.

And as for addressing you guys, that wasn't meant to be offending. Don't take life too seriously, you'll never make it alive out of it.

---

### Post by avsprasad on 2013-01-05
I wanted the same thing. My friend gave me this shell script to run along with clipit
============
#!/bin/bash

strings /home/avsprasad/.local/share/clipit/history | sed s/\00/~/g | sed s/\FF/~/g | sed s/\\~/~/g > /home/avsprasad/Documents/clipit_output.txt
=============

---

