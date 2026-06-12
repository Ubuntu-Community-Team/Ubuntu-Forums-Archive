---
title: "Shell Keyboard Layout"
date: 2004-11-04
forum: General Help
---

### Post by luiska on 2004-11-04
Hi 

Ubuntu installation doesn't ask for a keyboard map during installation. Fair enough it is easy enough to change it in Gnome and I figured out how to add my locale. But, when I do Alt-F1 and go to a virtual console my keyboard is not having the right keymap. 

Where do I setup the keyboard for that? 

thanks 
Luiska

---

### Post by luiska on 2004-11-05
Answering my own post: 
I googled a little bit more and found that 

loadkeys fi-latin1

in the console does the trick. Havent restarted the machine yet to see if the map stays in place but that will be easy enough to change with a entry in /etc/profile or something.

Hope this help someone else too!

Luiska

---

### Post by luiska on 2004-11-05
Hi Again

What a monologue!!!

sudo dpkg-reconfigure console-data

After that the finnish keymap was loaded by default when the system booted.

Louis

---

### Post by ubik on 2004-11-10
Your monologue was a great help to solve my keymap pb
I had the same VT switching problem and also missing keys but now it's over  :razz: 
I'm not very familiar with "dpkg-reconfigure", i was trying to find what config file loads keymaps but without any success.
so, thank you!

---

