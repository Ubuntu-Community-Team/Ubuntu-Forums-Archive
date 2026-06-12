---
title: "ProFTPD acting up."
date: 2008-03-12
forum: General Help
---

### Post by Turel on 2008-03-12
Let me just start by saying that I'm old-new to Linux. Used to use Red Hat many years ago, but have forgotten most of it.

Now, I'm running a forum on an apache2 server.
I'm using ProFTPD, and up until recently I could connect, no problems. But suddenly, whenever I try and access the ftp server (using WinSCP) I get the following error:

"Network error. Software caused the connection to abort."

So I tried to access it through SSH, and that's when I get the following error:

 - IPv4 getaddrinfo 'none' error: Name or service not known
 - warning: unable to determine IP address of 'none'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/etc/proftpd/proftpd.conf'


Any help with this would be greatly appreciated.

---

### Post by Oldsoldier2003 on 2008-03-12
> **Turel said:**
> Let me just start by saying that I'm old-new to Linux. Used to use Red Hat many years ago, but have forgotten most of it.

Now, I'm running a forum on an apache2 server.
I'm using ProFTPD, and up until recently I could connect, no problems. But suddenly, whenever I try and access the ftp server (using WinSCP) I get the following error:

"Network error. Software caused the connection to abort."

So I tried to access it through SSH, and that's when I get the following error:

 - IPv4 getaddrinfo 'none' error: Name or service not known
 - warning: unable to determine IP address of 'none'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/etc/proftpd/proftpd.conf'


Any help with this would be greatly appreciated.
try restarting proftpd if that doesn't solve the issue you might have to look into your configurations

---

### Post by Turel on 2008-03-12
Tried that, I still get the same error.

Here's my proftpd.conf file:

#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
#

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6                         on

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

# Use this to jail all users in their homes
# DefaultRoot                   ~

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
# RequireValidShell             off

# Port 21 is the standard FTP port.
Port                            21

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                  49152 65534

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
# MasqueradeAddress             1.2.3.4

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances                    30

# Set the user and group that the server normally runs at.
User                            proftpd
Group                           nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           022  022
# Normally, we want files to be overwriteable.
AllowOverwrite                  on

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
# PersistentPasswd              off

# Be warned: use of this directive impacts CPU average load!
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
#
# UseSendFile                   off

# Choose a SQL backend among MySQL or PostgreSQL.
# Both modules are loaded in default configuration, so you have to specify the backend
# or comment out the unused module in /etc/proftpd/modules.conf.
# Use 'mysql' or 'postgres' as possible values.
#
#<IfModule mod_sql.c>
# SQLBackend                    mysql
#</IfModule>

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

<IfModule mod_tls.c>
TLSEngine off
</IfModule>

<IfModule mod_quota.c>
QuotaEngine on
</IfModule>

<IfModule mod_ratio.c>
Ratios on
</IfModule>
<IfModule mod_ctrls.c>
ControlsEngine        on
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
AdminControlsEngine on
</IfModule>

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


As previously stated, any help would be greatly appreciated.

---

### Post by Turel on 2008-03-12
*shameless bump*

---

### Post by PinkFloyd102489 on 2008-03-12
Have you altered that config file in any way?

---

### Post by Turel on 2008-03-12
I changed ServerType from "inetd" to "standalone", but nothing else.

---

### Post by itzpapalotl on 2008-03-13
Check your /etc/hosts and /etc/hostname files. You are looking for 'none' in there somewhere. Comment it out and  maybe replace it with 'localhost' without the quotes.

You could post the contents of those two files as well. They should be short.

---

