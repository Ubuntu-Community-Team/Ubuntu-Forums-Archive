---
title: "simple ssh question"
date: 2007-06-23
forum: General Help
---

### Post by tronica on 2007-06-23
when i log into a machine with ssh, and run a command how to i logout and leave the task runing on that machine?

---

### Post by silverglade00 on 2007-06-23
use the -nohup option. say you want to run nautilus and then log out and leave it running. you type

nautilus -nohup

---

### Post by tronica on 2007-06-23
well that didnt work, heres the what i'm trying to do. i'm running rsync and it takes like an hour to complete. So when i do ssh ipaddress, then rsync -a point a to be, how can i exit ssh and still have that running on the server? i tried the command you me but it didn't work.

---

### Post by Maxtorm on 2007-06-24
Perhaps using "at" or "cron" would be more appropriate so that the job could execute without any intervention whatsoever?  Good cron page here: [http://www.unixgeeks.org/security/newbie/unix/cron-1.html](http://www.unixgeeks.org/security/newbie/unix/cron-1.html)

---

### Post by stylishpants on 2007-06-24
No, you really do want 'nohup'.  However, the previous advice you got about it is wrong.  'nohup' is a command, not an option flag to other commands.

To use nohup, simply type 'nohup' on right before your rsync command (on the same line -- not separately.)


"screen" would also do what you want.

---

### Post by HermanAB on 2007-06-25
The other way is to append an ampersand to the name of the program, to push it into the background like this:
# whatever &

Cheers,

Herman

---

### Post by asipi on 2007-06-25
nope
bg processes alsoends when logout...

---

### Post by feenster on 2007-06-25
I prefer to use the screen command for this kind of thing. Do the following:

```
screen -S name-you-can-remember
```

This will create a new screen with the name you specified. You can then do whatever you want. When you want to detach from it and do something else, press CTRL+A on your keyboard, then press 'D'. This will detach you from the screen. You can see what screen's you have running with...
```
screen -ls
```

And can reconnect to one using...
```
screen -R name-of-screen
```

The screen name you specified will be prefixed with numbers too, so don't forget to include them (you can see the full name with the "screen -ls" command

Matt

---

