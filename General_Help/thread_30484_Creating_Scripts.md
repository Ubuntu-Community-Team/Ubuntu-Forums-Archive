---
title: "Creating Scripts"
date: 2005-04-28
forum: General Help
---

### Post by xjb2003x on 2005-04-28
Let me explain what I would like to do, hopefully someone can point me to an info doc about how to do it :)

When I pull up a terminal window and type startup, I would like to have some programs startup.  Being the n00b that I am, I know you have to obviously know the path to the file and everything.  Let's take XMMS for example.  If I type startup in a terminal, I want XMMS to startup. Can anyone help?

Much appreciation in advance :)

---

### Post by Professor X on 2005-04-28
Edit the file .bashrc and add the line ```
xmms &
```.  I don't know why you would want to start xmms though.  Add ```
fortune
``` to your .bashrc if you want a random quote whenever you load a terminal.

Hope that helps.

---

### Post by nad on 2005-04-28
vi startup

(insert)

xmms &

(esc)

ZZ

chmod a+x startup

./startup

---

### Post by soce_32 on 2005-04-28
If you just want to launch a bunch of programs, 

#!/bin/bash
xmms
otherprogram
someotherthing

and so on.  This is a simple as it gets and assumes that all of those commands are in your PATH.  You can find out where commands are by using which, whereis or locate and add that to your script.

#!/bin/bash
/usr/bin/xmms

If you are just looking to launch applications upon login that do not understand session management, like firefox and thunderbird, you do not need a script.  You can link them in ~/Desktop/Autostart and they will fire up when you log in.

ln -s /usr/bin/xmms ~/Desktop/Autostart/

---

### Post by nad on 2005-04-28
LOL 

Fortune!

How long have you been around?

---

### Post by Professor X on 2005-04-28
[QUOTE=nad]LOL 

Fortune!

How long have you been around?[/QUOTE]
 I've been a fortune user since 2001.

---

