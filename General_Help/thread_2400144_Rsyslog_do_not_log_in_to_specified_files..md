---
title: "Rsyslog do not log in to specified files."
date: 2018-09-03
forum: General Help
---

### Post by smithbox on 2018-09-03
Hi everybody.
My data:
```
# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.4 LTS
Release:    16.04
Codename:    xenial
# uname -r
4.15.0-33-generic
# rsyslogd -version
rsyslogd 8.16.0, compiled with:
    PLATFORM:                x86_64-pc-linux-gnu
    PLATFORM (lsb_release -d):        
    FEATURE_REGEXP:                Yes
    GSSAPI Kerberos 5 support:        Yes
    FEATURE_DEBUG (debug build, slow code):    No
    32bit Atomic operations supported:    Yes
    64bit Atomic operations supported:    Yes
    memory allocator:            system default
    Runtime Instrumentation (slow code):    No
    uuid support:                Yes
    Number of Bits in RainerScript integers: 64

See http://www.rsyslog.com for more information.
# ps -A | grep rsyslog
18328 ?        00:00:00 rsyslogd
root@robin-desktop:~# rsyslogd -N1
rsyslogd: version 8.16.0, config validation run (level 1), master config /etc/rsyslog.conf
rsyslogd: command 'KLogPermitNonKernelFacility' is currently not permitted - did you already set it via a RainerScript command (v6+ config)? [v8.16.0 try http://www.rsyslog.com/e/2222 ]
rsyslogd: error during parsing file /etc/rsyslog.d/tcpconnections.conf, on or before line 2: warnings occured in file '/etc/rsyslog.d/tcpconnections.conf' around line 2 [v8.16.0 try http://www.rsyslog.com/e/2207 ]
```
Briefly, I spent 2 days tray to redirect used in iptables rules 2 prefixes:
```
 ctstate INVALID,NEW LOG level warning prefix "indrop"
ctstate INVALID,NEW LOG level warning prefix "outdrop"
```
My rsyslog configuration file:
```

#  /etc/rsyslog.conf    Configuration file for rsyslog.
#
#            For more information see
#            /usr/share/doc/rsyslog-doc/html/rsyslog_conf.html
#
#  Default logging rules can be found in /etc/rsyslog.d/50-default.conf


#################
#### MODULES ####
#################

module(load="imuxsock") # provides support for local system logging
module(load="imklog")   # provides kernel logging support
module(load="immark")  # provides --MARK-- message capability

#provides UDP syslog reception
module(load="imudp")
input(type="imudp" port="514")

# provides TCP syslog reception
module(load="imtcp")
input(type="imtcp" port="514")

# Enable non-kernel facility klog messages
$KLogPermitNonKernelFacility on

###########################
#### GLOBAL DIRECTIVES ####
###########################
# Use traditional timestamp format.
# To enable high precision timestamps, comment out the following line.
#
$ActionFileDefaultTemplate RSYSLOG_TraditionalFileFormat

# Filter duplicated messages
$RepeatedMsgReduction on

#
# Set the default permissions for all log files.
#
$FileOwner syslog
$FileGroup adm
$FileCreateMode 0640
$DirCreateMode 0755
$Umask 0022
$PrivDropToUser syslog
$PrivDropToGroup syslog

#
# Where to place spool and state files
#
$WorkDirectory /var/spool/rsyslog

#
# Include all config files in /etc/rsyslog.d/
#
$IncludeConfig /etc/rsyslog.d/*.conf
#
```
My edited rsyslog default.conf file:
```
#  Default rules for rsyslog.
#
#            For more information see rsyslog.conf(5) and /etc/rsyslog.conf

#
# First some standard log files.  Log by facility.
#
if $msg contains 'indrop' then -/var/log/indrop.log
& stop
#
if $msg contains 'outdrop' then -/var/log/outdrop.log
& stop
#
auth,authpriv.*            /var/log/auth.log
*.*;auth,authpriv.none        -/var/log/syslog
#cron.*                /var/log/cron.log
#daemon.*            -/var/log/daemon.log
kern.*                -/var/log/messages
#iptables log 
kern.debug                      -/var/log/iptables.log
#lpr.*                -/var/log/lpr.log
mail.*                -/var/log/mail.log
#user.*                -/var/log/user.log

#
# Logging for the mail system.  Split it up so that
# it is easy to write scripts to parse these files.
#
#mail.info            -/var/log/mail.info
#mail.warn            -/var/log/mail.warn
mail.err            /var/log/mail.err

#
# Logging for INN news system.
#
news.crit            /var/log/news/news.crit
news.err            /var/log/news/news.err
news.notice            -/var/log/news/news.notice

#
# Some "catch-all" log files.
#
#*.=debug;\
#    auth,authpriv.none;\
#    news.none;mail.none    -/var/log/debug
#*.=info;*.=notice;*.=warn;\
#    auth,authpriv.none;\
#    cron,daemon.none;\
#    mail,news.none        -/var/log/messages

#
# Emergencies are sent to everybody logged in.
#
*.emerg                                :omusrmsg:*

#
# I like to have messages displayed on the console, but only on a virtual
# console I usually leave idle.
#
#daemon,mail.*;\
#    news.=crit;news.=err;news.=notice;\
#    *.=debug;*.=info;\
#    *.=notice;*.=warn    /dev/tty8

# The named pipe /dev/xconsole is for the `xconsole' utility.  To use it,
# you must invoke `xconsole' with the `-file' option:
# 
#    $ xconsole -file /dev/xconsole [...]
#
# NOTE: adjust the list below, or you'll go crazy if you have a reasonably
#      busy site..
#
daemon.*;mail.*;\
    news.err;\
    *.=debug;*.=info;\
    *.=notice;*.=warn    |/dev/xconsole
