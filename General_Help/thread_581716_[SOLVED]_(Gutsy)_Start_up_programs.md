---
title: "[SOLVED] (Gutsy) Start up programs"
date: 2007-10-19
forum: General Help
---

### Post by Balazs_noob on 2007-10-19
sorry to bug you guys again but i have
another problem :)
i want a few program to start up after booting
in feisty i just had to go to system=>preference=>sessions
enter it and it was working.
but in Gutsy it doesn't, evan if i check the check box in 
Session Options. ( remember running applications )

Thanks in advance , Balázs :KS

---

### Post by Balazs_noob on 2007-10-19
nobody :confused:

---

### Post by jobbesat on 2007-10-19
I have the same problem and can't solve it

---

### Post by jobbesat on 2007-10-20
I solved in this way. try to see if you have a dir called autostart inside your /home/.config dir
If it's there, delete it and create a new one, it will work.
Otherwise, if you have a file called "autostart" inside the same dir, I tried to chage permissions (since it's write protected), but without success, so i just delete it with command
sudo rm autostart
and just create the dir autostart with command
mkdir autostart

---

### Post by FilmAficionado on 2007-10-20
I had the same "problem" since this is my first/second time using Linux and Ubuntu in particular. I know you said it didn't work, but this worked for me when I wanted Pidgin to start when my system boots (startup):

1. System > Preferences > Sessions > (Startup Programs tab) 
2. Click Add Program
3. Insert whatever name
4. Insert command for your program (e,g.: for Pidgin, it is simply **pidgin**), for Amarok it is simply amarok, etc.)

Does this work for you guys?

---

### Post by Balazs_noob on 2007-10-20
Thanks guys for your replies
 --> FilmAficionado
if i remember good then pidgin auto-starts always at start up
just like MSN , try any other software like firefox and it probably
won't work :(

--> jobbesat
your solution worked ;) i just had to make a 
autostart directory and delete autostart file :)

the Thread is solved

Thanks again guys 
Gutsy rocks
:guitar:

---

### Post by jobbesat on 2007-10-20
I'm happy for you!

---

