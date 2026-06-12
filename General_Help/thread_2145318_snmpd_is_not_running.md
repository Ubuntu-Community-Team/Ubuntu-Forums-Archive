---
title: "snmpd is not running"
date: 2013-05-15
forum: General Help
---

### Post by Ardok on 2013-05-15
I've installed and reinstalled snmp and snmpd.
but i cant get snmpd to get started.

```
# /etc/init.d/snmpd restart
 * Restarting network management services:               
# /etc/init.d/snmpd status
 * snmpd is not running
```

Looked to the firewall status:
```
# ufw status
Status: inactive
```

/etc/snmp/snmpd.conf
```
cat /etc/snmp/snmpd.conf | egrep -v "^\s*(#|$)"
agentAddress  udp:127.0.0.1:161
view   systemonly  included   .1.3.6.1.2.1.1
view   systemonly  included   .1.3.6.1.2.1.25.1
 rocommunity public  default    -V systemonly
 rouser   authOnlyUser
sysLocation    Sitting on the Dock of the Bay
sysContact     Me <me@example.org>
sysServices    72
proc  mountd
proc  ntalkd    4
proc  sendmail 10 1
disk       /     10000
disk       /var  5%
includeAllDisks  10%
load   12 10 5
 trapsink     localhost public
iquerySecName   internalUser
rouser          internalUser
defaultMonitors          yes
linkUpDownNotifications  yes
 extend    test1   /bin/echo  Hello, world!
 extend-sh test2   echo Hello, world! ; echo Hi there ; exit 35
 master          agentx
```

/etc/default/snmpd
```
cat /etc/default/snmpd | egrep -v "^\s*(#|$)"
export MIBS=
SNMPDRUN=yes
SNMPDOPTS='-Lsd -Lf /dev/null -u snmp -g snmp -I -smux -p /var/run/snmpd.pid'
TRAPDRUN=no
TRAPDOPTS='-Lsd -p /var/run/snmptrapd.pid'
SNMPDCOMPAT=yes
```

again to restart the service but cant get it to work. Can someone help me to get it to work?

---

### Post by sanderj on 2013-05-15
How do you know it's not running?

Did it run *before* you changed the config?


FWIW: it works for me. See below.

