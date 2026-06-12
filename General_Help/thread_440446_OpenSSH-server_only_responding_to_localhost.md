---
title: "OpenSSH-server only responding to localhost"
date: 2007-05-11
forum: General Help
---

### Post by tph on 2007-05-11
I want to be able to log on my computer from anywhere else, and I've had experience with ssh before.
I installed openssh-server, changed the port I want the server to run on, and everything looked fine. I could log in at localhost.
Then I tried to log in through my internet ip, but it didn't respond. so I had to shut ssh down with ctrl+c.
I have forwarded all the needed ports, so I don't see what's wrong.

sudo nmap -sS -p *** localhost
gives ***/tcp open  unknown

while sudo nmap -sS -p *** ***.***.***.***
gives ***/tcp filtered unknown

Also, here's my /etc/ssh/sshd_config:
```
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port ***
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
#AuthorizedKeysFile     %h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 913
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

Does anyone have an idea why I can't log in externally?

---

### Post by baka_rob on 2007-05-11
What does "netstat -ant | grep LISTEN" show (when sshd is running)?

If sshd is binding to 127.0.0.1 you may want to uncomment some of these lines in the config you pasted above:

#ListenAddress 0.0.0.0

0.0.0.0 will accept connections on all available interfaces (local, LAN, or otherwise).

If netstat -ant already shows it is listening on 0.0.0.0, you may want to check firewalls and, if local firewalls are configured to let traffic to/from the port through, you may want to call your ISP/upstream provider and see if there is some filtering being done there on that port.

---

### Post by carlosqueso on 2007-05-11
are you behind a router?

---

### Post by tph on 2007-05-11
I have forwarded the proper port on my router.
netstat -ant | grep LISTEN didn't list the port I'm running ssh on on 0.0.0.0 (it did list it though) before I un-commented the line, now it does, but I don't see any other differences.
It is strange, because when I try to connect to any other port I get the message that the port is closed, but on the ports I have forwarded its just quiet.

I haven't installed any soft firewalls.

---

### Post by baka_rob on 2007-05-11
Now that it is listening on 0.0.0.0 on your specified port, you still are unable to connect to it via your internet-facing IP?  Is there a local network you can use to try to connect over LAN, or is it just the one machine?  Can you ssh to the LAN IP you configured your router to send traffic on that port to?

---

### Post by tph on 2007-05-11
I'm still unable to connect through my internet IP, yes.
I'll try to connect to my pc with another pc in my LAN tomorrow.

---

### Post by Dr Small on 2007-05-11
> **tph said:**
> I'm still unable to connect through my internet IP, yes.
I'll try to connect to my pc with another pc in my LAN tomorrow.
Apparently you are behind a router.
You must access your router and set the settings to forward port 22 to your IP Address.

---

### Post by tph on 2007-05-11
I have written at least once that I have forwarded the port I'm running SSH on.
I also see that I have forwarded the port because on other ports I get connection refused, while on the port I'm running ssh on it's just not doing anything.

I will try to connect through another pc on my LAN tomorrow.

---

### Post by tph on 2007-05-12
Sorry for bumping, but I tried to connect through another pc in my lan (using the port and ip which I have forwarded), and it worked.
I tried to coonnect through my internet ip once more and capture what happend with wireshark.
It seemed that my computer simply wouldn't respond (all the packets sent were from a random port sending to my ssh-port).

---

### Post by baka_rob on 2007-05-12
Hmmm, so traffic makes it from the router and the lan (to the same port on the same host), but only the lan connection will let you log in?!

Does anything show up in /var/log/auth.log when you try to log in via the internet-facing IP?  If not, maybe increasing the log verbosity will help:

Change this section slightly:
# Logging
SyslogFacility AUTH
LogLevel INFO

To:
# Logging
SyslogFacility AUTH
LogLevel DEBUG

And then reload the configuration with:

root@shellprompt# /etc/init.d/ssh reload

It should tell sshd to send log messages to /var/log/auth.log (which it is already configured to do), but instead of creating ~5 lines, it will create 55 lines per login/logout test (at least from my brief testing).

I'm wondering if there are errors / warnings that show up from sshd in that log, or if something is wrong at some other level.

You could use cat /var/log/auth.log | grep 'sshd\['; to get all of the sshd entries in the file.  Or you could use the gui syslog viewer (I think) to look for such things.

If you do this test, you can revert back to LogLevel INFO and reload the daemon again the same way once you are done, to keep the log smaller :p

---

### Post by Subban on 2007-05-12
Just a quickie, are you trying to connect via the internet IP from your own network ?

If so as far as I am aware routers don't like that kind of thing and it won't work, forwarded or not. They don't like you looping out and back on themselves via the internet IP. You need to test via another outside machine

---

### Post by firdooze on 2007-05-12
does your ISP allows for static ip?

if not then you either have to get a static ip from your ISP or from sites like dydns,com or no-ip.com

---

### Post by tph on 2007-05-12
It seems that it is my router yes. I have a shell account at a friend's pc, and I tried to shell my way to me through ssh to him, and it worked.

Thanks for all the help, it was just my router after all.

---

