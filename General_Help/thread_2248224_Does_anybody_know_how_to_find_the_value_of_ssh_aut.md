---
title: "Does anybody know how to find the value of ssh_auth_sock= ?"
date: 2014-10-13
forum: General Help
---

### Post by MechaMechanism on 2014-10-13
Does anybody know how to find the value of ssh_auth_sock= ?

---

### Post by jamesisin on 2014-10-13
Have you tried echo?

*echo "$SSH_AUTH_SOCK"*

---

### Post by MechaMechanism on 2014-10-13
> **jamesisin said:**
> Have you tried echo?

*echo "$SSH_AUTH_SOCK"*

nate@triton:~$ echo "$SSH_AUTH_SOCK"
/tmp/ssh-ITdi1E890mua/agent.2454

Are the numbers at the end the socket?  Is that the value of sock?

---

### Post by tgalati4 on 2014-10-13
If you want the actual port that *ssh* is using to communicate, you can log into your server:

> gates@GNAS ~ $ env | grep SSH
SSH_CLIENT=XX.XX.XX.173 60133 22
SSH_TTY=/dev/pts/1
SSH_CONNECTION=XX.XX.XX.173 60133 10.10.XX.XX 22


In this case port 60133 is being used to direct traffic to port 22 on 10.10.XX.XX LAN.

The authorization socket file for this connection:

> 
gates@GNAS /tmp/ssh-ocn1S36iQPBO $ ls
agent.1657


---

### Post by MechaMechanism on 2014-10-13
> **tgalati4 said:**
> If you want the actual port that *ssh* is using to communicate, you can log into your server:



In this case port 60133 is being used to direct traffic to port 22 on 10.10.XX.XX LAN.

The authorization socket file for this connection:
Thank you.

---

