---
title: "Starting a program by default in xterm during X startup"
date: 2007-07-17
forum: General Help
---

### Post by xavier_r on 2007-07-17
Heres the file /usr/share/xsessions/xterm.desktop for gdm...

[Desktop Entry]
Encoding=UTF-8
Name=xterm
Comment=[B]
Exec=xterm[/B]
Icon=
Type=Application

Now when 
Exec=xterm
it works fine...

But when I give 
Exec=xterm -e myProg

It shows an error...
But if in that open xterm i give the same command, ie., xterm -e myProg it works...

How to get rid of that error?

---

### Post by moore.bryan on 2007-07-17
*i don't know about .xsessions stuff, but what if you added the entry ```
xterm -e myProg &
``` to your .xinitrc file?*

---

### Post by vambo on 2007-07-17
Try

exec = "xterm -e <full_pat>.myprog"

---

### Post by xavier_r on 2007-07-17
xterm -e "myprog"
worked...
But i cant pass options to xterm...
For example...

xterm -geometry 160x58 -e "myProg"
doesnt work...

Any idea?

---

