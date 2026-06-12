---
title: "ssh pubkey error after shutdown/reboot"
date: 2016-10-19
forum: General Help
---

### Post by courtney2 on 2016-10-19
I have a computer that I connect to via ssh with a shared key only (no password authentication permitted), and I found something interesting. If I do a reboot or shutdown I cannot connect to the computer via ssh unless I restart the daemon on the computer I connect to. Is there a way to prevent this from happening when I reboot to do updates?

---

### Post by kevdog on 2016-10-20
What version of Ubuntu are you running?  Yes the daemon has to be running, because in effect the server isn't listening for inbound ssh connections. 

If using 16.04 or later, the command would be
sudo systemctl enable sshd.service

---

### Post by courtney2 on 2016-10-21
The service is enabled by default on boot. I can no longer ssh from a remote network either. I don't know why, but after the very first shutdown I have had after creating my ssh shared keys, I have to restart the ssh daemon after reboot (even though it's enabled) and I am completely blocked from ssh'ing in remotely. The port is open

And it's Ubuntu 16.04

---

