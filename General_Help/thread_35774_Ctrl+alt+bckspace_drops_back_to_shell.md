---
title: "Ctrl+alt+bckspace drops back to shell"
date: 2005-05-20
forum: General Help
---

### Post by Er00 on 2005-05-20
Hey, after googling for a bit I eventually came up with a thread from just over a monht ago in which someone had this issue, but couldn't see any solutions so figured I'd repost and see if anyone has any ideas.

Ok, obviously I'm running the live cd, it doesn't detect the refresh rate for the monitor, so I go and add the lines it needs, and then try restarting X. This worked twice a few days ago, and then I tried the day before yesterday and it just dropped be back into the shell...ever since then it's been doing the same thing.

Anyone got any ideas? As far as I know, nothing has changed from  when it worked to now, so basically any ideas as to why it doesn't work *shrugs*

Thanks :)

---

### Post by Zelut on 2005-05-20
I'm not sure I understand what your question is.  What drops back to the shell?

---

### Post by Er00 on 2005-05-20
When I use ctrl+alt+backspace it doesn't restart X, more like kills it and doesn't restart it again. If that makes it any clearer:/ sorry, not great at explaining stuff :)

---

### Post by Zelut on 2005-05-20
When I've used ctrl-alt-bckspace its never restarted X.  Its only dropped me back to the command line after killin' X.  If its worked for you before & since stopped I don't know what to tell you.  Its never restarted for me... but I didn't expect it to either.

You should be able to use: startx at the prompt to get it going again after you've changed your settings.  I hope that helps.

---

### Post by Er00 on 2005-05-20
As far as I can tell ctrl+alt+backspace is meant to restart X. As in, seen around 5 sources from ubuntu that say so :p

But meh, I guess I'll live, it's just one of those annoying things I want to solve, it's not really much of an issue, just like to know why it's started doing it.

---

### Post by angrykeyboarder on 2005-05-20
[QUOTE=Er00]As far as I can tell ctrl+alt+backspace is meant to restart X. As in, seen around 5 sources from ubuntu that say so :p

But meh, I guess I'll live, it's just one of those annoying things I want to solve, it's not really much of an issue, just like to know why it's started doing it.[/QUOTE]

Actually it is in fact supposed to restart X.  I've had the same problem you have had as well. However, I only have it happen maybe 1/4 of the time. Usually, X restarts like it's supposed to.

---

### Post by svmaris on 2005-05-21
[QUOTE=angrykeyboarder]Actually it is in fact supposed to restart X.  I've had the same problem you have had as well. However, I only have it happen maybe 1/4 of the time. Usually, X restarts like it's supposed to.[/QUOTE]

Actually, CTRL-ALT-BACKSPACE is support to _kill_ X. The fact that it's restarting is due to GDM (or XDM). When you start X.org with 'startx', it will not restart.

In fact, you really don't need to use this method to end your session. Just quit your desktop- or windowmanager.

I only use ctrl-alt-backspace when something _really_ went wrong and I can't exit X.org normally.

---

### Post by krusbjorn on 2005-05-21
ctrl-alt-backspace drops me back to shell with the" blah@blah login:"

i'm a noob, but i figured as much out as that it actually dropped me back in the "ctrl-alt-F1" shell. since X runs in the "ctrl-alt-F7" shell, i tried going there, and ended up with an blank screen (except there was some sort of character at the upper left corner.)

i dont know why, but i remember that i thought it was an nvidia driver issue. 

sorry for being unable to describe it better. my english ;)

---

### Post by svmaris on 2005-05-22
> i'm a noob, but i figured as much out as that it actually dropped me back in the "ctrl-alt-F1" shell. since X runs in the "ctrl-alt-F7" shell, i tried going there, and ended up with an blank screen (except there was some sort of character at the upper left corner.)


If you press "ctrl-alt-F1" from X11, you will switch to the first virtual console (F2 will get you to the second, etcetera). From there, you can switch virtual consoles with alt-f2, alt-f3, alt-f4 and so on.

On Ubuntu, X11 will run on console #7, so alt-f7 will take you back to X11. BUT, if you use ctrl-alt-backspace from X11, it will EXIT and throw you back to the console it was started from (most likely #1). alt-f7 will not bring you back to X11, because it's not running anymore.

I hope this clears things up for you.

---

### Post by krusbjorn on 2005-05-22
[QUOTE=svmaris]If you press "ctrl-alt-F1" from X11, you will switch to the first virtual console (F2 will get you to the second, etcetera). From there, you can switch virtual consoles with alt-f2, alt-f3, alt-f4 and so on.

On Ubuntu, X11 will run on console #7, so alt-f7 will take you back to X11. BUT, if you use ctrl-alt-backspace from X11, it will EXIT and throw you back to the console it was started from (most likely #1). alt-f7 will not bring you back to X11, because it's not running anymore.

I hope this clears things up for you.[/QUOTE]

Ah, thanks. That surely cleared things up a bit.

But how come console #7 is blank after pressing ctrl-alt-backspace?

---

### Post by svmaris on 2005-05-22
[QUOTE=krusbjorn]Ah, thanks. That surely cleared things up a bit.

But how come console #7 is blank after pressing ctrl-alt-backspace?[/QUOTE]

Because there's no process running on that tty (tty is the technical/historical name for the 'virtual console').

If you look in /etc/inittab, you can see that the 'getty' process is started for tty1 to tty6 (so, that's alt-f1 to alt-f6). The 'getty' process handles the login-process on that console. The file also states that, if you need more virtual consoles, you can add additional getty's to /etc/inittab, but it tells you to skip tty7, because that's the one X11 will use when it starts.

So a virtual console with run either 'getty' or X11, but not both.

---

### Post by mohaham on 2005-05-22
Here's how to restart GDM from the console..

sudo killall gdm
sudo /etc/init.d/gdm start

---

### Post by angrykeyboarder on 2005-05-22
[QUOTE=svmaris]Actually, CTRL-ALT-BACKSPACE is support to _kill_ X. The fact that it's restarting is due to GDM (or XDM). When you start X.org with 'startx', it will not restart.[/QUOTE]

I stand corrected. :-)

---

