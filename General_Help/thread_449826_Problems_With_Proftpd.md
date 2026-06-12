---
title: "Problems With Proftpd"
date: 2007-05-20
forum: General Help
---

### Post by mazki516 on 2007-05-20
Hi all,

i'm a new linux ubuntu user(and as you called us "newbie" or "noob" or whatwever)....
any way, what i'm trying to do is actually make my computer into a server step by step...first apache server and php suppurt...etc.
second what i'm trying to do is to start FTP server on my computer, so i downloaded and install proftpd....for some reasons it's doesn't work, when i sudo /etc/init.d/proftpd restart i get this error messege:

user@server1mazki:~$ sudo /etc/init.d/proftpd restart
 * Stopping ftp server proftpd                                           [ OK ] 
 * Starting ftp server proftpd                                      
  - IPv6 getaddrinfo 'server1mazki' error: No address associated with hostname
                                                                                               [ OK ]

and as you can see it's writing "ok" but it's still not working....and when i    sudo ....../proftpd start      i get fail....

if some one know how to fix plz help me.
thank you all!!
mazki..;)

---

### Post by seamuso on 2007-05-20
It may be in your proftpd.conf

Here's a copy of mine .. you can see some of the options. You can probably disable the ipv6 support. I had a few issues getting proftpd running smoothly when I installed it (slow connections, slow transfers) that the settings I use have cleaned up.

```

#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6				off
UseReverseDNS                   off
IdentLookups                    off


ServerName			"BlueBuntu"
ServerType			standalone
DeferWelcome			off
TimesGMT			off
MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			on

TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                	"-l"

DenyFilter			\*.*/

# Use this to jail all users in their homes 
 DefaultRoot			~/public_html/ftp_root

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
# RequireValidShells		off

# Port 21 is the standard FTP port.
Port				21

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
PassivePorts                  49152 65534

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
# MasqueradeAddress		1.2.3.4

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			30

# Set the user and group that the server normally runs at.
User				proftpd
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
AllowOverwrite			on

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
# PersistentPasswd		off

# Be warned: use of this directive impacts CPU average load!
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
#
# UseSendFile			off

# Choose a SQL backend among MySQL or PostgreSQL.
# Both modules are loaded in default configuration, so you have to specify the backend 
# or comment out the unused module in /etc/proftpd/modules.conf.
# Use 'mysql' or 'postgres' as possible values.
#
#<IfModule mod_sql.c>
# SQLBackend			mysql
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


# Delay engine reduces impact of the so-called Timing Attack described in
# http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02
# It is on by default. 
<IfModule mod_delay.c>
DelayEngine on
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

 <Anonymous ~ftp>
   User				ftp
   Group				nogroup
   # We want clients to be able to login with "anonymous" as well as "ftp"
   UserAlias			anonymous ftp
   # Cosmetic changes, all files belongs to ftp user
   DirFakeUser	on ftp
   DirFakeGroup on ftp
 
   RequireValidShell		off
 
   # Limit the maximum number of anonymous logins
   MaxClients			10
 
   # We want 'welcome.msg' displayed at login, and '.message' displayed
   # in each newly chdired directory.
   DisplayLogin			welcome.msg
   DisplayFirstChdir		.message
 
   # Limit WRITE everywhere in the anonymous chroot
   <Directory *>
     <Limit WRITE>
       DenyAll
     </Limit>
   </Directory>
</Anonymous>

```

---

### Post by mazki516 on 2007-05-20
WOW!! this is really not funny!! look at my proftpd.conf

#
# Includes required DSO modules. This is mandatory in proftpd 1.3
#
Include	/etc/proftpd/modules.conf

<Global>
</Global>
Group ftpserver
ServerName Home1
DefaultServer on

---

### Post by mazki516 on 2007-05-20
i've copied your proftp.conf, to my proftpd.cond, change the hostname of course, and now it's says "ok"...any way, but i cant log in :( i've opend a user! force him to go only to the home directory....but i just can't connect to the server via another computer(and not from my computer as well)...

---

### Post by edlentz on 2007-06-26
I am having a problem with FTP ing.   My software manager says that ProFTP is installed, my services says it is running.  I am having a problem with consistantly FTPing thru a firewall specifically M0n0wall.  I suspect that the passive ports setting is amiss in ProFTP.  I have tried to  find the proftpd.conf file to change it like the example above but I can't find it.  I am running Ubuntu 6.06LTS  Can someone give me an idea where to look?  This is driving me crazy!


Thanks

---