```
sander@flappie:~$ sagi snmpd
[sudo] password for sander: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  snmpd
0 upgraded, 1 newly installed, 0 to remove and 13 not upgraded.
Need to get 76.8 kB of archives.
After this operation, 268 kB of additional disk space will be used.
Get:1 [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) raring/main snmpd amd64 5.4.3~dfsg-2.7ubuntu1 [76.8 kB]
Fetched 76.8 kB in 0s (604 kB/s) 
Preconfiguring packages ...
Selecting previously unselected package snmpd.
(Reading database ... 250253 files and directories currently installed.)
Unpacking snmpd (from .../snmpd_5.4.3~dfsg-2.7ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up snmpd (5.4.3~dfsg-2.7ubuntu1) ...
update-rc.d: warning: snmpd stop runlevel arguments (1) do not match LSB Default-Stop values (0 1 6)
 * Starting network management services:                                                                                                       Processing triggers for ureadahead ...


sander@flappie:~$ ps -ef | grep -i snmp
snmp     19452     1  0 19:23 ?        00:00:00 /usr/sbin/snmpd -Lsd -Lf /dev/null -u snmp -g snmp -I -smux -p /var/run/snmpd.pid
sander   19480 10676  0 19:23 pts/5    00:00:00 grep --color=auto -i snmp
sander@flappie:~$


sander@flappie:~$ snmpwalk -c public -v 2c localhost 
iso.3.6.1.2.1.1.1.0 = STRING: "Linux flappie 3.8.0-19-generic #30-Ubuntu SMP Wed May 1 16:35:23 UTC 2013 x86_64"
iso.3.6.1.2.1.1.2.0 = OID: iso.3.6.1.4.1.8072.3.2.10
iso.3.6.1.2.1.1.3.0 = Timeticks: (142571) 0:23:45.71
iso.3.6.1.2.1.1.4.0 = STRING: "Me <me@example.org>"
iso.3.6.1.2.1.1.5.0 = STRING: "flappie"
iso.3.6.1.2.1.1.6.0 = STRING: "Sitting on the Dock of the Bay"
iso.3.6.1.2.1.1.7.0 = INTEGER: 72
iso.3.6.1.2.1.1.8.0 = Timeticks: (5) 0:00:00.05
iso.3.6.1.2.1.1.9.1.2.1 = OID: iso.3.6.1.6.3.10.3.1.1
iso.3.6.1.2.1.1.9.1.2.2 = OID: iso.3.6.1.6.3.11.3.1.1
iso.3.6.1.2.1.1.9.1.2.3 = OID: iso.3.6.1.6.3.15.2.1.1
iso.3.6.1.2.1.1.9.1.2.4 = OID: iso.3.6.1.6.3.1
iso.3.6.1.2.1.1.9.1.2.5 = OID: iso.3.6.1.2.1.49
iso.3.6.1.2.1.1.9.1.2.6 = OID: iso.3.6.1.2.1.4
iso.3.6.1.2.1.1.9.1.2.7 = OID: iso.3.6.1.2.1.50
iso.3.6.1.2.1.1.9.1.2.8 = OID: iso.3.6.1.6.3.16.2.2.1
iso.3.6.1.2.1.1.9.1.3.1 = STRING: "The SNMP Management Architecture MIB."
iso.3.6.1.2.1.1.9.1.3.2 = STRING: "The MIB for Message Processing and Dispatching."
iso.3.6.1.2.1.1.9.1.3.3 = STRING: "The management information definitions for the SNMP User-based Security Model."
iso.3.6.1.2.1.1.9.1.3.4 = STRING: "The MIB module for SNMPv2 entities"
iso.3.6.1.2.1.1.9.1.3.5 = STRING: "The MIB module for managing TCP implementations"
iso.3.6.1.2.1.1.9.1.3.6 = STRING: "The MIB module for managing IP and ICMP implementations"
iso.3.6.1.2.1.1.9.1.3.7 = STRING: "The MIB module for managing UDP implementations"
iso.3.6.1.2.1.1.9.1.3.8 = STRING: "View-based Access Control Model for SNMP."
iso.3.6.1.2.1.1.9.1.4.1 = Timeticks: (5) 0:00:00.05
iso.3.6.1.2.1.1.9.1.4.2 = Timeticks: (5) 0:00:00.05
iso.3.6.1.2.1.1.9.1.4.3 = Timeticks: (5) 0:00:00.05
iso.3.6.1.2.1.1.9.1.4.4 = Timeticks: (5) 0:00:00.05
iso.3.6.1.2.1.1.9.1.4.5 = Timeticks: (5) 0:00:00.05
iso.3.6.1.2.1.1.9.1.4.6 = Timeticks: (5) 0:00:00.05
iso.3.6.1.2.1.1.9.1.4.7 = Timeticks: (5) 0:00:00.05
iso.3.6.1.2.1.1.9.1.4.8 = Timeticks: (5) 0:00:00.05
iso.3.6.1.2.1.25.1.1.0 = Timeticks: (27624497) 3 days, 4:44:04.97
iso.3.6.1.2.1.25.1.2.0 = Hex-STRING: 07 DD 05 0F 13 2F 18 00 2B 02 00 
iso.3.6.1.2.1.25.1.3.0 = INTEGER: 1536
iso.3.6.1.2.1.25.1.4.0 = STRING: "BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=534812aa-a5c9-4a36-9fc2-ac1bcdfa2e90 ro quiet splash vt.handoff=7
"
iso.3.6.1.2.1.25.1.5.0 = Gauge32: 6
iso.3.6.1.2.1.25.1.6.0 = Gauge32: 277
iso.3.6.1.2.1.25.1.7.0 = INTEGER: 0
iso.3.6.1.2.1.25.1.7.0 = No more variables left in this MIB View (It is past the end of the MIB tree)
sander@flappie:~$ 



```

---

