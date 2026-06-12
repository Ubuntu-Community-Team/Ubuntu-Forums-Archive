---
title: "Left &amp; Right Keys"
date: 2007-02-22
forum: General Help
---

### Post by erugalatha on 2007-02-22
Hello,

My left and right arrow keys have stopped working.  Even in a terminal they won't work to move the cursor left or right in a command that has been typed in.

How do I get them working again?

Thanks for any help.

---

### Post by cronholio on 2007-02-22
Sounds like a hardware problem. Can you use them in the BIOS menu (press DEL or F2 at boot time)?

---

### Post by erugalatha on 2007-02-22
Yeh, they work fine in the BIOS .... could it be something to do with Beryl/XGL maybe?

---

### Post by cronholio on 2007-02-22
Press Ctrl-Alt-F2. Can you use them in text mode?

(Press Ctrl-Alt-F7 to return.)

---

### Post by erugalatha on 2007-02-22
Yes, they work in text mode too.

---

### Post by cronholio on 2007-02-22
At least we have narrowed the problem down a bit. I doubt it is related to Beryl but I have no clue what else it could be, so give it a try and switch back to standard Metacity and see if it works.

```
metacity --replace
``` or 
```
killall beryl
```should do it.

---

### Post by erugalatha on 2007-02-22
ok .... I right-clicked on the diamond for Beryl svn and chose metacity as my window manager and now the keys work.  It must be Beryl causing a problem.

my ctrl+alt + left and right does not allow me to switch viewports either while beryl is running.

Do you know of a way to fix these keys to work with beryl?

---

### Post by cronholio on 2007-02-22
Looks like a Beryl bug, it would be best to report it or post it on [the Beryl forums.]("http://forum.beryl-project.org/")

---

