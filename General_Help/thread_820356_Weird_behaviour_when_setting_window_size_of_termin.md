---
title: "Weird behaviour when setting window size of terminal"
date: 2008-06-06
forum: General Help
---

### Post by bejurne on 2008-06-06
I am trying to set the window size of the terminal. 

To do this, I went to window rules in the Compiz Settings Manager and set the size of "class=Gnome-terminal". The weird thing is, that it only works occasionally. In about 50% of the cases it opens with the correct size and in the others it opens with the default size. I tried opening and closing it several times in succession and there seems to be no pattern to when it opens with the correct size and when not. When I minimize a window with the wrong size it will maximize to the correct size though. Really weird... I tried all sorts of things but couldn't find the reason for this behaviour.

This seems to be specific to setting the window size of the terminal, since making the terminal sticky and setting the window position in Place Windows works all the time. Setting the size works perfectly with other applications like gedit or firefox.

Is there maybe an error log of compiz, I could have a look at?

Btw, I use Ubuntu Hardy with all the latest updates.

---

### Post by chewearn on 2008-06-06
You can use --geometry switch to set the terminal window size without any need to use compiz.

E.g.
```
gnome-terminal --geometry=80x50
```

will open the terminal with 80 characters across by 50 lines down.

.

---

### Post by bejurne on 2008-06-09
Thanks, this works perfectly.

Although it doesn't solve the bug, it is exactly what I needed.

...still curious what caused this weird behaviour though.

---

