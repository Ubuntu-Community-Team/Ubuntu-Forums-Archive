---
title: "Starting a second X server"
date: 2007-07-26
forum: General Help
---

### Post by abrichr on 2007-07-26
In the spirit of learning, and so that I can quickly switch from a fullscreen game to my desktop, I'm trying to figure out how to run applications in a second x server.

i was unable to find any concise documentation on the subject, and what i know has only been pieced together from offhand mentions in threads on random subjects.

as i understand it, pressing ctrl+alt+[F1 through F6] gets you into six different terminals.  these are unable to start an x server.  at first i tried using the command "startx", but I got the message that the xserver is already running.  then i found out that i had to type "startx -- :1", which did actually start x, with nothing running.  after switching back to my current x by pressing F7, and going back by pressing F1, the x server had stopped, and it was stuck in a loop saying "AUDIT: [...] X: client 1 rejected from localhost"

After getting out of the loop, I tried "startx -- /usr/games/tremulous :1", which gave me a bunch of errors about not having the proper authority (i've seens ome posts about this but really don't understand it), as well as not being able to run OpenGL.

Pressing CTRL+ALT+F8 gets me into a terminal with no prompt, only the verbose startup messages, and I can't enter any commands.  F9-F12 are just black screens.

So now: what do I have to do to get this to work?

---

### Post by dreadlord_chris on 2007-07-26
> **abrichr said:**
> In the spirit of learning, and so that I can quickly switch from a fullscreen game to my desktop, I'm trying to figure out how to run applications in a second x server.

i was unable to find any concise documentation on the subject, and what i know has only been pieced together from offhand mentions in threads on random subjects.

as i understand it, pressing ctrl+alt+[F1 through F6] gets you into six different terminals.  these are unable to start an x server.  at first i tried using the command "startx", but I got the message that the xserver is already running.  then i found out that i had to type "startx -- :1", which did actually start x, with nothing running.  after switching back to my current x by pressing F7, and going back by pressing F1, the x server had stopped, and it was stuck in a loop saying "AUDIT: [...] X: client 1 rejected from localhost"

After getting out of the loop, I tried "startx -- /usr/games/tremulous :1", which gave me a bunch of errors about not having the proper authority (i've seens ome posts about this but really don't understand it), as well as not being able to run OpenGL.

Pressing CTRL+ALT+F8 gets me into a terminal with no prompt, only the verbose startup messages, and I can't enter any commands.  F9-F12 are just black screens.

So now: what do I have to do to get this to work?

You can start a new session from the Switch User menu - on mine this starts the new session on tty8
I can then switch back & forth with ctrl-alt-f7 & f8

---

### Post by abrichr on 2007-07-26
Seems that this requires me to log in as a second user -- using my own username and password sends me back to my desktop.

Also, I'd like to know how to do this without having to start Gnome, which is a waste of memory if I only want to start the second server to run a full screen 3d game, for example.

---

### Post by reckless2k2 on 2007-07-26
ok...i'm jumping in on this one and hopefully i can help. bring up another ttyl do this:

ctrl + alt + f2

it'll bring you to a login screen. login as any user you have on the box (yes you can log in as yourself more than once unless you tell it not to). then start an X window in that terminal on a new server like this:

xinit -- :1 vt12

then type:

startx

and then you'll be in. the :1 tells it server 1. you are already running server 0. you can choose up to 7 i think. can't remember. the vt12 binds it to the f12 key. so now if you do crtl + alt + f7 you'll go back to :0. if you do ctrl + alt + f12 .......you'll go to :1.  

get the idea?

it's all pretty neat and i use it quite often to run X over ssh to other PCs

---

### Post by abrichr on 2007-07-26
that worked perfectly!  many thanks indeed. :)

---

### Post by reckless2k2 on 2007-07-26
Not a problem. You can use those formats to start server 2, 3, 4...and so on like this:

xinit -- :2
xinit -- :3

You get the idea.

And bind it to a virtual terminal using "vt" 1,2,3 and so which is your "F" keys at the top on like this:

xinit -- :2 vt3
xinit -- :4 vt6

You get the idea. 

Just don't bind to vt7 because you are already running "0" on vt7 (F7). 

If you have other desktop managers you can run them as well instead of GNOME. Like KDE would be startkde. The "startx" is bound to gnome-session command. 

This method along with running X over SSH shows you the power of Linux as it's core design as a multi-user, multi-tasking platform. 

Enjoy! Glad to be of help.

---

### Post by Benedolt on 2007-11-04
Is it possible to execute xinit from a gnome terminal instead of a "real" terminal? When I attempt it, it gives me: ```
X: user not authorized to run the X server, aborting.
```

---

