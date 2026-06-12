---
title: "How do I increase console scrollback buffer"
date: 2007-04-15
forum: General Help
---

### Post by x1a4 on 2007-04-15
Hi,

How do I increase the amount of lines I can scroll back in the Console? 

Thank you.

---

### Post by motin on 2007-04-15
> **x1a4 said:**
> Hi,

How do I increase the amount of lines I can scroll back in the Console? 

Thank you.

In gnome-terminal or one of the Alt + Ctrl + Fn terminals?

Gnome-terminal: Check the menu therein for settings - there you can change it. 

For the tty's - I don't know.

---

### Post by x1a4 on 2007-04-15
Console=what you get when you Ctrl+Alt+F#
Terminal=Console emulator.  Examples include RXvt, xfterm4, xterm

I need to be able to scroll back more than 6 pages (what it's set to now) in the **Console**.

---

### Post by x1a4 on 2007-04-16
Would *fbset* do the trick?

---

### Post by jfinkels on 2007-04-16
If you don't figure anything out, you can insert your output into a file, or view it with less (you probably already know these, but why not...).

```

#view with less
*programfoo* | less

#insert into file
*programfoo* > *somefilebar*

```

---

### Post by x1a4 on 2007-04-20
So how do I do it?  Increase console scrollback buffer.

---

### Post by x1a4 on 2007-05-24
So how do I do it?  Anyone....

---

### Post by gotonpo on 2007-08-29
sorry to resurrect an old thread... but was there ever a solution found to this?

---

### Post by forestpixie on 2007-08-29
if you open terminal - edit profiles

then edit the profile, ther's a tab for scrolling

---

### Post by gotonpo on 2007-08-30
I have a large scrollback in the terminal, but I'm looking to increase the buffer in the tty consoles.. anyone know how to do this?

---

