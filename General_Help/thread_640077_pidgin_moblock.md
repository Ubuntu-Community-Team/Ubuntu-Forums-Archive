---
title: "pidgin moblock"
date: 2007-12-13
forum: General Help
---

### Post by blkno1 on 2007-12-13
For some reason pidgin (ver 3.2.1) can no longer connect to Yahoo Messenger unless I turn off moblock.  What do I need to change? 

Here is my moblock.conf

```
# moblock.conf - configuration file for moblock-control

# This file is sourced by a bash script. Any line which starts with a # (hash) 
# is a comment and is ignored. If you set the same variable several times,
# then only the last line will be used. You have to stop/restart/reload moblock
# if you change entries.

############################ General configuration ############################

# Specify the format of the blocklists that you use. You can´t mix different
# formats.
# d - eMule ipfilter.dat format
# n - peerguardian .p2b v2 binary format
# p - peerguardian .p2p text format
BLOCKLIST_FORMAT="p"

# Specify a NFQUEUE queue number (default 0)
# Works only with -nfq version
NFQUEUE_NUMBER="0"

# Turn on/off automatic start
# 0 - Don´t start MoBlock at system boot
# 1 - Start MoBlock at system boot
MOBLOCK_INIT="1"

# Turn on/off automatic blocklist update
# 0 - Don´t update the blocklists automatically
# 1 - Update the blocklists automatically
MOBLOCK_CRON="1"

# Set the verbosity of moblock-control
# 0 - No normal output to STDOUT, only to logfile
# 1 - Output to STDOUT and to logfile
VERBOSITY="1"

################## Settings for the iptables firewall rules ###################

# MoBlock requires the iptables rule NFQUEUE (nfq version)
# or the deprecated QUEUE (ipq version).

# Do a "moblock-control stop" before you change these iptables settings.

# Define how traffic is sent to MoBlock
# 0 - Don't set any iptables rules.
#     You or another script/firewall has to do this!
# 1 - NFQUEUE is in the chains moblock_in, moblock_out and moblock_fw.
# 2 - Set custom iptables rules (defined in
#     /etc/moblock/iptables-custom-insert.sh and iptables-custom-remove.sh)
IPTABLES_SETTINGS="1"

# Define when traffic is sent to the chain that contains NFQUEUE
# This section works only for IPTABLES_SETTINGS="1"
# 0 - Do nothing. You or another script/firewall has to do this!
# 1 - Insert the rules at the head of the chains.
# 2 - Append the rules to the end of the chains.
IPTABLES_ACTIVATION="2"

############################### Whitelist ports ###############################

# Whitelist ports by port number or with the associated service name
# (using iptables with the target RETURN)
# Seperate several entries with whitespace (" ")
# Port ranges are specified in the format "port:port"

# This section works only for IPTABLES_SETTINGS="1"
# Do a "moblock-control restart" when you have changed these settings.

WHITE_TCP_IN=""
WHITE_UDP_IN=""
WHITE_TCP_OUT=""
# This is an example to whitelist outgoing web traffic (port 80 is the service
# http, 443 is https) and the port range 1000-1024:
WHITE_TCP_OUT="80 443 1000:1024"
WHITE_UDP_OUT=""
WHITE_TCP_FORWARD=""
WHITE_UDP_FORWARD=""

################################ Whitelist IPs ################################

# Whitelist either a network name, a hostname (please note that specifying any
# name to be resolved with a remote query such as DNS is a really bad idea), a
# network IP address (with /mask), or a plain IP address.
# (using iptables with the target RETURN)
# The mask can be either a network mask or a plain number, specifying the number
# of 1's at the left side of the network mask. Thus, a mask of 24 is equivalent
# to 255.255.255.0.
# Seperate several entries with whitespace (" ")


# This section works only for IPTABLES_SETTINGS="1"
# Do a "moblock-control restart" when you have changed these settings.

IP_TCP_IN=""
IP_UDP_IN=""
IP_TCP_OUT=""
# This is an example to whitelist the range 192.168.178.1-192.168.178.255:
# IP_TCP_OUT="192.168.178.0/24"
IP_UDP_OUT=""
IP_TCP_FORWARD=""
IP_UDP_FORWARD=""

###################### Remove lines from the blocklist ########################

# Remove lines from the blocklist (using "grep -v -i")
# Warning for beginners: If you want to whitelist a special IP then check the
# above section. In most cases you won't succeed if you insert an IP here.
# Seperate values with a semicolon ";".

# Do a "moblock-control reload" when you have changed these settings.

IP_REMOVE=""
# This is an example to remove all lines from the blocklist which contain one
# of the words "google", "yahoo", "altavista", "debian" or "sourceforge":
# IP_REMOVE="google;yahoo;altavista;debian;sourceforge"	

########################### Full LSB compatibility ############################

# The control script uses /lib/lsb/init-functions. In Debian this file also
# provides functions which are not defined by the LSB standard. Change this
# entry if the script complains of not knowing a function.
# 0 - Debian compatible system (default)
# 1 - LSB 3.1 but not Debian compatible system
LSB_MODE=0
```

---

### Post by backup on 2007-12-15
Try opening TCP port 1863, like so:

```

# This is an example to whitelist outgoing web traffic (port 80 is the service
# http, 443 is https) and the port range 1000-1024:
# also added port 1863 for pidgin IM
WHITE_TCP_OUT="80 443 1000:1024 1863"

```

---

### Post by backup on 2007-12-15
Actually, allow me to correct myself, I think Yahoo Messenger uses port 5050. Port 1863 is used by MSN Messenger.

---

### Post by blkno1 on 2007-12-16
Worked like a charm!   \\:D/

thanks!

---

### Post by xlslx on 2008-04-01
i have a better solution for this. iam using moblock since yesterday as well and i have the same problem with my Yahoo-Plugin in Miranda. But opening a whole port isnt that good! Just whitelist the IP the Messenger uses to connect to yahoo. it works great for me and the standard Messenger-Login IP for Yahoo is the following:

DNS: scs.msg.yahoo.com
IP (pinged): 216.155.193.163

EDIT(!!!): Just a few minutes later the Domain above got the x.x.x.133 as the new IP so i changed the moblock.conf below from x.x.x.163 to x.x.x.0/24 so every ip within 216.155.193.1 to .254 will be never filtered.

just type it into the config like me as shown below:
------------------------------------------------
WHITE_IP_IN="216.155.193.0/24"
WHITE_IP_OUT="216.155.193.0/24"
# This is an example to whitelist the range 192.168.178.1-192.168.178.255:
# WHITE_IP_OUT=""
WHITE_IP_FORWARD="216.155.193.0/24"
------------------------------------------------

The adavantage of this solution is that every other IP will be checked and filtered on the "Yahoo-Port", so theres a lower risk, you understood?

Greets, Martin

PS: If there are any questions just PM/Mail me - and sorry for my partially bad english - iam german ;)

---

