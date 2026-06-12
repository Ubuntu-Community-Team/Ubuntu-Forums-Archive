---
title: "ZSNES Problem"
date: 2007-12-02
forum: General Help
---

### Post by Hawk__0 on 2007-12-02
When I open it, it closes.  So I decided to get the command line error.  I launch from command line, and I get this:
```
steve@steve:~$ zsnes
bash: /usr/bin/zsnes: No such file or directory
steve@steve:~$ zsnes
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event8. Make sure you have read permissions to it.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
Creating link /home/steve/.kde/socket-steve.
can't create mcop directory
steve@steve:~$ 

```

Anyone ever have this problem or have any idea how to fix it?

---

### Post by disturbedite on 2007-12-02
this has been answered before on the forum more than once.  i will kindly recommend a search.

(i'd tell you myself, but i don't remember what the solution was.  i've never had that error myself either).

---

### Post by Hawk__0 on 2007-12-02
ok thanks i managed to find a post, i had to do this:
```
mkdir ~/.kde/socket-`hostname`
chown -hR `id -n -g` ~/.kde
chmod 755 -R ~/.kde

```
But now i cant seem to change the resolution for some odd reason... =\
it jsut doesnt do ANYTHING.
how do i fix this?

---

### Post by disturbedite on 2007-12-03
did you install the version from the repo or did you compile it yourself?

---

