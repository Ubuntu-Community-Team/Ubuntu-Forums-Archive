---
title: "console on ttyS0 using Upstart"
date: 2007-06-13
forum: General Help
---

### Post by volumen1 on 2007-06-13
I'm trying to get console over serial working on a Ubuntu 7.04 box.  On a machine using sysVinit, I would edit inittab, but I see that upstart is supposed to read from /etc/event.d to definte jobs.  For some reason, that is failing for me.

I created /etc/event.d/ttyS0 with the following in it:

# ttyS0 - getty

start on runlevel-S
start on runlevel-1
start on runlevel-2
start on runlevel-3
start on runlevel-4
start on runlevel-5

stop on shutdown

respawn /sbin/getty -L ttyS0 9600 vt100


However,  after reboot, a "ps aux | grep tty" shows me this:

root      4402  0.0  0.0   1648   508 tty4     Ss+  16:55   0:00 /sbin/getty 38400 tty4
root      4403  0.0  0.0   1648   508 tty5     Ss+  16:55   0:00 /sbin/getty 38400 tty5
root      4406  0.0  0.0   1652   512 tty2     Ss+  16:55   0:00 /sbin/getty 38400 tty2
root      4410  0.0  0.0   1648   504 tty3     Ss+  16:55   0:00 /sbin/getty 38400 tty3
root      4413  0.0  0.0   1648   508 tty1     Ss+  16:55   0:00 /sbin/getty 38400 tty1
root      4419  0.0  0.0   1652   512 tty6     Ss+  16:55   0:00 /sbin/getty 38400 tty6

Also, running "sudo initctl start ttyS0" comes back with:
initctl: Unknown job: ttyS0

It sure seems like upstart isn't seeing my new ttyS0 job in event.d?  But, this is my first experience with upstart, so I could be wrong.

---

### Post by volumen1 on 2007-06-13
OF COURSE!  As soon as I post, I get the answer.  The syntax I was using for /etc/event.d/ttyS0 was wrong.  I changed it to:

start on runlevel 2
start on runlevel 3
start on runlevel 4
start on runlevel 5

stop on runlevel 0

respawn
exec /sbin/getty 9600 ttyS0

And now it works great!

---

