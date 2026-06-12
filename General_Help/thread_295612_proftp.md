---
title: "proftp"
date: 2006-11-08
forum: General Help
---

### Post by StreetSmart on 2006-11-08
adam@Mars:/home$ sudo /etc/init.d/proftpd restart
 * Stopping ftp server proftpd                                           [ok]
 * Starting ftp server proftpd  - IPv6 getaddrinfo 'localhost' error: Name or service not known

adam@Mars:/home$ cat /etc/hosts
127.0.0.1 localhost Mars
127.0.1.1 Mars

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback Mars
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

How do i fix this error?

---

### Post by taurus on 2006-11-08
First, need to stop proftpd

```
sudo /etc/init.d/proftpd stop
```
Then, edit your /etc/hosts and remove or put a # sign in front of "127.0.1.1 Mars".

```
nano -w /etc/hosts
```
Then, restart proftpd again and see if there is still a problem.  Otherwise, you can always install gproftpd to configure it since it's a GUI of proftpd.conf!

---

### Post by StreetSmart on 2006-11-08
adam@Mars:~$ cat /etc/hosts
127.0.0.1 localhost Mars
#127.0.1.1 Mars

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback Mars
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Still gives me the same error. I dont want to install gproftp. Im trying to avoid that. Any other suggestions

---

### Post by taurus on 2006-11-08
> **StreetSmart said:**
> adam@Mars:~$ cat /etc/hosts
127.0.0.1 localhost Mars
#127.0.1.1 Mars

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback Mars
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Still gives me the same error. I dont want to install gproftp. Im trying to avoid that. Any other suggestions
Remove "Mars" from "::1 ip6-localhost ip6-loopback Mars" then!!!
Stop and start proftpd again.

---

### Post by StreetSmart on 2006-11-08
I removed "Mars" from "::1 ip6-localhost ip6-loopback Mars"  and I still recieve the same error.

---

### Post by taurus on 2006-11-08
Okay, here is my /etc/hosts so you can see how it is on my Edgy...

```

127.0.0.1       localhost
127.0.1.1       Taurus.com   Taurus

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by StreetSmart on 2006-11-08
I've been trying various methods to get proftpd to work. But it doesnt seem to want to work. :( Any other suggestions?

---

### Post by taurus on 2006-11-08
Maybe you can now try vsftpd!!!

---

### Post by StreetSmart on 2006-11-08
Im sure this has got to be an easy fix. I just havent found any solutions using google. Time to try IRC maybe.

---

### Post by dannyboy79 on 2006-11-08
> **StreetSmart said:**
> Im sure this has got to be an easy fix. I just havent found any solutions using google. Time to try IRC maybe.

I get the wsame error:
- IPv6 getaddrinfo 'localhost' error: Name or service not known

and my server runs great. Just ignore it. If your server isn't working it's because of something else. Also, keep in mind that the newest proftpd from the repos doesn't have mod_tls compilled in so if you want to connect to your server with your password encrypted it's a no go, you'll have to compile it yourself. This  has been submitted to the dev's.

this was the guide I used and it got me going instantly:
[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

---

### Post by StreetSmart on 2006-11-08
Nobody can connect to the FTP tho. It refuses the connection

---

### Post by dannyboy79 on 2006-11-08
ok, well, you have another issue then because I am connected to mine as we speak. have you port forwarded ports 21 and 22 to your server's ip if you have a router that has a built-in firewall? did you enable any rules within iptables by either using firestarter or just by editing iptables? did you follow that guide I posted step by step??? those are the qwuestions you need to answer in order to find you issue.

---

### Post by StreetSmart on 2006-11-08
Ill tell you exactly what happened. I followed the tutorial step by step and it worked. my friend uploaded a movie to me. then i restarted my computer and it didnt work anymore. im trying to connect threw lan. so no router ports need to be forwarded.

---

### Post by dannyboy79 on 2006-11-08
is it running??? have you tried, sudo /etc/init.d/proftpd restart?

OOPS, dumb question. sorry. let me thing

---

### Post by dannyboy79 on 2006-11-08
when you type in ps aux, do you see a line like this anywhere?

nobody   16971  0.0  0.2   3000  1088 ?        Ss   12:05   0:00 proftpd: (accepting connections)

I run my server thru ineted or whatever, NOT as a standalone. I don't have a lot of connections so I chose to use inited. what client are you using. Filezilla is what I use from winbloz, it's free to.

---

### Post by taurus on 2006-11-08
And if you want, post your proftpd.conf and maybe somebody will spot something in there!!!

---

### Post by StreetSmart on 2006-11-08
```
#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf

