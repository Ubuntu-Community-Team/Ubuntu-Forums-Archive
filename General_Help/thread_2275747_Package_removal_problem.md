---
title: "Package removal problem"
date: 2015-04-28
forum: General Help
---

### Post by zkab on 2015-04-28
I installed 'unifi-beta' in Ubuntu server 15.04.
At the end of the installation process something went wrong.
------------------------------------------------------------
Setting up unifi-beta (4.6.3-4850) ...
Failed to start unifi.service: Unit unifi.service failed to load: No such file or directory.
dpkg: error processing package unifi-beta (--configure):
 subprocess installed post-installation script returned error exit status 6
Setting up icedtea-6-jre-cacao:amd64 (6b35-1.13.7-1ubuntu1) ...
Setting up icedtea-6-jre-jamvm:amd64 (6b35-1.13.7-1ubuntu1) ...
Setting up openjdk-6-jre-lib (6b35-1.13.7-1ubuntu1) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for systemd (219-7ubuntu3) ...
Processing triggers for ca-certificates (20141019) ...
Updating certificates in /etc/ssl/certs... 0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d....
done.
done.
Errors were encountered while processing:
 unifi-beta
E: Sub-process /usr/bin/dpkg returned an error code (1)
------------------------------------------------------------

When I tried 'sudo apt-get remove unifi-beta' I get this:
------------------------------------------------------------
Do you want to continue? [Y/n] 
Setting up unifi-beta (4.6.3-4850) ...
Failed to start unifi.service: Unit unifi.service failed to load: No such file or directory.
dpkg: error processing package unifi-beta (--configure):
 subprocess installed post-installation script returned error exit status 6
Errors were encountered while processing:
 unifi-beta
E: Sub-process /usr/bin/dpkg returned an error code (1)
------------------------------------------------------------

'dpkg -l unifi-beta' gives:    rF  unifi-beta 4.6.3-4850  all  Ubiquiti UniFi server

Question is - how to get rid of the package 'unfi-beta'

---

### Post by dino99 on 2015-04-28
seems it has not been ported to systemd; try logging with upstart and check again
you also can run nautilus's search and delete everything related to it; also search that 'unifi.service to know if it exist or not, or if its only need a chmod +x to access it

---

### Post by zkab on 2015-04-28
OK - I have never used upstart before and I will give it a try.
Meanwhile does this make any sense to you ...

sudo dpkg --configure -D 777 unifi-beta
D000001: ensure_diversions: new, (re)loading
D000001: process queue pkg unifi-beta:all queue.len 0 progress 1, try 1
D000040: checking dependencies of unifi-beta:all (- <none>)
D000400:   checking group ...
D000400:     checking possibility  -> mongodb-10gen
D000400:       not installed
D000400:         returning 0
D000400:     found 0
D000400:     checking possibility  -> mongodb-server
D000400:       checking non-provided pkg mongodb-server:amd64
D000400:       is installed, ok and found
D000400:     found 3
D000400:   found 3 matched 0 possfixbytrig -
D000400:   checking group ...
D000400:     checking possibility  -> openjdk-6-jre-headless
D000400:       checking non-provided pkg openjdk-6-jre-headless:amd64
D000400:       is installed, ok and found
D000400:     found 3
D000400:   found 3 matched 0 possfixbytrig -
D000400:   checking group ...
D000400:     checking possibility  -> jsvc
D000400:       checking non-provided pkg jsvc:amd64
D000400:       is installed, ok and found
D000400:     found 3
D000400:   found 3 matched 0 possfixbytrig -
D000040: ok 2 msgs >><<
D000040:     checking Breaks
D000400:      checking virtbroken unifi-controller
Setting up unifi-beta (4.6.3-4850) ...
D000002: fork/exec /var/lib/dpkg/info/unifi-beta.postinst ( configure  )
Failed to start unifi.service: Unit unifi.service failed to load: No such file or directory.
dpkg: error processing package unifi-beta (--configure):
 subprocess installed post-installation script returned error exit status 6
D000001: ensure_diversions: same, skipping
Errors were encountered while processing:
 unifi-beta


cat /var/lib/dpkg/info/unifi-beta.postinst
#!/bin/sh

set -e

NAME=unifi
CODEPATH=/usr/lib/${NAME}
DATAPATH=/var/lib/${NAME}
RUNPATH=/var/run/${NAME}
LOGPATH=/var/log/${NAME}

for i in `seq 1 10` ; do
    [ -z "$(pgrep -f ${CODEPATH}/lib/ace.jar)" ] && break
    # graceful shutdown
    [ $i -gt 1 ] && [ -d ${RUNPATH} ] && touch ${RUNPATH}/server.stop || true
    # savage shutdown
    [ $i -gt 7 ] && pkill -f ${CODEPATH}/lib/ace.jar || true
    sleep 1
done

if [ "$1" = "configure" ] ; then
    update-rc.d unifi defaults 92 08
    [ -d ${LOGPATH} ] || mkdir -p ${LOGPATH}
    ln -sf ${LOGPATH} ${CODEPATH}/logs
    [ -d ${DATAPATH} ] || mkdir -p ${DATAPATH}
    if [ -d ${CODEPATH}/data ]; then
        if [ ! -L ${CODEPATH}/data ]; then
            mv ${CODEPATH}/data ${CODEPATH}/data.autobak
        fi
    fi
    ln -sf ${DATAPATH} ${CODEPATH}/data
    [ -d ${RUNPATH} ] || mkdir -p ${RUNPATH}
    ln -sf ${RUNPATH} ${CODEPATH}/run
    ln -sf `which mongod` ${CODEPATH}/bin/mongod 

    rm -rf ${CODEPATH}/conf
fi

service unifi start

exit 0

---

### Post by dino99 on 2015-04-28
found that tuto , maybe it will give you some hints [http://bryanpopham.com/tutorials/Unifi.Ubuntu.Server.Howto.txt](http://bryanpopham.com/tutorials/Unifi.Ubuntu.Server.Howto.txt)

---

### Post by zkab on 2015-04-28
Thanks - I installed unifi in that way.
My problem is that I can't remove the *not-correctly-installed-package*

---

### Post by zkab on 2015-04-28
> **dino99 said:**
> try logging with upstart and check again

Sorry ... don't have enough knowledge to make an upstart with logging.
Are there some tutos ?

---

### Post by kd5ftn2 on 2015-07-27
> **zkab said:**
> Thanks - I installed unifi in that way.
My problem is that I can't remove the *not-correctly-installed-package*

Just hit this same problem, were you able to remove the bad install of unifi-beta?

Since the Unifi install package is designed to use the Upstart init daemon, and Ubuntu 15.04 has switched to Systemd, both the unifi installer and the MongoDB installer will fail. To work around this you can either switch up Upstart, or follow these guides to get the software to work on systemd - which I'm about to try.

[http://deviantengineer.com/2014/08/unifi-controller-centos7/](http://deviantengineer.com/2014/08/unifi-controller-centos7/)
[http://www.csamuel.org/2015/05/10/unifi-systemd-unit-file-for-ubuntu-15-04](http://www.csamuel.org/2015/05/10/unifi-systemd-unit-file-for-ubuntu-15-04)
[http://askubuntu.com/questions/617097/mongodb-2-6-does-not-start-on-ubuntu-15-04](http://askubuntu.com/questions/617097/mongodb-2-6-does-not-start-on-ubuntu-15-04)

---

### Post by zkab on 2015-07-30
I think the latest version of Unifi supports Systemd ...

---

