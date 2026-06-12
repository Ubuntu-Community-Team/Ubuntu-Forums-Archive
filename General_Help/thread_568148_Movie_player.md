---
title: "Movie player"
date: 2007-10-05
forum: General Help
---

### Post by octotom on 2007-10-05
I installed the codecs that I need to play movies, but when I go to play movies in movie player, it will open and then disappear.  What can fix this problem?

Thanks in advance!  You all have helped a lot as I start feeling out and using Ubuntu!

Tom

---

### Post by sumguy231 on 2007-10-05
Try launching totem (The movie player) from the command line and see if you get any error output when it crashes.

---

### Post by elliotjreed on 2007-10-05
No idea!

You could try using VLC Media Player, it's better, and already has the codecs built in!

---

### Post by octotom on 2007-10-05
Sorry if I sound dumb, but how do I launch totem from the command line?  I tried installing VLC media player but the same thing happens...as soon as a movie starts to load, it crashes.  =(

Thanks for your help guys!

Tom

---

### Post by elliotjreed on 2007-10-05
Just open up the terminal and type:
```

totem
```

You could also try:

```
sudo totem
```

just to see if your movie works like that

---

### Post by octotom on 2007-10-05
When I try to just open it in the terminal and then play a movie, this is what comes up:

The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 77 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by octotom on 2007-10-05
Here is what comes up when I try running sudo totem as well:

** (totem:8550): WARNING **: Failed to connect to the session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

** (totem:8550): WARNING **: Error connecting to DBus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

** (totem:8550): CRITICAL **: totem_remote_window_activated: assertion `DBUS_IS_G_PROXY (remote->media_player_keys_proxy)' failed

---

