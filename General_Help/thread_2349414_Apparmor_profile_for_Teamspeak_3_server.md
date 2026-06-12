---
title: "Apparmor profile for Teamspeak 3 server"
date: 2017-01-14
forum: General Help
---

### Post by ralphwiggum2 on 2017-01-14
Hi,

I have following problem:
I've installed a ts3 server and want to secure it now by adding a apparmor profile.
I used the command "aa-genprof /usr/local/teamspeak3/teamspeak3-server_linux_amd64/ts3server" and then scanned for activities (additionally with aa-logprof).
However apparmor doesn't find entries although i've started the server, added channels and users connected in the mean time.
The path is valid (checked several times already).

System: Ubuntu 16.04 64 Bit

What can i do differently?

Here my generated profile:
```
# Last Modified: Sat Jan 14 13:13:54 2017
#include <tunables/global>

/usr/local/teamspeak3/teamspeak3-server_linux_amd64/ts3server {
  #include <abstractions/base>

  /usr/local/teamspeak3/teamspeak3-server_linux_amd64/ts3server mr,

}
```

---

