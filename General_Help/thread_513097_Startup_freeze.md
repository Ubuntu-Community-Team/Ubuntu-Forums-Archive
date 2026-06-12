---
title: "Startup freeze"
date: 2007-07-30
forum: General Help
---

### Post by americanmetal07 on 2007-07-30
After the login screen, it seems to just freeze right when it gets to the desktop.
I changed it to gnome startup, freeze.
I changed it to safe gnome startup, freeze.

What could be causing this?
Ive been using this for about a month now, and I honestly have no clue where to start.

---

### Post by heimo on 2007-07-30
Couple things I'd do. Both mean you'll have to use virtual console (ctrl+alt+F2, F7 to get back). I'd try renaming .gnome2 (or is it .gnome?) directory in my homedir using something like:
```
sudo mv /home/myusername/.gnome2 /home/myusername/.gnome2_bak
```

And then retry logging in. If that doesn't work, I'd create another user account and try with that one.
```
sudo adduser mynewusername
```

If that doesn't work either, check that your localhost is configured properly. Sorry, I can't give detailed instructions for fixing it at the moment. But try pinging it and it should work.
```
ping localhost
```

Last one may seem odd, but it has been reason for Gnome not working couple times. Behaves just like you described. If pinging localhost doesn't work, you'll probably have to create new route, something like (and this is **unverified**):
```
sudo route add 127.0.0.1 lo
```

---

### Post by americanmetal07 on 2007-07-30
thanks ill give that a try

---

### Post by americanmetal07 on 2007-07-30
None of those helped :(

But when I booted up in safe mode, at the very end it said this **Setting up sensor limits... [[COLOR="Red"]Fail[/COLOR]]** 

I don't know if that has anything to do with it or what.

---

### Post by heimo on 2007-07-30
Search /var/log/messages for any errors and warnings. Also check dmesg.

```
less /var/log/messages
dmesg |less
```

Next thing I'd probably try is install xfce or kde (using apt-get or aptitude on command line) and try if those work.

---

### Post by charper_99 on 2007-07-30
Does this thread help? [http://ubuntuforums.org/showthread.php?t=34130]("http://ubuntuforums.org/showthread.php?t=34130")

---

