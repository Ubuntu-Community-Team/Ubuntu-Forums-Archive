---
title: "[SOLVED] gnome menu item dissapeared..."
date: 2007-09-28
forum: General Help
---

### Post by pixeltarian on 2007-09-28
my audio/video folder is gone... I would just re-add it but it's a bit hard to do because the gnome menu editor is buggy (drag/drop movement either doesn't work or doesn't show up unless I restart the menu editor, anyone have a fix for that?!) and, I don't know the name of every program I installed because I just grabbed all the ubuntu studio programs from the repo. 

So I the main question is: Is there a fix for the buggy menu editor.  

and should I just reinstall the ubuntu studio application suite to get the menu back? 

I tried reseting the menu, but that didn't bring anything back, it just renamed my custom folders to "alacarte-something-or-other"

any help or pointers on how to better diagnose the problem would be greatly appreciated, 

thank you so much, 

- pix

---

### Post by Wolki on 2007-09-28
> **pixeltarian said:**
> any help or pointers on how to better diagnose the problem would be greatly appreciated, 


Please post the contents of your /.config/menus/applications.menu file. It may be large, so it would be best if you could put it in code tags or attach it.

---

### Post by pixeltarian on 2007-09-28
> **Wolki said:**
> Please post the contents of your /.config/menus/applications.menu file. It may be large, so it would be best if you could put it in code tags or attach it.

hmmm... how do I do that ?

---

### Post by PurposeOfReason on 2007-09-28
In the terminal.
```
sudo gedit ~/.config/menus/applications.menu
```

---

### Post by FuturePilot on 2007-09-28
> **PurposeOfReason said:**
> In the terminal.
```
sudo gedit ~/.config/menus/applications.menu
```

There's no need for sudo to do that since it's in the home folder. Also another way to do it would be ```
cat ~/.config/menus/applications.menu
```

---

### Post by pixeltarian on 2007-09-28
here it is...

---

### Post by Wolki on 2007-09-28
Try replacing it with this one.

To do this, copy it into your ~/.config/menus/ directory and rename it to applications.menu (removing the already existing applications.menu file first), or do the following on the command line: "mv menu.txt /.config/menus/applications.menu" You need to be in the directory containing menu.txt.

Since I can't try it without the rest of your configuration, I'm not sure it's solved, but it was quite interesting. The Multimedia menu was moved to a submenu below itself - I wonder how that happened...

---

### Post by pixeltarian on 2007-09-28
> **Wolki said:**
> Try replacing it with this one.

To do this, copy it into your ~/.config/menus/ directory and rename it to applications.menu (removing the already existing applications.menu file first), or do the following on the command line: "mv menu.txt /.config/menus/applications.menu" You need to be in the directory containing menu.txt.

Since I can't try it without the rest of your configuration, I'm not sure it's solved, but it was quite interesting. The Multimedia menu was moved to a submenu below itself - I wonder how that happened...

thanks a lot, that worked! 
=================

anyone: 
has there been any talk about the glitchy-ness of dragging and dropping applications into submenus? sometimes the drag and drop doesn't work at all (and I try over and over like 20 times) and usually when it does work I have to close and reopen "edit menus" for it to show up. I can't be the only one who has experienced this. is there a fix for it? 

thanks again Wolki for the fix. I really appreciate it.

---

### Post by Wolki on 2007-09-28
Great to hear that it worked. Mind marking this thread as solved?

> **pixeltarian said:**
> has there been any talk about the glitchy-ness of dragging and dropping applications into submenus?

I rarely do that, when I last did I think it more or less worked ok. I'm sure the developers would appreciate a bug report if you have problems though.

[edit] Here's the bug of what happend in your case, it was already known: [https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/133668](https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/133668)
[edit2] Or not? I can't reproduce it.

---

### Post by pixeltarian on 2007-09-29
> **Wolki said:**
> Great to hear that it worked. Mind marking this thread as solved?



I rarely do that, when I last did I think it more or less worked ok. I'm sure the developers would appreciate a bug report if you have problems though.

[edit] Here's the bug of what happend in your case, it was already known: [https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/133668](https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/133668)
[edit2] Or not? I can't reproduce it.

yes. I think I'll do one of those fancy screencasts when I get around to it... it's so hard to explain bugs...

---

