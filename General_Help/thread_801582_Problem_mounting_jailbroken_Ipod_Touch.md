---
title: "Problem mounting jailbroken Ipod Touch"
date: 2008-05-20
forum: General Help
---

### Post by Nate9009 on 2008-05-20
Hi everyone.  I've been trying to get my Ipod Touch (version 1.1.4) mounted under Gutsy for a while now and I keep running into problems.  I have the necessary packages installed and ipod-convenience is configured to my ipod's static IP.

When I try to mount the Ipod I get this : ```
nathan@<my computer>:~$ ipod-touch-mount
ssh_exchange_identification: Connection closed by remote host
read: Connection reset by peer
```

Also, I tried to manually ssh into the Ipod.  Here is the output : ```
nathan@<my computer>:~$ ssh 192.168.1.107 -l root -v
OpenSSH_4.6p1 Debian-5ubuntu0.5, OpenSSL 0.9.8e 23 Feb 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.1.107 [192.168.1.107] port 22.
debug1: Connection established.
debug1: identity file /home/nathan/.ssh/identity type -1
debug1: identity file /home/nathan/.ssh/id_rsa type 1
debug1: identity file /home/nathan/.ssh/id_dsa type -1
ssh_exchange_identification: Connection closed by remote host
```

Any idea on what I should do?  I've run into a brick wall into mounting this thing...

---

### Post by d_eckert on 2008-05-26
Have you installed openSSH on the ipod touch?

I forgot about this when I was setting mine up recently


EDIT:
nevermind, your debug info says it was able to establish a connection but it was subsequently dropped, so the server must be running on the ipod touch.

you need to ssh into the ipod as root, what happens when you try ssh **root@**192.168.1.107 ???

---

### Post by Gunman1982 on 2008-05-26
Seems it doesn't like your ssh dsa public key. Did you configure it to let you in without a login? (.ssh/authorized_keys)

---

### Post by Nate9009 on 2008-06-01
Would this be something I would do from my computer?  I don't recall ever setting up login info. :P

Also, here is the output of root@192.168.1.107 :

```
nathan@<my computer>:~$ ssh root@192.168.1.107
ssh_exchange_identification: Connection closed by remote host
```

I also ran the command as root (sudo) but still got the same message.

---

