---
title: "Upgraded to 12.10 and am now having issues with log files, and packages."
date: 2012-11-16
forum: General Help
---

### Post by Scrumps on 2012-11-16
I upgraded from 12.04 to 12.10 over the past weekend (Sunday the 12th). Since then I have been running into problems with syslog related things.

The first was that I was getting lag problems with networking devices. This was solved by switching back to an older kernel.

Second, DHCP & DNS seem to have stopped logging to specific files. They used to do this with the following options:
DNS

named.conf:
```

...
include "/etc/bind/named.conf.logging";
...

```named.conf.logging
```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

logging {
channel query.log {
file "/var/log/named/query.log";
// Set the severity to dynamic to see all the debug messages.
severity debug 3;
};

//category queries { query.log; };
//            channel update_debug {
//                 file "/var/log/named/update-debug.log";
//                 severity  debug 3;
//                 print-category yes;
//                 print-severity yes;
//                 print-time     yes;
//            };
//            channel security_info    {
//                 file "/var/log/named/named-auth.info";
//                 severity  info;
//                 print-category yes;
//                 print-severity yes;
//                 print-time     yes;
//            };
//
  //          category update { update_debug; };
 //           category security { security_info; };
//       };
};

```But the last updates to either /var/log/named/query.log or /var/log/bind/query.log are:
```

andrew@server:~/Downloads$ ls -l /var/log/named/query.log 
-rw-r--r-- 1 bind bind 152318 Sep 21 09:29 /var/log/named/query.log
andrew@server:~/Downloads$ ls -l /var/log/bind/
total 4
-rw-r--r-- 1 bind bind 1103 Sep 20 22:49 query.log
andrew@server:~/Downloads$ 

```For DHCP, I use the isc-dhcp-package. In the dhcpd.conf file, I told it to do the following:
```

...
log-facility local7;
...
```This was logging to /var/log/dhcp/dhcpd.log, but has stopped on November 10th:```

andrew@server:~/Downloads$ ls -l /var/log/dhcp/dhcpd.log 
-rw-r--r-- 1 root root 1697945 Nov 10 12:09 /var/log/dhcp/dhcpd.log
``````

...
Nov 10 12:09:38 localhost dhcpd: DHCPREQUEST for 10.10.10.21 from 9c:02:98:28:44:af (android-4b3b8b50d1056a90) via eth1
Nov 10 12:09:38 localhost dhcpd: DHCPACK on 10.10.10.21 to 9c:02:98:28:44:af (android-4b3b8b50d1056a90) via eth1
andrew@server:~/Downloads$ 

```Now, for syslog, I am really confused as to what is happening here, because this is really strange. When I do 'cat /var/log/syslog', it displays nothing, here is an ls -l:
```

-rw-r----- 1 syslog      adm          0 Nov 16 07:37 syslog
-rw-r----- 1 syslog      adm         20 Nov 15 07:36 syslog.1.gz
-rw-r----- 1 syslog      adm         20 Nov 14 07:43 syslog.2.gz
-rw-r----- 1 syslog      adm         20 Nov 13 07:39 syslog.3.gz
-rw-r----- 1 syslog      adm         20 Nov 12 07:40 syslog.4.gz
-rw-r----- 1 syslog      adm      84817 Nov 12 07:39 syslog.5.gz
-rw-r----- 1 syslog      adm      94447 Nov 11 07:53 syslog.6.gz
-rw-r----- 1 syslog      adm      15198 Nov 10 07:57 syslog.7.gz

```My other files (messages, user.log, debug, dmesg, etc) all seem to have stopped reporting on November 11th. I am not really sure how to diagnose or resolve this.

Then finally, logwatcher, has stopped reporting anything, I assume because nothing is writing to these files. So hopefully once I figure out how to resolve all of the odds and ends that went with this upgrade, logwatcher will start working again.

I would appreciate all and any help, because it's really odd that logs seemed to have just stopped reporting. I disabled apparmor for the time being, because I thought that might be what is causing it, but after reloading and attempting to release and renew an IP, it didn't seem to resolve the dhcp log issues.

As I mentioned, I would appreciate any help you all could give.

EDIT:
Was asking for some help in #linux as I hadn't received a response in #kubuntu, it seems that syslog is completely broken, but I don't know how to fix it.

```

    andrew@server:~/Downloads$ dpkg -l | grep syslog
    rc  inetutils-syslogd                        2:1.8-6                                      amd64        system logging daemon
    ii  rsyslog                                  5.8.6-1ubuntu9                               amd64        reliable system and kernel logging daemon
    andrew@server:~/Downloads$ sudo apt-get install inetutils-syslogd rsyslog
    Reading package lists... Done
    Building dependency tree      
    Reading state information... Done
    rsyslog is already the newest version.
    Some packages could not be installed. This may mean that you have
    requested an impossible situation or if you are using the unstable
    distribution that some required packages have not yet been created
    or been moved out of Incoming.
    The following information may help to resolve the situation:
     
    The following packages have unmet dependencies:
     inetutils-syslogd : Conflicts: linux-kernel-log-daemon
                         Conflicts: system-log-daemon
     rsyslog : Conflicts: linux-kernel-log-daemon
               Conflicts: system-log-daemon
    E: Unable to correct problems, you have held broken packages.

```

---

