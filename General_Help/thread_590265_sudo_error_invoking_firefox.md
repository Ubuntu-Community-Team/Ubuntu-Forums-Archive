---
title: "sudo error invoking firefox"
date: 2007-10-24
forum: General Help
---

### Post by IndigoMontoya on 2007-10-24
I am running gutsy with compiz using the fglrx driver (through ubuntu restricted drivers) and when i try to run firefox as a different user I get the following error:

```
$ sudo -u video firefox
/usr/bin/md5sum: core: Permission denied
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified


(firefox-bin:15547): Gtk-WARNING **: cannot open display:  
/usr/bin/md5sum: core: Permission denied

```


If I su as that user and then run firefox I get the same thing.  It worked in feisty running compiz with no problem.  Any thoughst?

Thanks

---

### Post by nholling on 2007-10-24
You will have to run:
```
xhost +localhost
```

to get this to work. Run this command before trying to run filrefox and before su or sudo'ing.

Hope this helps,
-Nate

---

### Post by IndigoMontoya on 2007-10-24
Thanks for the response.

When I ran the command as the user I was logged in as it said "localhost being added to access control list"  

I then tried my sudo to no avail.

So I figured to try su'ing into my user I am trying to sudo run as and then run the command and it says 

```
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified

xhost:  unable to open display ":1.0"

```

So in other words, it didnt help :(

---

### Post by nholling on 2007-10-24
Install libgnomesu0 if its not installed already.

Then try:

```
gnomesu -u video firefox
```

---

### Post by IndigoMontoya on 2007-10-25
Interesting.  That did work.  

I got a popup window to enter my password in instead of the normal terminal prompt.  But these error messages were in the terminal
```

/home/spruce/.gtkrc-2.0:3: error: scanner: unterminated string constant - e.g. `style'
/usr/bin/md5sum: core: Permission denied


```

Since it works, its no big deal, but any ideas what the problem is?  Spruce is the user gnome is logged in as, not the su'ed user.

---

### Post by nholling on 2007-10-28
> **IndigoMontoya said:**
> Interesting.  That did work.  

I got a popup window to enter my password in instead of the normal terminal prompt.  But these error messages were in the terminal
```

/home/spruce/.gtkrc-2.0:3: error: scanner: unterminated string constant - e.g. `style'
/usr/bin/md5sum: core: Permission denied


```

Since it works, its no big deal, but any ideas what the problem is?  Spruce is the user gnome is logged in as, not the su'ed user.

Hmmm, Sounds like an old config file lying around.  Was this machine upgraded from Fiesty to Gutsy?  I've seen code many times, not upgrade config files property.  To get rid of this problem you may have to delete the file (make a backup copy first :-) ) specified in the error message "/home/spruce/.gtkrc-2.0:3". Logout then log back in.  Config file should be recreated.  You will have to adjust any settings you changed related to GTK.

-Nate

---

### Post by IndigoMontoya on 2007-10-29
Thanks for the tip.  I moved .gtkrc-2.0 (there is no xxxxx:3), and relogged in and it didnt give me the error anymore, although I still get the /usr/bin/md5sum error. Ah well thanks

---

