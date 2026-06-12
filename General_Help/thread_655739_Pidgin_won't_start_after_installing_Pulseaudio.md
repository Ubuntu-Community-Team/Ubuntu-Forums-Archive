---
title: "Pidgin won't start after installing Pulseaudio"
date: 2008-01-01
forum: General Help
---

### Post by Serori on 2008-01-01
So I spent a while trying to get my sound working - finally got flash, video, audio, and other system sounds to finally all work happily together after installing pulseaudio, all the alsa stuff in Synaptic, and playing with the Sound settings.

And now, after this, Pidgin won't start.  This is the only modification I've done since the last time I used pidgin and it was working at that point.  In the System monitor, it lists the process Pidgin as "sleeping".

I've tried running it from the terminal using the command "pidgin" or "usr/bin/pidgin", but nothing happens.

I've tried uninstalling it, sudo removing /usr/lib/pidgin, reinstalling.

I read something about libpurple or such files sitting in usr/local/lib and usr/lib, never found anything of the sort with Pidgin installed or not.  Maybe I'm not really looking correctly or something.

I've looked around on these forums and Google and can't seem to get the answer.

Any suggestions?

I'm very new to Linux in general, enjoying the experience so far despite the frustrations of getting some things to work.. its all working minus this so far.  I like it, its simple for the most part - all I do is music, email, and general stuff as a students... So, yeah, basically all that life story to tell you - please dumb it down for me, I'm not too sharp at this stuff yet.

Thanks for the help,
Dave

---

### Post by dlegend on 2008-01-01
Try opening up your terminal and typing "pidgin" and enter to execute the command. If the terminal outputs anything copy & paste it here. Doing this is usually one of the first things you should do to debug errors with applications.

Edit: You said nothing happens when you run it from terminal? No output at all?

---

### Post by Serori on 2008-01-01
Yeah, when I type "pidgin" in the terminal, it just does nothing.  It doesn't even bring me back to the input line, it just sits there.  The process pidgin starts according to the System Monitor, it opens up as "Zombie", then switches to "Sleeping".  If I end the pidgin process, the terminal brings me back to the input line.

EDIT: So I used sudo to open pidgin, and it opened finally - but then it disappears again.  Its like its minimized and I can't get to it - any other enlightenments?  I didn't touch any of it, it just disappeared suddenly.

---

### Post by dlegend on 2008-01-01
Sorry for the delay, how about trying to delete your pidgin settings? It should be in your home directory, called "**.purple**". It will be hidden so go to the view menu and click "show hidden files". Try opening pidgin again and see if it works.

---

### Post by Serori on 2008-01-01
So, though that didn't seem to work, I rebooted and ran a reinstalled pidgin again out of the sudo command.  This time it popped up with an account creator.  Then I couldn't find it again and the computer froze.  Upon reboot, I finally had an icon show up for Pidgin in my top panel when I started it and that brought up my buddy list.

And after that, I can now open it from the normal icon on my user account and it works fine.  Weird!

So, I guess its fixed - I have no idea how or why it happened to work this time, but it seems to have - so something must have worked!  And its consistently working now, I tinkered more with it.  Thanks for the help.

Dave

---

### Post by eldragon on 2008-03-04
ive got this very same problem, but pidgin segfaults when it tries to make sounds, so i just muted the app..

here is what pidgin drops to the term
```

tomas@lappy:~$ pidgin
*** PULSEAUDIO: Unable to connect: Connection refused
Pidgin 2.3.1 has segfaulted and attempted to dump a core file.
This is a bug in the software and has happened through
no fault of your own.

If you can reproduce the crash, please notify the developers
by reporting a bug at:
http://developer.pidgin.im/simpleticket/

Please make sure to specify what you were doing at the time
and post the backtrace from the core file.  If you do not know
how to get the backtrace, please read the instructions at
http://developer.pidgin.im/wiki/GetABacktrace

If you need further assistance, please IM either SeanEgn or 
LSchiere (via AIM).  Contact information for Sean and Luke 
on other protocols is at
http://developer.pidgin.im/wiki/DeveloperPages
Aborted (core dumped)

```

i'll keep on looking, if someone has a solution, please post!

---

