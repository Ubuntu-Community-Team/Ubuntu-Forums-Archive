---
title: "Snort"
date: 2007-12-16
forum: General Help
---

### Post by communized on 2007-12-16
So i got snort working using this tutorial.

[http://www.unix-tutorials.com/go.php?id=3422](http://www.unix-tutorials.com/go.php?id=3422)

which means i also got php, apache, and base all working, ( as far as i can tell )

BUT, on the BASE page, with snort running for about 10 mins now... it isn't logging any traffic.


Also ( i have two instances of snort running, one in daemon mode.. how do i get rid of it? )

administrator@administrator-desktop:~$ ps aux | grep snort
root      5726  0.0  3.3 100900 34592 ?        Ss   01:45   0:00 snort -c /etc/snort/snort.conf -i eth0 -D
root      5808  3.3  3.3 100816 34948 pts/0    S+   01:51   0:01 snort -c /etc/snort/snort.conf
1000      5830  0.0  0.0   5120   820 pts/1    R+   01:52   0:00 grep snort


Any help is appreciated, if you need to ask me a question ill answer as fast as possible

---

### Post by communized on 2007-12-16
HTTP Inspect - encodings (Note: stream-reassembled packets included):
    POST methods:                   0         
    GET methods:                    0         
    Post parameters extracted:      0         
    Unicode:                        0         
    Double unicode:                 0         
    Non-ASCII representable:        0         
    Base 36:                        0         
    Directory traversals:           0         
    Extra slashes ("//"):           0         
    Self-referencing paths ("./"):  0         
    Total packets processed:        6993     


when i stopped the snort that was not running in daemon mode.

so what i don't understand is, if im processing packets..

why is the traffic still showing as 

Traffic Profile by Protocol
TCP (0%)	
 
UDP (0%)	
 
ICMP (0%)	
 
Portscan Traffic (0%)

in the Basic Analysis and Security Engine (BASE) page

---

### Post by communized on 2007-12-16
bump

---

### Post by communized on 2007-12-16
bumplz

---

### Post by communized on 2007-12-16
this art bumped again

---

### Post by communized on 2007-12-16
Okay, ill give a little info i guess to who ever reads this..

when i run snort

> administrator@administrator-desktop:~$ sudo snort -c /etc/snort/snort.conf -i eth0
[sudo] password for administrator:
Running in IDS mode

        --== Initializing Snort ==--
Initializing Output Plugins!
Initializing Preprocessors!
Initializing Plug-ins!
Parsing Rules file /etc/snort/snort.conf
PortVar 'HTTP_PORTS' defined :  [ 80]
PortVar 'SHELLCODE_PORTS' defined :  [ 0:79 81:65535]
PortVar 'ORACLE_PORTS' defined :  [ 1521]
Frag3 global config:
    Max frags: 65536
    Fragment memory cap: 4194304 bytes
Frag3 engine config:
    Target-based policy: FIRST
    Fragment timeout: 60 seconds
    Fragment min_ttl:   1
    Fragment ttl_limit: 5
    Fragment Problems: 1
Stream5 global config:
    Track TCP sessions: ACTIVE
    Max TCP sessions: 8192
    Memcap (for reassembly packet storage): 8388608
    Track UDP sessions: INACTIVE
    Track ICMP sessions: INACTIVE
Stream5 TCP Policy config:
    Reassembly Policy: FIRST
    Timeout: 30 seconds
    Min ttl:  1
    Options:
        Static Flushpoint Sizes: YES
    Reassembly Ports:
      21 client (Footprint) 
      23 client (Footprint) 
      25 client (Footprint) 
      42 client (Footprint) 
      53 client (Footprint) 
      80 client (Footprint) 
      110 client (Footprint) 
      111 client (Footprint) 
      135 client (Footprint) 
      136 client (Footprint) 
      137 client (Footprint) 
      139 client (Footprint) 
      143 client (Footprint) 
      445 client (Footprint) 
      513 client (Footprint) 
      1433 client (Footprint) 
      1521 client (Footprint) 
      3306 client (Footprint) 
HttpInspect Config:
    GLOBAL CONFIG
      Max Pipeline Requests:    0
      Inspection Type:          STATELESS
      Detect Proxy Usage:       NO
      IIS Unicode Map Filename: /etc/snort/unicode.map
      IIS Unicode Map Codepage: 1252
    DEFAULT SERVER CONFIG:
      Server profile: All
      Ports: 80 8080 8180 
      Flow Depth: 300
      Max Chunk Length: 500000
      Inspect Pipeline Requests: YES
      URI Discovery Strict Mode: NO
      Allow Proxy Usage: NO
      Disable Alerting: NO
      Oversize Dir Length: 500
      Only inspect URI: NO
      Ascii: YES alert: NO
      Double Decoding: YES alert: YES
      %U Encoding: YES alert: YES
      Bare Byte: YES alert: YES
      Base36: OFF
      UTF 8: OFF
      IIS Unicode: YES alert: YES
      Multiple Slash: YES alert: NO
      IIS Backslash: YES alert: NO
      Directory Traversal: YES alert: NO
      Web Root Traversal: YES alert: YES
      Apache WhiteSpace: YES alert: NO
      IIS Delimiter: YES alert: NO
      IIS Unicode Map: GLOBAL IIS UNICODE MAP CONFIG
      Non-RFC Compliant Characters: NONE
      Whitespace Characters: 0x09 0x0b 0x0c 0x0d 
rpc_decode arguments:
    Ports to decode RPC on: 111 32771 
    alert_fragments: INACTIVE
    alert_large_fragments: ACTIVE
    alert_incomplete: ACTIVE
    alert_multiple_requests: ACTIVE
Portscan Detection Config:
    Detect Protocols:  TCP UDP ICMP IP
    Detect Scan Type:  portscan portsweep decoy_portscan distributed_portscan
    Sensitivity Level: Low
    Memcap (in bytes): 10000000
    Number of Nodes:   31347

Tagged Packet Limit: 256
Loading dynamic engine /usr/local/lib/snort_dynamicengine/libsf_engine.so... done
Loading all dynamic preprocessor libs from /usr/local/lib/snort_dynamicpreprocessor/...
  Loading dynamic preprocessor library /usr/local/lib/snort_dynamicpreprocessor//lib_sfdynamic_preprocessor_example.so... done
  Loading dynamic preprocessor library /usr/local/lib/snort_dynamicpreprocessor//libsf_dns_preproc.so... done
  Loading dynamic preprocessor library /usr/local/lib/snort_dynamicpreprocessor//libsf_ftptelnet_preproc.so... done
  Loading dynamic preprocessor library /usr/local/lib/snort_dynamicpreprocessor//libsf_dcerpc_preproc.so... done
  Loading dynamic preprocessor library /usr/local/lib/snort_dynamicpreprocessor//libsf_smtp_preproc.so... done
  Loading dynamic preprocessor library /usr/local/lib/snort_dynamicpreprocessor//libsf_ssh_preproc.so... done
  Finished Loading all dynamic preprocessor libs from /usr/local/lib/snort_dynamicpreprocessor/
FTPTelnet Config:
    GLOBAL CONFIG
      Inspection Type: stateful
      Check for Encrypted Traffic: YES alert: YES
      Continue to check encrypted data: NO
    TELNET CONFIG:
      Ports: 23 
      Are You There Threshold: 200
      Normalize: YES
      Detect Anomalies: NO
    FTP CONFIG:
      FTP Server: default
        Ports: 21 
        Check for Telnet Cmds: YES alert: YES
        Identify open data channels: YES
      FTP Client: default
        Check for Bounce Attacks: YES alert: YES
        Check for Telnet Cmds: YES alert: YES
        Max Response Length: 256

SMTP Config:
    Ports: 25 587 691 
    Inspection Type: Stateful
    Normalize: EXPN RCPT VRFY 
    Ignore Data: No
    Ignore TLS Data: No
    Ignore SMTP Alerts: No
    Max Command Line Length: Unlimited
    Max Specific Command Line Length: 
       ETRN:500 EXPN:255 HELO:500 HELP:500 MAIL:260 
       RCPT:300 VRFY:255 
    Max Header Line Length: Unlimited
    Max Response Line Length: Unlimited
    X-Link2State Alert: Yes
    Drop on X-Link2State Alert: No
    Alert on commands: None

DCE/RPC Decoder config:
    Autodetect ports ENABLED
    SMB fragmentation ENABLED
    DCE/RPC fragmentation ENABLED
    Max Frag Size: 3000 bytes
    Memcap: 100000 KB
    Alert if memcap exceeded DISABLED

DNS config: 
    DNS Client rdata txt Overflow Alert: ACTIVE
    Obsolete DNS RR Types Alert: INACTIVE
    Experimental DNS RR Types Alert: INACTIVE
    Ports: 53

+++++++++++++++++++++++++++++++++++++++++++++++++++
Initializing rule chains...
2830 Snort rules read
    2830 detection rules
    0 decoder rules
    0 preprocessor rules
2830 Option Chains linked into 215 Chain Headers
0 Dynamic rules
+++++++++++++++++++++++++++++++++++++++++++++++++++

+-------------------[Rule Port Counts]---------------------------------------
|             tcp     udp    icmp      ip
|     src     122      12       0       0
|     dst    2382     163       0       0
|     any      68      50      50      20
|      nc      22       8      15      18
|     s+d       3       3       0       0
+----------------------------------------------------------------------------

+-----------------------[thresholding-config]----------------------------------
| memory-cap : 1048576 bytes
+-----------------------[thresholding-global]----------------------------------
| none
+-----------------------[thresholding-local]-----------------------------------
| gen-id=1      sig-id=3273       type=Threshold tracking=src count=5   seconds=2  
| gen-id=1      sig-id=2494       type=Both      tracking=dst count=20  seconds=60 
| gen-id=1      sig-id=2523       type=Both      tracking=dst count=10  seconds=10 
| gen-id=1      sig-id=2275       type=Threshold tracking=dst count=5   seconds=60 
| gen-id=1      sig-id=2496       type=Both      tracking=dst count=20  seconds=60 
| gen-id=1      sig-id=2495       type=Both      tracking=dst count=20  seconds=60 
| gen-id=1      sig-id=3542       type=Threshold tracking=src count=5   seconds=2  
| gen-id=1      sig-id=2923       type=Threshold tracking=dst count=10  seconds=60 
| gen-id=1      sig-id=3527       type=Limit     tracking=dst count=5   seconds=60 
| gen-id=1      sig-id=3152       type=Threshold tracking=src count=5   seconds=2  
| gen-id=1      sig-id=3543       type=Threshold tracking=src count=5   seconds=2  
| gen-id=1      sig-id=2924       type=Threshold tracking=dst count=10  seconds=60 
+-----------------------[suppression]------------------------------------------
| none
-------------------------------------------------------------------------------
Rule application order: activation->dynamic->pass->drop->alert->log
Log directory = /var/log/snort
Verifying Preprocessor Configurations!
Warning: flowbits key 'realplayer.playlist' is checked but not ever set.
Warning: flowbits key 'dce.bind.veritas' is set but not ever checked.
Warning: flowbits key 'ms_sql_seen_dns' is checked but not ever set.
Warning: flowbits key 'smb.tree.create.llsrpc' is set but not ever checked.
35 out of 512 flowbits in use.

Initializing Network Interface eth0
Decoding Ethernet on interface eth0
database: compiled support for ( mysql )
database: configured to use mysql
database:          user = root
database: password is set
database: database name = snort
database:          host = localhost
database:   sensor name = 192.168.1.100
database:     sensor id = 1
database: schema version = 107
database: using the "log" facility

[ Port Based Pattern Matching Memory ]
+-[AC-BNFA Search Info Summary]------------------------------
| Instances        : 187
| Patterns         : 11444
| Pattern Chars    : 97540
| Num States       : 52756
| Num Match States : 7560
| Memory           :   1.83Mbytes
|   Patterns       :   0.44M
|   Match Lists    :   0.60M
|   Transitions    :   0.77M
+-------------------------------------------------

        --== Initialization Complete ==--

   ,,_     -*> Snort! <*-
  o"  )~   Version 2.8.0.1 (Build 72)  
   ''''    By Martin Roesch & The Snort Team: [http://www.snort.org/team.html](http://www.snort.org/team.html)
           (C) Copyright 1998-2007 Sourcefire Inc., et al.
           Using PCRE version: 7.4 2007-09-21

           Rules Engine: SF_SNORT_DETECTION_ENGINE  Version 1.6  <Build 11>
           Preprocessor Object: SF_SSH  Version 1.0  <Build 1>
           Preprocessor Object: SF_SMTP  Version 1.0  <Build 7>
           Preprocessor Object: SF_DCERPC  Version 1.0  <Build 4>
           Preprocessor Object: SF_FTPTELNET  Version 1.0  <Build 10>
           Preprocessor Object: SF_DNS  Version 1.0  <Build 2>
           Preprocessor Object: SF_Dynamic_Example_Preprocessor  Version 1.0  <Build 1>
Not Using PCAP_FRAMES
*** Caught Usr-Signal: 'Rotate Stats'
Performance log file '' not open


when i restart apache

> administrator@administrator-desktop:~$ /etc/init.d/apache2 restart
open: Permission denied
 * Restarting web server apache2                                               apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (pid 5877?) not running


now, apache finds my local ip as 127.0.1.1 instead of 192.168.1.100 like snort probably does. I didn't want to go into any config files until I heard some opinions... so i hope some one can help.

after 5 minutes this is what BASE shows me
Traffic Profile by Protocol
TCP (0%)	
 
UDP (0%)	
 
ICMP (0%)	
 
Portscan Traffic (0%)

so 0 traffic.. if i stop snort

Run time prior to being shutdown was 390.534067 seconds
===============================================================================
Packet Wire Totals:
   Received:         1244
   Analyzed:         1243 (99.920%)
    Dropped:            0 (0.000%)
Outstanding:            1 (0.080%)
===============================================================================
Breakdown by protocol (includes rebuilt packets):
      ETH: 1243       (100.000%)
  ETHdisc: 0          (0.000%)
     VLAN: 0          (0.000%)
     IPV6: 0          (0.000%)
  IP6 EXT: 0          (0.000%)
  IP6opts: 0          (0.000%)
  IP6disc: 0          (0.000%)
      IP4: 1243       (100.000%)
  IP4disc: 0          (0.000%)
    TCP 6: 0          (0.000%)
    UDP 6: 0          (0.000%)
    ICMP6: 0          (0.000%)
  ICMP-IP: 0          (0.000%)
      TCP: 1198       (96.380%)
      UDP: 45         (3.620%)
     ICMP: 0          (0.000%)
  TCPdisc: 0          (0.000%)
  UDPdisc: 0          (0.000%)
  ICMPdis: 0          (0.000%)
     FRAG: 0          (0.000%)
   FRAG 6: 0          (0.000%)
      ARP: 0          (0.000%)
    EAPOL: 0          (0.000%)
  ETHLOOP: 0          (0.000%)
      IPX: 0          (0.000%)
    OTHER: 0          (0.000%)
  DISCARD: 0          (0.000%)
InvChkSum: 186        (14.964%)
  Upconvt: 0          (0.000%)
  Up fail: 0          (0.000%)
   S5 G 1: 0          (0.000%)
   S5 G 2: 0          (0.000%)
    Total: 1243      
===============================================================================
Action Stats:
ALERTS: 0
LOGGED: 0
PASSED: 0
===============================================================================
Frag3 statistics:
        Total Fragments: 0
      Frags Reassembled: 0
               Discards: 0
          Memory Faults: 0
               Timeouts: 0
               Overlaps: 0
              Anomalies: 0
                 Alerts: 0
     FragTrackers Added: 0
    FragTrackers Dumped: 0
FragTrackers Auto Freed: 0
    Frag Nodes Inserted: 0
     Frag Nodes Deleted: 0
===============================================================================
Stream5 statistics:
            Total sessions: 45
              TCP sessions: 45
              UDP sessions: 0
             ICMP sessions: 0
                TCP Prunes: 0
                UDP Prunes: 0
               ICMP Prunes: 0
TCP StreamTrackers Created: 49
TCP StreamTrackers Deleted: 49
              TCP Timeouts: 4
              TCP Overlaps: 0
       TCP Segments Queued: 0
     TCP Segments Released: 0
       TCP Rebuilt Packets: 0
         TCP Segments Used: 0
              TCP Discards: 39
      UDP Sessions Created: 0
      UDP Sessions Deleted: 0
              UDP Timeouts: 0
              UDP Discards: 0
                    Events: 0
===============================================================================
HTTP Inspect - encodings (Note: stream-reassembled packets included):
    POST methods:                   0         
    GET methods:                    0         
    Post parameters extracted:      0         
    Unicode:                        0         
    Double unicode:                 0         
    Non-ASCII representable:        0         
    Base 36:                        0         
    Directory traversals:           0         
    Extra slashes ("//"):           0         
    Self-referencing paths ("./"):  0         
    Total packets processed:        376       
===============================================================================
database: Closing connection to database "snort"
Snort exiting
administrator@administrator-desktop:~$

---

### Post by g0tb00st on 2008-01-23
having the same issues here, snort, base, apache2 seems to be working fine using that same install guide that you followed, however i'm not seeing any activity being logged at all.....

can anyone help?

---

### Post by g0tb00st on 2008-01-30
for anyone reading this....the how-to instructions are in fact correct. the reason why i wasn't seeing any snort traffic was just due to my own inexperience.

if you'd like to check and make sure that snort is running correctly, use the following command "snort -c /etc/snort/snort.conf -i eth0 -v" this will show all traffic coming and going from your system.

the reason why all the traffic isn't being logged into BASE is because snort will only record specific types of traffic according to your rule set. PINGS, etc will not be logged.

if you'd like to trigger some alerts, i'd suggest using nmap to scan your system using the following "nmap -sV -O hostname" that should wake snort up and log things into mysql and BASE.

---

### Post by aredoble on 2008-04-19
Hi guys, Im trying to install snort 2.8.1 and mysql in ubuntu 7.10. I run ./configure using this

./configure --with-mysql=/usr/bin/mysql --with-mysql-includes=/usr/include/mysql/

yes, it was able to identify mysql as the database being used...everything workes fine when i ran make and make install.

but when i run snort using this command 

snort -i eth1 -T -c /usr/local/etc/snort/snort.conf

I get this error:

[COLOR="Red"]Decoding LoopBack on interface eth1
database: compiled support for ( )
database: configured to use mysql
database: 'mysql' support is not compiled into this build of snort

ERROR: If this build of snort was obtained as a binary distribution (e.g., rpm,
or Windows), then check for alternate builds that contains the necessary
'mysql' support.

If this build of snort was compiled by you, then re-run the
the ./configure script using the '--with-mysql' switch.
For non-standard installations of a database, the '--with-mysql=DIR'
syntax may need to be used to specify the base directory of the DB install.

See the database documentation for cursory details (doc/README.database).
and the URL to the most recent database plugin documentation.
Fatal Error, Quitting..[/COLOR]


Can anyone tell me what I did wrong? by the way, mysql was installed using the LAMP installation of ubuntu server.

thanks

---

