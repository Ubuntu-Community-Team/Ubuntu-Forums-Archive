---
title: "Apache Start, Stop from Panel"
date: 2006-07-21
forum: General Help
---

### Post by Burgresso on 2006-07-21
Hello

I am trying to figure out how to make a link, button, drawer, or launcher that will launch, stop, and restart apache from a panel in GNome. Any ideas?

Gracias

burgresso

---

### Post by scxtt on 2006-07-21
try creating a 'custom application launcher' on the gnome panel w/ the command:
[indent]sudo /etc/init.d/apache2 start
sudo /etc/init.d/apache2 stop
sudo /etc/init.d/apache2 restart[/indent] ...it may require gksudo, not sure ...

---

### Post by Burgresso on 2006-07-21
I'll try that and tell you how it goes...thanks for the reply

---

### Post by scxtt on 2006-07-21
you're very welcome ...

i was curious myself after i posted that, so this is what i tried (it was in XFCE, cause that's where i have apache2 running):

1. added a custom launcher w/ **sudo /etc/init.d/apache2 stop**[indent]a. set it to 'run in terminal'[/indent]

result: it popped up a terminal asking me for my sudo pw - i entered it and apache2 was indeed stopped

2. edited launcher from 1 and used **gksudo /etc/init.d/apache2 stop**

result: got the sudo popup request, entered my pw and apache2 was stopped again

lookin' good to me :D

---

### Post by az on 2006-07-21
All you need is 
/etc/init.d/apache2 restart
and
/etc/init.d/apache2 stop

The restart script is smart enough to force-reload if apache2 is already running, instead of actually restarting.  It is also smart enough to start it if it is not already running.


Use sudo or gksudo....

---

### Post by scxtt on 2006-07-21
azz -

just cause i'm curious, what was the intention of your post? -- to summarize?
Burgresso already established that he was looking to stop/restart and i established using
**{sudo/gksudo} /etc/init.d/apache2 {stop/restart}** in conjunction w/ the panel, so i'm just wondering what exactly you were getting at ...

---

### Post by Anduu on 2006-07-22
> **scxtt said:**
> azz -

just cause i'm curious, what was the intention of your post? -- to summarize?
Burgresso already established that he was looking to stop/restart and i established using
**{sudo/gksudo} /etc/init.d/apache2 {stop/restart}** in conjunction w/ the panel, so i'm just wondering what exactly you were getting at ...

He was just clarifying the fact that the start command is not needed as restart works without giving an error message if Apache is already running.

---

### Post by scxtt on 2006-07-22
it wasn't an issue (and neither is this :p) but i just found it strange that he basically repeated the 'procedure' i'd outlined in more of a 'no, this is how you do it' way ... most likely all parties involved are aware of the 'start when already running' feature ...

---

### Post by Burgresso on 2006-07-28
Thanks for the replies for on this thread - very helpful. Now I just need to find cool icons to for start/stop/restart apache :)

---

