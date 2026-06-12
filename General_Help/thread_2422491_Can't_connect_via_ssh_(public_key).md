---
title: "Can't connect via ssh (public key)"
date: 2019-07-08
forum: General Help
---

### Post by theycallmevirgo on 2019-07-08
I'm running 18.04.2 LTS through WSL. I added my public key to vi ~/.ssh/authorized_keys but and restarted sshd but the putty connection is still refused with "no supported authentication methods available (server sent: publickey). What can I try?

Thanks so much

Joe

---

### Post by TheFu on 2019-07-10
I know ZERO about Windows or WSL or 18.04, but I've been around a long time and using Unix systems 25+ yrs.  I've heard of putty, but haven't used it in over a decade, probably.  I have no idea how to troubleshoot from Windows unless you use the openssh-client tools.

First, try increasing the verbosity.
```
$ ssh -vvvv  remote-userid@remote-IP
```
Obviously, change the arguments for your needs.

Also, know that ssh is very picky about directory and file permissions, so those must be correct.
Some more ssh troubleshooting ideas: [https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)

---

