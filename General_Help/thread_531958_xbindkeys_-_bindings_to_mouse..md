---
title: "xbindkeys - bindings to mouse."
date: 2007-08-22
forum: General Help
---

### Post by evissecx on 2007-08-22
Hi, I have looked around the forum but haven't found the answer about binding
a mouse button to the mouse. What I want to do is to bind 

**Super + button 1 to button 8**

on my mx518. All I see is how to bind Alt_L + right/left to a mouse button.
Wich is great too. I use it. 
Here is my .xbindkeysrc file. 

[B]"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:6
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:7[/B]

So I have been testing it on my own a bit. But didn't get it to work.
this is the binding I want. But it doesn't work like that.
[B]
"/usr/bin/xvkbd -xsendevent -text "\[Super]\[button 1]""
  m:0x0 + b:8[/B]

With this binding, I will be able to move windows with only the mouse without having to grab the titlebar. 
Any ideas?

Thanks in advance!

---

