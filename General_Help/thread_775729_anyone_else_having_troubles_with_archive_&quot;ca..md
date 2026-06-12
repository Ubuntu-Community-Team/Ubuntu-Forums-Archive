---
title: "anyone else having troubles with archive &quot;ca.archive.ubuntu.*&quot;?"
date: 2008-04-30
forum: General Help
---

### Post by atuzyk on 2008-04-30
Hey, just a question

when ever i run update manager or a synaptic of any kind, whenever it requests something from repo or archive with the prefix "ca.archive" it ALWAYS fails. Even when I upgraded from 7.10 to 8.04 it did the same thing. I had to follow a work around I found somewhere else. And well, it didn't work great, but thats probably because I like to mess around in the terminal way to much :D. BUT, the same problem still applies. Is there anything I can do? ANOTHER work around perhaps? 

Any info would be great 

Thanks yo

---

### Post by bve on 2008-04-30
I'm currenlty having problems with the repo.

```

burke@zeus:~$ ping ca.archive.ubuntu.com
PING mirror.csclub.uwaterloo.ca (129.97.134.71) 56(84) bytes of data.

--- mirror.csclub.uwaterloo.ca ping statistics ---
12 packets transmitted, 0 received, 100% packet loss, time 11001ms

burke@zeus:~$ ping ca.archive.ubuntu.com
PING mirror.csclub.uwaterloo.ca (129.97.134.71) 56(84) bytes of data.

--- mirror.csclub.uwaterloo.ca ping statistics ---
20 packets transmitted, 0 received, 100% packet loss, time 19003ms


```

I should mention this is the first problem I've had though, it usually works just fine.

---

### Post by bollix47 on 2008-04-30
System > Administration > Software Sources

Click on the arrows at the end of Download from .... and change to Main Server.

---

### Post by ryth on 2008-04-30
> **atuzyk said:**
> Hey, just a question

when ever i run update manager or a synaptic of any kind, whenever it requests something from repo or archive with the prefix "ca.archive" it ALWAYS fails. Even when I upgraded from 7.10 to 8.04 it did the same thing. I had to follow a work around I found somewhere else. And well, it didn't work great, but thats probably because I like to mess around in the terminal way to much :D. BUT, the same problem still applies. Is there anything I can do? ANOTHER work around perhaps? 

Any info would be great 

Thanks yo

I've been having the same issues.  As suggested above I switched to the main archive, but ideally I'd prefer to use the Canadian archive to keep the load off the main server.

---

### Post by atuzyk on 2008-04-30
thank you, lol. I should've looked right in front my nose. 

anyway, all is well, all is working. I'll switch back to the Canada source in a couple days, she where shes at.

thanks guys!

---

### Post by bve on 2008-05-01
FYI the Canadian archive is working for me this morning.

---

### Post by cyrusrayne on 2008-05-01
I selected "other server" then "gulus.usherbrooke.ca".  Seems to be working alright.

---

