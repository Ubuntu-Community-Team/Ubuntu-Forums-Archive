---
title: "imfile rsyslog confiog sporadic cince upgrade to ubuntu20"
date: 2024-04-17
forum: General Help
---

### Post by didds1962 on 2024-04-17
Caveat:  I've recently inherited a bunch of ubuntu systems with very little historical knowledge available to me.

Systems:  Ubuntu 20 (recent upgrade in-line from ubuntu 18)

Scenario:
While servers were ubuntu 18, clients had a a application that wrote logs into a non standard system log  /var/log/node/Tlog.log   (name obfuscated ;-) )
Previous rsyslog.conf configurations were in place to capture and include this log into rsyslog for central syslogging purposes where the log would appear on the central syslog server in /var/log/external/<client>/node/Tlog-<date>.log

client config:

$ModLoad imfile
...
$InputFileName /var/log/node/Tlog.log
$InputFileTag tserv-stdout
$InputFileStateFile tserv-stdout
$InputFileSeverity info
$InputFileFacility local4
$InputRunFileMonitor



That worked well for years.

a few months ago these systems were upgraded to ubuntu 20.  It was shortly afterwards noted that the central logging wasn't working well...  logs were very sporadic if at all.

Then it was discovered that somewhere along the line the ubuntu 20 config was needed to be altered (who knew?)

So now the client has 

module(
    load = "imfile"
    pollingInterval = "1"
        statefile.directory = "/var/log/node"
)
...
input(
    type = "imfile"
    tag = "tserv-stdout"
    facility = "local4"
    severity = "info"
    file = "/var/log/node/Tlog.log"
)


That seemed to fix matters - logs to Tlog.log on the client were appearing in the central syslog log as well.

then about a week ago it just stopped working.  All configs are as above ie the ones that were working. rsyslogd is running.  nothing obvious is in any other log to suggest issues with rsyslog. Other system logs are updated centrally as normal.  Its just this extraneous log that has stopped "working". Tlog.log on the client is constantly updated via its app  (ie it is not a silent/inactive log)

Any thoughts/pointers as to what the proverbial is happening, or how better to troubleshoot it?

I've chucked a local4.* /var/log/node/Tlog.log entry into rsyslog.conf and logger -p local4.info logs locally and centrally as expected using that.  Just the other log updates to Tlog.log dont now get centrally logged any longer.

---

### Post by didds1962 on 2024-04-17
and FWIW, both systems (client and rsyslog server) have this version of rsyslogd

rsyslogd  8.2001.0 (aka 2020.01) compiled with:
        PLATFORM:                               x86_64-pc-linux-gnu
        PLATFORM (lsb_release -d):
        FEATURE_REGEXP:                         Yes
        GSSAPI Kerberos 5 support:              Yes
        FEATURE_DEBUG (debug build, slow code): No
        32bit Atomic operations supported:      Yes
        64bit Atomic operations supported:      Yes
        memory allocator:                       system default
        Runtime Instrumentation (slow code):    No
        uuid support:                           Yes
        systemd support:                        Yes
        Config file:                            /etc/rsyslog.conf
        PID file:                               /run/rsyslogd.pid
        Number of Bits in RainerScript integers: 64

---

