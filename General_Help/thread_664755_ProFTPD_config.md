---
title: "ProFTPD config"
date: 2008-01-11
forum: General Help
---

### Post by Bailey321 on 2008-01-11
I setup with np using this guide [http://ubuntuforums.org/showthread.php?t=51611](http://ubuntuforums.org/showthread.php?t=51611)

I think need some help to no if my config file is setup correctly. What ive done is set it up to enable fxp  via google. 

The options i had to add were...

1/  <Global>
      AllowForeignAddress on
     </Global>

2/ PassivePorts 49152 65534

3/ Masqueradeaddress  <my_ip> (blanked out my ip)

Thing is the fxp keeps stallin between transfers, Im pretty sure its something to do with my config file or rather the way i setup the conf, not sure. Normal FTP is fine and doesnt stall. Would someone take a look at my proftpd.conf and let me no i have them two options in the correct position or suggest to me what the prob maybe....:)

my proftpd.conf

```

#
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
#

ServerName                      "Debian"
ServerType                      standalone

<Global>
AllowForeignAddress     on
</Global>

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
#Quotas 

# Uncomment this if you would use ratio module:
#Ratios                         on

# Port 21 is the standard FTP port.
Port                            2341
PassivePorts                    49152 65534
masqueradeaddress              <my_ip>

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances                    30

# Set the user and group that the server normally runs at.
User                             nobody
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
#
# </Anonymous>
```

---

