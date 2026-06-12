---
title: "Ctlr-Alt-F* does not switch to text console"
date: 2013-04-06
forum: General Help
---

### Post by superpyrin on 2013-04-06
I need keyboard layout where left Alt (Alt_L) acts as Mod4. After making changes to .Xmodmap file I cannot use Ctrl-Alt-F* combination to switch to text console. I am using Lubuntu 12.10.

Here is the content of my ~/.Xmodmap file:

[FONT=courier new]! map Alt_L as Mod4 (equivalent of Windows key)
remove Mod1 = Alt_L
add Mod4 = Alt_L[/FONT]

After that Ctrl-Alt-F* stopped working. Note, that I press right Alt (Alt_R) key.

I tried also different approach:

[FONT=courier new]! map Alt_L as Mod4 (equivalent of Windows key)[/FONT]
[FONT=courier new]clear Mod1
clear Mod4
add Mod1 = Alt_R
add Mod4 = Alt_L[/FONT]

Also in this case Ctrl-Alt-F* does not work. What am I doing wrong?

---

