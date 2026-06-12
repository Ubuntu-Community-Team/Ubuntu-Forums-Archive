---
title: "Can not redirect rsyslog logs to different lokalization."
date: 2017-09-18
forum: General Help
---

### Post by smithbox on 2017-09-18
Hi, everybody.
I use Ubuntu 16.10 with iptables 1.6 as firewall.
The Problem - all logs are mixed in syslog, kern.log lokalization.
What I need is to separate all iptables logs (firewall.service) in one destination.
My firewall service working great.
My iptables script config for firewall.service:
```
#!/bin/sh

conntrack -F

iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT

iptables -F
iptables -X

iptables -A INPUT -i lo -j ACCEPT

iptables -A INPUT -m limit --limit 2/min -j LOG --log-prefix "ipT4 DROP INPUT: " 
iptables -A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
iptables -A INPUT -m conntrack --ctstate INVALID -m limit --limit 2/min -j LOG --log-prefix "ipT4 DROP INVALID IN: "
iptables -A INPUT -m conntrack --ctstate INVALID -j DROP



iptables -A FORWARD -m conntrack --ctstate INVALID -j LOG --log-prefix "ipT4 DROP INVALID FWD: "
iptables -A FORWARD -m conntrack --ctstate INVALID -j DROP

iptables -I OUTPUT -m state -p tcp --state NEW -i eth0 -m limit --limit 1/m --limit-burst 1 -j LOG --log-uid --log-prefix "ipT4 Outbound Connection:  "
iptables -A OUTPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -m conntrack --ctstate INVALID -m limit --limit 2/min -j LOG --log-prefix "ipT4 DROP INVALID OUT: "
iptables -A OUTPUT -m conntrack --ctstate INVALID -j DROP




ip6tables -F
ip6tables -X
ip6tables -P INPUT DROP
ip6tables -P FORWARD DROP
ip6tables -P OUTPUT ACCEPT
ip6tables -A INPUT -i lo -j ACCEPT
ip6tables -A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT

```

My /etc/rsyslog.conf:
```
  /etc/rsyslog.conf    Configuration file for rsyslog.
#
#                       For more information see
#                       /usr/share/doc/rsyslog-doc/html/rsyslog_conf.html
#
#  Default logging rules can be found in /etc/rsyslog.d/50-default.conf


#################
#### MODULES ####
#################

module(load="imuxsock") # provides support for local system logging
#module(load="immark")  # provides --MARK-- message capability

# provides UDP syslog reception
#module(load="imudp")
#input(type="imudp" port="514")

# provides TCP syslog reception
#module(load="imtcp")
#input(type="imtcp" port="514")

# provides kernel logging support and enable non-kernel klog messages
module(load="imklog" permitnonkernelfacility="on")

###########################
#### GLOBAL DIRECTIVES ####
###########################

#
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

```

My /etc/rsyslog.d/10-custom.conf
```
kern warning                    /var/log/iptables.log
kern.warning   ~
*.*            /var/log/messages
```
My: /var/log/firewall
      /var/log/iptables.log
still empty.
Whats wrong?:confused:

---

