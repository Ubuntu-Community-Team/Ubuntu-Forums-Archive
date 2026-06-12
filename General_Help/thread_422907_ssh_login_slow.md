---
title: "ssh login slow"
date: 2007-04-25
forum: General Help
---

### Post by bugler on 2007-04-25
My ultimate goal is to ssh tunnel web browsing from my lappy via a spare winxp box at work and my home machine.

I am having a slow login on a cygwin sshd box.  I have cygwin installed on 2 boxes.

I have commented out GSSAPI stuff and uncommented protocol and selected only 2.

My linux box is ubuntu feisty (which works great on my hp dv6450 lappy).

Here's what happens:  I login with ssh -ND 9999 user@domain.  When after about 5 sec or so i get the password prompt.  I have checked all the other threads pertaining to this and cannot get it going.  when I ssh -v from lappy to cygwin box the response hangs the longest on this message
> debug1: SSH2_MSG_SERVICE_ACCEPT received
this hangs on both cygwin sshd server machines.

additionally I cannot connect from the outside with a response of 
> connection refused

Router forwarded port to static ip cygwin box. 

Any help would be great.  If you need more information let me know.

PS I just read about useDNS=no and will try that on the box when I get to work.

Bugler

---

### Post by buttari on 2007-05-03
Hi,
I had the same problem and I solved it commenting out everything in my /etc/ssh/ssh_config file. 
Alfredo

---

### Post by hdotcom on 2007-05-26
Hi all,

I've experienced a similar problem and i managed to resolve it by changing the value for  “GSSAPIAuthentication” to "no" on my /etc/ssh/ssh_config file. This will disable the DNS look up feature for this security API.

Rgds,

H.

---

### Post by tjansson on 2007-08-14
It had similar problems with connection from a laptop whit a dhcp address not written into the /etc/hosts. When connection to a ubuntu machine on the network it would fail. This would not happen if the machine on my server which had static IP written in /etc/hosts.

To fix this problem I added the following to /etc/ssh/sshd_config
```

UseDNS no

```
and reloaded the ssh server with
```

root@bohr:~# /etc/init.d/ssh reload

```

---

