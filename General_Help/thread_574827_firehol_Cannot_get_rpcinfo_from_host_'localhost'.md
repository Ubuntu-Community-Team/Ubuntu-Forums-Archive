---
title: "firehol: Cannot get rpcinfo from host 'localhost'"
date: 2007-10-13
forum: General Help
---

### Post by jmvidalvia on 2007-10-13
I couldn't find help in Google. 
I am getting these 2 error messages while doing firehol try: 
 
```
-------------------------------------------------------------------------------- 
ERROR #: 1 
WHAT : Getting RPC information from server 'localhost' 
WHY : Cannot get rpcinfo from host 'localhost' (using the previous firewall rules) 
COMMAND: server ping\ ftp\ icp\ ICMP\ microsoft_ds\ webcache\ upnp\ samba\ netbios_dgm\ netbios_ns\ netbios_ssn\ ssh\ cups\ nfs\ portmap\ squid accept  
SOURCE : line INIT of /etc/firehol/firehol.conf 
 
 
-------------------------------------------------------------------------------- 
ERROR #: 2 
WHAT : Getting RPC information from server 'localhost' 
WHY : Complex service 'nfs' returned an error (1). 
COMMAND: server ping\ ftp\ icp\ ICMP\ microsoft_ds\ webcache\ upnp\ samba\ netbios_dgm\ netbios_ns\ netbios_ssn\ ssh\ cups\ nfs\ portmap\ squid accept  
SOURCE : line INIT of /etc/firehol/firehol.conf 
```
 
My firehol.conf is: 
 
```
version 5 
FIREHOL_LOG_MODE="ULOG" 
DEFAULT_CLIENT_PORTS="1024:65535" 
 
interface eth0 interface1 src "192.168.103.0/24" dst 192.168.103.123 
protection strong 10/sec 10 
server "ping ftp icp ICMP microsoft_ds webcache upnp samba netbios_dgm netbios_ns netbios_ssn ssh cups nfs portmap squid" accept 
client all accept 
policy drop 
 
interface eth0 interface2 src not "${UNROUTABLE_IPS} 192.168.103.0/24" dst 192.168.103.123 
protection strong 10/sec 10 
server "icp ICMP microsoft_ds webcache upnp netbios_dgm netbios_ns netbios_ssn ssh squid" accept 
client all accept 
policy drop 
 
UNMATCHED_INPUT_POLICY="DROP" 
UNMATCHED_OUTPUT_POLICY="DROP" 
FIREHOL_LOG_LEVEL=4 
```
  
Thanks a lot for your help!

---

### Post by jmvidalvia on 2007-10-13
Solved!
Portmap was stopped.
Thanks anyway.

---

