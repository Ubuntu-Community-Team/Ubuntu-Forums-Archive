---
title: "taking a screenshot of a console"
date: 2007-05-26
forum: General Help
---

### Post by fakie_flip on 2007-05-26
How can I take a screenshot of a tty console?

---

### Post by yabbadabbadont on 2007-05-26
If you use the framebuffer console, then you can use fbgrab I believe.  Otherwise, run GPM and use your mouse to select the text and paste it into a file on another screen.

---

### Post by WW on 2007-05-26
This might not be the kind of screen shot that you want, but for what it's worth:

You can dump the contents of a tty console to a file with the **setterm** command.  For example, to get the contents of console 2 (i.e. the console used when ctrl-alt-F2 is pressed), you can give this command (in another console, or in a terminal in your X session):
```

sudo setterm -dump 2

```
This creates the file screen.dump.  The file is a text file containing whatever text is on the console.  (It may also have special characters for screen attributes such as color; I'm not sure how it handles that.)

More details [here]("http://www.tldp.org/HOWTO/Keyboard-and-Console-HOWTO-20.html").

---

### Post by fakie_flip on 2007-05-27
> **yabbadabbadont said:**
> If you use the framebuffer console, then you can use fbgrab I believe.  Otherwise, run GPM and use your mouse to select the text and paste it into a file on another screen.

What is a framebuffer console? What is the difference? When I run finch, it does not display borders correctly in the tty consoles. Instead it is showing strange characters where the borders should be.

---

