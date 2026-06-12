---
title: "Dvorak Help Needed"
date: 2007-11-21
forum: General Help
---

### Post by nutter78 on 2007-11-21
Hi All
I've just made the switch to dvorak, but have hit a huge snag!  :confused: :(
How do I enable Ubuntu(not X or gnome etc) to recognise dvorak.
In other words, if I hit cntl-alt-F2 - how can i get tty2 to recognise dvorak??


Thx in advance

---

### Post by tragicglee on 2007-11-21
> sudo dpkg-reconfigure console-setup 
^ On 7.10, at least. The option's on the third screen in.

Under Dapper, you can temporarily change with: > sudo loadkeys /usr/share/keymaps/i386/dvorak/dvorak*TAB to get a list of file names because I forget exactly*  but it doesn't seem to work in Gutsy, and I'm unsure about Edgy or Feisty.

---

### Post by der_joachim on 2007-11-21
Or if you prefer to edit by hand, open /etc/default/console-setup in your favourite text editor and change the following line:
> 
XKBLAYOUT="us(us)" #<-- or whatever your current layout is.

to
> 
XKBLAYOUT="us(dvorak)"


---

### Post by nutter78 on 2007-11-22
Thx Guys - will give these solutions a try, & will report back!

---

### Post by nutter78 on 2007-11-22
Hi tragicglee
> **tragicglee said:**
> sudo dpkg-reconfigure console-setup
 Thanks very much - this seemed to do the trick!!!!  :)

:guitar: :guitar: :guitar:

---

### Post by nutter78 on 2007-11-22
> **der_joachim said:**
> Or if you prefer to edit by hand, open /etc/default/console-setup in your favourite text editor and change the following line:
 XKBLAYOUT="us(us)" #<-- or whatever your current layout is.
to
Quote:
XKBLAYOUT="us(dvorak)"


Hi - looking @ this - it seems it would just change the "X" environment!

---

### Post by der_joachim on 2007-11-22
> **nutter78 said:**
> Hi - looking @ this - it seems it would just change the "X" environment!

IIRC, both X and the console use the [XKB]("http://en.wikipedia.org/wiki/XKB") protocol.

---

### Post by nutter78 on 2007-11-22
> **der_joachim said:**
> IIRC, both X and the console use the [XKB]("http://en.wikipedia.org/wiki/XKB") protocol.

You r most probably right - as i'm really new to Linux. Thanks 4 your reply though - this is what makes ubuntu so great!

---

### Post by lsl on 2007-12-06
Doesn't seem to work in KDE.

---

