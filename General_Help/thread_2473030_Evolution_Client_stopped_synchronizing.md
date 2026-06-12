---
title: "Evolution Client stopped synchronizing"
date: 2022-03-21
forum: General Help
---

### Post by Jonners59 on 2022-03-21
For some reason, my Evolution mail client (3.40.4-1ubuntu2) has stopped synchronizing.

I use 5 x Gmail and one Hotmail account.  Worked flawlessly, then started to become erratic a couple of days ago and now just won't sync.  No messages just after a while it says timed out.

Linux 5.13.0-35-generic #40-Ubuntu x86_64 GNU/Linux

ANy help, please?????

---

### Post by #&amp;thj^% on 2022-03-21
Lets see if we can generate some better info. 
show this please:
```
ps ax | grep evolution
```
while were at it also show:
```
ps ax | grep bonobo
```

---

### Post by Jonners59 on 2022-03-22
> **1fallen said:**
> Lets see if we can generate some better info. 
show this please:
```
ps ax | grep evolution
```
while were at it also show:
```
ps ax | grep bonobo
```

Thank you.
```
ps ax | grep evolution
```
[HTML]   2636 ?        Sl     0:00 /usr/libexec/evolution-data-server/evolution-alarm-notify
   2784 ?        Ssl    0:00 /usr/libexec/evolution-source-registry
   2855 ?        Ssl    0:07 /usr/libexec/evolution-calendar-factory
   3260 ?        Sl     1:30 evolution
   3421 ?        Ssl    0:00 /usr/libexec/evolution-addressbook-factory
   6988 pts/0    S+     0:00 grep --color=auto evolution[/HTML]
```
ps ax | grep bonobo
```
[HTML]7526 pts/0    S+     0:00 grep --color=auto bonobo[/HTML]
Not sure it will show you much today as it has decided to work perfectly.  It's like going to the doctor!

---

### Post by #&amp;thj^% on 2022-03-22
> **Jonners59 said:**
> 
Not sure it will show you much today as it has decided to work perfectly.  It's like going to the doctor!
:lolflag: Thanks for the smile.

My current guess is that an environment variable that's set up when
running GNOME doesn't get set by the XFCE environment, and the
bonobo-activation-server is confused.  It may fix things if you run
**"evolution --force-shutdown"**, kill the bonobo-activation-server
process and any other processes associated with evolution.
Keep us posted.
```
ps ax | grep evolution
 663811 ?        Sl     0:01 evolution
 663818 ?        Ssl    0:00 /usr/lib/evolution-source-registry
 663826 ?        Sl     0:00 /usr/lib/evolution-data-server/evolution-alarm-notify
 663901 ?        Ssl    0:00 /usr/lib/evolution-calendar-factory
 663914 ?        Ssl    0:00 /usr/lib/evolution-addressbook-factory
 664393 pts/0    S+     0:00 grep evolution

```
And:
```
ps ax | grep evolution-data-server
 663826 ?        Sl     0:00 /usr/lib/evolution-data-server/evolution-alarm-notify
 669335 pts/0    S+     0:00 grep evolution-data-server

```

---

### Post by Jonners59 on 2022-03-22
> **1fallen said:**
> :lolflag: Thanks for the smile.

My current guess is that an environment variable that's set up when
running GNOME doesn't get set by the XFCE environment, and the
bonobo-activation-server is confused.  It may fix things if you run
**"evolution --force-shutdown"**, kill the bonobo-activation-server
process and any other processes associated with evolution.
Keep us posted.

Thank you 1fallen...  I'll leave this open for such time as it happens again and report back the same commands (find out what is playing up at least) and also try the shutdown command.

---

