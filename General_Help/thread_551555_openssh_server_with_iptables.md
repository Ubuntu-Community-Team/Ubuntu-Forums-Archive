---
title: "openssh server with iptables"
date: 2007-09-15
forum: General Help
---

### Post by bone2006 on 2007-09-15
I was told to change my default ssh server to another port than 22, I changed it in the config file, changed it on the router, but when I'm using fliezilla remotely it's not allowing me in. 
Since I changed only the router and the  /etc/ssh/sshd_config  do I also need to change iptables or something else?  I'm running the latest ubuntu server with LAMPS

thanks in advance

---

### Post by Wicca on 2007-09-15
Hi!

Did it all work before you changed the port?

Have you configured iptables? If you did not, then iptables is allowing all traffic so that cannot be the problem. What is the output of

```
sudo iptables -L
```?

---

### Post by qpieus on 2007-09-15
I'm not familiar with filezilla, but I assume you would need to specify an alternate ssh port somewhere in the filezilla settings. I'm guessing it would use port 22 as default and since you are using something different, you need to tell it so. Also, double check that the alternate port is forwarded correctly on your router.

---

### Post by bone2006 on 2007-09-15
yeah, filezilla worked and everything worked ok, then I just went into that config file changed the ports to a high number with 5 numbers in total, went into my router that has dd-wrt firmware and changed the portforwarding from 22 to the new port like 44444 and then I tried fliezilla putting in my real IP as I've done before instead of the internal IP and it didn't work.  It's been TCP port forwarding as it was before.

The print out is this 

sudo iptables -L


Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

yes the port is in filezilla alright

---

### Post by bone2006 on 2007-09-15
here's what I'm seeing in filezilla

Response:	fzSftp started
Command:	open user@IP PORT
Error:	Could not connect to server
Error:	Connection refused

I just edited the values for user, IP and PORT

---

### Post by qpieus on 2007-09-15
In the dd-wrt port forwarding area, did you change both the "port from" and the "port to" to your new ssh port number?

As far as iptables go, I know nothing, so hopefully someone else can join in and help out there.

---

### Post by Wicca on 2007-09-15
iptables -L shows that Iptables is not blocking anything, so there is no problem.

You changed sshd_config, but only the portnumber, nothing else, right?

In that case the most logical explanation is that your router configuration is wrong.
Make sure, as qpieus mentioned,  that the incoming AND outgoing port are both set to your new portnumber.

---

### Post by bone2006 on 2007-09-15
Well the only thing else I changed was not to allow root login, I don't have a root account created anywhere or at least not assigned a password.  I only have my main account and one more I created.

I tried to see what would happen if I did it in ssh in the terminal on my main machine and say my IP is 1.1.1.1 and the port is 33333 it says this:

$ ssh -l user 67.162.171.212:22222
ssh: 1.1.1.1:3333: Name or service not known

$ ssh -l user 1.1.1.1
ssh: connect to host 1.1.1.1 port 22: Connection refused

$ ssh -l user 1.1.1.1:3333
ssh: 61.1.1.1:3333: Name or service not known

Here's the file

> # Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 33333
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

---

### Post by bone2006 on 2007-09-15
I think the port fowarding on the box isn't working.  When I type in 

ssh -jasz 1.1.1.1 

I can login, but if I type in 

ssh -jasz 1.1.1.1:33333

Just using local IP it won't work.  So isn't the first one default 22? Isn't ssh default 22, such as http being 80 and ftp being 21..etc?  So that since I'm using the terminal and did not specify the port, it must be using port 21 still right?

---

### Post by bone2006 on 2007-09-15
should I have stopped openssh server and restarted it after saving the configuration?  I don't have a monitor or keyboard connected to this box, so I was hoping not to have to reboot, just encase the mobo complains about not having a monitor hooked up to it

---

### Post by bone2006 on 2007-09-15
I did  sudo /etc/init.d/ssh restart 
now I can't get in 22 nor 33333

---

### Post by Wicca on 2007-09-15
> **bone2006 said:**
> I think the port fowarding on the box isn't working.  When I type in 

ssh -jasz 1.1.1.1 

I can login, but if I type in 

ssh -jasz 1.1.1.1:33333

Just using local IP it won't work.  So isn't the first one default 22? Isn't ssh default 22, such as http being 80 and ftp being 21..etc?  So that since I'm using the terminal and did not specify the port, it must be using port 21 still right?

In a terminal the right syntax is ssh user@1.1.1.1 -p 33333. If you leave the -p out port 22 is assumed.

> **bone2006 said:**
> 
I tried to see what would happen if I did it in ssh in the terminal on my main machine and say my IP is 1.1.1.1 and the port is 33333 it says this:

$ ssh -l user 67.162.171.212:22222
ssh: 1.1.1.1:3333: Name or service not known

$ ssh -l user 1.1.1.1
ssh: connect to host 1.1.1.1 port 22: Connection refused

$ ssh -l user 1.1.1.1:3333
ssh: 61.1.1.1:3333: Name or service not known

Here's the file

Although the syntax is not correct, this shows to me that your router does not forward port 3333. It does forward port 22 (which it should not). So again, check your router config.

What you call your main machine: is it outside your network, so connecting through your router to your server?

---

### Post by bone2006 on 2007-09-15
that did the trick you so much much and every one else who helped me

---

### Post by qpieus on 2007-09-15
Please post what exactly the solution was, so that others may benefit. Was it your router settings that were not correct?

I'm glad you fixed it :)

---

### Post by bone2006 on 2007-09-15
The solution was I never restarted the server.  I had to do

sudo /etc/init.d/ssh restart 

router was fine and everything else was fine the server just needed restarted.

---

### Post by bone2006 on 2007-09-15
to specific port you -p and not like an ftp with : following the port

So edit the config file, then reboot the server (biggest mistake-wasn't aware), then to login to say IP 1.1.1.1 and port 33333 do:

ssh -l user 1.1.1.1 -p33333

hope this helps

the reboot instructions were already posted and that was the biggest mistake in getting the ports to change, not firewall, not router, nothing else

I did sudo /etc/init.d/ssh restart

---

### Post by qpieus on 2007-09-16
> **bone2006 said:**
> The solution was I never restarted the server.  I had to do

sudo /etc/init.d/ssh restart 

router was fine and everything else was fine the server just needed restarted.
cool, thanks for the update. Funny it was something so simple.

Another format for the ssh command that works is:

ssh -p 33333 user@1.1.1.1

---

