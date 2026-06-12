---
title: "ProFTP Problem..."
date: 2006-07-30
forum: General Help
---

### Post by Jivicin on 2006-07-30
I've been using ProFTP on my server for awhile now, and following the HOWTO on the [unofficial starter guide]("http://ubuntuguide.org/wiki/Dapper") worked flawlessly (aside from setting it up with xinetd).

My latest and greates problem is I want to use it outside my local network (which means moving it off ot port 21 since my ISP has it blocked).  So I edited the /etc/proftpd.conf file, changed the port from 21 to 9997, and restarted xinetd.  No change.  An nmap of my server showed that it was still on 21.  So I tried adding an entry to the my /etc/xinetd.d/ftp file.  Something like this:
```
service ftp
{
        socket_type     = stream
        protocol        = tcp
        wait            = no
        user            = root
        server          = /usr/sbin/proftpd
        flags           = REUSE
        instances       = 50
        port            = 9997
}
```

Still no change.  So I moved the ftp file out of /etc/xinetd.d temporarily, and setup ProFTP as a standalone.  This time when I restarted xinetd and ProFTP, I could at least connect on port 9997.

Now, when I'm using the server and I ftp to itself on 9997, it works without incident.  When I use another computer on my network and try to ftp to it I can successfully login, but when I try to "dir" or "ls" I get:
```
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> dir
200 PORT command successful
```
Then it hangs indefinetly.  Any thoughts?

My /etc/proftpd.conf file:

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
Port                            9997

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances                    30

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

# <Anonymous ~ftp>
#   User                                ftp
#   Group                               nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias                   anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser on ftp
#   DirFakeGroup on ftp
#
#   RequireValidShell           off
#
#   # Limit the maximum number of anonymous logins
#   MaxClients                  10
#
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin                        welcome.msg
#   DisplayFirstChdir           .message
#
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory *>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
#
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask                           022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
#
# </Anonymous>

# These ports should be safe...
PassivePorts 60000 65535

UseReverseDNS off
IdentLookups off

```

---

### Post by Jivicin on 2006-07-31
Bump... Anyone?

---

### Post by pygmaelion on 2006-07-31
So, when you say that things are working fine, but when you do a dir or an ls, it hangs indefinitely... 

Does working fine include logging in? Does it also include the transfer of files?

If you're only logging in, and every command that involves data (dir/ls/get/put) fails, then you may be running into problems establishing the data connection. So, putting the command port at 9997 is great for the initial connection in place of 21, but data takes place on another port. 

Try browsing through this page, it usually sorts me out when I get confused about ftp.

[http://www.ncftp.com/ncftpd/doc/misc/ftp_and_firewalls.html](http://www.ncftp.com/ncftpd/doc/misc/ftp_and_firewalls.html)

I hope this helps, maybe defined data ports will get you rolling.

---

### Post by cstudent on 2006-07-31
There is a gui frontend called gproftpd in the repositories. Makes things much easier IMHO.

---

### Post by Jivicin on 2006-07-31
Thanks guys.  Passive ports ended up doing the trick, I just didn't have them open on my router.

---

