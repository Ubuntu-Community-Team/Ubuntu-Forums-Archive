---
title: "Panel1&amp;2 task bar"
date: 2007-04-13
forum: General Help
---

### Post by Kizilbas on 2007-04-13
Hi, my sister turn the pc off from the switch & now the too panels that were at the top & bottom of the screen have disappeared.

Luckily I had a shortcut to the terminal on my desktop.

How can I get my panels back by typing in commands at the terminal. Ok, so can I create a new account that is root privileged and copy my personal files on the account I'm currently using now on CDs and then delete this current account because it doesn't have the panels and I can't access the Applications menu or anything from here.

The way I was able to access my browser was by typing in 'firefox' without the quotes in the Terminal I had on my desktop to as shortcut to.

Please help me :)

Thank you


(I know its a funny case)

lol

---

### Post by murlosad on 2007-04-13
try typing > gnome-panel

you may also want to try> nautilus and if you don't have any window decorations type > metacity

/type those into your terminal, you probably will only need the first one though. :)

---

### Post by Kizilbas on 2007-04-13
Murlosad thank you, but they didn't work.

---

### Post by jocko on 2007-04-13
I think this will do it:
```
gconftool-2 --recursive-unset /apps/panel
killall gnome-panel

```

---

### Post by Kizilbas on 2007-04-13
> **jocko said:**
> I think this will do it:
```
gconftool-2 --recursive-unset /apps/panel
killall gnome-panel

```

no, no hope..

---

### Post by jocko on 2007-04-13
Oh, sorry, I just assumed you use Ubuntu (gnome).
Now I see you use xubuntu, which means I probably won't be able to help you...

What happens if you try to run 'xfce4-panel' from a terminal?

---

### Post by Kizilbas on 2007-04-13
lol ok

anyone there to help me?

How can I create a new account with root privileges and delete this current stupid account?

Probably that'll be the only way to get around :(... :'(..

---

### Post by aysiu on 2007-04-13
Did you try running ```
xfce4-panel &
``` or not?

---

