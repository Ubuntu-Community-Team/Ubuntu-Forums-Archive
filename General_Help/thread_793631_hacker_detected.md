---
title: "hacker detected ??"
date: 2008-05-13
forum: General Help
---

### Post by Q-ro on 2008-05-13
Well i'm really noob as you may notice, but i'm really paranoid, because i was trying some commands on the terminal and when i tried 

```
$ who
```

it says that there where actually 2 users connected, and the 2 of them is me, so i got all paranoid and didn't understand what was going on.

this is what i actually got when i used who : 

```

Me     tty7         2008-05-13 21:42 (:0)
Me     pts/0        2008-05-13 22:34 (:0.0)

```

science i don't really get what is this all about, i was wishing that some one may help me, and tell me, is there some one else connected to my computer, or is just something else...

PD: please don't hit me to hard if this is the worst noob post you ever read :(

---

### Post by zenwalker on 2008-05-13
You can read man who page on cmd line for further detailed info.

But the first tty7 is the Graphical terminal to which u r have logged in.

---

### Post by Patrick793 on 2008-05-13
> **Q-ro said:**
> Well i'm really noob as you may notice, but i'm really paranoid, because i was trying some commands on the terminal and when i tried 

```
$ who
```

```

Me     tty7         2008-05-13 21:42 (:0)
Me     pts/0        2008-05-13 22:34 (:0.0)

```



Don't worry. I just typed in ```
who
``` and I got the same thing.

---

### Post by |{urse on 2008-05-13
and pts/0 is the screen 0 on the xserver. 
noones hacked you yet =)

> kurse@kurse-desktop:~$ who
kurse    tty7         2008-05-13 16:34 (:0)
kurse    pts/0        2008-05-13 23:48 (:0.0)


---

### Post by Q-ro on 2008-05-17
lol, ok ty, i was all paranoid becouse for mi it does not make any sence to have 2 times the same user logged on , i thought maybe it was an error from the system, or that some one was using my account to log in as me, ok so it is nothing to worry about, but still being to much strange to have the same user logged 2 times =P

---

### Post by bodhi.zazen on 2008-05-17
Your user will be listed with each log in, ie each terminal (try launching a new terminal) or if you log in via ssh ... or consul ...

---

### Post by ibuclaw on 2008-05-17
I can see you getting paranoid over the command:
[PHP]who -q | tail -1 # <-- This command lists the number of users logged into your system[/PHP]
But it is all nothing that you should worry about.
[EDIT]
This command uses text manipulation, but is even more hysterical! (don't worry, it is lying to you!)
[PHP] who -q | tail -1 | sed 's/users/no of spies logged into your system as root/'[/PHP]
:lolflag:

But, back on track...
There are multiple levels of "logging in" in Linux.

type in:
```
who -a
```
And you'll see sort of what I mean.

Regards
Iain

---

