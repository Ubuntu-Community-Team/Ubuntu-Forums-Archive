---
title: "Using upstart to execute commands during boot"
date: 2008-04-03
forum: General Help
---

### Post by timothyp on 2008-04-03
Hi,

Before rc5 I need to make changes to a few files.

I created a script in /etc/event.d/ and added the following

```
start on runlevel 3
console logged

script
 #code here, using cat to add contents of a file to another
end script

```

When I use 
```
initctl emit runlevel 3
```

The script is executed and does what it's supposed to do,
but when I reboot the system it does not.

What could be causing this?
Where is all this being logged, for example if I execute echo "hello" or something?

Timothy.

---

### Post by reacocard on 2008-04-03
> **timothyp said:**
> Hi,

Before rc5 I need to make changes to a few files.

I created a script in /etc/event.d/ and added the following

```
start on runlevel 3
console logged

script
 #code here, using cat to add contents of a file to another
end script

```

When I use 
```
initctl emit runlevel 3
```

The script is executed and does what it's supposed to do,
but when I reboot the system it does not.

What could be causing this?
Where is all this being logged, for example if I execute echo "hello" or something?

Timothy.

default runlevel for ubuntu is 2.

---

### Post by timothyp on 2008-04-03
I see,
so how does that work for the graphical user interface and such then?

I know... (or at least I think) in the past
rc5 was the graphical user interface and rc3 was multiuser with networking?

Is this all different now ?

Thank you.

I need to execute changes before X11 is started.


(btw start on runlevel 2 does execute the script, so thank you for that :-))

---

### Post by cdenley on 2008-04-03
> I know... (or at least I think) in the past
rc5 was the graphical user interface and rc3 was multiuser with networking?
It depends on the distribution. I think debian-based distributions use runlevel 2.
[http://www.debian.org/doc/FAQ/ch-customizing.en.html#s-booting](http://www.debian.org/doc/FAQ/ch-customizing.en.html#s-booting)

You can also do this with an init script. I'm not sure which is the better way.

---

### Post by bodhi.zazen on 2008-04-03
Actually, with upstart there are no run levels any longer. The event scripts emulate run levels.

I wish I knew a little more about how upstart works, see if this link helps :

[http://www.linux.com/feature/125977](http://www.linux.com/feature/125977)

---

