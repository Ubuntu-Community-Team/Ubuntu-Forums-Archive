---
title: "Logitech Cordless Keyboard EX110 - anyone have, and if so does your X shortcut work"
date: 2007-05-06
forum: General Help
---

### Post by wulfhound on 2007-05-06
I am assuming I got a defective keyboard, since this keyboard's shortcut buttons all work perfectly with Ubuntu Edgy except for the X shortcut key, on the left of the keyboard right above the left pointing arrow button shortcut key.

I also wonder what is that key's shortcut (if someone has it that works) code. Because the left arrow pointing key shortcut is. Some of them are like 0xa1 and such. I wonder if I type the one that corresponds to that key, if I could see if it is defective. 

Sandaili

---

### Post by wulfhound on 2007-05-06
I also just realized, where can I actually manually edit the shortcut keys? I want to be able to type into the Close shortcut :XF86Close (if that's the shortcut name for closing it) and see if it works, but of course Ubuntu won't let me do that in the shortcut key assignment window.

Anyone know how?

Thanks,

Sandaili'

---

### Post by strabes on 2007-05-06
I believe it's in gconf-editor under /apps/metacity/keybinding_commands and global_keybindings. I wrote a blog post about this awhile ago: [http://strabes.wordpress.com/2006/11/13/create-custom-keyboard-shortcuts-in-ubuntu/](http://strabes.wordpress.com/2006/11/13/create-custom-keyboard-shortcuts-in-ubuntu/)

I'm not sure if you can enter "XF86Close" in there or not but it's worth a try.

---

