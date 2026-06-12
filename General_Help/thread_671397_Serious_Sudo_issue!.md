---
title: "Serious Sudo issue!"
date: 2008-01-18
forum: General Help
---

### Post by Geran on 2008-01-18
It seems as though all sudo has gone. Whenever I run a command that requires sudo, it just cuts off and dies. For exmaple...

sudo /etc/init.d/dhcp3-server restart.

this returns no output, and doesn't do anything useful, it just ignores it. When I tried to open an administrator program, it tells me that the underlying system (sudo) will not allow this to happen. 

as always, help is much appreciated,

cheers,

G

---

### Post by danwood76 on 2008-01-18
You need to add yourself to the sudo group using the recovery console.
So reboot and select recovery mode.
then nano /etc/group

and make sure your username is in the admin group.

regards,
Danny

---

### Post by Geran on 2008-01-18
Thanks a lot, I'll try that.

---

