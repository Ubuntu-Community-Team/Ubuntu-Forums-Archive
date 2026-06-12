---
title: "OpenSSH Server - Auth failure"
date: 2007-04-13
forum: General Help
---

### Post by seantheman100 on 2007-04-13
I have been looking around a bit, not sure what the answer to my problem is; I have tried a bunch of things.

Alright. I have ubuntu edgy installed on my iMac G5 PowerPC. Everything has been going fine, working great.

I have hit a rut though, with OpenSSH.

I have installed OpenSSH through apt-get. When attempting to access my Ubuntu machine through my PC, over a local area network (router), I have been able to connect to it. However, the authentication methods are not working correctly for some reason.

**Example**: Through PuTTY, accessing ssh server.
```
login as: sean
sean@192.168.1.100's password:
Access denied
sean@192.168.1.100's password:
```

I know for a fact I am using the correct authentication password as I have on Ubuntu, so authentication errors on my part are outruled.

Can anyone help? I have tried a few configuration changes, rebooted the server, and still nothing. Please overview my options as to fixing this.

Thanks in advance,

---

### Post by nemarasu on 2007-04-13
what does your sshd config look like?

---

### Post by seantheman100 on 2007-04-13
**Content** of sshd_config (Path:/etc/ssh/sshd_config)
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
```

---

### Post by seantheman100 on 2007-04-13
Might I add those configurations are written on a fresh install, after removal of sshd_config and reinstall through apt-get.

---

### Post by nemarasu on 2007-04-13
The only thing I see different between my config and yours is my PasswordAuthentication is uncommented:

# Change to no to disable tunnelled clear text passwords
PasswordAuthentication yes

---

### Post by seantheman100 on 2007-04-13
**Change** 1: Attempting to uncomment the *PasswordAuthentication* line.

**Effect** 1:

```
login as: sean
sean@192.168.1.100's password:
Access denied
sean@192.168.1.100's password:
```

Same thing. What else would be doing this? PAM?

---

### Post by seantheman100 on 2007-04-13
Tried fiddling with PAM (as far as writing an sshd file in pam.d, no effect).

---

### Post by seantheman100 on 2007-04-13
Any idea, anyone?

---

### Post by seantheman100 on 2007-04-13
Here is a peice of my auth.log

**Content**: /var/log/auth.log [ section ]
```
Apr 13 16:56:48 host sshd[7618]: WARNING: /etc/ssh/moduli does not exist, using fixed modulus
Apr 13 16:56:52 host sshd[7618]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.1.101  user=sean
Apr 13 16:56:54 host sshd[7618]: Failed password for sean from 192.168.1.101 port 2971 ssh2
```

---

### Post by seantheman100 on 2007-04-13
Ideas?

-Sean

---

### Post by louieb on 2007-04-13
in the users home folder there is a hidden directory named .ssh it contains an encrypted file named known_hosts. anyway thats where it is in Ubuntu Linux on both the client and the server. Don't know where putty and windows keeps it. I was getting the auth error. What I did was edit the known_host file and left it empty. The next time I ssh into the server it rebuilt the known_host file and the auth error went away. Can't remember why I did it but it worked form maybe it will work for you to.

---

### Post by seantheman100 on 2007-04-13
Would this directory be located in /home or /home/user?

I tried to "cd" into /home/sean/.ssh, failed, therefore when I used nano to edit .ssh/known_hosts it failed as well.

I'll try using find to locate it.

---

### Post by seantheman100 on 2007-04-13
Ah, on the client end you mean?

The file was already blank.

What else could be doing it?

---

### Post by seantheman100 on 2007-04-13
Anymore ideas anyone?

---

### Post by seantheman100 on 2007-04-13
Anyone?

---

### Post by seantheman100 on 2007-04-13
bump.

Hate to bump. I am just really need to get SSH working on this computer.

Thanks,

---

### Post by louieb on 2007-04-14
> **seantheman100 said:**
> Ah, on the client end you mean?
The file was already blank.
What else could be doing it?
On mine I found the file **known_hosts** in ~/.ssh on both the server and the client. Its been a while since I did it and I'm pretty sure I only blanked out the one on the client. So I'm clueless. At least you get another bump.

---

### Post by seantheman100 on 2007-04-14
Yeah, but I am running PuTTY on my Windows machine.

There's got to be something to it thats doing this. It's taken a day for me to try all of this and I need it to work :(

---

### Post by stylishpants on 2007-04-14
Just to narrow down the possibilities, try to ssh from your ubuntu machine to itself, like this:

```
ssh localhost
```

If you can do this with no trouble, it could indicate that the ssh client config on your Windows box has a problem.

Also, just so we're completely clear, post the results of this command (run it on your ubuntu machine):

```
ls ~/.ssh
```

---

### Post by seantheman100 on 2007-04-14
Okay, I will try it.

---

### Post by seantheman100 on 2007-04-14
I have attempted through many different systems other than PuTTY as well as having my friends attempt to do it (I forwarded), and they receive the "Access Denied" error, after entering a password. This shows that it isn't a certain box problem, I know it isn't a passcode problem, and that it is connecting just fine, but not working correct.

After performing ls ~/.ssh, I recieved the following output through bash.

```
ls: /home/sean/.ssh: No such file or directory
```

Also, I reinstalled again, and installed OpenSSH two times, one with data from the Ubuntu Install CD, and the other with data downloaded with apt-get, and there is still no change in the outcome; I am still getting the "Access Denied" message when attmpting to log in through PuTTY and other systems.

---

### Post by seantheman100 on 2007-04-14
Update:

I think I know what the issue is.

When attempting to perform *ssh localhost*, I am able to access my OpenSSH server and connect to it. But, when I try to do it through the domain I have set up that points to my server, I get the permission denied error when connecting.

This means something in PAM or in the Ubuntu firewall is keeping me from logging in if I am not localhost.

How does PAM work? Where would configurations of allowed hosts to login with (I'm not talking connecting, as it is connecting fine, just no logging in) be located?

Is there somewhere in a file that PAM depends on that blocks hosts?

---

### Post by seantheman100 on 2007-04-14
Still nothing after fiddling with PAM a bit, I don't know what else to do.

---

### Post by seantheman100 on 2007-04-14
Can someone please help?

---

### Post by stylishpants on 2007-04-15
OK, here is some more stuff to try.  We still don't know why this is happening, so we're still in the data collecting phase here.

First, on your ubuntu machine, do another "ssh localhost", and log yourself in succesfully.  Then run this command, and post the output:
```
sudo tail /var/log/auth.log
```


Second, try again to ssh to your ubuntu box from your windows box.  Immediately after it fails, run that same command on your ubuntu box.  We want to see the authentication log message that gets generated when the login fails.  Again, post the output.


Third, find out what IP address you have on your ubuntu box like so:
```
ifconfig | grep cast
```
From your windows box, try to ssh to that IP address, instead of trying to ssh to the hostname.  It probably won't make any difference but it is one more thing to rule out.

One more thing: we know you can succesfully log in to your ubuntu box from itself with "ssh localhost".  You should also try to ssh to your ubuntu box from itself using the domain name you set up in place of "localhost".  Post the result.  Also keep an eye on the auth log as you do this and report anything unusual looking.

---

### Post by seantheman100 on 2007-04-15
**Issue Resolved.**

There is some bug in PAM I discovered that doesn't allow, no matter what is in the main configurations, other-than-localhost-pam-authentication. Hopefully, this is resolved.

I used a simple method of keys to authenticate myself. Yet, while in SSH through my windows box, a strange thing occured. I was unable to use the "sudo" command (because, of course, it uses PAM authentication).

There's a config somewhere.

Also how to you allow a user to have root access without using sudo? :) (e.g. normal user with root shell)

The idiot I am, I accidently, instead of my home directory, started to remove all files that could be in root, using the evil find. So, I reformatted, repartitioned, reconstructed, reinstalled Mac, then Ubuntu, and now I am going to update my installation, remove X once and for all, install links, then zlib, some other things I need to install so that I can compile ircII, then I will get a pair of RSA keys generated and install em into PuTTY. :)

---

### Post by seantheman100 on 2007-04-15
After reinstalling, I used a different password (this one with lowercase letters).

It works without keys now :)

---

### Post by t4thfavor on 2007-05-31
Just for the sake of being complete, I had the same problem with Putty, and when I put in the IP instead of the hostname it worked just fine. Don't know why, it just did.

---

