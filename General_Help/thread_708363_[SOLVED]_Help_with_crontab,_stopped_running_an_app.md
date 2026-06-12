---
title: "[SOLVED] Help with crontab, stopped running an application"
date: 2008-02-26
forum: General Help
---

### Post by FooAtari on 2008-02-26
I have the following set to run in the system cron (/etc/crontab)

I originally set it up in Kubuntu and it worked fine and appeared to OK after install Ubuntu.  But recently it stopped running one of the applications and I can't figure out why

Here it is

```
#kill klibido
31 15 * * * pc killall klibido

#start stunnel
31 15 * * * root stunnel4 /etc/stunnel/stunnel.conf

#start klibido
32 15 * * * pc export DISPLAY=:0 && /usr/bin/klibido -r

#kill stunnel4
33 15 * * * root killall stunnel4
```

Everything works fine except  #start klibido.  It just doesn't start.

I can't see anything wrong, anyone got any ideas?

I'm not sure if its related but when looking through the logs I saw this under Xorg.0.log

**AUDIT: Tue Feb 26 15:32:01 2008: 5452 X: client 32 rejected from local host (uid 1000)**

---

### Post by astrotech226 on 2008-02-26
The problem with exporting the DISPLAY=:0 is that it is effective for whichever user is logged with a desktop (or X).  I'm not sure how to make that permanent for you, but you can log in as user "pc" and do this from a commandline:

```
xhost local:root
```

In other cases where I've had to run applications that forced a display even though there was never anything to show, I've run a virtual frame buffer.  It's sort of a service that will allow programs to draw to a screen in ram.

After you install it, you can fire this at start up:

```
/usr/bin/Xvfb :1 &
```

Then export DISPLAY=:1 and everything should just work as there's no more X authentication.

---

### Post by FooAtari on 2008-02-26
> The problem with exporting the DISPLAY=:0 is that it is effective for whichever user is logged with a desktop (or X). I'm not sure how to make that permanent for you, but you can log in as user "pc" and do this from a commandline:


I don't really follow this, can you explain this further?  I don't rally understand what the problem is :)

And what does

```
xhost local:root
```

do?

---

### Post by astrotech226 on 2008-02-26
Let's say that user "pc" is the one running the cronjob and you are logged in as "someone" with a Gnome desktop.  Normal permissions will not allow the user "pc" to display anything on the screen which now belongs to "someone".  So the user "someone" will need to allow it.

That's what the "xhost local:root" does. It disables security for local, non-network X connections.  It allows any local user to display to the screen.

But it can be difficult to get that command to run correctly and automatically.  There are config files, but I've never had much luck with them when multiple users log into the computer.

Does the cron job display something to the screen?  Or is the export DISPLAY a requirement for java or something?

---

### Post by FooAtari on 2008-02-26
Well the cronjob is basically to schedule usenet downloads.  So yeah it starts Klibido.

I'm always logged in as "pc" so don't think the issue you are describing should be a problem?

I have an SSH VNC session (hope I described that correctly) for display:1 that I use to log into remotely, the cronjob may have stopped working at the same time I set that up. Would that cause any issues?

---

### Post by astrotech226 on 2008-02-26
This should be pretty easy to do if you are always logged in as user "pc".  A simple test will to do this from the command line and see if the cronjob runs ok.

```
xhost local:root
```

There's a number of places you can put that to run during startup.  A good one might be in ~/.xsession.  Every time you boot up and log in, it will allow the cronjob to run correctly.

I also imagine if you are running gnome, you could put it in your sessions.  I think if you click System -> Preferences -> Sessions you can do it there.

---

### Post by FooAtari on 2008-02-26
Ok,

I'll try it in the morning and let you know how it goes

Thanks

---

### Post by FooAtari on 2008-02-27
Well that fixed it. Thanks a lot :)

I'm still not sure why it became a problem in the first place.  I understand the problem (i think) and the fix is straight forward enough, but I can't think what changed to cause the problem.

---

