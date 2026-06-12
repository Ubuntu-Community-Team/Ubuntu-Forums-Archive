---
title: "Cannot SSH to sever"
date: 2007-02-21
forum: General Help
---

### Post by dsims on 2007-02-21
I have been trying to ssh to my server and i keep on getting the error message:

Server resonded "No futher authentication methods Avaliable.".No more authentication methods avaliable.

I reinstalled the ssh openssh-server and reconfigure the port that my school lets us which is 22 and when I went to the sshd_config file I changed the option

PasswordAuthentication no

which at least give me my banner but doesnt let me go any futher than that....  but before I change that option I kept on recieving the message:

"Connection Closed by remote Host" 

I have tried many different things:

reinstall ssh
did the nestat to make sure it was running in the background 
/etc/init.d/sshd restart

Ive been searching for a solution and cannot find one... Can any one help me???

Thanks, 
D

---

### Post by gamerteck on 2007-02-21
Can you post your auth.log?

---

### Post by dsims on 2007-02-21
The last lines of the /auth.log file>> 

Feb 21 07:06:24 localhost vsftpd: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=some ip
Feb 21 07:06:25 localhost vsftpd: (pam_unix) check pass; user unknownFeb 21 07:06:25 localhost vsftpd: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=some ip
Feb 21 07:06:26 localhost vsftpd: (pam_unix) check pass; user unknown
Feb 21 07:06:27 localhost vsftpd: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=some ip
Feb 21 07:06:27 localhost vsftpd: (pam_unix) check pass; user unknown
Feb 21 07:06:27 localhost vsftpd: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=some ip
Feb 21 07:06:28 localhost vsftpd: (pam_unix) check pass; user unknown
Feb 21 07:06:28 localhost vsftpd: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=some ip
Feb 21 07:06:30 localhost vsftpd: (pam_unix) check pass; user unknown
Feb 21 07:06:30 localhost vsftpd: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=some ip
Feb 21 07:06:30 localhost vsftpd: (pam_unix) check pass; user unknown
Feb 21 07:06:30 localhost vsftpd: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=some ip
Feb 21 07:06:31 localhost vsftpd: (pam_unix) check pass; user unknown
Feb 21 07:06:31 localhost vsftpd: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=some ip
Feb 21 07:06:32 localhost vsftpd: (pam_unix) check pass; user unknown

---

### Post by gamerteck on 2007-02-21
The part of the log you posted looks like it's for FTP.  If it was for ssh it would read something like this instead.

=========
Feb 20 15:22:35 Myserver sshd[25556]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=218.188.$
Feb 20 15:22:36 Myserver sshd[25556]: Failed password for invalid user admin from 218.188.21.102 port 60752 ssh2
=========

---

### Post by dsims on 2007-02-21
How about this:

=====
Feb 21 02:53:13 localhost vsftpd: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=some ip
Feb 21 02:53:13 localhost sshd[15405]: fatal: Timeout before authentication for some ip
=====

---

### Post by dsims on 2007-02-21
Also:
=====
Feb 21 08:09:40 localhost vsftpd: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=some ip
Feb 21 08:09:40 localhost sshd[27576]: reverse mapping checking getaddrinfo for graphics-p650-4 failed - POSSIBLE BREAKIN AT$
=====

---

### Post by gamerteck on 2007-02-21
Can you post your **/etc/ssh/sshd_config** file. 

Are you trying to FTP through SSH?

---

### Post by dsims on 2007-02-21
I dont know if im connecting through ftp but i do know im using the port 22...

here is the sshd_config file:

 # Package generated configuration file
# See the sshd(8) manpage for details 
# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0Protocol 2
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
#AuthorizedKeysFile     %h/.ssh/authorized_keys 
# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hostsRhosts
RSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
IgnoreUserKnownHosts no 
# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no 
# Change to yes to enable challenge-response passwords (beware issues with# some PAM modules and threads)
ChallengeResponseAuthentication no 
# Change to no to disable tunnelled clear text passwords
PasswordAuthentication no 
# To change Kerberos options
#KerberosAuthentication no
#KerberosOrLocalPasswd yes
#AFSTokenPassing no
#KerberosTicketCleanup no 
# Kerberos TGT Passing does only work with the AFS kaserver
#KerberosTgtPassing yes 

X11Forwarding yesX11
DisplayOffset 10
PrintMotd no
PrintLastLog yes
KeepAlive yes
#UseLogin no 
#MaxStartups 10:30:60
Banner /etc/issue.net 
# Allow TCP forwarding (for tunneling with SSH)AllowTcpForwarding yes 
# Allow client to pass locale environment variables
AcceptEnv LANG LC_* 

