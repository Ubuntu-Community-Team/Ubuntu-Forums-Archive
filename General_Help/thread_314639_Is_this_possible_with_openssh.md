---
title: "Is this possible with openssh?"
date: 2006-12-07
forum: General Help
---

### Post by lemonsCC on 2006-12-07
[LIST=1]
[*]I would like to be able to message all logged in users on my Ubuntu system using openssh via my powerbook.  I know echo will repeat something to my user....but I don't know how to message the other logged in users
[*]Next, is it possible to logout a user from terminal?  I believe it is possible using their UID, but again I don't know the commands.
[*]Lastly is it possible to connect to my Ubuntu box (using ssh) from a computer not on my network, say from school or elsewhere on the internet?
[/LIST]

---

### Post by IYY on 2006-12-07
> 
I would like to be able to message all logged in users on my Ubuntu system using openssh via my powerbook.  I know echo will repeat something to my user....but I don't know how to message the other logged in users


The 'write' command might be what you're looking for. 'man write' to read its manual page.

> Next, is it possible to logout a user from terminal?  I believe it is possible using their UID, but again I don't know the commands.

I don't know if it's the best way, but 'ps -u someusername' will give you the PIDs of all processes from user someusername. You can kill a process using 'kill -9 123' where '123' is the PID.

> 
Lastly is it possible to connect to my Ubuntu box (using ssh) from a computer not on my network, say from school or elsewhere on the internet?


Yes, I do it all the time. If you are behind a router, you will need to forward the SSH port (I think it's 22) to the machine you wish to access.

---

### Post by lemonsCC on 2006-12-07
Thanks for the prompt response.  

1)  Write is **exactly** what i needed!
2)  This seems a little blunt...i will keep looking for a "nicer" method
3)  Simple enough for me.

---

### Post by SyvanX on 2006-12-07
As an extra, if you are going to use ssh from outside your network, use a port other than 22, you can go up to about 64,000.  You may also want to consider only allowing ssh logins from authorized users.  You can change these in /etc/ssh/sshd_config

---

### Post by CoolHand on 2006-12-07
> **lemonsCC said:**
> [LIST=1]
[*]I would like to be able to message all logged in users on my Ubuntu system using openssh via my powerbook.  I know echo will repeat something to my user....but I don't know how to message the other logged in users
[*]Next, is it possible to logout a user from terminal?  I believe it is possible using their UID, but again I don't know the commands.
[*]Lastly is it possible to connect to my Ubuntu box (using ssh) from a computer not on my network, say from school or elsewhere on the internet?
[/LIST]

For the first question you have two options.  If they are on terminals then the command you want is wall.  Here is an example "echo help me | wall"
If you need something that will show up in an X session then you may want to look into linpopup.

For your second question a quick google search found a good help page with many examples. [http://www.cyberciti.biz/tips/howto-linux-kill-and-logout-users.html]("http://www.cyberciti.biz/tips/howto-linux-kill-and-logout-users.html")

For number three it depends on your home setup.  I log in remotely to ssh all the time.  I have a small router with port 22 (ssh) forwarded to the machine I want access to remotely.  Then I set up a dns name using the free dyndns service so I can find my host.  If you have a direct connection to the net it is even easier.  Just make sure you forward and/or open port 22 through any firewalls needed to get to the machine you want.

---

### Post by lemonsCC on 2006-12-07
syvan i will look into that file later

coolhand i am looking at linpopup as i type this.  the external access was more of a can i not that i actually will.  


How secure is openssh?

---

### Post by RAOF on 2006-12-07
> **lemonsCC said:**
> ...

How secure is openssh?

Very.  Pretty much the most secure way to allow remote users to login, which is just about the biggest security hole you can introduce :).

You might want to check out the ssh-howto on the WIKI if you're concerned about security.  [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by Johan! on 2006-12-08
To improve the security of an open SSH port, you can install fail2ban.

---

### Post by lemonsCC on 2006-12-08
> **SyvanX said:**
> As an extra, if you are going to use ssh from outside your network, use a port other than 22, you can go up to about 64,000.  You may also want to consider only allowing ssh logins from authorized users.  You can change these in /etc/ssh/sshd_config

How would I specify authorized users?

/etc/ssh/sshd_config:

```
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
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
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile     %h/.ssh/authorized_keys

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
```

---

### Post by kosmic on 2006-12-08
Please do not allow ROOT LOGINS, it is a serious security flaw

# Authentication:
LoginGraceTime 120
PermitRootLogin yes (change it to no)
StrictModes yes

To allow users just type in the same file :
[B]AllowUsers username (where username is your username)

[/B]

---

### Post by CoolHand on 2006-12-08
> **lemonsCC said:**
> syvan i will look into that file later

coolhand i am looking at linpopup as i type this.  the external access was more of a can i not that i actually will.  


How secure is openssh?

I agree with the above that ssh is very secure.  There are a few things to note though.  As stated above disable root logins.  Also do not allow version 1 of the protocol only ssh 2.  Version one had some holes in it.  If you really want to make it secure you could also look into an additional service called port knocking.  What it does is makes port 22 look like it is not open until is receives a certain pattern of access attempts then it accepts the connection as normal and goes on with the service you set it up for.  I am pretty sure there are windows port knock clients available as well but I don't currently have it set up.  I was just considering setting it up.

---

### Post by Ramses de Norre on 2006-12-08
DenyHosts is a very useful and configurable program to secure your ssh server too, take a look at it it's in the repos.

---

### Post by lemonsCC on 2006-12-09
I have tried write and wall and linpopup... none of them work.

write and wall need a terminal open to display and linpopup cant be run over ssh as far as i know.

So:  I am still looking for a way to message users.  And I am now looking for a way to logoff users, both via ssh.

---

### Post by CoolHand on 2006-12-10
> **lemonsCC said:**
> I have tried write and wall and linpopup... none of them work.

write and wall need a terminal open to display and linpopup cant be run over ssh as far as i know.

So:  I am still looking for a way to message users.  And I am now looking for a way to logoff users, both via ssh.

This may be a bit difficult if you aren't too familiar with command line but if you are and are willing to read a bit from the man page you may want to try gmessage.  It is a tool to allow a small group of gui widgets to be called from a script or the command line.  It's very easy to use and if you have root access you should, according to the man page, be able to specify which X display to use so you could display it to whichever user you wish.  You may have to play with xhost some to get access or the various display choices but it is an option.

---

