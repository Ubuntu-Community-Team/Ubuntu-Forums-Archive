---
title: "Switching to Kernel?"
date: 2008-07-02
forum: General Help
---

### Post by FLCL on 2008-07-02
I was wondering how i would go about switching to kernel rather than GUI of ubuntu, aslo, how to switch back into the GUI of ubuntu from kernel. can anyone help me out with that? Don't like it when people try to use my computer, so im going to make it hard for them ;)

---

### Post by iaculallad on 2008-07-02
> **FLCL said:**
> I was wondering how i would go about switching to kernel rather than GUI of ubuntu, aslo, how to switch back into the GUI of ubuntu from kernel. can anyone help me out with that? Don't like it when people try to use my computer, so im going to make it hard for them ;)

If what you're trying to say is entering the Virtual Terminal(s): 

Press Ctrl+Alt+F1 to go to Terminal 1. Pressing Ctrl+Alt+F7 would bring you back to your GUI.

---

### Post by FLCL on 2008-07-03
Is there anyway to have it boot the way server boots? Strictly command?

---

### Post by angry_johnnie on 2008-07-03
You could go to system > administration > services, and then disable gdm.

You would boot into a terminal login.

To get back to the desktop, you would have to type either

```
sudo /etc/init.d/gdm start
```

to get the whole graphical login

or

```
startx
```

to go right into the desktop.

To get it to boot directly into GUI again, you'd have to re-enable gdm (system > administration > services)

EDIT:

You could create a file in your /home folder, called .xinitrc, which is sort of a pointer for the startx command, in case you don't want it to go directly into GNOME.

More info [here]("https://wiki.ubuntu.com/CustomXSession"),

---

