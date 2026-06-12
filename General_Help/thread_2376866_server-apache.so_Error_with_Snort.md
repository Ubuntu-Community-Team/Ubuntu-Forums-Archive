---
title: "server-apache.so Error with Snort"
date: 2017-11-06
forum: General Help
---

### Post by h.hittini on 2017-11-06
Good Day Everyone,

I'm trying to run snort, compilation was successful and it worked fine with test rule.
But after downloading the community rules I'm not able to start it
I'm getting [U][I]server-apache.so: ELF file OS ABI invalid Fatal Error
[/I][/U]I have used the official installation guide "Snort 2.9.9.x on Ubuntu 14 -16" by Noah Dietrich available here [https://www.snort.org/documents#OfficialDocumentation](https://www.snort.org/documents#OfficialDocumentation)

```

hosam@Sniff:~$ sudo snort -T -c /etc/snort/snort.conf -i enp0s8
Running in Test mode
 
        --== Initializing Snort ==--
Initializing Output Plugins!
Initializing Preprocessors!
Initializing Plug-ins!
Parsing Rules file "/etc/snort/snort.conf"
PortVar 'HTTP_PORTS' defined :  [ 80:81 311 383 591 593 901 1220 1414 1741 1830 2301 2381 2809 3037 3128 3702 4343 4848 5250 6988 7000:7001 7144:7145 7510 7777 7779 8000 8008 8014 8028 8080 8085 8088 8090 8118 8123 8180:8181 8243 8280 8300 8800 8888 8899 9000 9060 9080 9090:9091 9443 9999 11371 34443:34444 41080 50002 55555 ]
PortVar 'SHELLCODE_PORTS' defined :  [ 0:79 81:65535 ]
PortVar 'ORACLE_PORTS' defined :  [ 1024:65535 ]
PortVar 'SSH_PORTS' defined :  [ 22 ]
PortVar 'FTP_PORTS' defined :  [ 21 2100 3535 ]
PortVar 'SIP_PORTS' defined :  [ 5060:5061 5600 ]
PortVar 'FILE_DATA_PORTS' defined :  [ 80:81 110 143 311 383 591 593 901 1220 1414 1741 1830 2301 2381 2809 3037 3128 3702 4343 4848 5250 6988 7000:7001 7144:7145 7510 7777 7779 8000 8008 8014 8028 8080 8085 8088 8090 8118 8123 8180:8181 8243 8280 8300 8800 8888 8899 9000 9060 9080 9090:9091 9443 9999 11371 34443:34444 41080 50002 55555 ]
PortVar 'GTP_PORTS' defined :  [ 2123 2152 3386 ]
Detection:
   Search-Method = AC-Full-Q
    Split Any/Any group = enabled
    Search-Method-Optimizations = enabled
    Maximum pattern length = 20
Tagged Packet Limit: 256
Loading dynamic engine /usr/local/lib/snort_dynamicengine/libsf_engine.so... done
Loading all dynamic detection libs from /usr/local/lib/snort_dynamicrules...
  Loading dynamic detection library /usr/local/lib/snort_dynamicrules/server-apache.so... ERROR: Failed to load /usr/local/lib/snort_dynamicrules/server-apache.so: /usr/local/lib/snort_dynamicrules/server-apache.so: ELF file OS ABI invalid
Fatal Error, Quitting..

```

Please find below versions and system info
```

hosam@Sniff:~$ uname -a
Linux Sniff 4.4.0-98-generic #121-Ubuntu SMP Tue Oct 10 14:24:03 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
 
hosam@Sniff:~$ cat /proc/version
Linux version 4.4.0-98-generic (buildd@lcy01-03) (gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.4) ) #121-Ubuntu SMP Tue Oct 10 14:24:03 UTC 2017

hosam@Sniff:~$ snort -V
 
   ,,_     -*> Snort! <*-
  o"  )~   Version 2.9.11 GRE (Build 125)
   ''''    By Martin Roesch & The Snort Team: [http://www.snort.org/contact#team](http://www.snort.org/contact#team)
           Copyright (C) 2014-2017 Cisco and/or its affiliates. All rights reserved.
           Copyright (C) 1998-2013 Sourcefire, Inc., et al.
           Using libpcap version 1.7.4
           Using PCRE version: 8.38 2015-11-23
           Using ZLIB version: 1.2.8
 
hosam@Sniff:~/snort_src/daq-2.2.2$ ./configure
[&#8230;]
Build AFPacket DAQ module.. : yes
Build Dump DAQ module...... : yes
Build IPFW DAQ module...... : yes
Build IPQ DAQ module....... : no
Build NFQ DAQ module....... : no
Build PCAP DAQ module...... : yes
Build netmap DAQ module.... : no
 
hosam@Sniff:~$ /usr/local/bin/pulledpork.pl -V
PulledPork v0.7.3 - Making signature updates great again!
 
```

Is there any way to upgrade the shared object?
Thank you

Hosam,

---

### Post by h.hittini on 2017-11-12
Any thoughts on that please?

---

