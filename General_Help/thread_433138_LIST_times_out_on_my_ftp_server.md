---
title: "LIST times out on my ftp server"
date: 2007-05-04
forum: General Help
---

### Post by tlacuache on 2007-05-04
I've been trying to set up an FTP server using proftpd. I've followed several of the posts here and got my proftpd.conf file set up the way I want respecting users, access rules, etc. I can log into the server when I'm on "localhost" and it works perfectly, just the way it should.

However, when I try to log into it from another computer whether inside my home network or externally (I've got my DSL router set to forward the port I've chosen for FTP to this particular machine) I have a problem.

The FTP client connects to the server, gets the welcome message, and does authentication correctly. But it is not able to list the files (hostname and port hidden for your viewing pleasure):

```

Status:	Connecting to *************:**** ...
Status:	Connected with *************:****. Waiting for welcome message...
Response:	220 These aren't the droids you're looking for
Command:	USER *******
Response:	331 Password required for ********
Command:	PASS ********
Response:	230 Welcome!
Command:	SYST
Response:	215 UNIX Type: L8
Command:	FEAT
Response:	211-Features:
Response:	 MDTM
Response:	 REST STREAM
Response:	 SIZE
Response:	211 End
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/ftp" is current directory.
Command:	TYPE A
Response:	200 Type set to A
Command:	PASV
Response:	227 Entering Passive Mode (192,168,0,2,129,228).
Command:	LIST
Error:	Timeout detected!
Error:	Could not retrieve directory listing
```

That's what happens when filezilla is set to use "passive mode." 192.168.0.2, by the way, is the IP address of the machine with the FTP server on my internal home network.

If I try to use active mode, this is what happens:

```

Status:	Connecting to *************:**** ...
Status:	Connected with *************:****. Waiting for welcome message...
Response:	220 These aren't the droids you're looking for
Command:	USER family
Response:	331 Password required for ********
Command:	PASS ********
Response:	230 Welcome!
Command:	SYST
Response:	215 UNIX Type: L8
Command:	FEAT
Response:	211-Features:
Response:	 MDTM
Response:	 REST STREAM
Response:	 SIZE
Response:	211 End
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/ftp" is current directory.
Command:	TYPE A
Response:	200 Type set to A
Command:	PORT 10,0,0,69,208,71
Response:	500 Illegal PORT command
Error:	Could not retrieve directory listing

```

I don't really know enough about proftpd (or FTP in general, for that matter) to know what I'm doing wrong. Any ideas? 

Here's my conf file for proftpd. 

```

# To really apply changes reload proftpd after modifications.

UserAlias friends userftp

ServerName			"GroverFTP"
ServerType 			standalone
DeferWelcome			on

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin                    60

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so don't use it for security reasons (choose here the port you want)
Port				2819

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 shared

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "Welcome!"
# This message is displayed for each access good or not
ServerIdent on "These aren't the droids you're looking for"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/shared

# Lock all the users in home directory, ***** really important *****
# DefaultRoot ~

MaxLoginAttempts    10

#VALID LOGINS
<Limit LOGIN>
  AllowUser userftp
  DenyAll
</Limit>

<Directory /home/shared>
  <Limit WRITE>
    DenyAll
  </Limit>
  <Limit DELE>
    DenyAll
  </Limit>
</Directory>
```

---

