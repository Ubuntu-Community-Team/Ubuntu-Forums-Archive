---
title: "Setting up sshd for port 80?"
date: 2004-12-03
forum: General Help
---

### Post by diebels on 2004-12-03
I have a webserver at home with ssh running. At work port 22 is blocked, so I'm having trouble using putty to connect to my server. Could I just set my sshd to listen to port 80, or both 22 and 80?
sshd_config :
Port 22
Port 80

Or would would this break anything or be insecure?

---

### Post by diebels on 2004-12-03
Got an answer at #ubuntu. I think I'll set up iptables to
forward incoming requests to port 80 from gateway ip-addresses at my work to sshd (@port 22), from other ip adresses to apache.

---

