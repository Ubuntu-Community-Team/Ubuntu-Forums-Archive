---
title: "gnome-lokkit will not run"
date: 2007-10-26
forum: General Help
---

### Post by Johnny K on 2007-10-26
Several people have asked this question before ([[1]]("http://ubuntuforums.org/showthread.php?t=375747") [[2]]("http://ubuntuforums.org/showthread.php?t=497937") [[3]]("http://ubuntuforums.org/showthread.php?t=352596")), but no one received an answer. I hope you all don't mind that I'm bringing it up again, but it seems like alot of people are having trouble with this.

When I try to run **gksudo gnome-lokkit** from terminal, I get the following message:
```
Gdk-ERROR **: BadDrawable (invalid Pixmap or Window parameter)
  serial 56 error_code 9 request_code 145 minor_code 5
Gdk-ERROR **: BadDrawable (invalid Pixmap or Window parameter)
  serial 57 error_code 9 request_code 55 minor_code 0

```

Does anybody have any idea what is causing this? According to what I read, the problem is worse in Gutsy than in Feisty. In Feisty, the dialog popped up, but produced that message upon the user clicking "Next". In Gutsy, the dialog never even pops up, the message is displayed immediately.

---

### Post by Johnny K on 2007-11-15
Interesting update...

I realized that running **gksudo lokkit** from terminal displays lokkit in terminal (lokkit_screenshot1.png). If you try to interact with the program, though, you end up interacting with terminal itself (lokkit_screenshot2.png). Is this a bug?

***edit:*** I just realized that running **sudo lokkit** from terminal allows lokkit to run normally in terminal. I also just realized that my original problem was not with lokkit, but with gnome-lokkit. I am still unabme to get gnome-lokkit to run in any way.

---

