---
title: "Terminal- autocomplete doesn't work"
date: 2018-04-30
forum: General Help
---

### Post by PDA1 on 2018-04-30
I upgraded from Ubuntu 12.04 to Ubuntu Mate 18.04 and all is well.

However, Terminal doesn't auto-complete like it did when using 12.04.

Here's an example when in terminal command line

PDA1$  pdftk A=Filename.pdf   

When I type "A=" and then type "File"  (or Fi) terminal doesn't auto-complete the name of the file UNLESS I put a space between the = sign and type the name of the file and then go back and delete the space (so the command will work).  In 12.04 I didn't need to add the space but in Mate 18.04 I do.

Do you know how I can fix this problem?

Thank you,

Peter

---

### Post by pqwoerituytrueiwoq on 2018-04-30
[FONT=courier new]cp /etc/skel/.bashrc ~/.bashrc[/FONT]
start a new terminal instance to see if it fixed it
If you have anything custom in your .bashrc you may want to back it up

---

### Post by PDA1 on 2018-04-30
Nuts.  Nothing changed.  Still the same problem.

---