ServerName			"Adam's FTP Server"
ServerType			standalone
DeferWelcome			on

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

#DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so don't use it for security reasons (choose here the port you want)
Port				1980

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/FTP-shared

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>

```

adam@Mars:~$ ps aux | grep proftp
nobody    4878  0.0  0.0   8732  1608 ?        Ss   15:48   0:00 proftpd: (accepting connections)

I remember making proftpd as a standalone in the setup. Do you think that might be the problem?

---

### Post by dannyboy79 on 2006-11-09
well you couldn't have followed the guide EXACTLY because you're missing many things that I can't really say if they matter or not but maybe just to try to make the troubleshooting easier you should make your's more like the guide. Here is mine, i use an alias to login and I noticed you don't.

# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on
# Choose here the user alias you want !!!!
UserAlias daniel ftp
ServerName "UBUNTU FTP Server"
ServerType                      inited
DeferWelcome                    on
MultilineRFC2228 on
DefaultServer                   on
ShowSymlinks                    off
TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 600
DisplayFirstChdir               .message
ListOptions                     "-l"
RequireValidShell               off
TimeoutLogin 20
RootLogin                       off
# It's better for debug to create log files ;-)
ExtendedLog                     /var/log/ftp.log
TransferLog                     /var/log/xferlog
SystemLog               /var/log/syslog.log
#DenyFilter                     \*.*/
# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off
# Allow to restart a download
AllowStoreRestart on
Port                            21
# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8
# Set the user and group that the server normally runs at.
User nobody
Group nogroup
# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           022     022
PersistentPasswd                off
MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8
# Display a message after a successful login
AccessGrantMsg "YOU MADE IT!"
# This message is displayed for each access good or not
ServerIdent on "you're at home"
# Set /home/ftp directory as home directory
DefaultRoot /home/ftp
# Lock all the users in home directory, ***** really important *****
#DefaultRoot ~
MaxLoginAttempts 5
UseReverseDNS                   off
IdentLookups                    off
#VALID LOGINS
<Limit LOGIN>
AllowUser ftp
DenyALL
</Limit>
<Directory /home/ftp>
Umask 022 022
AllowOverwrite off
        <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>
<Directory /home/ftp/download/*>
Umask 022 022
AllowOverwrite off
        <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>
<Directory> /home/ftp/upload/>
Umask 022 022
AllowOverwrite on
        <Limit READ DELE>
        DenyAll
        </Limit>
        <Limit STOR RMD RNFR RNTO CWD MKD>
        AllowAll
        </Limit>
</Directory>
#added for encrypting all transfers thru ssh and ssl
<IfModule mod_tls.c>
TLSEngine on
TLSLog Log /var/ftpd/tls.log
TLSProtocol TLSv1
    # Are clients required to use FTP over TLS when talking to this ser
TLSRequired off
    # Server's certificate
TLSRSACertificateFile /etc/ftpcert/server.crt
    TLSRSACertificateKeyFile /etc/ftpcert/server.key
    # CA the server trusts
    TLSCACertificateFile /etc/ftpcert/ca.crt
    # Authenticate clients that want to use FTP over TLS?
TLSVerifyClient on
</IfModule>

and you're sure you don't have any rules in iptables? also, what client are you trying it with. also, what is the exact error message?? i have saw around that there is some error I think like 531? you can most likely gogle the error numnber and you should find the answer.

---

