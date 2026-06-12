---
title: "cron and rhythmbox"
date: 2007-05-09
forum: General Help
---

### Post by kragen on 2007-05-09
I was trying to get cron to work with rhythmbox - alarm-clock style, my cron-tab looked like this:

```
* * * * * export DISPLAY=:0 && rhythmbox-client --play-pause
```

This should have played / paused rhythmbox every miniute... but instead what happened is it opened a second instance of rhythmbox (a second item), which was paused, then a miniute later it started playing / pausing that copy of rhythmbox once a miniute. My multimedia keys and "rhythmbox-client --play-pause" commands all affected the first instance of rhythmbox (even if I prefixed them with export DISPLAY=:0)

If I set the cron job up without the export DISPLAY=:0 bit, it just does nothing, which is even worse.

I'm stumped, I can't see any way to force cron to use the existing rhythmbox instance, and as it is, its a tad useless (I've given up and started using quodt-libets alarm plugin for now - but i'd like to get this working).

Any ideas?

---

### Post by moterpent on 2007-05-10
Hi kragen,

Why this has worked for some people and not others, I'm not sure.  Your question made me curious so I did some testing.

On my system (Feisty 7.04), I found that "rhythmbox-client" seems to want access to the "DBUS_SESSION_BUS_ADDRESS" environment variable.  If that variable isn't present, which it is not under a cron job, I would get a, "(rhythmbox-client:22236): Rhythmbox-WARNING **: Failed to execute dbus-launch to autolaunch D-Bus session" error.  

If you open a terminal window and type:

```
echo $DBUS_SESSION_BUS_ADDRESS
```

...you will see what I mean.

By specifying that environment variable as part of my cron entry the "rhythmbox-client" worked perfectly.  In fact I didn't even need the "DISPLAY" environment variable at all.

My cron entry ended up looking something like this:
```
* * * * * export DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-nsYoZqZYL3,guid=a6244e7a45f6e224f1288f004642a3bc && /usr/bin/rhythmbox-client --play-pause > /tmp/rb-debug.out 2>&1
```

The file redirection in the above example was just so that I could catch any output on STDIN or STDERR that rhythmbox-client might be spewing (it's how I found the error message mentioned earlier).

I haven't done the due dilligence to discover what that variable is all about but it is obviously, at least in my case, necessary.  Hopefully you find this useful.  Good luck and let us know how it works out.

---

### Post by kragen on 2007-05-10
ah nice, I've done some hunting and I think I've worked out what the variable is: DBUS messages are sent either over a systemwide bus, or a per-login-session bus. Rhythmbox uses the per-session bus to send messages whenever rhythmbox-client is used, but cron doesn't  as its a systemwide process.

Here's the page I found which was most helpful:

[http://blogs.gnome.org/view/ovitters/2005/11](http://blogs.gnome.org/view/ovitters/2005/11)

Thanks very much for the response, I would have never figured this out :D As far as I can tell the only problem now is that the session variable will obviously change, but I think a modification of the script given on the page I linked should be able to fix that.

---

