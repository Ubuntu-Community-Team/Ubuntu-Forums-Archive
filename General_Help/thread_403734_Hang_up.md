---
title: "Hang up"
date: 2007-04-07
forum: General Help
---

### Post by csyckad on 2007-04-07
Ubuntu 6.06, software raid 1, Install  Vmware-server for testing

I dont know why, my machine already run 2 month, is very ok, but suddenly hang up with kernel panic. no response to the keyboard.

After reboot the server, I cat /proc/mdstat, i see the raid is resync, is it mean that my raid is dead before, so imply kernel panic? 

Where can i see more information, dmesg or /var/log/debug or /var/log/kern.log


Thanks

---

### Post by MoLE on 2007-04-19
all those logs could contain useful information on this.  Post your output of dmesg first and see if anyone here can point you in the right direction.

---

