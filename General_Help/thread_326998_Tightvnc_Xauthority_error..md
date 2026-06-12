---
title: "Tightvnc Xauthority error."
date: 2006-12-28
forum: General Help
---

### Post by cmspaz on 2006-12-28
I'm running ubuntu desktop on my server, which for most of the time is headless.

I access it using shh or vnc, but I would like to use vnc through an ssh tunnel. However, whenever I start the vncserver over ssh, I get this:

```
xauth:  error in locking authority file /home/camiller/.Xauthority
xauth:  error in locking authority file /home/camiller/.Xauthority
```

Though the server starts up fine after this, when I access it the screen is gray, even though I have it correctly set to start gnome, and it has done so successfully before. The gray screen may be unrelated, I'm thinking that it may be a result of just closing the vncviewer window instead of logging out of the session, even though it persists after the vncserver has been stopped and restarted, and even on a separate session.

---

### Post by bernied on 2006-12-28
Maybe you just need to delete the .Xauthority file - do this when you are NOT running any X or vnc sessions.

If in doubt, take a copy of this file, or simply move it
```
mv ~/.Xauthority ~/.Xauthority.old
```
I use 
```
vncserver -kill :1
```
to kill a session (number 1 in this case). I have made an alias for this, so my command is 'vnckill :1'.
In my experience logging out from the vnc desktop makes no difference, except for saving desktop settings.

---

### Post by cmspaz on 2006-12-29
That didn't help, I still get the error.

EDIT
Yes, it did, no idea why it continued showing the error a few times there, it eventually just stopped.
/EDIT

And I never get a gray screen until I try to log in to a vnc session after not logging out before killing the server. I just tested this.

Is there any way to get tightvnc to start on display:0? I'd really like to be able to start a session over vnc (after a reboot, for example), and have that session persist on the monitor if I choose to plug it in later.

---

### Post by bernied on 2006-12-29
> **cmspaz said:**
> Is there any way to get tightvnc to start on display:0? I'd really like to be able to start a session over vnc (after a reboot, for example), and have that session persist on the monitor if I choose to plug it in later.
I don't know about this. I'm pretty sure you can start a *shared* vncserver session from within a desktop environment, but don't think this can be done before logging in.

It's not entirely what you asked for, but you can access the vnc session from the local machine:
```
vncviewer localhost:1
```

---

### Post by cmspaz on 2006-12-29
Thanks for your help so far.

Now, one last question, to solve the gray screen issue, I would most likely have to kill the  gnome session that was run by the vnc server in order to start another working vnc session. How would I go about doing this?

---

### Post by bernied on 2006-12-29
Again, I don't know about this, I've never experienced the gray screen through vnc.

But, if your'e right about needing to kill a gnome session, you could try
```
ps -ef | grep gnome
```this means show me all running processes (ps -e), including the command used to star them (-f), then pipe (|) the results to the search utility called grep and look for the word gnome. Note that one of the lines of output you get will be the search itself. One of them may also be the gnome session that you are running now, so be careful.

The first number in this output is the process ID (PID) which you can use to kill the process. So then try:
```
kill 1234
```where 1234 is the PID you got from your ps | grep 
This may not kill it, but give it a chance anyway - remember how long gnome takes to shut down normally. If it doesn't work (check by repeating the ps | grep) then you can 'kill it harder' with:
```
kill -9 1234
```

---

