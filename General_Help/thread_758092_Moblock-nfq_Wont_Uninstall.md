---
title: "Moblock-nfq Wont Uninstall"
date: 2008-04-17
forum: General Help
---

### Post by rocker9455 on 2008-04-17
hi i have messed up again using moblock i accidentally tried to install moblock-nfq (being curious because i wasnt sure what it was) i already had moblock and mobloquer installed and this messed everything up and i have uninstalled moblock and mobloquer but when ever i try to do anything involving packages (eg sudo aptitude apt-get etc) it wont work saying there are conflicts because of moblock-nfq and i just want to get rid of it and get moblock and mobloquer back!

heres the error:
```
will@will-desktop:~$ sudo aptitude remove moblock-nfq -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  moblock-nfq 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 229kB will be freed.
Writing extended state information... Done
(Reading database ... 116166 files and directories currently installed.)
Removing moblock-nfq ...
Stopping MoBlock   ...fail!
invoke-rc.d: initscript moblock-nfq, action "stop" failed.
dpkg: error processing moblock-nfq (--remove):
 subprocess pre-removal script returned error exit status 3
Starting MoBlock   ...fail!
invoke-rc.d: initscript moblock-nfq, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 moblock-nfq
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done   
```

please i need help this is really annoying !

---

### Post by rocker9455 on 2008-04-17
i dont know if this helps but i have a odd log of blocked ips when i run tail -f /var/log/moblock.log
```
Duplicated range ( 147.147.11 )
Duplicated range ( 07.51.11 )
Duplicated range ( 13.169.1 )
Duplicated range ( 21.213.1 )
Duplicated range ( 108.109.23 )
Duplicated range ( 0.205.16 )
Duplicated range ( 7.52.8 )
Duplicated range ( 232.126.17 )
Duplicated range ( 232.126. )
Ranges loaded: 313139

```

---

### Post by rocker9455 on 2008-04-17
it says something to do with dpkg using a background process locking it so it cant be removed any way abround that ?

---

### Post by rocker9455 on 2008-04-18
please can someone help all i need to know is how to forcible remove the package when i try to you synaptic i get the error :
E: moblock-nfq: subprocess pre-removal script returned error exit status 3

can anyone help, can i get rid of it if i boot into recovery mode?

---

### Post by rocker9455 on 2008-04-18
if i delete all of these entries will it be gone:

/.
/etc
/etc/logrotate.d
/etc/logrotate.d/moblock-nfq
/etc/cron.daily
/etc/cron.daily/moblock-nfq
/etc/moblock
/etc/moblock/blocklists.list
/etc/moblock/MoBlock-nfq.sh
/etc/moblock/iptables-custom-remove.sh
/etc/moblock/moblock.conf
/etc/moblock/iptables-custom-insert.sh
/etc/init.d
/etc/init.d/moblock-nfq
/usr
/usr/bin
/usr/bin/moblock-nfq-control
/usr/bin/moblock-nfq
/usr/share
/usr/share/doc
/usr/share/doc/moblock-nfq
/usr/share/doc/moblock-nfq/README.gz
/usr/share/doc/moblock-nfq/changelog.Debian.gz
/usr/share/doc/moblock-nfq/README.Debian
/usr/share/doc/moblock-nfq/copyright
/usr/share/doc/moblock-nfq/changelog.gz
/usr/share/doc/moblock-nfq/README.blocklists.gz
/usr/share/doc/moblock-nfq/TODO
/usr/share/doc/moblock-nfq/NEWS.Debian.gz
/usr/share/doc/moblock-nfq/TODO.Debian
/usr/share/doc/moblock-nfq/THANKS
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/moblock-control.1.gz
/usr/share/man/man1/moblock.1.gz
/var
/var/spool
/var/spool/moblock
/var/spool/moblock/used
/usr/bin/moblock
/usr/bin/moblock-control
/usr/share/man/man1/moblock-nfq-control.1.gz
/usr/share/man/man1/moblock-nfq.1.gz

