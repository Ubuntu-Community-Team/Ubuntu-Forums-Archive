---
title: "Computer crashes"
date: 2013-05-30
forum: General Help
---

### Post by scarabcoder on 2013-05-30
My Ubuntu (12.04) crashes every now and then, displaying error text. I can't find the problem. Sometimes, I can still move the mouse, and when it goes over a text field (I can't see the screen), it will turn into the text mouse. Is it a video card issue, or an Ubuntu error? Please help.
Also, I get errors on my computer popping up a lot. Any way to fix this? I am also getting errors when I install stuff from the Software Center.

---

### Post by lykwydchykyn on 2013-05-31
Your graphics problem sounds like a driver issue.   Do you know what kind of graphics hardware is in your system?  If not, this command entered into the terminal can tell you:

```

lspci |grep -i vga

```

As for the errors... you need to be more specific.  I'm guessing the errors contain text, and that text probably contains information about what's actually wrong and possibly how to fix it.  The next time you get an error, post the text to the forum.

---