### Post by Ardok on 2013-05-15
```
ps -ef | grep -i snmp
root      6530  5216  0 19:58 pts/0    00:00:00 grep --color=auto -i snmp


snmpwalk -c public -v 2c localhost 

Cannot adopt OID in UCD-DISKIO-MIB: ucdDiskIOMIB ::= { ucdExperimental 15 }
Cannot adopt OID in UCD-DLMOD-MIB: ucdDlmodMIB ::= { ucdExperimental 14 }
Cannot adopt OID in UCD-SNMP-MIB: dskEntry ::= { dskTable 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: netSnmpAgentMIB ::= { netSnmpModuleIDs 2 }
Cannot adopt OID in LM-SENSORS-MIB: lmFanSensorsValue ::= { lmFanSensorsEntry 3 }
Cannot adopt OID in LM-SENSORS-MIB: lmFanSensorsDevice ::= { lmFanSensorsEntry 2 }
Cannot adopt OID in LM-SENSORS-MIB: lmFanSensorsIndex ::= { lmFanSensorsEntry 1 }
Cannot adopt OID in LM-SENSORS-MIB: lmTempSensorsValue ::= { lmTempSensorsEntry 3 }
Cannot adopt OID in LM-SENSORS-MIB: lmTempSensorsDevice ::= { lmTempSensorsEntry 2 }
Cannot adopt OID in LM-SENSORS-MIB: lmTempSensorsIndex ::= { lmTempSensorsEntry 1 }
Cannot adopt OID in UCD-SNMP-MIB: logMatchTable ::= { logMatch 2 }
Cannot adopt OID in UCD-SNMP-MIB: logMatchMaxEntries ::= { logMatch 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsLoggingEntry ::= { nsLoggingTable 1 }
Cannot adopt OID in UCD-SNMP-MIB: fileErrorMsg ::= { fileEntry 101 }
Cannot adopt OID in UCD-SNMP-MIB: fileErrorFlag ::= { fileEntry 100 }
Cannot adopt OID in UCD-SNMP-MIB: fileMax ::= { fileEntry 4 }
Cannot adopt OID in UCD-SNMP-MIB: fileSize ::= { fileEntry 3 }
Cannot adopt OID in UCD-SNMP-MIB: fileName ::= { fileEntry 2 }
Cannot adopt OID in UCD-SNMP-MIB: fileIndex ::= { fileEntry 1 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendOutput2Table ::= { nsExtendObjects 4 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendOutput1Table ::= { nsExtendObjects 3 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendConfigTable ::= { nsExtendObjects 2 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendNumEntries ::= { nsExtendObjects 1 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendOutput1Entry ::= { nsExtendOutput1Table 1 }
Cannot adopt OID in UCD-SNMP-MIB: ssRawSwapOut ::= { systemStats 63 }
Cannot adopt OID in UCD-SNMP-MIB: ssRawSwapIn ::= { systemStats 62 }
Cannot adopt OID in UCD-SNMP-MIB: ssCpuRawSoftIRQ ::= { systemStats 61 }
Cannot adopt OID in UCD-SNMP-MIB: ssRawContexts ::= { systemStats 60 }
Cannot adopt OID in UCD-SNMP-MIB: ssRawInterrupts ::= { systemStats 59 }
Cannot adopt OID in UCD-SNMP-MIB: ssIORawReceived ::= { systemStats 58 }
Cannot adopt OID in UCD-SNMP-MIB: ssIORawSent ::= { systemStats 57 }
Cannot adopt OID in UCD-SNMP-MIB: ssCpuRawInterrupt ::= { systemStats 56 }
Cannot adopt OID in UCD-SNMP-MIB: ssCpuRawKernel ::= { systemStats 55 }
Cannot adopt OID in UCD-SNMP-MIB: ssCpuRawWait ::= { systemStats 54 }
Cannot adopt OID in UCD-SNMP-MIB: ssCpuRawIdle ::= { systemStats 53 }
Cannot adopt OID in UCD-SNMP-MIB: ssCpuRawSystem ::= { systemStats 52 }
Cannot adopt OID in UCD-SNMP-MIB: ssCpuRawNice ::= { systemStats 51 }
Cannot adopt OID in UCD-SNMP-MIB: ssCpuRawUser ::= { systemStats 50 }
Cannot adopt OID in UCD-SNMP-MIB: ssCpuIdle ::= { systemStats 11 }
Cannot adopt OID in UCD-SNMP-MIB: ssCpuSystem ::= { systemStats 10 }
Cannot adopt OID in UCD-SNMP-MIB: ssCpuUser ::= { systemStats 9 }
Cannot adopt OID in UCD-SNMP-MIB: ssSysContext ::= { systemStats 8 }
Cannot adopt OID in UCD-SNMP-MIB: ssSysInterrupts ::= { systemStats 7 }
Cannot adopt OID in UCD-SNMP-MIB: ssIOReceive ::= { systemStats 6 }
Cannot adopt OID in UCD-SNMP-MIB: ssIOSent ::= { systemStats 5 }
Cannot adopt OID in UCD-SNMP-MIB: ssSwapOut ::= { systemStats 4 }
Cannot adopt OID in UCD-SNMP-MIB: ssSwapIn ::= { systemStats 3 }
Cannot adopt OID in UCD-SNMP-MIB: ssErrorName ::= { systemStats 2 }
Cannot adopt OID in UCD-SNMP-MIB: ssIndex ::= { systemStats 1 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendOutput2Entry ::= { nsExtendOutput2Table 1 }
Cannot adopt OID in UCD-SNMP-MIB: laEntry ::= { laTable 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsCacheTable ::= { nsCache 3 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsCacheEnabled ::= { nsCache 2 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsCacheDefaultTimeout ::= { nsCache 1 }
Cannot adopt OID in UCD-SNMP-MIB: logMatchEntry ::= { logMatchTable 1 }
Cannot adopt OID in UCD-SNMP-MIB: extEntry ::= { extTable 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsConfigLogging ::= { nsConfiguration 2 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsConfigDebug ::= { nsConfiguration 1 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpExampleString ::= { netSnmpExampleScalars 3 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpExampleSleeper ::= { netSnmpExampleScalars 2 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpExampleInteger ::= { netSnmpExampleScalars 1 }
Cannot adopt OID in LM-SENSORS-MIB: lmVoltSensorsValue ::= { lmVoltSensorsEntry 3 }
Cannot adopt OID in LM-SENSORS-MIB: lmVoltSensorsDevice ::= { lmVoltSensorsEntry 2 }
Cannot adopt OID in LM-SENSORS-MIB: lmVoltSensorsIndex ::= { lmVoltSensorsEntry 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsCacheEntry ::= { nsCacheTable 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsDebugTokenTable ::= { nsConfigDebug 4 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsDebugDumpPdu ::= { nsConfigDebug 3 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsDebugOutputAll ::= { nsConfigDebug 2 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsDebugEnabled ::= { nsConfigDebug 1 }
Cannot adopt OID in UCD-DEMO-MIB: ucdDemoPassphrase ::= { ucdDemoPublic 4 }
Cannot adopt OID in UCD-DEMO-MIB: ucdDemoUserList ::= { ucdDemoPublic 3 }
Cannot adopt OID in UCD-DEMO-MIB: ucdDemoPublicString ::= { ucdDemoPublic 2 }
Cannot adopt OID in UCD-DEMO-MIB: ucdDemoResetKeys ::= { ucdDemoPublic 1 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpExampleHeartbeatName ::= { netSnmpExampleNotificationObjects 2 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpExampleHeartbeatRate ::= { netSnmpExampleNotificationObjects 1 }
Cannot adopt OID in NET-SNMP-PASS-MIB: netSnmpPassExamples ::= { netSnmpExamples 255 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpExampleNotifications ::= { netSnmpExamples 3 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpExampleTables ::= { netSnmpExamples 2 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpExampleScalars ::= { netSnmpExamples 1 }
Cannot adopt OID in NET-SNMP-VACM-MIB: nsVacmAccessTable ::= { netSnmpVacmMIB 1 }
Cannot adopt OID in UCD-SNMP-MIB: ucdShutdown ::= { ucdTraps 2 }
Cannot adopt OID in UCD-SNMP-MIB: ucdStart ::= { ucdTraps 1 }
Cannot adopt OID in LM-SENSORS-MIB: lmMiscSensorsTable ::= { lmSensors 5 }
Cannot adopt OID in LM-SENSORS-MIB: lmVoltSensorsTable ::= { lmSensors 4 }
Cannot adopt OID in LM-SENSORS-MIB: lmFanSensorsTable ::= { lmSensors 3 }
Cannot adopt OID in LM-SENSORS-MIB: lmTempSensorsTable ::= { lmSensors 2 }
Cannot adopt OID in LM-SENSORS-MIB: lmSensorsMIB ::= { lmSensors 1 }
Cannot adopt OID in UCD-SNMP-MIB: mrEntry ::= { mrTable 1 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendConfigEntry ::= { nsExtendConfigTable 1 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpHostRowStatus ::= { netSnmpHostsEntry 5 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpHostStorage ::= { netSnmpHostsEntry 4 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpHostAddress ::= { netSnmpHostsEntry 3 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpHostAddressType ::= { netSnmpHostsEntry 2 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpHostName ::= { netSnmpHostsEntry 1 }
Cannot adopt OID in UCD-SNMP-MIB: prEntry ::= { prTable 1 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpExampleNotification ::= { netSnmpExampleNotifications 1 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpExampleNotificationObjects ::= { netSnmpExampleNotifications 2 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpExampleNotificationPrefix ::= { netSnmpExampleNotifications 0 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpHostsTable ::= { netSnmpExampleTables 2 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpIETFWGTable ::= { netSnmpExampleTables 1 }
Cannot adopt OID in NET-SNMP-PASS-MIB: netSnmpPassOID ::= { netSnmpPassEntry 3 }
Cannot adopt OID in NET-SNMP-PASS-MIB: netSnmpPassInteger ::= { netSnmpPassEntry 2 }
Cannot adopt OID in NET-SNMP-PASS-MIB: netSnmpPassIndex ::= { netSnmpPassEntry 1 }
Cannot adopt OID in NET-SNMP-VACM-MIB: netSnmpVacmMIB ::= { netSnmpObjects 9 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsVersion ::= { netSnmpObjects 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsMibRegistry ::= { netSnmpObjects 2 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsExtensions ::= { netSnmpObjects 3 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsDLMod ::= { netSnmpObjects 4 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsCache ::= { netSnmpObjects 5 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsErrorHistory ::= { netSnmpObjects 6 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsConfiguration ::= { netSnmpObjects 7 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsTransactions ::= { netSnmpObjects 8 }
Cannot adopt OID in UCD-DEMO-MIB: ucdDemoMIB ::= { ucdavis 14 }
Cannot adopt OID in UCD-SNMP-MIB: logMatch ::= { ucdavis 16 }
Cannot adopt OID in UCD-SNMP-MIB: fileTable ::= { ucdavis 15 }
Cannot adopt OID in UCD-SNMP-MIB: ucdTraps ::= { ucdavis 251 }
Cannot adopt OID in UCD-SNMP-MIB: systemStats ::= { ucdavis 11 }
Cannot adopt OID in UCD-SNMP-MIB: mrTable ::= { ucdavis 102 }
Cannot adopt OID in UCD-SNMP-MIB: snmperrs ::= { ucdavis 101 }
Cannot adopt OID in UCD-SNMP-MIB: version ::= { ucdavis 100 }
Cannot adopt OID in UCD-SNMP-MIB: laTable ::= { ucdavis 10 }
Cannot adopt OID in UCD-SNMP-MIB: dskTable ::= { ucdavis 9 }
Cannot adopt OID in UCD-SNMP-MIB: memory ::= { ucdavis 4 }
Cannot adopt OID in UCD-SNMP-MIB: extTable ::= { ucdavis 8 }
Cannot adopt OID in UCD-SNMP-MIB: prTable ::= { ucdavis 2 }
Cannot adopt OID in UCD-SNMP-MIB: ucdSnmpAgent ::= { ucdavis 250 }
Cannot adopt OID in UCD-SNMP-MIB: ucdExperimental ::= { ucdavis 13 }
Cannot adopt OID in UCD-SNMP-MIB: ucdInternal ::= { ucdavis 12 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsModuleEntry ::= { nsModuleTable 1 }
Cannot adopt OID in UCD-SNMP-MIB: dskErrorMsg ::= { dskEntry 101 }
Cannot adopt OID in UCD-SNMP-MIB: dskErrorFlag ::= { dskEntry 100 }
Cannot adopt OID in UCD-SNMP-MIB: dskPercentNode ::= { dskEntry 10 }
Cannot adopt OID in UCD-SNMP-MIB: dskPercent ::= { dskEntry 9 }
Cannot adopt OID in UCD-SNMP-MIB: dskUsed ::= { dskEntry 8 }
Cannot adopt OID in UCD-SNMP-MIB: dskAvail ::= { dskEntry 7 }
Cannot adopt OID in UCD-SNMP-MIB: dskTotal ::= { dskEntry 6 }
Cannot adopt OID in UCD-SNMP-MIB: dskMinPercent ::= { dskEntry 5 }
Cannot adopt OID in UCD-SNMP-MIB: dskMinimum ::= { dskEntry 4 }
Cannot adopt OID in UCD-SNMP-MIB: dskDevice ::= { dskEntry 3 }
Cannot adopt OID in UCD-SNMP-MIB: dskPath ::= { dskEntry 2 }
Cannot adopt OID in UCD-SNMP-MIB: dskIndex ::= { dskEntry 1 }
Cannot adopt OID in UCD-DISKIO-MIB: diskIOTable ::= { ucdDiskIOMIB 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsLoggingGroup ::= { nsConfigGroups 2 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsDebugGroup ::= { nsConfigGroups 1 }
Cannot adopt OID in UCD-SNMP-MIB: snmperrErrMessage ::= { snmperrs 101 }
Cannot adopt OID in UCD-SNMP-MIB: snmperrErrorFlag ::= { snmperrs 100 }
Cannot adopt OID in UCD-SNMP-MIB: snmperrNames ::= { snmperrs 2 }
Cannot adopt OID in UCD-SNMP-MIB: snmperrIndex ::= { snmperrs 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsTransactionTable ::= { nsTransactions 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsLogStatus ::= { nsLoggingEntry 5 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsLogMaxLevel ::= { nsLoggingEntry 4 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsLogType ::= { nsLoggingEntry 3 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsLogToken ::= { nsLoggingEntry 2 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsLogLevel ::= { nsLoggingEntry 1 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendResult ::= { nsExtendOutput1Entry 4 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendOutNumLines ::= { nsExtendOutput1Entry 3 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendOutputFull ::= { nsExtendOutput1Entry 2 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendOutput1Line ::= { nsExtendOutput1Entry 1 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendOutLine ::= { nsExtendOutput2Entry 2 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendLineIndex ::= { nsExtendOutput2Entry 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsNotifyStart ::= { netSnmpNotifications 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsNotifyShutdown ::= { netSnmpNotifications 2 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsNotifyRestart ::= { netSnmpNotifications 3 }
Cannot adopt OID in UCD-SNMP-MIB: laErrMessage ::= { laEntry 101 }
Cannot adopt OID in UCD-SNMP-MIB: laErrorFlag ::= { laEntry 100 }
Cannot adopt OID in UCD-SNMP-MIB: laLoadFloat ::= { laEntry 6 }
Cannot adopt OID in UCD-SNMP-MIB: laLoadInt ::= { laEntry 5 }
Cannot adopt OID in UCD-SNMP-MIB: laConfig ::= { laEntry 4 }
Cannot adopt OID in UCD-SNMP-MIB: laLoad ::= { laEntry 3 }
Cannot adopt OID in UCD-SNMP-MIB: laNames ::= { laEntry 2 }
Cannot adopt OID in UCD-SNMP-MIB: laIndex ::= { laEntry 1 }

```

