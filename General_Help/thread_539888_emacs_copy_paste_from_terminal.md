---
title: "emacs copy paste from terminal"
date: 2007-08-31
forum: General Help
---

### Post by ecoxmit on 2007-08-31
When trying to run emacs inside konsole, or gnome-terminal (emacs-nox), i loose the ability to paste to other programs the selection from emacs. 

In particular, the proposed solution of adding to .emacs the following lines:

```
(setq x-select-enable-clipboard t)
(setq interprogram-paste-function 'x-cut-buffer-or-selection-value)

```

which works beautifully when emacs is loaded outside a terminal (in its own x-window), doesn't work anymore when running emacs inside the terminal. 

Yanking from the terminal returns a "Symbol's function definition is void: x-cut-buffer-or-selection-value". 

Any help?

---

### Post by bogolisk on 2007-08-31
> **ecoxmit said:**
> When trying to run emacs inside konsole, or gnome-terminal (emacs-nox), i loose the ability to paste to other programs the selection from emacs. 

In particular, the proposed solution of adding to .emacs the following lines:

```
(setq x-select-enable-clipboard t)
(setq interprogram-paste-function 'x-cut-buffer-or-selection-value)

```

which works beautifully when emacs is loaded outside a terminal (in its own x-window), doesn't work anymore when running emacs inside the terminal. 

Yanking from the terminal returns a "Symbol's function definition is void: x-cut-buffer-or-selection-value". 

Any help?

I think that's expected, isn't it! emacs in a terminal is **not** an X program so it won't be able to create or use an X-selection! Also AFAIR, emacs-nox is not event linked to Xlib.

---

### Post by ecoxmit on 2007-09-01
any ideas then on how to copy/paste something from emacs into another program? 

(thing is, i did manage to get the opposite to work, i can paste into emacs in the terminal from other apps)

---

### Post by bogolisk on 2007-09-01
> **ecoxmit said:**
> any ideas then on how to copy/paste something from emacs into another program? 

(thing is, i did manage to get the opposite to work, i can paste into emacs in the terminal from other apps)

Actually, you pasted into the terminal, and the terminal simulate keystrokes and send them to emacs. The point is to use the mouse to select/paste text into/from the terminal (that run emacs).

---

### Post by ecoxmit on 2007-09-02
bobolisk, using the mouse is too restrictive: you can only copy/paste things that fit into one length of the terminal window. 

No more ideas?

---

### Post by bogolisk on 2007-09-04
> **ecoxmit said:**
> bobolisk, using the mouse is too restrictive: you can only copy/paste things that fit into one length of the terminal window. 

No more ideas?

Sorry, I can't think any other way. Something which might work for you is to run the write-region command (M-x write-region) to the emacs's selection into a file then figure away to use that file in your other programs.

---

### Post by ecoxmit on 2007-09-04
thanks.. i'll see what i do then

---

### Post by eph1973 on 2007-09-04
Out of curiosity, must you use emacs?  i.e. would xemacs suit your needs?  You can run xemacs from the terminal and do all the copying and pasting you like between windows, and it is very similar to emacs.

---

### Post by BLTicklemonster on 2007-09-04
Speaking of Terminal, isn't it about time someone updated it so that you can use ctrl+c and ctrl+v instead of manually clicking a mouse in it and right clicking?

---

### Post by bogolisk on 2007-09-04
> **BLTicklemonster said:**
> Speaking of Terminal, isn't it about time someone updated it so that you can use ctrl+c and ctrl+v instead of manually clicking a mouse in it and right clicking?

In the Terminal, you just  have to add Shift (Sh-Ctl-c, Sh-Ctl-v). Ctl-c and Ctl-v are reserved for (and sent to) the application running in the Terminal.

---

### Post by bogolisk on 2007-09-04
> **eph1973 said:**
> Out of curiosity, must you use emacs?  i.e. would xemacs suit your needs?  You can run xemacs from the terminal and do all the copying and pasting you like between windows, and it is very similar to emacs.

I don't see how xemacs would do better than gnu-emacs for original question: cutting the emacs's region and paste it to a X prorgram.

---

### Post by BLTicklemonster on 2007-09-04
No way. Just add shift to it all, and that's it? Ain't that just a slap in the head.

THANK YOU!

---

### Post by ecoxmit on 2007-09-04
**eph1973**, yes, I could go back and use emacs outside the terminal (either xemacs or standard one). 
Although I do prefer working on the terminal instead.

---

### Post by yenliangl on 2007-12-17
Can you try to use mouse to copy the region you want, and click middle-button to paste?

(xterm-mouse-mode may be required. :) )

--
josh

---

