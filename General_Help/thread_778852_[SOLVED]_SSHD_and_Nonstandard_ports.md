---
title: "[SOLVED] SSHD and Nonstandard ports"
date: 2008-05-02
forum: General Help
---

### Post by snowjm on 2008-05-02
Hi there, I am trying to setup sshd to run on a nonstandard port. However when I edit the new port number into sshd_config and restart sshd I can no longer connect. I keep getting the error "Read from socket failed: Connection reset by peer" whenever I try to connect while it is running on the nonstandard port. However if I set sshd to run on port 22 again it seems to function normally. Anyone have any ideas?

---

### Post by sefs on 2008-05-02
I think they are two config files related to ssh in /etc/ssh

and they both have in a place where you have to set those custom port numbers.

Also have you remembered to set your routers/firewalls up with these new ports?

---

### Post by shad0w_walker on 2008-05-02
Have you checked that the server is actually listening on the new port? I would recommend checking it's listening on the port using something like

```
netstat -l
```

or

```
nmap -sT localhost
```

Nmap seems to find the open ports much quicker however it's not an option if you don't have it installed, so I included netstat.

---

### Post by snowjm on 2008-05-02
Firewall is changed to filter the correct port. Also the two configs are for the client and the server. The server config file is sshd_config, which is the file I need to edit to make sshd run on the port I want it too. For some reason though whenever I change the port I get the above behavior. =/

---

### Post by warp99 on 2008-05-02
> **snowjm said:**
> Hi there, I am trying to setup sshd to run on a nonstandard port. However when I edit the new port number into sshd_config and restart sshd I can no longer connect. I keep getting the error "Read from socket failed: Connection reset by peer" whenever I try to connect while it is running on the nonstandard port. However if I set sshd to run on port 22 again it seems to function normally. Anyone have any ideas?

When you issue the new command include the port number like so:
```
 ssh -p 9999 my_machine.com
```
you can make this permanent by editing the ssh_config file on your client machine by uncommenting the 'port 22' line and changing it to the new port.

Edit:

In your sshd_config add the new port number like so:
```
# What ports, IPs and protocols we listen for
Port 22
Port 9999
```
also make sure that port is not in use by another service and that the new port is accessible by your firewall and/or router if accessing the computer behind a router.

---

### Post by snowjm on 2008-05-02
> **warp99 said:**
> When you issue the new command include the port number like so:
```
 ssh -p 9999 my_machine.com
```
you can make this permanent by editing the ssh_config file on your client machine uncommenting the 'port 22' line and changing it to the new port.

Doing that already as well. I will clarify a little more the scenario that occurs.

I edit my sshd_config file to run on port 'XXX' by changing the following line

```
Port 22
```

to be
```
Port XXX
```

I then restart sshd, and check to make sure that is running on the correct port with

```
netstat -l | grep XXX
```

and make sure that its open with nmap as well, which it is. (I do love nmap!)

and then i try connecting to my ssh server from both localhost and from a foriegn computer, making sure to specify the port I need to connect to in the command. However I still get the error

```
Read from socket failed: Connection reset by peer
```

---

### Post by Monicker on 2008-05-02
Were there any errors in /var/log/messages or /var/log/auth.log relating to the attempted connections?

---

### Post by snowjm on 2008-05-02
Ugh... found the problem. I had two instances of the server running, one as root and one as a non-root user. I just killed the non-root user and everything seems to be working normally now. The non-root user was also running on the nonstandard port I was trying to set it to. 

Thanks for the help guys. :)

---

### Post by shad0w_walker on 2008-05-02
Lol, that's always the sort of thing that happens with cases like this. Don't forget to tag the thread as solved in case someone else has this happen.

---

### Post by snowjm on 2008-05-02
Will do.

---

### Post by FastZ on 2008-05-02
Whenever you change the port that sshd listens on you must attempt to connect via that port by using the -p option.

For example:

Say I changed the listening port for sshd to 5678 in /etc/ssh/ssh_config.  I restarted sshd, then, in order to connect to that machine via ssh you have to use the following type command.

ssh -p 5678 ipaddress.of.remote.host

---

### Post by shad0w_walker on 2008-05-02
Uh, I'm afraid you're a little late. The problem was already fixed.

[http://ubuntuforums.org/showpost.php?p=4862822&postcount=8](http://ubuntuforums.org/showpost.php?p=4862822&postcount=8)

---

