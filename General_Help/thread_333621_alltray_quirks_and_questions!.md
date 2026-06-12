---
title: "alltray quirks and questions!"
date: 2007-01-07
forum: General Help
---

### Post by tich on 2007-01-07
i installed alltray and have been running it for about a day which has led me to believe that it is a handy little tool but also to some quandaries:

when i open a program with alltray from a command line (such as 'alltray firefox') it opens minimized --is there a way to have it open automatically in a window (but not necessarily maximized)?

alltray doesn't seem to work with some programs (such as abiword) --has anyone else had this occur? is it normal? why does it happen?

i have had no luck in running alltray and then clicking on a window to put it in the systray.  it just doesn't work. the alltray info window appears telling me to click on a window, and my pointer changes but nothing happens when click on a window, i just have to cancel alltray.

and... is there anyway to just run alltray automatically for every app?  that would be awesome!  i could stop using the window list applet and just use the systray.  
i know that i can make icons (for the panel or desktop) with 'alltray' added before the app command but i would love if it just ran even if i picked something from the applications list.

---

### Post by 23meg on 2007-01-07
> 
when i open a program with alltray from a command line (such as 'alltray firefox') it opens minimized --is there a way to have it open automatically in a window (but not necessarily maximized)?
Use the -s option.> 
alltray doesn't seem to work with some programs (such as abiword) --has anyone else had this occur? is it normal? why does it happen?I haven't come across any.
> 
i have had no luck in running alltray and then clicking on a window to put it in the systray. it just doesn't work. the alltray info window appears telling me to click on a window, and my pointer changes but nothing happens when click on a window, i just have to cancel alltray.
Same here; I faintly recall it used to work in previous Ubuntu versions.
> and... is there anyway to just run alltray automatically for every app? that would be awesome! i could stop using the window list applet and just use the systray.
i know that i can make icons (for the panel or desktop) with 'alltray' added before the app command but i would love if it just ran even if i picked something from the applications list.You could modify each menu item with the menu editor to do that. Alltray's most serious limitation is that you can't drag and drop to applications you run with it; keep that in mind before you try this.

---

### Post by tich on 2007-01-07
thanks. you are fast i just finished reading that about the --show (-s) option.  i somehow missed it first time through the man.

---

### Post by 23meg on 2007-01-07
> i somehow missed it first time through the man.It's usually harder to miss if you search the manual pages before scanning through them.```
man *application* | grep *feature*
```

---

