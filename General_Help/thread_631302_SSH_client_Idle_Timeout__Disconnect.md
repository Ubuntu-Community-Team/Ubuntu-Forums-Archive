---
title: "SSH client Idle Timeout / Disconnect"
date: 2007-12-04
forum: General Help
---

### Post by bensode on 2007-12-04
I found this article about a keep alive packet and was wondering if there is a host specific setting that this could be applied to.

[http://ubuntu.wordpress.com/2006/02/03/keeping-ssh-sessions-alive/](http://ubuntu.wordpress.com/2006/02/03/keeping-ssh-sessions-alive/)

There is a single host that I would prefer not to timeout so quickly as it's my shell to a remote Redhat server that I keep Pine open.  Is there anyway to force ssh from the command prompt to not idle timeout or to change the idle timeout parameter without affecting every session by default?  Thanks!

Bensode

---

### Post by milton1 on 2007-12-04
there is a -o option for "connectTimeout" that might do the trick. Alternately, you could use "-F <configFile>" to substitute a custom config for that connection.

---

### Post by ScatterBrain on 2008-01-11
I've built two Gutsy servers now and both of them drop connections after a minute or so. This doesn't happen with my Dapper machines. I was just about to file a bug on this issue. (Actually did a Google search looking for previous bugs when I found this post.)
 
What actually happens is my Putty session gets disconnected and I have to restart (actually close and re-open) Putty to make new connections. At first I thought it was Putty, but then I connected to one of my Dapper boxes and left the session open and idle for more than 3 hours just to test it. Dapper connections work, Gutsy connections don't.
 
And unlike the response mentioned in bensode's link above, I don't have a router/firewall/NAT box between my workstation and the servers in question.
 
So my quiestions are: Is this now by design? Is there a way I can prevent this from happening? Is this a Debian/Ubuntu thing or an OpenSSH thing?

---

### Post by mooklyn on 2008-03-06
I am having the same problem. Default OpenSSH installation with keepalive, but Putty (on a Win workstation) randomly disconnects. This happens from different workstations. The same workstations connect successfully (indefinitely) to other OpenSSH servers on my Debian Machines, it's just my new install that's having trouble with Putty

ScatterBrain- I was able to connect and stay connected to that server via SSH in a terminal from another Lin-box just fine. It's just with Putty on my Win boxes that is dropping out. Maybe you want to try that?

Checking with netstat, the server still thinks it is connected for about 30 seconds and refuses new Putty connections until it disappears.

In the logs, there is a "received signal 15" for the disconnect, but google was not my friend in getting any solid leads on what is causing it.

Again, SSH via a linux terminal stays up just fine, it just appears to be with Putty.

Weird.

---

### Post by mooklyn on 2008-03-06
The problem is not specific to Putty, as I ran a Windows binary of Openssh (from sourceforge). It has the same problem as Putty - disconnecting my session after a few minutes. No problems from a remote linux terminal with ssh

I forgot to mention that my server is 64-bit, fresh install. The windows boxes connect fine to other 32-bit systems.

---

### Post by mooklyn on 2008-03-09
Well, count me out of this discussion.

After finding out about Dell sc440 specific issues with the NIC cards, swapping some drivers, etc, I just decided to pop in a PCI NIC that I had around, and viola- no disconnects.

BTW, before testing the new NIC, I installed VMware Server and was having sudden disconnects after a few minutes from VMware consoles on separate windows boxes as well with the onboard NIC.

In short, I am not going to fuss around with what is probably a bad onboard NIC implementation on the SC440. I'd rather put a nice intel card in it and leave my kernel drivers stock. Hopefully, that is the only flaw in this cheap machine.

---

### Post by bodhi.zazen on 2008-03-10
This is an old thread, but ...

For putty, there is a keep alive option in the (putty) gui, I use 120.

(you can run putty on both Linux and windows, it is in the repos).

For your server (if you have root access) :

Add this to /etc/ssh/sshd_config :
> KeepAlive yes
ClientAliveInterval 60

Again, I find 120 works just fine ...

For your client, there is not an option on the command line, rather add those same lines to your /etc/ssh/ssh_config (sshd_config is for the server, ssh_config is for the client)

HTH

---

### Post by bensode on 2008-03-10
Yeah I had similar problems with the SC440 from Dell just getting through installation.  I think I will be disabling that integrated NIC and putting in an Intel as well.  Nice catch!

---

