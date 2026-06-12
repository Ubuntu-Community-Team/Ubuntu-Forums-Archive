---
title: "Killing an X Session from command line"
date: 2007-11-29
forum: General Help
---

### Post by MagicTom on 2007-11-29
I've recently gotten into the habit of running my games in a brand new X session, and for a TwinView user like myself, it's made life so much easier.  But I'm a stickler for making everything automatic, and so it's really bothering me that I can have my setup perfected with a script that launches the new X session with a single-monitor configuration, runs the game in that session, but .. is incapable of closing the X session once I quit the game.

I've read of the Ctrl+Alt+Backspace key combination time and time again -- I know I can just use that to close the session and be done with it.  But it would be so much more smooth if I could have my launcher wait until I quit the game and automatically execute a command to end the session.

But no amount of googling or greping through config files is giving me my answer.  I know there's a way, because I used to use it years ago to clean up my VNC sessions.  Anyone remember what that command is?

---

### Post by -grubby on 2007-11-29
it would probably be something like

```
killall xserver
```

---

### Post by MagicTom on 2007-11-29
Oh, I'm not looking to kill ALL of my x sessions, just one specifically.  I have my main desktop running on :0, but I open up games in :1.  I'm looking for a command to just close :1 without touching :0.

Thanks for chiming in, though! :)

---

### Post by seamuso on 2007-11-29
ps aux | grep /usr/bin/X

kill the one that comes back with the :1

---

