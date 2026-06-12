---
title: "Installing NUT wit APT"
date: 2014-12-21
forum: General Help
---

### Post by carelburger on 2014-12-21
I am trying to install NUT on my server running Ubuntu Desktop 14.04 and APT fails installing. I have never come across this error in the 8 years of using Ubuntu. Not sure where to start looking. Could anyone maybe point me in the right direction?

```
apt-get -y install nut-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nut-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.

Setting up nut-server (2.7.1-1ubuntu1) ...
insserv: Service udev has to be enabled to start service nut-server
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package nut-server (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of nut:
 nut depends on nut-server; however:
  Package nut-server is not configured yet.

dpkg: error processing package nut (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          
Errors were encountered while processing:
 nut-server
 nut
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Bashing-om on 2014-12-21
carelburger; Humm ...

Does the package manager give us any additional hints/info with:
As a normal user interface:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgade
sudo dpkg-reconfigure nut-server

```

[INDENT][INDENT]a failure to communicate ?
[/INDENT][/INDENT]

---

### Post by carelburger on 2014-12-21
No none of that helps. Gives the exact same output. No network or communication issues.

---

### Post by bapoumba on 2014-12-21
```
nut-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
```

Which dependencies are not satisfied ?
[http://packages.ubuntu.com/trusty/nut-server](http://packages.ubuntu.com/trusty/nut-server)

I'm guessing you have all the ubuntu repositories enabled ?
```
cat -n /etc/apt/sources.list
```

---

### Post by carelburger on 2014-12-21
Yes they are all on:

```
# deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)]/ trusty main restricted
     2	
     3	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4	# newer versions of the distribution.
     5	deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) trusty main restricted
     6	deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) trusty main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
    11	deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team. Also, please note that software in universe WILL NOT receive any
    15	## review or updates from the Ubuntu security team.
    16	deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) trusty universe
    17	deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) trusty universe
    18	deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) trusty-updates universe
    19	deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) trusty-updates universe
    20	
    21	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22	## team, and may not be under a free licence. Please satisfy yourself as to 
    23	## your rights to use the software. Also, please note that software in 
    24	## multiverse WILL NOT receive any review or updates from the Ubuntu
    25	## security team.
    26	deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) trusty multiverse
    27	deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) trusty multiverse
    28	deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
    29	deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
    30	
    31	## N.B. software from this repository may not have been tested as
    32	## extensively as that contained in the main release, although it includes
    33	## newer versions of some applications which may provide useful features.
    34	## Also, please note that software in backports WILL NOT receive any review
    35	## or updates from the Ubuntu security team.
    36	deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
    37	deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
    38	
    39	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
    40	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
    41	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
    42	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
    43	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
    44	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
    45	
    46	## Uncomment the following two lines to add software from Canonical's
    47	## 'partner' repository.
    48	## This software is not part of Ubuntu, but is offered by Canonical and the
    49	## respective vendors as a service to Ubuntu users.
    50	# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
    51	# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
    52	
    53	## This software is not part of Ubuntu, but is offered by third-party
    54	## developers who want to ship their latest software.
    55	deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
    56	deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
```

But this concerns me :

```
Setting up nut-server (2.7.1-1ubuntu1) ...
insserv: Service udev has to be enabled to start service nut-server
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
```

How do I check that everything is normal with udev?

---

### Post by bapoumba on 2014-12-22
Any ppa ?
```
ls -la /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*
```

I'm still wondering which package is not fully installed or removed :
```
sudo apt-get -f install
```

If I understand this correctly, insserv is used to enable an init script (boot script) by reading the comment header of the script (quoting) so that means the problem is either with insserv or the script itself imho. Your error states :
> update-rc.d: error: insserv rejected the script header
[https://wiki.debian.org/LSBInitScripts/DependencyBasedBoot](https://wiki.debian.org/LSBInitScripts/DependencyBasedBoot)
[http://www.linux-tutorial.info/modules.php?name=ManPage&sec=8&manpage=insserv](http://www.linux-tutorial.info/modules.php?name=ManPage&sec=8&manpage=insserv)

According to this : [http://svn.savannah.nongnu.org/viewvc/insserv/trunk/insserv.c?root=sysvinit&view=markup](http://svn.savannah.nongnu.org/viewvc/insserv/trunk/insserv.c?root=sysvinit&view=markup), insserv is going to be looking in /etc/init.d
The following part, that looks like your error, is int the "Check dependencies for name as a service" section :
```
warn("FATAL: service %s has to be enabled to use service %s\n",
		 name, cur->name);
```

So I'd say, fix the dependencies or fix the script header. I probably can help you around with the first one (please run the -f install command to see which package is not fully installed), not sure about the second :)

---

### Post by carelburger on 2014-12-22
I have already tried to fix the dependency issues with ***apt-get -f install***.

```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up nut-server (2.7.1-1ubuntu1) ...
insserv: Service udev has to be enabled to start service nut-server
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package nut-server (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of nut:
 nut depends on nut-server; however:
  Package nut-server is not configured yet.

dpkg: error processing package nut (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 nut-server
 nut
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I have check that udev is installed.

```
apt-get install udev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
udev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

Then I remove NUT :

```
apt-get remove --purge nut-server nut-client
```

The I tried to reinstall:

```
apt-get install nut-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libupsclient3 nut-client
Suggested packages:
  nut-monitor nut-cgi nut-snmp nut-ipmi nut-xml
The following NEW packages will be installed:
  libupsclient3 nut-client nut-server
0 upgraded, 3 newly installed, 0 to remove and 2 not upgraded.
Need to get 0 B/756 kB of archives.
After this operation, 5*101 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Selecting previously unselected package libupsclient3:amd64.
(Reading database ... 219350 files and directories currently installed.)
Preparing to unpack .../libupsclient3_2.7.1-1ubuntu1_amd64.deb ...
Unpacking libupsclient3:amd64 (2.7.1-1ubuntu1) ...
Selecting previously unselected package nut-client.
Preparing to unpack .../nut-client_2.7.1-1ubuntu1_amd64.deb ...
Unpacking nut-client (2.7.1-1ubuntu1) ...
Selecting previously unselected package nut-server.
Preparing to unpack .../nut-server_2.7.1-1ubuntu1_amd64.deb ...
Unpacking nut-server (2.7.1-1ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
Setting up libupsclient3:amd64 (2.7.1-1ubuntu1) ...
Setting up nut-client (2.7.1-1ubuntu1) ...
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cron'
insserv: warning: script 'mongodb' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `mongodb'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `mongodb'
insserv: warning: script 'friendly-recovery' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `friendly-recovery'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `friendly-recovery'
 * nut-client disabled, please adjust the configuration to your needs
 * Then set MODE to a suitable value in /etc/nut/nut.conf to enable it
Processing triggers for ureadahead (0.100.0-16) ...
Setting up nut-server (2.7.1-1ubuntu1) ...
insserv: Service udev has to be enabled to start service nut-server
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package nut-server (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for libc-bin (2.19-0ubuntu6.4) ...
Processing triggers for ureadahead (0.100.0-16) ...
Errors were encountered while processing:
 nut-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Seems like the same problem still. I did however change ubuntu to legacy boot order earlier to try and solve an issue with ZFS and SAMBA. This was before installing NUT. The ZFS issue now is resolved and I removed the file which was created by ***touch /etc/init.d/.legacy-bootordering***. AFAIK after ***rm /etc/init.d/.legacy-bootordering*** everything should have gone back to normal. Could this have caused interference with NUT?

---

### Post by bapoumba on 2014-12-22
```
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cron'
insserv: warning: script 'mongodb' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `mongodb'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `mongodb'
insserv: warning: script 'friendly-recovery' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `friendly-recovery'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `friendly-recovery'
 * nut-client disabled, please adjust the configuration to your needs
 * Then set MODE to a suitable value in /etc/nut/nut.conf to enable it
```

An old bug that looks solved but was triggering the same errors : [https://bugs.launchpad.net/ubuntu/+source/insserv/+bug/467000](https://bugs.launchpad.net/ubuntu/+source/insserv/+bug/467000) ; [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=547235](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=547235)

May be here a solution to edit the int scripts : [http://help.directadmin.com/item.php?id=379](http://help.directadmin.com/item.php?id=379), but not sure if this is the right solution.
Here is the beginning of /etc/init.d/cron, I do not have the two other ones :
```
#!/bin/sh
# Start/stop the cron daemon.
#
### BEGIN INIT INFO
# Provides:          cron
# Required-Start:    $remote_fs $syslog $time
# Required-Stop:     $remote_fs $syslog $time
# Should-Start:      $network $named slapd autofs ypbind nscd nslcd
# Should-Stop:       $network $named slapd autofs ypbind nscd nslcd
# Default-Start:     2 3 4 5
# Default-Stop:
# Short-Description: Regular background program processing daemon
# Description:       cron is a standard UNIX program that runs user-specified 
#                    programs at periodic scheduled times. vixie cron adds a 
#                    number of features to the basic UNIX cron, including better
#                    security and more powerful configuration options.
### END INIT INFO
```

---