Subsystem sftp /usr/lib/openssh/sftp-server 

UsePAM yes

---

### Post by gamerteck on 2007-02-21
The only thing I noticed in your sshd_config file is that it should be

**TCPKeepAlive Yes**

yours just says

**KeepAlive Yes**

Try changing it to TCP. 

I'm still a little suspicious on the **vsftpd** trying to be accessed.  Did you install and FTP server as well?

Have you tried to use SSH locally, can you connect that way?

---

### Post by dsims on 2007-02-21
I can only log into the server terminal itself... But I cannot ssh into it:

I get the message :

Server responded "No futher authentication methods avaliable.".
No more authentication methods avaliable.

---

### Post by dsims on 2007-02-21
And also the modification to the TCPkill thing and it gave the same error...

---

### Post by llamakc on 2007-02-21
Are you logging in by IP? Do you have a conflcting IP in /etc/hosts?

---

### Post by schilcha on 2007-02-21
your sshd_config says:
```

...
# Change to yes to enable challenge-response passwords (beware issues with# some PAM modules and threads)
ChallengeResponseAuthentication no
# Change to no to disable tunnelled clear text passwords
PasswordAuthentication no 
...

```
try setting either one of these options to yes. Otherwise sshd will not ask you for your pwd.

---

### Post by dsims on 2007-02-21
> **schilcha said:**
> your sshd_config says:
```

...
# Change to yes to enable challenge-response passwords (beware issues with# some PAM modules and threads)
ChallengeResponseAuthentication no
# Change to no to disable tunnelled clear text passwords
PasswordAuthentication no 
...

```
try setting either one of these options to yes. Otherwise sshd will not ask you for your pwd.


I tried and change both of them:

I was successful in loginning in:
ChallengeResponseAuthentication no
PasswordAuthentication yes

-But when i exited the ssh client shell and tried to login again I recieved the same message:

"Connection Closed by remote host"

I then tried the:
ChallengeResponseAuthentication yes
PasswordAuthentication no

and i was successfully logged in but when i exited and logged back in I recieved the "connection closed" again.  But when I tried logging in by continously pressing the ssh transfer button to log in i have a succes rate of 1 out of 8 times... Now i have no personal problem with this result but the users and professors at my university will not find my trick professional...

I also tried the 
ChallengeResponseAuthentication yes
PasswordAuthentication yes
approach and that gave me no success....

Is there any other suggestions???

---

### Post by llamakc on 2007-02-21
What do you mean by the "ssh transfer" button? What piece of software are you using to connect with?

---

### Post by dsims on 2007-02-21
I am using the SSH Secure Shell Version: 2.3... I meant the ssh connect button...

---

### Post by llamakc on 2007-02-21
On what operating system does this software run?  Your original post does not mention that at all.

---

### Post by dsims on 2007-02-21
The ssh secure shell is running on Microsoft Windows XP...

---

### Post by llamakc on 2007-02-21
For the sake of testing, would you download and try connecting through PuTTy?

[http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe)

And let us know if THAT works?

---

### Post by dsims on 2007-02-21
Ran it and got the message:

Server unexpectedly closed connection

---

### Post by llamakc on 2007-02-21
Have you tried removing openssh-server, purging the files, and reinstalling?

---

### Post by dsims on 2007-02-21
I have re-installed many time but have not removed it and reinstalled it or either purged it... 

The commands that I have been using are found by the following:
[http://www.cyberciti.biz/tips/howot-install-ubuntu-linux-ssh-server.html](http://www.cyberciti.biz/tips/howot-install-ubuntu-linux-ssh-server.html)

what is the command to remove all of openssh-server from server and the correct installation process and how do I purge the files?

---

### Post by llamakc on 2007-02-21
Uhm that pages suggests that you change the port to 512. Have you done that?

What part from that page did you do, and what part did you not do? Also, are you running any firewall on that machine?

---

### Post by dsims on 2007-02-21
Yea the school has firewall and only certain ports are avaliable to our department.  I did change the port setting to 512 and it caused an uproar because it only accessable oncampus and not off... So I change it back to Port 22, because it has off site access... But it is failing to work like it used to...

---

### Post by llamakc on 2007-02-22
Any time you are editing the conf files, you ARE restarting the ssh daemon, correct?

sudo /etc/init.d/ssh restart

---

### Post by gamerteck on 2007-02-23
To remove and purge all configuration files for your openssh-server, if that's the package name, it would be as so.

> 
apt-get remove --purge openssh-server


So are you saying they are blocking port 22 at your school?  Might want to talk to one the security admins at the school to find out if this is so?

---

### Post by dsims on 2007-03-08
The solution to this problem was udating the ssh client shell to a better version

---