```
I lost 2 days time and stress, please ---- help ):P

---

### Post by smithbox on 2018-09-03
Hi everybody.
My data:
```
# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.4 LTS
Release:    16.04
Codename:    xenial
# uname -r
4.15.0-33-generic
# rsyslogd -version
rsyslogd 8.16.0, compiled with:
    PLATFORM:                x86_64-pc-linux-gnu
    PLATFORM (lsb_release -d):        
    FEATURE_REGEXP:                Yes
    GSSAPI Kerberos 5 support:        Yes
    FEATURE_DEBUG (debug build, slow code):    No
    32bit Atomic operations supported:    Yes
    64bit Atomic operations supported:    Yes
    memory allocator:            system default
    Runtime Instrumentation (slow code):    No
    uuid support:                Yes
    Number of Bits in RainerScript integers: 64

See http://www.rsyslog.com for more information.
# ps -A | grep rsyslog
18328 ?        00:00:00 rsyslogd
root@robin-desktop:~# rsyslogd -N1
rsyslogd: version 8.16.0, config validation run (level 1), master config /etc/rsyslog.conf
rsyslogd: command 'KLogPermitNonKernelFacility' is currently not permitted - did you already set it via a RainerScript command (v6+ config)? [v8.16.0 try http://www.rsyslog.com/e/2222 ]
rsyslogd: error during parsing file /etc/rsyslog.d/tcpconnections.conf, on or before line 2: warnings occured in file '/etc/rsyslog.d/tcpconnections.conf' around line 2 [v8.16.0 try http://www.rsyslog.com/e/2207 ]
```
Briefly, I spent 2 days tray to redirect used in iptables rules 2 prefixes:
```
 ctstate INVALID,NEW LOG level warning prefix "indrop"
ctstate INVALID,NEW LOG level warning prefix "outdrop"
```
My rsyslog configuration file:
```

#  /etc/rsyslog.conf    Configuration file for rsyslog.
#
#            For more information see
#            /usr/share/doc/rsyslog-doc/html/rsyslog_conf.html
#
#  Default logging rules can be found in /etc/rsyslog.d/50-default.conf


#################
#### MODULES ####
#################

module(load="imuxsock") # provides support for local system logging
module(load="imklog")   # provides kernel logging support
module(load="immark")  # provides --MARK-- message capability

#provides UDP syslog reception
module(load="imudp")
input(type="imudp" port="514")

# provides TCP syslog reception
module(load="imtcp")
input(type="imtcp" port="514")

# Enable non-kernel facility klog messages
$KLogPermitNonKernelFacility on

###########################
#### GLOBAL DIRECTIVES ####
###########################
# Use traditional timestamp format.
# To enable high precision timestamps, comment out the following line.
#
$ActionFileDefaultTemplate RSYSLOG_TraditionalFileFormat

# Filter duplicated messages
$RepeatedMsgReduction on

#
# Set the default permissions for all log files.
#
$FileOwner syslog
$FileGroup adm
$FileCreateMode 0640
$DirCreateMode 0755
$Umask 0022
$PrivDropToUser syslog
$PrivDropToGroup syslog

#
# Where to place spool and state files
#
$WorkDirectory /var/spool/rsyslog

#
# Include all config files in /etc/rsyslog.d/
#
$IncludeConfig /etc/rsyslog.d/*.conf
#
```
My edited rsyslog default.conf file:
```
#  Default rules for rsyslog.
#
#            For more information see rsyslog.conf(5) and /etc/rsyslog.conf

#
# First some standard log files.  Log by facility.
#
if $msg contains 'indrop' then -/var/log/indrop.log
& stop
#
if $msg contains 'outdrop' then -/var/log/outdrop.log
& stop
#
auth,authpriv.*            /var/log/auth.log
*.*;auth,authpriv.none        -/var/log/syslog
#cron.*                /var/log/cron.log
#daemon.*            -/var/log/daemon.log
kern.*                -/var/log/messages
#iptables log 
kern.debug                      -/var/log/iptables.log
#lpr.*                -/var/log/lpr.log
mail.*                -/var/log/mail.log
#user.*                -/var/log/user.log

#
# Logging for the mail system.  Split it up so that
# it is easy to write scripts to parse these files.
#
#mail.info            -/var/log/mail.info
#mail.warn            -/var/log/mail.warn
mail.err            /var/log/mail.err

#
# Logging for INN news system.
#
news.crit            /var/log/news/news.crit
news.err            /var/log/news/news.err
news.notice            -/var/log/news/news.notice

#
# Some "catch-all" log files.
#
#*.=debug;\
#    auth,authpriv.none;\
#    news.none;mail.none    -/var/log/debug
#*.=info;*.=notice;*.=warn;\
#    auth,authpriv.none;\
#    cron,daemon.none;\
#    mail,news.none        -/var/log/messages

#
# Emergencies are sent to everybody logged in.
#
*.emerg                                :omusrmsg:*

#
# I like to have messages displayed on the console, but only on a virtual
# console I usually leave idle.
#
#daemon,mail.*;\
#    news.=crit;news.=err;news.=notice;\
#    *.=debug;*.=info;\
#    *.=notice;*.=warn    /dev/tty8

# The named pipe /dev/xconsole is for the `xconsole' utility.  To use it,
# you must invoke `xconsole' with the `-file' option:
# 
#    $ xconsole -file /dev/xconsole [...]
#
# NOTE: adjust the list below, or you'll go crazy if you have a reasonably
#      busy site..
#
daemon.*;mail.*;\
    news.err;\
    *.=debug;*.=info;\
    *.=notice;*.=warn    |/dev/xconsole
```
In spite of all my efforts, log files are still empty.
[https://imgur.com/a/s2gRvtu](https://imgur.com/a/s2gRvtu)
I lost 2 days time and stress, please ---- help ):P

---

### Post by wildmanne39 on 2018-09-03
Hello, I moved both of your threads into this one and put it in General help because you posted it in the Resolution Centre, the only threads that belong in the Resolution Centre are on topics of the following.
> This is the place to contact a forum admin concerning problems with your forum account, to appeal moderator action, to request a thread be moved from the jail, or to file a complaint about forum harrassment or abuse. 

Please do not create more then one thread on the same issue it is confusing and dilutes community effort.

---

