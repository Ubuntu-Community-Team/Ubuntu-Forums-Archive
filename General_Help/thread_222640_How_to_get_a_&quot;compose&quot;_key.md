---
title: "How to get a &quot;compose&quot; key?"
date: 2006-07-25
forum: General Help
---

### Post by johann_p on 2006-07-25
I am using Ubuntu on computers with German (no dead keys) and US keyboards, but recently I need to type accented characters of other languages a lot. A long time ago, under Solaris, I had a "compose" key that would allow me to create all of these accented characters by pressing and holding compose and then typing to other keys.

For instance in order to get a Spanish enje I would press compose and then n and ~. To get an e with a circumflex, compose and then e and ^. To get a swedish O with a slash I would press compose then O and / and so on.

Is there a way to configure Ubuntu so that one of those keys I never use becomes such a "compose" key? 

I am using an ordinary Windows keybord and the "Start" key does not seem to have any function I ever need.

---

### Post by viciouslime on 2006-07-25
Hi, goto, system preferences, keyboard, layout options. There you will find a drop down menu where you can set the compose key. I have a UK keyboard and find it very useful for typing German.

---

### Post by johann_p on 2006-07-25
> **viciouslime said:**
> Hi, goto, system preferences, keyboard, layout options. There you will find a drop down menu where you can set the compose key. I have a UK keyboard and find it very useful for typing German.

Ah thank you!
This works fine, but it seems only for certain keys that can be assigned.

For the record, I have in the meantime found another solution:
1) use xev to find the keycode of the desired key -- in my case, ScrollLock which is 78 with my keyboard.
2) create a file .Xmodmap that containes the line
"keycode 78 = Multi_key"

Ubuntu recognizes this file when you next log in and asks if it should be loaded on each login. If you select yes, the ScrollLock key will be assigned the Compose function.

---

### Post by viciouslime on 2006-07-26
Wow, that's cool. Do you just put the file in your home directory or does it go into one of the '.something' folders?

---

### Post by johann_p on 2006-07-26
> **viciouslime said:**
> Wow, that's cool. Do you just put the file in your home directory or does it go into one of the '.something' folders?
 I just created the file .Xmodmap in my home directory. The internet has lots of pages that explain how to use xmodmap configuration to change the behavior of the keyboard.

I wonder how the GNOME preferences -> keyboard settings come in here. Do they maintain their own xmodmap file somewhere hidden? And will these settings get loaded before or after the .Xmodmap file I created? 

As much as I like the nice GUIs and easy way to do things in GNOME, I hate the difficulty that is associated with finding out how things work under the hood and how one would need to extend these mechanisms for stuff that is not directly supported.

---

### Post by ryu kun on 2007-05-18
Thank you, it is nice to know of that hidden file.

---

