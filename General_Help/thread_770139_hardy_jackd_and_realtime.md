---
title: "hardy: jackd and realtime"
date: 2008-04-27
forum: General Help
---

### Post by dentament on 2008-04-27
i just switched from feisty to hardy
under feisty, since i needed to run jackd in realtime as a normal user (not root), i had installed the realtime-lsm module and its init script, so to prepare the system in order to be able to use jackd in realtime as a normal user was as easy as doing "/etc/init.d/realtime start" from root, which unloaded the "commoncap" module and loaded the "realtime" one.
under hardy the realtime module doesn't build:
---
Failed: Security Capabilities not configured as module
---
ie the "commoncap" module is now directly built into the kernel (i'm now using the -rt kernel, but the same applied to -generic).
is there anyway i can use jackd (or other rt apps) as a normal user under hardy?
thanks, bye

---

### Post by kahi on 2008-04-28
yes, there is: since support for realtime-lsm has been discontinued, the preferred way these days is to allow users to schedule real-time tasks by editing /etc/security/limits.conf

adding, for example
```

*               hard    rtprio          0
*               soft    rtprio          0
@realtime       hard    rtprio          20
@realtime       soft    rtprio          10
myuser          hard    rtprio          50
myuser          soft    rtprio          30

```

enables every user in the group 'realtime' to run tasks with real time priorities up to 20 and the user 'myuser' even up to 50.
the upper two lines supposedly make processes drop their real-time capabilities properly when they fork and change their effective UID.

HTH,
kahi

---

### Post by dentament on 2008-04-29
thanks a lot, it works :)
for jackd I only had to add

```
@realtime       -    memlock 250000
```

("memlock" value should be ~ half your available ram)

however they should advertise this change, and add a note to the "realtime" and "realtime-lsm" packages description to say something like "this no longer builds with standard ubuntu kernels, the correct way to give users realtime priority etc."

bye

---

### Post by lukanova on 2008-06-25
hi.

thanks, this was very very helpfull. i had some problems because i forgot to add my user to group realtime:

# addgroup realtime
# addgroup MYUSERNAME realtime

restart seems to be needed.

i'm now using  2.6.24-19-rt #1 SMP PREEMPT RT kernel with this setup, and jackd (+ pure data in -rt) seems to be rock-solid. 

thanks again.

---

