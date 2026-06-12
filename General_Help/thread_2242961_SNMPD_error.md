---
title: "SNMPD error"
date: 2014-09-05
forum: General Help
---

### Post by vavoem3 on 2014-09-05
On my ubuntu 14.04 i try to monitor some process actively
I receive the following errors when i run

```
sudo snmpd -f -Le localhost:161
```

 Line 22 is where it says default monitors = yes in snmpd.conf

i've installed snmp-mib-downloader

any ideas?



```
payload OID: prNames
/etc/snmp/snmpd.conf: line 22: Error: unknown payload OID
Unknown payload OID: prNames
/etc/snmp/snmpd.conf: line 22: Error: Unknown payload OID
payload OID: prErrMessage
/etc/snmp/snmpd.conf: line 22: Error: unknown payload OID
Unknown payload OID: prErrMessage
/etc/snmp/snmpd.conf: line 22: Error: Unknown payload OID
trigger OID: prErrorFlag
/etc/snmp/snmpd.conf: line 22: Error: unknown monitor OID
payload OID: memErrorName
/etc/snmp/snmpd.conf: line 22: Error: unknown payload OID
Unknown payload OID: memErrorName
/etc/snmp/snmpd.conf: line 22: Error: Unknown payload OID
payload OID: memSwapErrorMsg
/etc/snmp/snmpd.conf: line 22: Error: unknown payload OID
Unknown payload OID: memSwapErrorMsg
/etc/snmp/snmpd.conf: line 22: Error: Unknown payload OID
trigger OID: memSwapError
/etc/snmp/snmpd.conf: line 22: Error: unknown monitor OID
payload OID: extNames
/etc/snmp/snmpd.conf: line 22: Error: unknown payload OID
Unknown payload OID: extNames
/etc/snmp/snmpd.conf: line 22: Error: Unknown payload OID
payload OID: extOutput
/etc/snmp/snmpd.conf: line 22: Error: unknown payload OID
Unknown payload OID: extOutput
/etc/snmp/snmpd.conf: line 22: Error: Unknown payload OID
trigger OID: extResult
/etc/snmp/snmpd.conf: line 22: Error: unknown monitor OID
payload OID: dskPath
/etc/snmp/snmpd.conf: line 22: Error: unknown payload OID
Unknown payload OID: dskPath
/etc/snmp/snmpd.conf: line 22: Error: Unknown payload OID
payload OID: dskErrorMsg
/etc/snmp/snmpd.conf: line 22: Error: unknown payload OID
Unknown payload OID: dskErrorMsg
/etc/snmp/snmpd.conf: line 22: Error: Unknown payload OID
trigger OID: dskErrorFlag
/etc/snmp/snmpd.conf: line 22: Error: unknown monitor OID
payload OID: laNames
/etc/snmp/snmpd.conf: line 22: Error: unknown payload OID
Unknown payload OID: laNames
/etc/snmp/snmpd.conf: line 22: Error: Unknown payload OID
payload OID: laErrMessage
/etc/snmp/snmpd.conf: line 22: Error: unknown payload OID
Unknown payload OID: laErrMessage
/etc/snmp/snmpd.conf: line 22: Error: Unknown payload OID
trigger OID: laErrorFlag
/etc/snmp/snmpd.conf: line 22: Error: unknown monitor OID
payload OID: fileName
/etc/snmp/snmpd.conf: line 22: Error: unknown payload OID
Unknown payload OID: fileName
/etc/snmp/snmpd.conf: line 22: Error: Unknown payload OID
payload OID: fileErrorMsg
/etc/snmp/snmpd.conf: line 22: Error: unknown payload OID
Unknown payload OID: fileErrorMsg
/etc/snmp/snmpd.conf: line 22: Error: Unknown payload OID
trigger OID: fileErrorFlag
/etc/snmp/snmpd.conf: line 22: Error: unknown monitor OID
payload OID: snmperrErrMessage
/etc/snmp/snmpd.conf: line 22: Error: unknown payload OID
Unknown payload OID: snmperrErrMessage
/etc/snmp/snmpd.conf: line 22: Error: Unknown payload OID
trigger OID: snmperrErrorFlag
/etc/snmp/snmpd.conf: line 22: Error: unknown monitor OID
Turning on AgentX master support.
net-snmp: 33 error(s) in config file(s)
NET-SNMP version 5.7.2
/etc/snmp/snmpd.conf: line 22: Error: unknown payload OID
Unknown payload OID: prNames



```

this is the relevant portion of snmpd.conf
 ```


view   systemonly  included   .1.3.6.1.2.1.1
view   systemonly  included   .1.3.6.1.2.1.25.1
rocommunity Nopenotgoingtotellyou  192.168.0.0/16
createUser disman       MD5 veryheavilyencryptedpassword
rouser disman   auth
agentSecName disman
sysLocation    KWHMD6
sysContact     IT operations <it.ops@somecompany.com>
sysServices    72
proc  mountd
proc  ntalkd    4
proc  sendmail 10 1
proc  apache2
#monitor -r 10 -o prNames.4 -o prErrMessage.4 "Apache2 not running" prErrorFlag.4 != 0
disk       /     10000
disk       /var  5%
includeAllDisks  10%
load   12 10 5
trap2sink     someip thisissecret
iquerySecName   disman
rouser  disman
defaultMonitors          yes
linkUpDownNotifications  yes
# extend    test1   /bin/echo  Hello, world!
# extend-sh test2   echo Hello, world! ; echo Hi there ; exit 35
 master          agentx

```

this is /etc/default/snmpd

```

 This file controls the activity of snmpd and snmptrapd


# Don't load any MIBs by default.
# You might comment this lines once you have the MIBs downloaded.
export MIBDIRS=/usr/share/snmp/mibs/


# snmpd control (yes means start daemon).
SNMPDRUN=yes


# snmpd options (use syslog, close stdin/out/err).
SNMPDOPTS='-Lsd -Lf /dev/null -u snmp -g snmp -I -smux,mteTrigger,mteTriggerConf -p /var/run/snmpd.pid'


# snmptrapd control (yes means start daemon).  As of net-snmp version
# 5.0, master agentx support must be enabled in snmpd before snmptrapd
# can be run.  See snmpd.conf(5) for how to do this.
TRAPDRUN=no


# snmptrapd options (use syslog).
TRAPDOPTS='-Lsd -p /var/run/snmptrapd.pid'

```

---

### Post by texpat on 2014-09-10
Does this thread help?: [http://ubuntuforums.org/showthread.php?t=2019175](http://ubuntuforums.org/showthread.php?t=2019175)

---

