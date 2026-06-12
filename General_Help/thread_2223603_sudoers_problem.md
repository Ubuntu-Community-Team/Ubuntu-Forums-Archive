---
title: "sudoers problem"
date: 2014-05-12
forum: General Help
---

### Post by madnbri on 2014-05-12
Hi,
I've a strange problem in **sudoers**. I used these settings before (maybe I forget the correct way), but it doesn't work now:
```
User_Alias SHUTDOWN_USERS = user1, user2
Cmnd_Alias SHUTDOWN_CMNDS = /sbin/poweroff, /sbin/halt, /sbin/reboot
SHUTDOWN_USERS ALL=ALL(ALL) NOPASSWD: SHUTDOWN_CMNDS
```
When I save, it is ok.
```
$sudo poweroff
[sudo] passwd for user1: _
```
Are there any mistake in my sudoers?
Thanks for advance,
m

---

### Post by jensmaucher on 2014-05-12
Try this one:

SHUTDOWN_USERS ALL = NOPASSWD: SHUTDOWN_CMNDS

---

### Post by madnbri on 2014-05-12
It also doesn't work as SHUTDOWN_USERS ALL=(ALL:ALL) NOPASSWD: SHUTDOWN_CMNDS

---

### Post by jensmaucher on 2014-05-12
My sudoers, and it works now:
```

Cmnd_Alias DOWN = /sbin/poweroff, /sbin/reboot, /sbin/halt
my_username ALL = (ALL) ALL, NOPASSWD: DOWN 

```

$sudo reboot

and pc is rebooting without password

---

### Post by madnbri on 2014-05-12
But not at me :(

---

### Post by jensmaucher on 2014-05-12
Hm, strange :frown:

Last try..
Put your line
```
SHUTDOWN_USERS ALL=ALL(ALL) NOPASSWD: SHUTDOWN_CMNDS
```
**after** the line with the rule for the admin group.

```

.
.
%admin ...
%sudo ...
SHUTDOWN_USERS ALL=ALL(ALL) NOPASSWD: SHUTDOWN_CMNDS

#includedir /etc/sudoers.d

```

---

### Post by madnbri on 2014-05-12
OK, it was the last try from you. sudoers manual didn't help (of course, why should it be useable?). Somebody else? Has anybody a working sudoers to post here?

... edited ...

SHUTDOWN_USERS ALL=(ALL) NOPASSWD: SHUTDOWN_CMNDS working now. I do not know why does and why didn't earlier.

Thanks for help!

P.S.: I don't mark the post [solved] still I don't understand.

---

