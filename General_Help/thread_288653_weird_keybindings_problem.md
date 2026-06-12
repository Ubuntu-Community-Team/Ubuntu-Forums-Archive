---
title: "weird keybindings problem"
date: 2006-10-30
forum: General Help
---

### Post by dave_blob on 2006-10-30
fairly advanced keybindings question.

I have 15 or so multimedia keys that do nothing. Now what I mean by nothing, is that they generate no event in xev, *neither* do they generate unknown key errors in dmesg.

So the kernal obviously knows about them, but whats happening to the keypress events? 
showkey can see them, and i get e0xx codes. However, when i try to use setkeycodes to map these keys, i get:

dave@dave-ubuntu:~$ sudo setkeycodes e019 200
KDSETKEYCODE: No such device
failed to set scancode 99 to keycode 200

for *any* key I try to map, even the ones that work. 

Whats going on here? is setkeycodes broken?

---

### Post by dave_blob on 2006-10-31
no clues?

---

