---
title: "Midnight Commander not displaying correctly"
date: 2007-01-29
forum: General Help
---

### Post by webwiz on 2007-01-29
[IMG]http://tech.telcove.com/ScreenshotError.jpg[/IMG]

What would be the cause of this??  How come it doesn't display correctly?   Is it because i use Aterm?

---

### Post by electronpusher on 2007-05-16
I'm having the same problem- I tried Midnight Commander with aterm, xterm and gnome-terminal and the problem only occured with aterm- so the problem must be connected with aterm- I still can't figure the cause though! I'd appreciate any ideas anyone has.

---

### Post by stylishpants on 2007-05-16
What is the result of this command?

echo $TERM

---

### Post by semka on 2007-05-16
This ---> xterm

---

### Post by semka on 2007-05-16
I need change lang for displaying correctly , now i have lang FR, and MC display not correctly like this : àààààààààààààààààààààààààààààààààààààààààààà    , and i need to change for lang EN , LANG=EN

how i can do this?

---

### Post by stylishpants on 2007-05-17
In both putty and aterm, mc seems to work if your LANG environment var is set to C.

Test it by running this command, which modifies the LANG environment variable only for the duration of that one command:

```
LANG=C mc
```

If that works, you could add LANG=C  to your ~/.bashrc to make it the default.

Or, to be a little more cautious, you could instead have only mc use the special LANG setting by aliasing it.  To do this, add the following line to ~/.bashrc:
```
alias mc="LANG=C mc"

```

---