---

### Post by rocker9455 on 2008-04-18
does no one know how to fix this ? i am at a total loss and cant do much with m system at present

---

### Post by rocker9455 on 2008-04-18
i just reinstalled ubuntu now..

---

### Post by jre on 2008-04-30
Well, I might help but it seems to be to late.
For future reference (or other people having the same problem):
Could you tell me your version of lsb-base (dpkg --list lsb-base)

---

### Post by TremerePuck on 2008-05-06
I'm having the same problem

sh-3.2$ dpkg --list lsb-base
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  lsb-base       3.2-4ubuntu1   Linux Standard Base 3.2 init script function

---

### Post by jre on 2008-05-06
Argh, this is indeed a bug of lsb-base :-/
I don't know when it was introduced (can't be very long ago) but in Debian it was fixed in 3.2-8, see here: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=475258](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=475258).
The bug is that a "error 3" is given when the process is not running and shall be stopped - although the LSB specifies to return "0" in this case. Didn't understand me? Don't worry, just try this: Start MoBlock before you try to uninstall it.

Or install the current Debian package (it is architecture all): [http://packages.debian.org/sid/lsb-base](http://packages.debian.org/sid/lsb-base)

In case it still doesn't work have a look at /var/log/moblock-control.log and post again here.

Greets
jre

---

### Post by TremerePuck on 2008-05-06
Updating lsb-base worked! Many thanks!

---

### Post by Vock on 2008-07-23
I'm having issues uninstalling MoBlock as well, same problem, but for some reason the same solution isn't working.

Started moblock and tried to remove... didn't work
updated the latest lsb-base and still didn't uninstall.

```

vick@vick-desktop:/etc/moblock$ sudo apt-get remove --purge moblock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnfnetlink0 libnetfilter-queue1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  moblock*
0 upgraded, 0 newly installed, 1 to remove and 8 not upgraded.
After this operation, 360kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 174432 files and directories currently installed.)
Removing moblock ...
 * Stopping MoBlock moblock                                              [fail] 
invoke-rc.d: initscript moblock, action "stop" failed.
dpkg: error processing moblock (--purge):
 subprocess pre-removal script returned error exit status 3
Errors were encountered while processing:
 moblock
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

The contents of the moblock.conf are

```

# moblock.conf - configuration file for moblock-control

# This file is sourced by a shell script. Any line which starts with a # (hash)
# is a comment and is ignored. If you set the same variable several times,
# then only the last line will be used. You have to stop/restart/reload moblock
# if you change entries.

# Values from this file (moblock.conf) will be overwritten by moblock.default
# (/etc/default/moblock) if they are set there.

############################ General configuration ############################

# Set the format of the blocklists that you use. All your blocklists have to be
# in this format.
# d - eMule ipfilter.dat format
#     Example line:
#     001.000.000.000 , 001.255.255.255 , 100 , Some organization
# n - PeerGuardian .p2b v2 binary format
# p - PeerGuardian .p2p text format (default)
#     Example line:
#     Some organization:1.0.0.0-1.255.255.255
BLOCKLIST_FORMAT="p"

# Turn on/off MoBlock's logging to stdout (this isn't supported in
# moblock-control since moblock is started in the background)
# For moblock-control's output to STDOUT see the VERBOSITY setting below.
#LOG_STDOUT="0"

# Turn on/off timestamping in the logfile
# 0 - No timestamping
# 1 - Timestamping (default)
LOG_TIMESTAMP="1"

# Turn on/off the MoBlock daemon's logging to syslog
# 0 - Don't log to syslog (default)
# 1 - Log to syslog
LOG_SYSLOG="0"

# Iptables logging of blocked packets
# Set an iptables target for blocked packets. This will only work if marking
# matched (IP is in the blocklist) packets is on (i.e. REJECT="1").
# The iptables rules will be inserted directly before the iptables rule which
# decides what happens to "marked block" packets.
# Examples:
# "" (empty string): no rule will be inserted (default)
# "LOG --log-level info": blocked packets will be logged to syslog with "info"
#     log level. This allows to find out e.g. the port and to verify if a packet
#     is really blocked and not just "marked block".
LOG_IPTABLES=""

# Set the verbosity of moblock-control
# This only affects the output to STDOUT by moblock-control, cron and init.
# This does not affect logging or the output of the MoBlock daemon.
# 0 - Output to STDOUT is off (only errors will be reported)
# 1 - Output to STDOUT is on (default)
# 2 - Output to STDOUT is on, but no warning will be shown if an operation is
#     configured not to be executed.
VERBOSITY="1"

# Turn on/off automatic start
# Note: this tells the MoBlock init script from starting on "start". Therefore
# MoBlock will not be started at system boot. The same behaviour can be achieved
# by removing/tweaking the init file and the links pointing to it. You can do
# this manually or by using an application such as rcconf.
# 0 - Don´t start MoBlock at system boot
# 1 - Start MoBlock at system boot (default)
MOBLOCK_INIT="1"

# Turn on/off automatic blocklist update
# 0 - Don´t update the blocklists automatically
# 1 - Update the blocklists automatically (default)
MOBLOCK_CRON="1"

################## Settings for the iptables firewall rules ###################

# MoBlock checks traffic in userspace. Iptables rules decide which traffic gets
# there.

# Do a "moblock-control stop" before you change these iptables settings and a
# "moblock-control start" afterwards.

# Is the netfilter iptables system supported by kernel modules?
# 0 - No, netfilter iptables support is built into the kernel directly. Do not
#     use this option unless you know what you are doing.
# 1 - Yes, the netfilter iptables system is available as kernel modules.
#     (default)
IPTABLES_MODULES="1"

# Set the iptables target for sending traffic to userspace.
# NFQUEUE - available since kernel version 2.6.13 (default)
# QUEUE - (depreciated, you have to recompile MoBlock to use this)
IPTABLES_TARGET="NFQUEUE"

# Set the NFQUEUE queue number.
# Valid queue numbers are 0 to 65535. The default value is 0.
NFQUEUE_NUMBER="0"

# Set how traffic is sent to MoBlock
# 0 - Don't set any iptables rules.
#     You or another script/firewall has to do this!
# 1 - Place NFQUEUE in the chains moblock_in/moblock_out/moblock_fw.
#     (default)
# 2 - Set custom iptables rules (set in /etc/moblock/iptables-custom-insert.sh
#     and iptables-custom-remove.sh)
IPTABLES_SETTINGS="1"

# Activate MoBlock's iptables chains?
# This section works only for IPTABLES_SETTINGS="1"
# 0 - Do nothing. You or another script/firewall has to do this!
# 1 - Insert the rules at the head of the chains INPUT, OUTPUT and FORWARD. This
#     will send all new traffic to the chains that contain NFQUEUE (or QUEUE).
#     (default)
# 2 - obsolete
IPTABLES_ACTIVATION="1"

# Set what happens to matched (IP is in the blocklist) packets.
# 0 - DROP them directly (as in MoBlock 0.8).
# 1 - MARK them. Further iptables rules decide what happens to them. E.g. this
#     allows to REJECT packets to avoid the long timeout which occurs when
#     packets are DROPped, see below. This setting is also necessary for
#     iptables logging to syslog, see above. (default)
REJECT="1"

# Set the corresponding MARK
REJECT_MARK="10"

# Set the iptables target for "marked block" packets.
# This section works only for IPTABLES_ACTIVATION="1"
# Valid values are all iptables targets. Be careful: senseless values are also
# accepted.
# REJECT: The sender of the packet is notified that the packet was blocked.
# DROP: The sender of the packet is not notified that the packet was blocked.
REJECT_IN="DROP"
REJECT_OUT="REJECT"
REJECT_FW="DROP"

# Set what happens to non-matched (IP is not in the blocklist) packets.
# 0 - ACCEPT them directly (as in MoBlock 0.8)
# 1 - MARK them. MoBlock will then ignore them. This allows integration with
#     other firewalls. (default)
ACCEPT="1"

# Set the corresponding MARK
ACCEPT_MARK="20"

# Set the iptables target for whitelisting packets.
# Valid values are all iptables targets. Be careful: senseless values are also
# accepted.
# ACCEPT: The packets are accepted directly.
# RETURN: Further iptables rules decide what happens to the packets. MoBlock
# will ignore them. This allows integration with other firewalls. (default)
IPTABLES_TARGET_WHITELISTING="RETURN"

# Whitelist local traffic
# 0 - Do nothing.
# 1 - Automatically whitelist LAN traffic and traffic on the loopback device.
#     (default)
# 2 - Whitelist the loopback device (same as obsolete setting LOOPBACK="1").
WHITE_LOCAL="1"

############################### Whitelist ports ###############################

# Whitelist ports by port number or with the associated service name. Port
# ranges are specified in the format "port:port". Up to 15 ports can be
# specified. A port range (port:port) counts as two ports.
# Seperate several entries with whitespace (" "). Be careful: senseless values
# are also accepted.
#
# Common ports:
#   80 - http
#  443 - https
#   22 - ssh
#
# This section works only for IPTABLES_SETTINGS="1"
# Do a "moblock-control restart" when you have changed these settings.

WHITE_TCP_IN=""
WHITE_UDP_IN=""
WHITE_TCP_OUT="80 443"
WHITE_UDP_OUT=""
WHITE_TCP_FORWARD=""
WHITE_UDP_FORWARD=""
# This is an example to whitelist outgoing web traffic:
# WHITE_TCP_OUT="80 443"
# This is an example to whitelist the port range 1000-1024:
# WHITE_TCP_OUT="1000:1024"


################################ Whitelist IPs ################################

# This section works only for IPTABLES_SETTINGS="1"
# Do a "moblock-control restart" when you have changed these settings.

# New in version 0.9~rc2-12:
# You can specify IP ranges that shall not be checked by Moblock in a seperate
# file. Per default this is /etc/moblock/allow.p2p. See the ALLOW_[IN|OUT|FW]
# settings below if you want to change the default.

# The variables WHITE_IP_[IN|OUT|FORWARD] are depreciated. You can still use
# them but they will be removed in a future version.
WHITE_IP_IN=""
WHITE_IP_OUT=""
WHITE_IP_FORWARD=""

###################### Remove lines from the blocklist ########################

# Remove lines from the blocklist matching the specified pattern (the search
# pattern is case-insensitive).
# Seperate patterns with a semicolon ";". Be careful: senseless values are also
# accepted.
# Warning for beginners: If you want to whitelist a special IP then use the
# allowlist. If you specify an IP here you will most likely fail.
#
# Do a "moblock-control reload" when you have changed these settings.

IP_REMOVE=""
# This is an example to remove all lines from the blocklist which contain one
# of the words "google", "yahoo", "altavista", "debian" or "sourceforge":
# IP_REMOVE="google;yahoo;altavista;debian;sourceforge"

############################## General settings ###############################

PATH="/sbin:/bin:/usr/sbin:/usr/bin"

# The name of the application: moblock or nfblockd.
# Don't set this in moblock.default because most paths are set depending
# on the NAME variable before moblock.default is loaded
NAME="moblock"

# The path of the moblock binary (for nfblockd /usr/sbin/nfblockd will be chosen
# automatically):
DAEMON="/usr/bin/$NAME"

# The path of the moblock-control script
CONTROL_SCRIPT="/usr/bin/$NAME-control"

# The path of the configuration files' directory. Because others variables
# depend on this you have to set this here, not in moblock.default.
CONF_DIR="/etc/$NAME"

# The path of moblock.default
CONTROL_DEFAULT="/etc/default/$NAME"

# The path of the master blocklist directory
MASTER_BLOCKLIST_DIR="/etc/$NAME"

# The path of the directory where the blocklists are downloaded to
BLOCKLISTS_DIR="/var/spool/$NAME"

# The path of the directory where completely downloaded blocklists are copied to
BLOCKLISTS_DIR_USED="$BLOCKLISTS_DIR/used"

# The path of blocklists.list
BLOCKLISTS_LIST="$CONF_DIR/blocklists.list"

# The path to the allow lists
# Note that per default the same allow list is used for all (in, out and
# forwarded) connections.
# The path to the allow list for incoming connections
ALLOW_IN="$CONF_DIR/allow.p2p"
# The path to the allow list for outgoing connections
ALLOW_OUT="$CONF_DIR/allow.p2p"
# The path to the allow list for forwarded connections
ALLOW_FW="$CONF_DIR/allow.p2p"

# The path of iptables-custom-insert.sh
IPTABLES_CUSTOM_INSERT="$CONF_DIR/iptables-custom-insert.sh"

# The path of iptables-custom-remove.sh
IPTABLES_CUSTOM_DELETE="$CONF_DIR/iptables-custom-remove.sh"

# The path of the logfiles' directory and the logfiles
LOG_DIR="/var/log"
DAEMON_LOG="$LOG_DIR/$NAME.log"
CONTROL_LOG="$LOG_DIR/$NAME-control.log"

# The daemon's stat file
STATFILE="/var/log/MoBlock.stats"

# The path of moblock's pid file
PIDFILE="/var/run/$NAME.pid"

# The path of the lsb init functions
LSB="/lib/lsb/init-functions"

# Before updating the blocklists check if this host is reachable
TESTHOST="www.bluetack.co.uk"

# Full LSB compatibility
# moblock-control was created to run with every LSB 3.1 compatible system. You
# need a file /lib/lsb/init-functions. If your distribution misses this file
# you can download one based on the Debian version from
# moblock-deb.sourceforge.net.
# 0 - Debian compatible system (uses start-stop-daemon instead of start_daemon)
#     (default)
# 1 - LSB 3.1 but not Debian compatible system
LSB_MODE="0"

```

contents of moblock-control.log are:

```

2008-07-23 07:04:43 PM EDT Begin: moblock-control stop
Deleting iptablesiptables v1.3.8: Couldn't load target `moblock_in':/lib/iptables/libipt_moblock_in.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.8: Couldn't load target `moblock_out':/lib/iptables/libipt_moblock_out.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.8: Couldn't load target `moblock_fw':/lib/iptables/libipt_moblock_fw.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
 [33m*[39;49m Some iptables rules could not be deleted. The most common reason for this is
 [33m*[39;49m that they did not exist. If MoBlock was not running this is the correct
 [33m*[39;49m behaviour. But if MoBlock was running there is some problem. Make sure that
 [33m*[39;49m MoBlock inserts its iptables rules correctly and that other software, e.g.
 [33m*[39;49m firewall applications, don't delete them. Make sure that MoBlock is started
 [33m*[39;49m after other firewall applications.
Stopping MoBlock
[87G[[31mfail[39;49m]
2008-07-23 07:04:43 PM EDT End: moblock-control stop
2008-07-23 07:04:43 PM EDT Begin: moblock-control stop
Deleting iptablesiptables v1.3.8: Couldn't load target `moblock_in':/lib/iptables/libipt_moblock_in.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.8: Couldn't load target `moblock_out':/lib/iptables/libipt_moblock_out.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.8: Couldn't load target `moblock_fw':/lib/iptables/libipt_moblock_fw.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
 [33m*[39;49m Some iptables rules could not be deleted. The most common reason for this is
 [33m*[39;49m that they did not exist. If MoBlock was not running this is the correct
 [33m*[39;49m behaviour. But if MoBlock was running there is some problem. Make sure that
 [33m*[39;49m MoBlock inserts its iptables rules correctly and that other software, e.g.
 [33m*[39;49m firewall applications, don't delete them. Make sure that MoBlock is started
 [33m*[39;49m after other firewall applications.
Stopping MoBlock
[87G[[31mfail[39;49m]
2008-07-23 07:04:43 PM EDT End: moblock-control stop
2008-07-23 07:11:19 PM EDT Begin: moblock-control stop
Deleting iptablesiptables v1.3.8: Couldn't load target `moblock_in':/lib/iptables/libipt_moblock_in.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.8: Couldn't load target `moblock_out':/lib/iptables/libipt_moblock_out.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.8: Couldn't load target `moblock_fw':/lib/iptables/libipt_moblock_fw.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
 [33m*[39;49m Some iptables rules could not be deleted. The most common reason for this is
 [33m*[39;49m that they did not exist. If MoBlock was not running this is the correct
 [33m*[39;49m behaviour. But if MoBlock was running there is some problem. Make sure that
 [33m*[39;49m MoBlock inserts its iptables rules correctly and that other software, e.g.
 [33m*[39;49m firewall applications, don't delete them. Make sure that MoBlock is started
 [33m*[39;49m after other firewall applications.
Stopping MoBlock
[74G[[31mfail[39;49m]
2008-07-23 07:11:19 PM EDT End: moblock-control stop
2008-07-23 07:11:57 PM EDT Begin: moblock-control stop
Deleting iptablesiptables v1.3.8: Couldn't load target `moblock_in':/lib/iptables/libipt_moblock_in.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.8: Couldn't load target `moblock_out':/lib/iptables/libipt_moblock_out.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.8: Couldn't load target `moblock_fw':/lib/iptables/libipt_moblock_fw.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
 [33m*[39;49m Some iptables rules could not be deleted. The most common reason for this is
 [33m*[39;49m that they did not exist. If MoBlock was not running this is the correct
 [33m*[39;49m behaviour. But if MoBlock was running there is some problem. Make sure that
 [33m*[39;49m MoBlock inserts its iptables rules correctly and that other software, e.g.
 [33m*[39;49m firewall applications, don't delete them. Make sure that MoBlock is started
 [33m*[39;49m after other firewall applications.
Stopping MoBlock
[74G[[31mfail[39;49m]
2008-07-23 07:11:57 PM EDT End: moblock-control stop
2008-07-23 07:11:57 PM EDT Begin: moblock-control stop
Deleting iptablesiptables v1.3.8: Couldn't load target `moblock_in':/lib/iptables/libipt_moblock_in.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.8: Couldn't load target `moblock_out':/lib/iptables/libipt_moblock_out.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.8: Couldn't load target `moblock_fw':/lib/iptables/libipt_moblock_fw.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
 [33m*[39;49m Some iptables rules could not be deleted. The most common reason for this is
 [33m*[39;49m that they did not exist. If MoBlock was not running this is the correct
 [33m*[39;49m behaviour. But if MoBlock was running there is some problem. Make sure that
 [33m*[39;49m MoBlock inserts its iptables rules correctly and that other software, e.g.
 [33m*[39;49m firewall applications, don't delete them. Make sure that MoBlock is started
 [33m*[39;49m after other firewall applications.
Stopping MoBlock
[74G[[31mfail[39;49m]
2008-07-23 07:11:57 PM EDT End: moblock-control stop
2008-07-23 07:17:47 PM EDT Begin: moblock-control stop
Deleting iptablesiptables v1.3.8: Couldn't load target `moblock_in':/lib/iptables/libipt_moblock_in.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.8: Couldn't load target `moblock_out':/lib/iptables/libipt_moblock_out.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.8: Couldn't load target `moblock_fw':/lib/iptables/libipt_moblock_fw.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
 [33m*[39;49m Some iptables rules could not be deleted. The most common reason for this is
 [33m*[39;49m that they did not exist. If MoBlock was not running this is the correct
 [33m*[39;49m behaviour. But if MoBlock was running there is some problem. Make sure that
 [33m*[39;49m MoBlock inserts its iptables rules correctly and that other software, e.g.
 [33m*[39;49m firewall applications, don't delete them. Make sure that MoBlock is started
 [33m*[39;49m after other firewall applications.
Stopping MoBlock
[74G[[31mfail[39;49m]
2008-07-23 07:17:47 PM EDT End: moblock-control stop
2008-07-23 07:24:34 PM EDT Begin: moblock-control start
 [31m*[39;49m Error 7: Missing file /etc/moblock/guarding.p2p.
 [31m*[39;49m Check the BLOCKLIST settings in /etc/moblock/moblock.conf.
 [31m*[39;49m Also check /etc/default/moblock.
2008-07-23 07:24:47 PM EDT Begin: moblock-control stop
Deleting iptablesiptables v1.3.8: Couldn't load target `moblock_in':/lib/iptables/libipt_moblock_in.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.8: Couldn't load target `moblock_out':/lib/iptables/libipt_moblock_out.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.8: Couldn't load target `moblock_fw':/lib/iptables/libipt_moblock_fw.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
 [33m*[39;49m Some iptables rules could not be deleted. The most common reason for this is
 [33m*[39;49m that they did not exist. If MoBlock was not running this is the correct
 [33m*[39;49m behaviour. But if MoBlock was running there is some problem. Make sure that
 [33m*[39;49m MoBlock inserts its iptables rules correctly and that other software, e.g.
 [33m*[39;49m firewall applications, don't delete them. Make sure that MoBlock is started
 [33m*[39;49m after other firewall applications.
Stopping MoBlock
[74G[[31mfail[39;49m]
2008-07-23 07:24:47 PM EDT End: moblock-control stop
2008-07-23 07:26:24 PM EDT Begin: moblock-control stop
Deleting iptablesiptables v1.3.8: Couldn't load target `moblock_in':/lib/iptables/libipt_moblock_in.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.8: Couldn't load target `moblock_out':/lib/iptables/libipt_moblock_out.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.8: Couldn't load target `moblock_fw':/lib/iptables/libipt_moblock_fw.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
 [33m*[39;49m Some iptables rules could not be deleted. The most common reason for this is
 [33m*[39;49m that they did not exist. If MoBlock was not running this is the correct
 [33m*[39;49m behaviour. But if MoBlock was running there is some problem. Make sure that
 [33m*[39;49m MoBlock inserts its iptables rules correctly and that other software, e.g.
 [33m*[39;49m firewall applications, don't delete them. Make sure that MoBlock is started
 [33m*[39;49m after other firewall applications.
Stopping MoBlock
[74G[[31mfail[39;49m]
2008-07-23 07:26:24 PM EDT End: moblock-control stop
2008-07-23 07:28:12 PM EDT Begin: moblock-control stop
Deleting iptablesiptables v1.3.8: Couldn't load target `moblock_in':/lib/iptables/libipt_moblock_in.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.8: Couldn't load target `moblock_out':/lib/iptables/libipt_moblock_out.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.8: Couldn't load target `moblock_fw':/lib/iptables/libipt_moblock_fw.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
 [33m*[39;49m Some iptables rules could not be deleted. The most common reason for this is
 [33m*[39;49m that they did not exist. If MoBlock was not running this is the correct
 [33m*[39;49m behaviour. But if MoBlock was running there is some problem. Make sure that
 [33m*[39;49m MoBlock inserts its iptables rules correctly and that other software, e.g.
 [33m*[39;49m firewall applications, don't delete them. Make sure that MoBlock is started
 [33m*[39;49m after other firewall applications.
Stopping MoBlock
[74G[[31mfail[39;49m]
2008-07-23 07:28:12 PM EDT End: moblock-control stop

```

Also, if it helps any:
when I type sudo moblock-control start
and then
pidof moblock or pidof moblock-control, all i get are blank lines after, I'm assuming that means they're not running?

---

