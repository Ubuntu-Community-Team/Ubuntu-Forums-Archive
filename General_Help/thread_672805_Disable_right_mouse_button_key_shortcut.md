---
title: "Disable right mouse button key shortcut"
date: 2008-01-20
forum: General Help
---

### Post by mickthejew on 2008-01-20
On my notebook I have a "right mouse button" key, which for some reason in Ubuntu is really sensitive, often when I'm typing it will do crazy things like deleting a whole block of text or changing justification of a paragraph, at first I thought it was a touchpad problem (which I fixed already).  

I want to know if there is anyway I can disable this key as its driving me nuts!!

Thanks

---

### Post by PurposeOfReason on 2008-01-20
Explain this key more please. What kind of laptop? Is it basically tapping? To disable tapping while typing make sure your touchpad part of your xorg.conf has this line
```
    Option "SHMConfig" "on"
``` and the type this in the terminal
```
syndaemon -d -t -i 2
```.

Put in in your startup applications to always have it run.

---

### Post by mickthejew on 2008-01-20
its actually nothing to do with the touchpad at all.  Which is what i first though too.

The laptop is a Benq S53 Joybook.  

On the keyboard in between the right ALT key and Right CTRL key there is a button which if pressed acts as if it is the right mouse button, so bring up a menu, and if you are typing fast you can undo, cut, paste text without really knowing it.  For some reason its really really sensitive in Ubuntu, i never had this problem in Windows XP at all.

---

### Post by PurposeOfReason on 2008-01-20
That is a sleak looking notebook. So what I gather from the pictures, it's just a normal key just like a fn key? If that is that case (I'm surprised it worked it worked) I'm not sure it can be changed.

---

### Post by mickthejew on 2008-01-20
yeah its a pretty nice notebook.  Actually I thought I fixed that touchpad problem, but I added your commands and now the problem is fixed, so actually it wasn't the FN key at all, but the touchpad!

So thanks a lot for your help!

---

