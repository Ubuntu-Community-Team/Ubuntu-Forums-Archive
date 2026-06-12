---
title: "Ubuntu logs off unexpectedly"
date: 2008-04-24
forum: General Help
---

### Post by GTengineer on 2008-04-24
Hi all,

I have this really annoying problem that causes my system (Ubuntu 8.04) to suddenly log off for no reason that I can tell. It is really annoying me because it happens unexpectedly and I lose any data I am working on. I am using NVIDIA 8800GT with restricted drivers. Can anyone help me resolve this?

Thanks!

---

### Post by savagenator on 2008-04-24
you won't get a good reponse unfortunatly unless you tell us what appears in your logs

check the files 

/var/log/messages
ande
/var/log/debug

---

### Post by GTengineer on 2008-04-24
> **savagenator said:**
> you won't get a good reponse unfortunatly unless you tell us what appears in your logs

check the files 

/var/log/messages
ande
/var/log/debug

savagenator, thanks for the quickly reply. I am a noob so bare with me...

I ran cat /var/log/messages and cat /var/log/debug I can post them but the files are very long. Is there anything specific I am looking for? I went through them but could not find anything that would tell me a problem exists.

My Windows XP virtualbox has also been crashing but I don't know if the problem is related. It usually just closes with this error below but does not log me off.

> Log created: 2008-04-18T13:14:10.777039000Z
Executable: /usr/lib/virtualbox/VirtualBox
Arg[0]: /usr/lib/virtualbox/VirtualBox
Arg[1]: -comment
Arg[2]: Microsoft Windows XP (32bit)
Arg[3]: -startvm
Arg[4]: e2fe1043-8106-496e-5f80-b6a034bca3de

!!Assertion Failed!!
Expression: <NULL>
Location  : /build/buildd/virtualbox-ose-1.5.6-dfsg/src/VBox/Devices/Storage/DevATA.cpp(4844) void ataReset(PDMDEVINS*)
Async I/O thread busy after reset

---

### Post by GTengineer on 2008-04-26
My machine just logged me off right now and this is the closest event logged around the time this happened....

from:
> cat /var/log/messages

> Apr 26 22:55:40 leonidas pulseaudio[17427]: pid.c: Stale PID file, overwriting.

Anyone has any ideas? :confused:

---

### Post by babanesma on 2008-11-24
I have the same problem on 8.10

---

