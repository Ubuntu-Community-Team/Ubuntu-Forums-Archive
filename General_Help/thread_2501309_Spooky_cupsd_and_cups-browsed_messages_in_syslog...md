---
title: "Spooky cupsd and cups-browsed messages in syslog.. :-/"
date: 2024-10-01
forum: General Help
---

### Post by bswebdk on 2024-10-01
Recently I heard about a [cups-browsed vulnerability](https://securitylabs.datadoghq.com/articles/emerging-vulnerability-cups/), today I noticed some CUPS related messages in the syslog from one of my computers which has been acting strangely for some days and today it would not boot the system normally. Has the computer been compromized? I have disabled the cups-browsed service, but should I do other things to mitigate the problem?

```

Sep 29 08:36:43 desktop cups.cupsd[815]: + LINE=Listen /run/cups/cups.sock
Sep 29 08:36:43 desktop cups.cupsd[1019]: + echo Listen /run/cups/cups.sock
Sep 29 08:36:43 desktop cups.cupsd[1020]: + head -1
Sep 29 08:36:43 desktop cups.cupsd[1021]: + perl -p -e s:^\s*Listen\s+(\S+)\s*$:\1:
Sep 29 08:36:43 desktop cups.cupsd[815]: + SYSTEM_CUPS_SERVER=/run/cups/cups.sock
Sep 29 08:36:43 desktop cups.cupsd[815]: + PORT=631
Sep 29 08:36:43 desktop cups.cupsd[815]: + ALTPORT=10631
Sep 29 08:36:43 desktop cups.cupsd[815]: + DOMAINSOCKET=/run/cups/cups.sock
Sep 29 08:36:43 desktop cups.cupsd[815]: + [ ! -d /run/cups ]
Sep 29 08:36:43 desktop cups.cupsd[815]: + ALTDOMAINSOCKET=/var/snap/cups/common/run/cups.sock
Sep 29 08:36:43 desktop cups.cupsd[815]: + [ YES = YES ]
Sep 29 08:36:43 desktop cups.cupsd[815]: + PORT=
Sep 29 08:36:43 desktop cups.cupsd[815]: + DOMAINSOCKET=/var/snap/cups/common/run/cups.sock
Sep 29 08:36:43 desktop cups.cupsd[815]: + [ ! -f /var/snap/cups/common/etc/cups/cupsd.conf ]
Sep 29 08:36:43 desktop cups.cupsd[815]: + [ YES = YES ]
Sep 29 08:36:43 desktop cups.cupsd[1032]: + grep -v Listen
Sep 29 08:36:43 desktop cups.cupsd[1031]: +
Sep 29 08:36:43 desktop cups.cupsd[1033]: +
Sep 29 08:36:43 desktop cups.cupsd[1031]: cat /var/snap/cups/common/etc/cups/cupsd.conf
Sep 29 08:36:43 desktop cups.cupsd[1033]: grep -v Port
Sep 29 08:36:43 desktop cups.cupsd[815]: + mv /var/snap/cups/common/etc/cups/cupsd.conf.new /var/snap/cups/common/etc/cups/cupsd.conf
Sep 29 08:36:43 desktop cups.cupsd[815]: + LISTENLINES=
Sep 29 08:36:43 desktop cups.cupsd[815]: + [ /var/snap/cups/common/run/cups.sock = /var/snap/cups/common/run/cups.sock ]
Sep 29 08:36:43 desktop cups.cupsd[815]: + LISTENLINES=Listen /var/snap/cups/common/run/cups.sock
Sep 29 08:36:43 desktop cups.cupsd[1037]: + grep -v Listen
Sep 29 08:36:43 desktop cups.cupsd[1036]: + cat /var/snap/cups/common/etc/cups/cupsd.conf
Sep 29 08:36:43 desktop cups.cupsd[815]: + echo Listen /var/snap/cups/common/run/cups.sock
Sep 29 08:36:43 desktop cups.cupsd[815]: + cat /var/snap/cups/common/etc/cups/cupsd.conf.new
Sep 29 08:36:43 desktop cups.cupsd[815]: + rm -f /var/snap/cups/common/etc/cups/cupsd.conf.new
Sep 29 08:36:43 desktop cups.cupsd[815]: + touch /var/snap/cups/common/etc/cups/client.conf
Sep 29 08:36:43 desktop cups.cupsd[1043]: + cat /var/snap/cups/common/etc/cups/client.conf
Sep 29 08:36:43 desktop cups.cupsd[1044]: + grep -v ServerName
Sep 29 08:36:43 desktop cups.cupsd[1042]: + true
Sep 29 08:36:43 desktop cups.cupsd[815]: + echo ServerName /var/snap/cups/common/run/cups.sock
Sep 29 08:36:43 desktop cups.cupsd[815]: + cat /var/snap/cups/common/etc/cups/client.conf.new
Sep 29 08:36:43 desktop cups.cupsd[815]: + rm -f /var/snap/cups/common/etc/cups/client.conf.new
Sep 29 08:36:43 desktop cups.cupsd[815]: + [ ! -f /var/snap/cups/common/etc/cups/snmp.conf ]
Sep 29 08:36:43 desktop cups.cupsd[1047]: + yes n
Sep 29 08:36:43 desktop cups.cupsd[1048]: + cp -ri /snap/cups/1058/etc/cups/ppd /var/snap/cups/common/etc/cups/
Sep 29 08:36:43 desktop cups.cupsd[1049]: + yes n
Sep 29 08:36:43 desktop cups.cupsd[1050]: + cp -ri /snap/cups/1058/etc/cups/ssl /var/snap/cups/common/etc/cups/
Sep 29 08:36:43 desktop cups.cupsd[815]: + SCHEDULER=cupsd
Sep 29 08:36:43 desktop cups.cupsd[815]: + CUPS_PID=1051
Sep 29 08:36:43 desktop cups.cupsd[1051]: +
Sep 29 08:36:43 desktop cups.cupsd[815]: + echo 1051
Sep 29 08:36:43 desktop cups.cupsd[1051]: exec cupsd -f -s /var/snap/cups/common/etc/cups/cups-files.conf -c /var/snap/cups/common/etc/cups/cupsd.conf
Sep 29 08:36:43 desktop cups.cupsd[815]: + [ YES = YES ]
Sep 29 08:36:43 desktop cups.cupsd[815]: + PROXY_DAEMON=cups-proxyd
Sep 29 08:36:43 desktop cups.cupsd[815]: + PROXYD_PID=1052
Sep 29 08:36:43 desktop cups.cupsd[815]: + echo 1052
Sep 29 08:36:43 desktop cups.cupsd[815]: + wait 1051
Sep 29 08:36:43 desktop cups.cupsd[1052]: + exec cups-proxyd /var/snap/cups/common/run/cups.sock /run/cups/cups.sock -l --logdir /var/snap/cups/1058/var/log
...
Sep 29 08:36:44 desktop cups.cups-browsed[812]: + [ -r /var/snap/cups/1058/var/run/cupsd.pid ]
Sep 29 08:36:44 desktop cups.cups-browsed[1101]: + cat /var/snap/cups/1058/var/run/cupsd.pid
Sep 29 08:36:44 desktop cups.cups-browsed[812]: + PID=1051
Sep 29 08:36:44 desktop cups.cups-browsed[812]: + [ -n 1051 ]
Sep 29 08:36:44 desktop cups.cups-browsed[812]: + kill -0 1051
Sep 29 08:36:44 desktop cups.cups-browsed[812]: + CUPSSTARTED=1
Sep 29 08:36:44 desktop cups.cups-browsed[812]: + break
Sep 29 08:36:44 desktop cups.cups-browsed[812]: + [ 1 = 0 ]
Sep 29 08:36:44 desktop cups.cups-browsed[812]: + PID=
Sep 29 08:36:44 desktop cups.cups-browsed[812]: + [ ! -e /var/snap/cups/1058/var/run/proxy-mode ]
Sep 29 08:36:44 desktop cups.cups-browsed[812]: + PID=1103
Sep 29 08:36:44 desktop cups.cups-browsed[1103]: +
Sep 29 08:36:44 desktop cups.cups-browsed[812]: +
Sep 29 08:36:44 desktop cups.cups-browsed[1103]: true
Sep 29 08:36:44 desktop cups.cups-browsed[812]: echo
Sep 29 08:36:44 desktop cups.cups-browsed[812]:  1103
Sep 29 08:36:44 desktop cups.cups-browsed[1103]: +
Sep 29 08:36:44 desktop cups.cups-browsed[1103]: sleep 3600
Sep 29 08:36:44 desktop cups.cups-browsed[812]: + wait 1103
...
Sep 29 14:25:35 desktop cups.cups-browsed[816]: + mkdir -p /var/snap/cups/1058/var/log
Sep 29 14:25:35 desktop cups.cupsd[823]: + mkdir -p /var/snap/cups/1058/var/run/certs
Sep 29 14:25:35 desktop cups.cups-browsed[816]: + mkdir -p /var/snap/cups/1058/var/cache
Sep 29 14:25:35 desktop cups.cups-browsed[816]: + mkdir -p /var/snap/cups/1058/var/run
Sep 29 14:25:35 desktop cups.cupsd[823]: + mkdir -p /var/snap/cups/1058/var/log
Sep 29 14:25:35 desktop cups.cups-browsed[816]: + mkdir -p /var/snap/cups/common/etc/cups
Sep 29 14:25:35 desktop cups.cupsd[823]: + mkdir -p /var/snap/cups/1058/var/cache/fontconfig
Sep 29 14:25:35 desktop cups.cups-browsed[816]: + CONF=/var/snap/cups/common/etc/cups/cups-browsed.conf
Sep 29 14:25:35 desktop cups.cups-browsed[816]: + CLIENTCONF=/var/snap/cups/common/etc/cups/client.conf
Sep 29 14:25:35 desktop cups.cups-browsed[816]: + DAEMON=cups-browsed
Sep 29 14:25:35 desktop cups.cups-browsed[816]: + export LC_ALL=C.UTF-8
Sep 29 14:25:35 desktop cups.cups-browsed[816]: + export LANG=C.UTF-8
Sep 29 14:25:35 desktop cups.cups-browsed[816]: + TMPDIR=/var/snap/cups/1058/tmp
Sep 29 14:25:35 desktop cups.cups-browsed[816]: + mkdir -p /var/snap/cups/1058/tmp
Sep 29 14:25:35 desktop cups.cupsd[823]: + mkdir -p /var/snap/cups/common/etc/cups/ppd
Sep 29 14:25:35 desktop cups.cups-browsed[816]: + CUPSSTARTED=0
Sep 29 14:25:35 desktop cups.cups-browsed[975]: + seq 60
Sep 29 14:25:35 desktop cups.cupsd[823]: + mkdir -p /var/snap/cups/common/etc/cups/ssl
Sep 29 14:25:35 desktop cups.cupsd[823]: + mkdir -p /var/snap/cups/common/run
Sep 29 14:25:35 desktop cups.cupsd[823]: + mkdir -m 0755 -p /run/cups
Sep 29 14:25:35 desktop cups.cups-browsed[816]: + [ -r /var/snap/cups/1058/var/run/cupsd.pid ]
Sep 29 14:25:35 desktop cups.cups-browsed[816]: + sleep 1
Sep 29 14:25:35 desktop cups.cupsd[823]: + export LC_ALL=C.UTF-8
Sep 29 14:25:35 desktop cups.cupsd[823]: + export LANG=C.UTF-8
Sep 29 14:25:35 desktop cups.cupsd[823]: + export TMPDIR=/var/snap/cups/1058/tmp
Sep 29 14:25:35 desktop cups.cupsd[823]: + mkdir -p /var/snap/cups/1058/tmp
Sep 29 14:25:35 desktop cups.cupsd[823]: + CUPSTMPDIR=/var/snap/cups/1058/var/spool/tmp
Sep 29 14:25:35 desktop cups.cupsd[823]: + [ -d /var/snap/cups/1058/tmp ]
Sep 29 14:25:35 desktop cups.cupsd[823]: + chown -R root.root /var/snap/cups/1058/tmp
Sep 29 14:25:35 desktop cups.cupsd[823]: + chmod -R u+rwX /var/snap/cups/1058/tmp
Sep 29 14:25:35 desktop cups.cupsd[823]: + rm -rf /var/snap/cups/1058/tmp
Sep 29 14:25:35 desktop cups.cupsd[823]: + [ -d /var/snap/cups/1058/tmp ]
Sep 29 14:25:35 desktop cups.cupsd[823]: + [ -d /var/snap/cups/1058/var/spool/tmp ]
Sep 29 14:25:35 desktop cups.cupsd[823]: + chown -R root.root /var/snap/cups/1058/var/spool/tmp
Sep 29 14:25:35 desktop cups.cupsd[823]: + chmod -R u+rwX /var/snap/cups/1058/var/spool/tmp
Sep 29 14:25:35 desktop cups.cupsd[823]: + rm -rf /var/snap/cups/1058/var/spool/tmp
Sep 29 14:25:35 desktop cups.cupsd[823]: + [ -d /var/snap/cups/1058/var/spool/tmp ]
Sep 29 14:25:35 desktop cups.cupsd[823]: + mkdir -p /var/snap/cups/1058/tmp
Sep 29 14:25:35 desktop cups.cupsd[823]: + chown -R root.root /var/snap/cups/1058/tmp
Sep 29 14:25:35 desktop cups.cupsd[823]: + chmod -R 1777 /var/snap/cups/1058/tmp
Sep 29 14:25:35 desktop cups.cupsd[823]: + mkdir -p /var/snap/cups/1058/var/spool/tmp
Sep 29 14:25:35 desktop cups.cupsd[823]: + chown -R root.snap_daemon /var/snap/cups/1058/var/spool/tmp
Sep 29 14:25:35 desktop cups.cupsd[823]: + chmod -R 1770 /var/snap/cups/1058/var/spool/tmp
Sep 29 14:25:35 desktop cups.cupsd[823]: + CUPSUSER=snap_daemon
Sep 29 14:25:35 desktop cups.cupsd[823]: + ALTCUPSUSER=root
Sep 29 14:25:35 desktop cups.cupsd[823]: + CUPSGROUP=snap_daemon
Sep 29 14:25:35 desktop cups.cupsd[823]: + ALTCUPSGROUP=root
Sep 29 14:25:35 desktop cups.cupsd[823]: + CUPSSYSTEMGROUP=lpadmin
Sep 29 14:25:35 desktop cups.cupsd[823]: + ALTCUPSSYSTEMGROUP=adm
Sep 29 14:25:35 desktop cups.cupsd[823]: + TESTFILE=/var/snap/cups/1058/tmp/testfile
Sep 29 14:25:35 desktop cups.cupsd[823]: + touch /var/snap/cups/1058/tmp/testfile
Sep 29 14:25:35 desktop cups.cupsd[823]: + chown snap_daemon /var/snap/cups/1058/tmp/testfile
Sep 29 14:25:35 desktop cups.cupsd[823]: + chgrp snap_daemon /var/snap/cups/1058/tmp/testfile
Sep 29 14:25:35 desktop cups.cupsd[823]: + rm -f /var/snap/cups/1058/tmp/testfile
Sep 29 14:25:35 desktop cups.cupsd[823]: + getent group lpadmin
Sep 29 14:25:35 desktop cups.cupsd[823]: + [ ! -f /var/snap/cups/common/etc/cups/cups-files.conf ]
Sep 29 14:25:35 desktop cups.cupsd[823]: + perl -p -i -e s:^(\s*\#)?\s*User\s+\S+\s*$:User snap_daemon\n:; -e s:^(\s*\#)?\s*Group\s+.*$:Group snap_daemon:; -e s:^(\s*\#)?\s*SystemGroup\s+.*$:SystemGroup lpadmin root:; -e s:^(\s*\#)?\s*AccessLog\s+.*$:AccessLog /var/snap/cups/1058/var/log/access_log:; -e s:^(\s*\#)?\s*CacheDir\s+.*$:CacheDir /var/snap/cups/1058/var/cache:; -e s:^(\s*\#)?\s*DataDir\s+.*$:DataDir /snap/cups/1058/share/cups:; -e s:^(\s*\#)?\s*DocumentRoot\s+.*$:DocumentRoot /snap/cups/1058/share/cups/doc:; -e s:^(\s*\#)?\s*ErrorLog\s+.*$:ErrorLog /var/snap/cups/1058/var/log/error_log:; -e s:^(\s*\#)?\s*FontPath\s+.*$:\#FontPath (NOT SUPPORTED ANY MORE):; -e s:^(\s*\#)?\s*PageLog\s+.*$:PageLog /var/snap/cups/1058/var/log/page_log:; -e s:^(\s*\#)?\s*Printcap\s+.*$:Printcap /var/snap/cups/common/etc/printcap:; -e s:^(\s*\#)?\s*RequestRoot\s+.*$:RequestRoot /var/snap/cups/1058/var/spool:; -e s:^(\s*\#)?\s*ServerBin\s+.*$:ServerBin /snap/cups/1058/lib/cups:; -e s:^(\s*\#)?\s*ServerRoot\s+.*$:ServerRoot /var/snap/cups/common/etc/cups:; -e s:^(\s*\#)?\s*StateDir\s+.*$:StateDir /var/snap/cups/1058/var/run:; -e s:^(\s*\#)?\s*TempDir\s+.*$:TempDir /var/snap/cups/1058/var/spool/tmp:; /var/snap/cups/common/etc/cups/cups-files.conf
Sep 29 14:25:36 desktop cups.cupsd[823]: + PROXY_MODE=NO
Sep 29 14:25:36 desktop cups.cupsd[823]: + SYSTEM_CUPS_SERVER=
Sep 29 14:25:36 desktop cups.cupsd[823]: + rm -f /var/snap/cups/1058/var/run/proxy-mode
Sep 29 14:25:36 desktop cups.cupsd[823]: + [ ! -f /var/snap/cups/common/no-proxy ]
Sep 29 14:25:36 desktop cups.cupsd[823]: + [ -r /etc/cups/cupsd.conf ]
Sep 29 14:25:36 desktop cups.cupsd[823]: + touch /var/snap/cups/1058/var/run/proxy-mode
Sep 29 14:25:36 desktop cups.cupsd[823]: + PROXY_MODE=YES
Sep 29 14:25:36 desktop cups.cupsd[823]: + SYSTEM_CUPS_SERVER=localhost:631
Sep 29 14:25:36 desktop cups.cupsd[1008]: + grep -E ^[ \t]*Listen[ \t]+/ /etc/cups/cupsd.conf
Sep 29 14:25:36 desktop cups.cupsd[823]: + LINE=Listen /run/cups/cups.sock
Sep 29 14:25:36 desktop cups.cupsd[1017]: + echo Listen /run/cups/cups.sock
Sep 29 14:25:36 desktop cups.cupsd[1018]: + head -1
Sep 29 14:25:36 desktop cups.cupsd[1019]: + perl -p -e s:^\s*Listen\s+(\S+)\s*$:\1:
Sep 29 14:25:36 desktop cups.cupsd[823]: + SYSTEM_CUPS_SERVER=/run/cups/cups.sock
Sep 29 14:25:36 desktop cups.cupsd[823]: + PORT=631
Sep 29 14:25:36 desktop cups.cupsd[823]: + ALTPORT=10631
Sep 29 14:25:36 desktop cups.cupsd[823]: + DOMAINSOCKET=/run/cups/cups.sock
Sep 29 14:25:36 desktop cups.cupsd[823]: + [ ! -d /run/cups ]
Sep 29 14:25:36 desktop cups.cupsd[823]: + ALTDOMAINSOCKET=/var/snap/cups/common/run/cups.sock
Sep 29 14:25:36 desktop cups.cupsd[823]: + [ YES = YES ]
Sep 29 14:25:36 desktop cups.cupsd[823]: + PORT=
Sep 29 14:25:36 desktop cups.cupsd[823]: + DOMAINSOCKET=/var/snap/cups/common/run/cups.sock
Sep 29 14:25:36 desktop cups.cupsd[823]: + [ ! -f /var/snap/cups/common/etc/cups/cupsd.conf ]
Sep 29 14:25:36 desktop cups.cupsd[823]: + [ YES = YES ]
Sep 29 14:25:36 desktop cups.cupsd[1022]: + cat /var/snap/cups/common/etc/cups/cupsd.conf
Sep 29 14:25:36 desktop cups.cupsd[1023]: + grep -v Listen
Sep 29 14:25:36 desktop cups.cupsd[1024]: + grep -v Port
Sep 29 14:25:36 desktop cups.cupsd[823]: + mv /var/snap/cups/common/etc/cups/cupsd.conf.new /var/snap/cups/common/etc/cups/cupsd.conf
Sep 29 14:25:36 desktop cups.cupsd[823]: + LISTENLINES=
Sep 29 14:25:36 desktop cups.cupsd[823]: + [ /var/snap/cups/common/run/cups.sock = /var/snap/cups/common/run/cups.sock ]
Sep 29 14:25:36 desktop cups.cupsd[823]: + LISTENLINES=Listen /var/snap/cups/common/run/cups.sock
Sep 29 14:25:36 desktop cups.cupsd[1027]: + cat /var/snap/cups/common/etc/cups/cupsd.conf
Sep 29 14:25:36 desktop cups.cupsd[1028]: + grep -v Listen
Sep 29 14:25:36 desktop cups.cupsd[823]: + echo Listen /var/snap/cups/common/run/cups.sock
Sep 29 14:25:36 desktop cups.cupsd[823]: + cat /var/snap/cups/common/etc/cups/cupsd.conf.new
Sep 29 14:25:36 desktop cups.cupsd[823]: + rm -f /var/snap/cups/common/etc/cups/cupsd.conf.new
Sep 29 14:25:36 desktop cups.cupsd[823]: + touch /var/snap/cups/common/etc/cups/client.conf
Sep 29 14:25:36 desktop cups.cupsd[1034]: + cat /var/snap/cups/common/etc/cups/client.conf
Sep 29 14:25:36 desktop cups.cupsd[1035]: + grep -v ServerName
Sep 29 14:25:36 desktop cups.cupsd[1033]: + true
Sep 29 14:25:36 desktop cups.cupsd[823]: + echo ServerName /var/snap/cups/common/run/cups.sock
Sep 29 14:25:36 desktop cups.cupsd[823]: + cat /var/snap/cups/common/etc/cups/client.conf.new
Sep 29 14:25:36 desktop cups.cupsd[823]: + rm -f /var/snap/cups/common/etc/cups/client.conf.new
Sep 29 14:25:36 desktop cups.cupsd[823]: + [ ! -f /var/snap/cups/common/etc/cups/snmp.conf ]
Sep 29 14:25:36 desktop cups.cupsd[1038]: + yes n
Sep 29 14:25:36 desktop cups.cupsd[1039]: + cp -ri /snap/cups/1058/etc/cups/ppd /var/snap/cups/common/etc/cups/
Sep 29 14:25:36 desktop cups.cupsd[1040]: + yes n
Sep 29 14:25:36 desktop cups.cupsd[1041]: + cp -ri /snap/cups/1058/etc/cups/ssl /var/snap/cups/common/etc/cups/
Sep 29 14:25:36 desktop cups.cupsd[823]: + SCHEDULER=cupsd
Sep 29 14:25:36 desktop cups.cupsd[823]: + CUPS_PID=1042
Sep 29 14:25:36 desktop cups.cupsd[823]: + echo 1042
Sep 29 14:25:36 desktop cups.cupsd[823]: + [ YES = YES ]
Sep 29 14:25:36 desktop cups.cupsd[823]: + PROXY_DAEMON=cups-proxyd
Sep 29 14:25:36 desktop cups.cupsd[823]: + PROXYD_PID=1043
Sep 29 14:25:36 desktop cups.cupsd[823]: + echo 1043
Sep 29 14:25:36 desktop cups.cupsd[823]: + wait 1042
Sep 29 14:25:36 desktop cups.cupsd[1042]: + exec cupsd -f -s /var/snap/cups/common/etc/cups/cups-files.conf -c /var/snap/cups/common/etc/cups/cupsd.conf
Sep 29 14:25:36 desktop cups.cupsd[1043]: + exec cups-proxyd /var/snap/cups/common/run/cups.sock /run/cups/cups.sock -l --logdir /var/snap/cups/1058/var/log
Sep 29 14:25:36 desktop cups.cups-browsed[816]: + [ -r /var/snap/cups/1058/var/run/cupsd.pid ]
Sep 29 14:25:36 desktop cups.cups-browsed[1084]: + cat /var/snap/cups/1058/var/run/cupsd.pid
Sep 29 14:25:36 desktop cups.cups-browsed[816]: + PID=1042
Sep 29 14:25:36 desktop cups.cups-browsed[816]: + [ -n 1042 ]
Sep 29 14:25:36 desktop cups.cups-browsed[816]: + kill -0 1042
Sep 29 14:25:36 desktop cups.cups-browsed[816]: + CUPSSTARTED=1
Sep 29 14:25:36 desktop cups.cups-browsed[816]: + break
Sep 29 14:25:36 desktop cups.cups-browsed[816]: + [ 1 = 0 ]
Sep 29 14:25:36 desktop cups.cups-browsed[816]: + PID=
Sep 29 14:25:36 desktop cups.cups-browsed[816]: + [ ! -e /var/snap/cups/1058/var/run/proxy-mode ]
Sep 29 14:25:36 desktop cups.cups-browsed[816]: + PID=1086
Sep 29 14:25:36 desktop cups.cups-browsed[816]: + echo 1086
Sep 29 14:25:36 desktop cups.cups-browsed[1086]: +
Sep 29 14:25:36 desktop cups.cups-browsed[816]: + wait 1086
Sep 29 14:25:36 desktop cups.cups-browsed[1086]: true
Sep 29 14:25:36 desktop cups.cups-browsed[1086]: + sleep 3600

```

Thanks for any advice! :-)

---

