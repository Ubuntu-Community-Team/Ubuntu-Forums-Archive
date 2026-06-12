---
title: "Copy and paste from terminal in ubuntu vmware"
date: 2007-02-11
forum: General Help
---

### Post by PerseP on 2007-02-11
Hi,
I want to know if it's possible to copy and paste from windows xp host to an ubuntu 6.10 terminal windows. That is, i have ubunut 6.10 installed in vmware without X Windows, only a command line system.

All the references I've seen so far are with X windows not without them.

I've installed vmware tools and vmware-tools status reports vmware-guestd is running.

I have windows xp sp2 as host and ubuntu 6.10 as guest and vmware 5.5.2.

I can select, copy and paste between terminals with gpm but dowsn't work from/to vmware and win xp

Thanks

---

### Post by koenn on 2007-02-11
you can do this with puTTY. It's a "terminal" that runs on windows, and you can connect it to the (virtual) ubuntu via SSH (it's an option in puTTY, you'll see). You will have a terminal in Windows, but everything you do there will happen on the Ubuntu machine. 

This requires
- openserver installed and running in the ubuntu machine
- network available between vnware and host. This is een option you can configure but i don't remember excatly where and how.

---

### Post by PerseP on 2007-02-11
Hi,

thanks for the suggestion, it's worth a try.
I think you mean openssh instead of openserver?

---

### Post by koenn on 2007-02-11
yeah, i always mix those up. ssh, sshd ssh-server, openssh ... 
you just need an ssh server,

---

