---
title: "trickle problem"
date: 2005-09-26
forum: General Help
---

### Post by haren on 2005-09-26
HI!
I'm running ubuntu 5.04 SERVER.

I was trying to netlimit my upload on the apache service.

I run this command : trickle -u 5 apache2

Iget this error:

(13)Permission denied: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs

and some times this:
(98)Address already in use: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs

What is wrong ?

---

### Post by dis-abled on 2005-10-07
[QUOTE=haren]HI!
I'm running ubuntu 5.04 SERVER.

I was trying to netlimit my upload on the apache service.

I run this command : trickle -u 5 apache2

Iget this error:

(13)Permission denied: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs

and some times this:
(98)Address already in use: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs

What is wrong ?[/QUOTE]


I got the exact same error after building apache from scratch and compiling. humm

---

### Post by jimcooncat on 2005-10-07
Googling "trickle apache" didn't come up with much. I wonder if you might have to use the trickled daemon instead. The paper below mentions Apache -- it doesn't say how to use trickle with it, but instead points out that Apache has several modules available for shaping. Maybe it would be better to look for one of those instead?

[http://monkey.org/~marius/trickle/trickle.pdf](http://monkey.org/~marius/trickle/trickle.pdf)

Thanks for bringing trickle to my attention -- I've been looking for a simple way to throttle my offsite backups.

---

