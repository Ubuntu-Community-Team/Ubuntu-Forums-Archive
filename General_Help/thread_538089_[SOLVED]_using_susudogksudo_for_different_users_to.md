---
title: "[SOLVED] using su/sudo/gksudo for different users to maintain separate settings from"
date: 2007-08-29
forum: General Help
---

### Post by sloggerkhan on 2007-08-29
So I have a laptop that I use as my only computer. For some applications, it's nice if things are set up differently depending on where I am.

So I figured I could make different users and name them things like "school" "home" "public" and such, and set up the apps for each program as a I wished for that location. Then, when wanting to use it, setup a launcher for it like 
$gksudo -u mobile rhythmbox
or
$gksudo -u public deluge 
or whatever.
However, the console always says that it can't connect to DISPLAY when this happens...
Even if I try forcing to :0.0 it still doesn't work...
(The main reason I want to do this is I have more media on an external drive than I keep on my laptop and I want to be able to use the external drive library when at home, the laptop library when elsewhere.)
So is there some way to allow user authority to display on the xserver when they aren't logged in as the main gui user? (For example, as it does if you run something gksudo'd as root or superuser.)

```

$ gksudo -u mobile rhythmbox --display=$DISPLAY 
GTK Accessibility Module initialized
cannot open display: 
Run 'rhythmbox --help' to see a full list of available command line options.
No protocol specified

```

```

~$ su mobile
Password: 
mobile@opboxkhan:/home/slogger$ rhythmbox
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

cannot open display: 

```

---

### Post by bogolisk on 2007-08-29
> **sloggerkhan said:**
> So I have a laptop that I use as my only computer. For some applications, it's nice if things are set up differently depending on where I am.

So I figured I could make different users and name them things like "school" "home" "public" and such, and set up the apps for each program as a I wished for that location. Then, when wanting to use it, setup a launcher for it like 
$gksudo -u mobile rhythmbox
or
$gksudo -u public deluge 
or whatever.
However, the console always says that it can't connect to DISPLAY when this happens...
Even if I try forcing to :0.0 it still doesn't work...
(The main reason I want to do this is I have more media on an external drive than I keep on my laptop and I want to be able to use the external drive library when at home, the laptop library when elsewhere.)
So is there some way to allow user authority to display on the xserver when they aren't logged in as the main gui user? (For example, as it does if you run something gksudo'd as root or superuser.)

```

$ gksudo -u mobile rhythmbox --display=$DISPLAY 
GTK Accessibility Module initialized
cannot open display: 
Run 'rhythmbox --help' to see a full list of available command line options.
No protocol specified

```

```

~$ su mobile
Password: 
mobile@opboxkhan:/home/slogger$ rhythmbox
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

cannot open display: 

```

open the terminal and run this 
```

xhost +local:

```

---

### Post by sloggerkhan on 2007-08-29
That seems to work, though I doI get errors:
 ```

(rhythmbox:13501): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(rhythmbox:13501): Rhythmbox-WARNING **: couldn't connect to session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(rhythmbox:13501): Rhythmbox-WARNING **: Couldn't connect to system bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```
Is there a reason to use +local:
and not +local:OTHERUSERNAME ?

---

### Post by bogolisk on 2007-08-30
> **sloggerkhan said:**
> That seems to work, though I doI get errors:
 ```

(rhythmbox:13501): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(rhythmbox:13501): Rhythmbox-WARNING **: couldn't connect to session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(rhythmbox:13501): Rhythmbox-WARNING **: Couldn't connect to system bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```


does (untested)
```

gksudo -u mobile rhythmbox --sm-disable

```
work for you?
> 
Is there a reason to use +local:
and not +local:OTHERUSERNAME ?

Up to you but "+local:" specify that you only allow xclients from the local labtop anyway.

---

### Post by sloggerkhan on 2007-08-30
Thanks bogo.
gksudo -u mobile 'rhythmbox --sm-disable'
still gets the error messages. (without the '  ' it seem to interpret the --sm-disable option as a flag for gksudo.)
Hey, at least the program run that way, right?

---

