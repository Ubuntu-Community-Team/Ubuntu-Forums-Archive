---
title: "Can't stop SSH server (12.10)"
date: 2012-11-15
forum: General Help
---

### Post by CosmicFlux on 2012-11-15
Hi,

I'm trying to use the **sudo /etc/init.d/ssh stop** command to stop the ssh server I'm running, but I get the following message:

[I]Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service ssh stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop ssh
ssh stop/waiting
[/I]

The problem is issuing **service stop ssh** gives me the following:

[I]stop: Rejected send message, 1 matched rules; type="method_call", sender=":1.91" (uid=1000 pid=5754 comm="stop ssh ") interface="com.ubuntu.Upstart0_6.Job" member="Stop" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")
[/I]

What's going on? I have ssh listening on my network, which I'm quite concerned about!

Cosmic

---

### Post by drmrgd on 2012-11-15
It may be because you inverted the words stop and ssh.  Try:

```
sudo service ssh stop
```

---

### Post by CosmicFlux on 2012-11-15
Yeah, that worked. Thanks! 

I'm still having a problem actually connecting to my remote host though. I use sudo ssh -p {port number} user@host-IP and hit enter but nothing happens. The cursor just blinks and I have to issue a break to kill the attempt. 

I used ifconfig on the remote host to get the IP address, so I'm pretty sure it's correct. 

Any ideas? 


Cosmic

---

### Post by drmrgd on 2012-11-15
> **CosmicFlux said:**
> Yeah, that worked. Thanks! 

I'm still having a problem actually connecting to my remote host though. I use sudo ssh -p {port number} user@host-IP and hit enter but nothing happens. The cursor just blinks and I have to issue a break to kill the attempt. 

I used ifconfig on the remote host to get the IP address, so I'm pretty sure it's correct. 

Any ideas? 


Cosmic


It's usually helpful to use the very verbose (-vvv) option of ssh when you try to connect.  That will give you some debugging info to help determine what's messing up the works.  It's a bit hard to diagnose without.  Try running:

```
ssh -vvv -p <port> <user>@<domanin>
```

And see what you get.

---

### Post by Lars Noodén on 2012-11-15
Also, you might want to avoid calling ssh using sudo.  It's not necessary.  You can call ssh from your regular account.

---

### Post by CosmicFlux on 2012-11-15
I get **ssh_connect: needpriv 0 **

and it then hangs on trying to connect to the host. 

The host *is* running a firewall. Is that blocking the connection?

---

### Post by drmrgd on 2012-11-15
It could be.  I wondered that when you mentioned that you use a different port than 22 (or at least that was my assumption based the use of the -p option).  You might make sure that whatever alternate port you're using is open to connections.

---

