---
title: "Shortcut Binding"
date: 2007-02-22
forum: General Help
---

### Post by sweetthdevil on 2007-02-22
Hi, I'm trying to use my mouse (MX518) application touch {bouton 8} to do a key combination to open a certain menu from it. 

So to be clear, i'm trying to bind my bouton 8 from my mouse, to do like a Control+Alt_L+U
Which will open USP. 

So I set up my .xbindkeysrc like so:
```

"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[left]""
  m:0x0 + b:6
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[right]""
 m:0x0 + b:7
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Control_L]\[u]""
 m:0x0 + b:8
```

But obviously it doesn't work!

Please, what am I doing wrong?

---

