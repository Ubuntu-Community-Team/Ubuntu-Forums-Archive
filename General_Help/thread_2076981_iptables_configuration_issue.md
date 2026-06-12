---
title: "iptables configuration issue"
date: 2012-10-27
forum: General Help
---

### Post by esolve on 2012-10-27
I want to configure remote desktop TigerVNC following the guide:
[setting up vncserver on Fedora 16 | zeusville](http://zeusville.wordpress.com/2012/01/27/setting-up-vncserver-on-fedora-16/)

the author said:
```

let’s update iptables:

sudo vi /etc/sysconfig/iptables

Add this to the file:

-A INPUT -p tcp -m state --state NEW -m tcp --dport 5903 -j ACCEPT

Save the file, then restart iptables and verify that the port is active.

sudo systemctl restart iptables.service

sudo iptables --list | grep 5903
ACCEPT     tcp  --  anywhere             anywhere             state NEW tcp d

```
but I get
```

[root@canard tor_capture]# systemctl restart iptables.service
[root@canard tor_capture]# iptables --list 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  

```

how to deal with this?
thanks!

BTW, the /etc/sysconfig/iptables on the remote machine is:

```

# Load additional iptables modules (nat helpers)
#   Default: -none-
# Space separated list of nat helpers (e.g. 'ip_nat_ftp ip_nat_irc'), which
# are loaded after the firewall rules are applied. Options for the helpers are
# stored in /etc/modprobe.conf.
IPTABLES_MODULES=""

# Unload modules on restart and stop
#   Value: yes|no,  default: yes
# This option has to be 'yes' to get to a sane state for a firewall
# restart or stop. Only set to 'no' if there are problems unloading netfilter
# modules.
IPTABLES_MODULES_UNLOAD="yes"

# Save current firewall rules on stop.
#   Value: yes|no,  default: no
# Saves all firewall rules to /etc/sysconfig/iptables if firewall gets stopped
# (e.g. on system shutdown).
IPTABLES_SAVE_ON_STOP="no"

# Save current firewall rules on restart.
#   Value: yes|no,  default: no
# Saves all firewall rules to /etc/sysconfig/iptables if firewall gets
# restarted.
IPTABLES_SAVE_ON_RESTART="no"

# Save (and restore) rule and chain counter.
#   Value: yes|no,  default: no
# Save counters for rules and chains to /etc/sysconfig/iptables if
# 'service iptables save' is called or on stop or restart if SAVE_ON_STOP or
# SAVE_ON_RESTART is enabled.
IPTABLES_SAVE_COUNTER="no"

# Numeric status output
#   Value: yes|no,  default: yes
# Print IP addresses and port numbers in numeric format in the status output.
IPTABLES_STATUS_NUMERIC="yes"

# Verbose status output
#   Value: yes|no,  default: yes
# Print info about the number of packets and bytes plus the "input-" and
# "outputdevice" in the status output.
IPTABLES_STATUS_VERBOSE="no"

# Status output with numbered lines
#   Value: yes|no,  default: yes
# Print a counter/number for every rule in the status output.
IPTABLES_STATUS_LINENUMBERS="yes"

-A INPUT -p tcp -m state --state NEW -m tcp --dport 5903 -j ACCEPT

```

---