And:
```
/etc/init.d/snmpd status
 * snmpd is not running

```

---

### Post by sanderj on 2013-05-15
Did you answer all my questions ... ?

Anyway:

In one terminal:

```
sudo /usr/sbin/snmpd -f
```

If it keeps running, open another terminal and run:

```
snmpwalk -c public -v 2c localhost
```

---

### Post by Ardok on 2013-05-17
Yes it did work before. I had installed lm-sensors, but removed it again. Sinds then everythings ****** up.

i inserted your command: **sudo /usr/sbin/snmpd -f**
and this is what i get:

```
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsTransactions ::= { netSnmpObjects 8 }
Cannot adopt OID in UCD-DEMO-MIB: ucdDemoMIB ::= { ucdavis 14 }
Cannot adopt OID in UCD-SNMP-MIB: logMatch ::= { ucdavis 16 }
Cannot adopt OID in UCD-SNMP-MIB: fileTable ::= { ucdavis 15 }
Cannot adopt OID in UCD-SNMP-MIB: ucdTraps ::= { ucdavis 251 }
Cannot adopt OID in UCD-SNMP-MIB: systemStats ::= { ucdavis 11 }
Cannot adopt OID in UCD-SNMP-MIB: mrTable ::= { ucdavis 102 }
Cannot adopt OID in UCD-SNMP-MIB: snmperrs ::= { ucdavis 101 }
Cannot adopt OID in UCD-SNMP-MIB: version ::= { ucdavis 100 }
Cannot adopt OID in UCD-SNMP-MIB: laTable ::= { ucdavis 10 }
Cannot adopt OID in UCD-SNMP-MIB: dskTable ::= { ucdavis 9 }
Cannot adopt OID in UCD-SNMP-MIB: memory ::= { ucdavis 4 }
Cannot adopt OID in UCD-SNMP-MIB: extTable ::= { ucdavis 8 }
Cannot adopt OID in UCD-SNMP-MIB: prTable ::= { ucdavis 2 }
Cannot adopt OID in UCD-SNMP-MIB: ucdSnmpAgent ::= { ucdavis 250 }
Cannot adopt OID in UCD-SNMP-MIB: ucdExperimental ::= { ucdavis 13 }
Cannot adopt OID in UCD-SNMP-MIB: ucdInternal ::= { ucdavis 12 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsModuleEntry ::= { nsModuleTable 1 }
Cannot adopt OID in UCD-SNMP-MIB: dskErrorMsg ::= { dskEntry 101 }
Cannot adopt OID in UCD-SNMP-MIB: dskErrorFlag ::= { dskEntry 100 }
Cannot adopt OID in UCD-SNMP-MIB: dskPercentNode ::= { dskEntry 10 }
Cannot adopt OID in UCD-SNMP-MIB: dskPercent ::= { dskEntry 9 }
Cannot adopt OID in UCD-SNMP-MIB: dskUsed ::= { dskEntry 8 }
Cannot adopt OID in UCD-SNMP-MIB: dskAvail ::= { dskEntry 7 }
Cannot adopt OID in UCD-SNMP-MIB: dskTotal ::= { dskEntry 6 }
Cannot adopt OID in UCD-SNMP-MIB: dskMinPercent ::= { dskEntry 5 }
Cannot adopt OID in UCD-SNMP-MIB: dskMinimum ::= { dskEntry 4 }
Cannot adopt OID in UCD-SNMP-MIB: dskDevice ::= { dskEntry 3 }
Cannot adopt OID in UCD-SNMP-MIB: dskPath ::= { dskEntry 2 }
Cannot adopt OID in UCD-SNMP-MIB: dskIndex ::= { dskEntry 1 }
Cannot adopt OID in UCD-DISKIO-MIB: diskIOTable ::= { ucdDiskIOMIB 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsLoggingGroup ::= { nsConfigGroups 2 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsDebugGroup ::= { nsConfigGroups 1 }
Cannot adopt OID in UCD-SNMP-MIB: snmperrErrMessage ::= { snmperrs 101 }
Cannot adopt OID in UCD-SNMP-MIB: snmperrErrorFlag ::= { snmperrs 100 }
Cannot adopt OID in UCD-SNMP-MIB: snmperrNames ::= { snmperrs 2 }
Cannot adopt OID in UCD-SNMP-MIB: snmperrIndex ::= { snmperrs 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsTransactionTable ::= { nsTransactions                                                                              1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsLogStatus ::= { nsLoggingEntry 5 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsLogMaxLevel ::= { nsLoggingEntry 4 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsLogType ::= { nsLoggingEntry 3 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsLogToken ::= { nsLoggingEntry 2 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsLogLevel ::= { nsLoggingEntry 1 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendResult ::= { nsExtendOutput1Ent                                                                             ry 4 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendOutNumLines ::= { nsExtendOutpu                                                                             t1Entry 3 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendOutputFull ::= { nsExtendOutput                                                                             1Entry 2 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendOutput1Line ::= { nsExtendOutpu                                                                             t1Entry 1 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendOutLine ::= { nsExtendOutput2En                                                                             try 2 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendLineIndex ::= { nsExtendOutput2                                                                             Entry 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsNotifyStart ::= { netSnmpNotifications                                                                              1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsNotifyShutdown ::= { netSnmpNotificati                                                                             ons 2 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsNotifyRestart ::= { netSnmpNotificatio                                                                             ns 3 }
Cannot adopt OID in UCD-SNMP-MIB: laErrMessage ::= { laEntry 101 }
Cannot adopt OID in UCD-SNMP-MIB: laErrorFlag ::= { laEntry 100 }
Cannot adopt OID in UCD-SNMP-MIB: laLoadFloat ::= { laEntry 6 }
Cannot adopt OID in UCD-SNMP-MIB: laLoadInt ::= { laEntry 5 }
Cannot adopt OID in UCD-SNMP-MIB: laConfig ::= { laEntry 4 }
Cannot adopt OID in UCD-SNMP-MIB: laLoad ::= { laEntry 3 }
Cannot adopt OID in UCD-SNMP-MIB: laNames ::= { laEntry 2 }
Cannot adopt OID in UCD-SNMP-MIB: laIndex ::= { laEntry 1 }
payload OID: prNames
/etc/snmp/snmpd.conf: line 143: Error: unknown payload OID
Unknown payload OID: prNames
/etc/snmp/snmpd.conf: line 143: Error: Unknown payload OID
payload OID: prErrMessage
/etc/snmp/snmpd.conf: line 143: Error: unknown payload OID
Unknown payload OID: prErrMessage
/etc/snmp/snmpd.conf: line 143: Error: Unknown payload OID
trigger OID: prErrorFlag
/etc/snmp/snmpd.conf: line 143: Error: unknown monitor OID
payload OID: memErrorName
/etc/snmp/snmpd.conf: line 143: Error: unknown payload OID
Unknown payload OID: memErrorName
/etc/snmp/snmpd.conf: line 143: Error: Unknown payload OID
payload OID: memSwapErrorMsg
/etc/snmp/snmpd.conf: line 143: Error: unknown payload OID
Unknown payload OID: memSwapErrorMsg
/etc/snmp/snmpd.conf: line 143: Error: Unknown payload OID
trigger OID: memSwapError
/etc/snmp/snmpd.conf: line 143: Error: unknown monitor OID
payload OID: extNames
/etc/snmp/snmpd.conf: line 143: Error: unknown payload OID
Unknown payload OID: extNames
/etc/snmp/snmpd.conf: line 143: Error: Unknown payload OID
payload OID: extOutput
/etc/snmp/snmpd.conf: line 143: Error: unknown payload OID
Unknown payload OID: extOutput
/etc/snmp/snmpd.conf: line 143: Error: Unknown payload OID
trigger OID: extResult
/etc/snmp/snmpd.conf: line 143: Error: unknown monitor OID
payload OID: dskPath
/etc/snmp/snmpd.conf: line 143: Error: unknown payload OID
Unknown payload OID: dskPath
/etc/snmp/snmpd.conf: line 143: Error: Unknown payload OID
payload OID: dskErrorMsg
/etc/snmp/snmpd.conf: line 143: Error: unknown payload OID
Unknown payload OID: dskErrorMsg
/etc/snmp/snmpd.conf: line 143: Error: Unknown payload OID
trigger OID: dskErrorFlag
/etc/snmp/snmpd.conf: line 143: Error: unknown monitor OID
payload OID: laNames
/etc/snmp/snmpd.conf: line 143: Error: unknown payload OID
Unknown payload OID: laNames
/etc/snmp/snmpd.conf: line 143: Error: Unknown payload OID
payload OID: laErrMessage
/etc/snmp/snmpd.conf: line 143: Error: unknown payload OID
Unknown payload OID: laErrMessage
/etc/snmp/snmpd.conf: line 143: Error: Unknown payload OID
trigger OID: laErrorFlag
/etc/snmp/snmpd.conf: line 143: Error: unknown monitor OID
payload OID: fileName
/etc/snmp/snmpd.conf: line 143: Error: unknown payload OID
Unknown payload OID: fileName
/etc/snmp/snmpd.conf: line 143: Error: Unknown payload OID
payload OID: fileErrorMsg
/etc/snmp/snmpd.conf: line 143: Error: unknown payload OID
Unknown payload OID: fileErrorMsg
/etc/snmp/snmpd.conf: line 143: Error: Unknown payload OID
trigger OID: fileErrorFlag
/etc/snmp/snmpd.conf: line 143: Error: unknown monitor OID
payload OID: snmperrErrMessage
/etc/snmp/snmpd.conf: line 143: Error: unknown payload OID
Unknown payload OID: snmperrErrMessage
/etc/snmp/snmpd.conf: line 143: Error: Unknown payload OID
trigger OID: snmperrErrorFlag
/etc/snmp/snmpd.conf: line 143: Error: unknown monitor OID
Turning on AgentX master support.
Turning on AgentX master support.
/usr/share/snmp/snmpd.conf: line 111: Error: Already have an entry for this proc                                                                             ess.
/usr/share/snmp/snmpd.conf: line 112: Error: Already have an entry for this proc                                                                             ess.
/usr/share/snmp/snmpd.conf: line 113: Error: Already have an entry for this proc                                                                             ess.
/usr/share/snmp/snmpd.conf: line 164: Error: missing COMMUNITY parameter

/usr/share/snmp/snmpd.conf: line 165: Error: includeAllDisks already specified.
/usr/share/snmp/snmpd.conf: line 165: Error:    ignoring: includeAllDisks 10%
payload OID: prNames
/usr/share/snmp/snmpd.conf: line 167: Error: unknown payload OID
Unknown payload OID: prNames
/usr/share/snmp/snmpd.conf: line 167: Error: Unknown payload OID
payload OID: prErrMessage
/usr/share/snmp/snmpd.conf: line 167: Error: unknown payload OID
Unknown payload OID: prErrMessage
/usr/share/snmp/snmpd.conf: line 167: Error: Unknown payload OID
trigger OID: prErrorFlag
/usr/share/snmp/snmpd.conf: line 167: Error: unknown monitor OID
payload OID: memErrorName
/usr/share/snmp/snmpd.conf: line 167: Error: unknown payload OID
Unknown payload OID: memErrorName
/usr/share/snmp/snmpd.conf: line 167: Error: Unknown payload OID
payload OID: memSwapErrorMsg
/usr/share/snmp/snmpd.conf: line 167: Error: unknown payload OID
Unknown payload OID: memSwapErrorMsg
/usr/share/snmp/snmpd.conf: line 167: Error: Unknown payload OID
trigger OID: memSwapError
/usr/share/snmp/snmpd.conf: line 167: Error: unknown monitor OID
payload OID: extNames
/usr/share/snmp/snmpd.conf: line 167: Error: unknown payload OID
Unknown payload OID: extNames
/usr/share/snmp/snmpd.conf: line 167: Error: Unknown payload OID
payload OID: extOutput
/usr/share/snmp/snmpd.conf: line 167: Error: unknown payload OID
Unknown payload OID: extOutput
/usr/share/snmp/snmpd.conf: line 167: Error: Unknown payload OID
trigger OID: extResult
/usr/share/snmp/snmpd.conf: line 167: Error: unknown monitor OID
payload OID: dskPath
/usr/share/snmp/snmpd.conf: line 167: Error: unknown payload OID
Unknown payload OID: dskPath
/usr/share/snmp/snmpd.conf: line 167: Error: Unknown payload OID
payload OID: dskErrorMsg
/usr/share/snmp/snmpd.conf: line 167: Error: unknown payload OID
Unknown payload OID: dskErrorMsg
/usr/share/snmp/snmpd.conf: line 167: Error: Unknown payload OID
trigger OID: dskErrorFlag
/usr/share/snmp/snmpd.conf: line 167: Error: unknown monitor OID
payload OID: laNames
/usr/share/snmp/snmpd.conf: line 167: Error: unknown payload OID
Unknown payload OID: laNames
/usr/share/snmp/snmpd.conf: line 167: Error: Unknown payload OID
payload OID: laErrMessage
/usr/share/snmp/snmpd.conf: line 167: Error: unknown payload OID
Unknown payload OID: laErrMessage
/usr/share/snmp/snmpd.conf: line 167: Error: Unknown payload OID
trigger OID: laErrorFlag
/usr/share/snmp/snmpd.conf: line 167: Error: unknown monitor OID
payload OID: fileName
/usr/share/snmp/snmpd.conf: line 167: Error: unknown payload OID
Unknown payload OID: fileName
/usr/share/snmp/snmpd.conf: line 167: Error: Unknown payload OID
payload OID: fileErrorMsg
/usr/share/snmp/snmpd.conf: line 167: Error: unknown payload OID
Unknown payload OID: fileErrorMsg
/usr/share/snmp/snmpd.conf: line 167: Error: Unknown payload OID
trigger OID: fileErrorFlag
/usr/share/snmp/snmpd.conf: line 167: Error: unknown monitor OID
payload OID: snmperrErrMessage
/usr/share/snmp/snmpd.conf: line 167: Error: unknown payload OID
Unknown payload OID: snmperrErrMessage
/usr/share/snmp/snmpd.conf: line 167: Error: Unknown payload OID
trigger OID: snmperrErrorFlag
/usr/share/snmp/snmpd.conf: line 167: Error: unknown monitor OID
/usr/share/snmp/snmpd.conf: line 168: Error: duplicate trigger name
/usr/share/snmp/snmpd.conf: line 168: Error: duplicate trigger name
duplicate table data attempted to be entered. row exists
Failed to register extend entry 'test1' - possibly duplicate name.
duplicate table data attempted to be entered. row exists
Failed to register extend entry 'test2' - possibly duplicate name.
net-snmp: 74 error(s) in config file(s)
Error opening specified endpoint "udp:161"
Server Exiting with code 1
```

---

### Post by sanderj on 2013-05-17
I would do this:

find the config file that snmpd uses. Delete it.
remove snmpd, and purge it
install snmpd. make sure it has a fresh config file.
run snmpd like above; it should keep running and not exit. If not, go back to step 1
bingo: you have snmpd running

---

