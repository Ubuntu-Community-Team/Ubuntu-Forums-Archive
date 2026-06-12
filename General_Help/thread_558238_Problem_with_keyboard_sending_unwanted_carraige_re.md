---
title: "Problem with keyboard sending unwanted carraige returns?"
date: 2007-09-23
forum: General Help
---

### Post by BlueSpam on 2007-09-23
Hi everyone, I hope this is the correct place to post. I just installed Feisty on my laptop (Toshiba M45-S165) and so far so good, except for one annoying problem - when I'm typing and press shift-a, shift-b, or shift-n I get a carraige return and then the uppercase letter I try and type. This obviously is making typing documents or working at the command line almost impossible, does anyone have any ideas?

Thanks

---

### Post by ddrichardson on 2007-09-24
Use xev from the terminal:```
xev
```
Try the troublesome key combinations then see what keycode is reported in xev. Do the same again using the other shift key and see if the scan codes are different.

You can use xbindkeys to reassign the keycode - there's a guide [here]("http://www.howtoforge.com/linux_multimedia_keyboard").

---

