---
title: "FTP configuration issues..."
date: 2006-08-02
forum: General Help
---

### Post by cleverselfreferentialname on 2006-08-02
All right, I'm trying to only allow the user 'music' to FTP into my machine, so I can access my music while I am abroad. I don't want to worry about people accessing my account or others. I get error 421, however, when trying to list the directory after logging in with this config:

```
#
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
#

ServerName                      "Debian"
ServerType                      standalone
DeferWelcome                    off

MultilineRFC2228                on
DefaultServer                   on
ShowSymlinks                    on

TimeoutNoTransfer               600
TimeoutStalled                  600
TimeoutIdle                     1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                     "-l"

DenyFilter                      \*.*/

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
#PersistentPasswd               off

# Uncomment this if you would use TLS module:
#TLSEngine                      on

# Uncomment this if you would use quota module:
#Quotas                         on

# Uncomment this if you would use ratio module:
#Ratios                         on

# Port 21 is the standard FTP port.
Port                            21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances                    15

<limit LOGIN>
DenyAll
AllowGroup                      ftpusers
</limit>

# Set the user and group that the server normally runs at.
User                            nobody
Group                           nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           022  022
# Normally, we want files to be overwriteable.
AllowOverwrite                  on

# Delay engine reduces impact of the so-called Timing Attack described in
# http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02
# It is on by default.
#DelayEngine                    off

# A basic anonymous configuration, no upload directories.


```

From the shell:

```
230 User music logged in.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
200 PORT command successful
421 Service not available, remote server has closed connection
```

---

### Post by philippe_carlo on 2006-08-02
Why don't you use SSH/SFTP? It is much more secure and less of a hassle.

---

### Post by cleverselfreferentialname on 2006-08-02
My mistake. I just had to reverse that one section to look like this:

```

<limit LOGIN>
DenyAll
AllowGroup                      ftpusers
</limit>
```

---

