---
title: "[SOLVED] printscreen/screen capture isnt working"
date: 2007-09-23
forum: General Help
---

### Post by Chymera on 2007-09-23
ok, so my keyboard is mapped right, the printscreen button works, its correctly set on the keyboard shortcuts list.... but for some reason it doesn't work.... i tried setting some other key binding... but still nothing.

I can only take screenz through accessories>take screenshot, or through the compiz plugin (but that requires me to drag a box around what i want to capture, which is impossible if for example i want to photograph my cube...

any ideas?

---

### Post by beyboo on 2007-09-23
> **Chymera said:**
> ok, so my keyboard is mapped right, the printscreen button works, 
any ideas?

maybe a stupid question - how do you know it works ?

I've gpt an MS keyboard and th've got this F Lock key I need to press everytime I want to use the prtscn function out of the 3 possible combos they got on that !!

---

### Post by Chymera on 2007-09-23
hmmmm... i set it as a shortcut key for something else, and it worked... pretty shrewd eh?

(just joking, even an idiot would have thought of it :p )

---

### Post by strabes on 2007-09-23
You can use gconf-editor to set custom keyboard shortcuts. Check [this page](http://strabes.wordpress.com/2006/11/13/create-custom-keyboard-shortcuts-in-ubuntu/) for how to do that. You'll have to find out the name of the key using the keyboard shortcuts window. Here's the command you should set it to:

```
gnome-screenshot --interactive
```

---

### Post by Chymera on 2007-09-23
it has nothing to do with the keyboard.... i tried to set the shortcut keys to smth else, it didnt work! I tried to set the printscreen key to smth else, it worked! The printscreen operation is faulty....

---

### Post by Chymera on 2007-09-26
anyone?

---

### Post by strabes on 2007-09-26
Did you try to do what I said or did you just ignore it because you didn't understand?

---

### Post by Chymera on 2007-09-29
yes, i tried it, but that wasn't the command i needed... anyways, that was the right approach... if anyone else gets this problem, just run these lines one at a time if you dont know how to edit the gconf entries manually.... you may want to make sure command 7 or whatever number you choose isnt already taken.... but unless you've done a lot of customizing on your comp it probably isn't

gconftool-7 -t str --set /apps/metacity/global_keybindings/run_command_9 "Print"
gconftool-7 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-screenshot"

---

