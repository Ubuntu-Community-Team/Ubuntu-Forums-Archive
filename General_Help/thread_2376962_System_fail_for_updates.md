---
title: "System fail for updates"
date: 2017-11-07
forum: General Help
---

### Post by Gnusboy on 2017-11-07
[FONT=Century Schoolbook L, serif][COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]I'mhaving a difficult time trying to update my system. I usually installregular common updates when they become available. Until last week,it always worked the way it's designed without trouble.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Lastweek, I started getting a message about unable to update package.That's not the exact wording, but it's the gist of it. I triedseveral times and got the same response. But then, I got a message toreboot to finish install up date. [/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Iam going to attach screenshots for the messages I get, to make surey'all know what is happening. I will try to explain the issues as Iprogressed.[/FONT][/COLOR][IMG]https://ubuntuforums.org/[/IMG][IMG]https://ubuntuforums.org/[/IMG][IMG]https://ubuntuforums.org/[/IMG]

[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Thereboot brought another message to enter my password to access problemreports. I have never sen this before, so I canceled out. When Itried to make a report, the message said I'd already reported andcouldn't do it again.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Afterall this, I still have not been able to update my system - It isprobably not a huge issue at the moment, but I want to know what ishappening to my system, because I also have a couple of other issuesI'm concerned about, [/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]butI will save those for a different post to keep this problem asconcise as possible. [/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Ify'all see a major problem at this time, I'll try to give as much infoas I have.[/FONT][/COLOR][/FONT]


Thanks

---

### Post by Bashing-om on 2017-11-07
Gnusboy; Hello;

Difficult to work from images. 
We work best from text files.
In terminal execute and post the results - Between Code Tags -
```

sudo apt update
sudo apt full-upgrade
sudo apt -f install

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

see what tale gets told

---

### Post by Gnusboy on 2017-11-07
Bashing-om
Thanks for your reply. Here's the code you asked for. P.S. I most likely screwed up on the code tags. Forgivable offense?


```
jess@ranha-system:~$ sudo apt updatesudo: unable to resolve host ranha-system
[sudo] password for jess: 
Ign:1 cdrom://Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719) xenial InRelease
Err:2 cdrom://Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719) xenial Release
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit:3 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Get:4 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]    
Get:5 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]     
Hit:6 http://archive.canonical.com/ubuntu xenial InRelease                     
Get:7 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [543 kB]
Get:8 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [51.4 kB]
Get:9 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [85.1 kB]
Get:10 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [60.1 kB]
Get:11 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [62.6 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [517 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [174 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [249 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [652 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [616 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [307 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [227 kB]
Reading package lists... Done                                                  
E: The repository 'cdrom://Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719) xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
jess@ranha-system:~$ 
```

```


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-93 linux-headers-4.4.0-93-generic
  linux-image-4.4.0-93-generic linux-image-extra-4.4.0-93-generic
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  gnome-software gnome-software-common resolvconf ubuntu-software
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 2,821 kB of archives.
After this operation, 8,192 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 resolvconf all 1.78ubuntu5 [52.0 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 ubuntu-software amd64 3.20.5-0ubuntu0.16.04.6 [11.6 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 gnome-software amd64 3.20.5-0ubuntu0.16.04.6 [237 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 gnome-software-common all 3.20.5-0ubuntu0.16.04.6 [2,520 kB]
Fetched 2,821 kB in 5s (538 kB/s)                  
Preconfiguring packages ...
(Reading database ... 273788 files and directories currently installed.)
Preparing to unpack .../resolvconf_1.78ubuntu5_all.deb ...
Unpacking resolvconf (1.78ubuntu5) over (1.78ubuntu4) ...
Preparing to unpack .../ubuntu-software_3.20.5-0ubuntu0.16.04.6_amd64.deb ...
Unpacking ubuntu-software (3.20.5-0ubuntu0.16.04.6) over (3.20.5-0ubuntu0.16.04.5) ...
Preparing to unpack .../gnome-software_3.20.5-0ubuntu0.16.04.6_amd64.deb ...
Unpacking gnome-software (3.20.5-0ubuntu0.16.04.6) over (3.20.5-0ubuntu0.16.04.5) ...
Preparing to unpack .../gnome-software-common_3.20.5-0ubuntu0.16.04.6_all.deb ...
Unpacking gnome-software-common (3.20.5-0ubuntu0.16.04.6) over (3.20.5-0ubuntu0.16.04.5) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for systemd (229-4ubuntu21) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.48.2-0ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Setting up linux-image-4.4.0-98-generic (4.4.0-98.121) ...
Running depmod.
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/cmac.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/md4.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/tgr192.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/cts.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/chacha20poly1305.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/blowfish_common.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/twofish_generic.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/tea.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/anubis.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/lz4.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/842.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/tcrypt.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/async_tx/async_tx.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/async_tx/async_memcpy.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/async_tx/async_xor.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/async_tx/async_pq.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/async_tx/async_raid6_recov.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/async_tx/raid6test.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/drivers/net/bonding/bonding.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/drivers/net/macvtap.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/drivers/net/caif/caif_virtio.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/drivers/net/vmxnet3/vmxnet3.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/drivers/md/raid1.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/drivers/md/raid456.ko: Exec format error
Failed to run depmod
dpkg: error processing package linux-image-4.4.0-98-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-98-generic:
 linux-image-extra-4.4.0-98-generic depends on linux-image-4.4.0-98-generic; however:
  Package linux-image-4.4.0-98-generic is not configured yet.


dpkg: error processing package linux-image-extra-4.4.0-98-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-4.4.0-98-generic; however:
  Package linux-image-4.4.0-98-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-4.4.0-98-generic; however:
  Package linux-image-extra-4.4.0-98-generic is not configured yet.


dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.4.0.98.103); however:
  Package linux-image-generic is not configuredNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                         No apport report written because the error message indicates its a followup error from a previous failure.
                   No apport report written because MaxReports is reached already
  yet.


dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up resolvconf (1.78ubuntu5) ...
Setting up gnome-software-common (3.20.5-0ubuntu0.16.04.6) ...
Setting up gnome-software (3.20.5-0ubuntu0.16.04.6) ...
Setting up ubuntu-software (3.20.5-0ubuntu0.16.04.6) ...
Processing triggers for resolvconf (1.78ubuntu5) ...
Errors were encountered while processing:
 linux-image-4.4.0-98-generic
 linux-image-extra-4.4.0-98-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
```
jess@ranha-system:~$ sudo apt -f installReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-93 linux-headers-4.4.0-93-generic
  linux-image-4.4.0-93-generic linux-image-extra-4.4.0-93-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-4.4.0-98-generic (4.4.0-98.121) ...
Running depmod.
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/cmac.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/md4.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/tgr192.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/cts.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/chacha20poly1305.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/blowfish_common.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/twofish_generic.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/tea.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/anubis.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/lz4.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/842.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/tcrypt.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/async_tx/async_tx.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/async_tx/async_memcpy.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/async_tx/async_xor.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/async_tx/async_pq.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/async_tx/async_raid6_recov.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/async_tx/raid6test.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/drivers/net/bonding/bonding.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/drivers/net/macvtap.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/drivers/net/caif/caif_virtio.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/drivers/net/vmxnet3/vmxnet3.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/drivers/md/raid1.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/drivers/md/raid456.ko: Exec format error
Failed to run depmod
dpkg: error processing package linux-image-4.4.0-98-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-98-generic:
 linux-image-extra-4.4.0-98-generic depends on linux-image-4.4.0-98-generic; however:
  Package linux-image-4.4.0-98-generic is not configured yet.


dpkg: error processing package linux-image-extra-4.4.0-98-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-4.4.0-98-generic; however:
  Package linux-image-4.4.0-98-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-4.4.0-98-generic; however:
  Package linux-image-extra-4.4.0-98-generic is not configured yet.


dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.4.0.98.103); however:
  Package linux-image-generic is not configuredNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                         No apport report written because the error message indicates its a followup error from a previous failure.
                   No apport report written because MaxReports is reached already
  yet.


dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-4.4.0-98-generic
 linux-image-extra-4.4.0-98-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
jess@ranha-system:~$ 

```

---

### Post by Bashing-om on 2017-11-07
Gnusboy; Hummmm.......

1stly is to uncheck the CD source box in the software center.

Then what results:
```

sudo dpkg-reconfigure linux-image-extra-4.4.0-98-generic

```

depending on what the package manager does and says, is what we do next.

[INDENT][INDENT]it be a process
[/INDENT][/INDENT]

---

### Post by Gnusboy on 2017-11-07
If I'm looking in the right place, "software and updates" in the system settings, there is nothing listed as "CD source"
[h=3]All** I've got checked is the standard Cononical supported ... a**nd** Cononical Maintained ....**[/h] There is nothing showing in the box on the bottom "to install from a CD-Rom or DVD[h=3][/h]

---

### Post by ian-weisser on 2017-11-07
> **Gnusboy said:**
> **All[B] I've got checked is the standard Cononical supported ... a**nd** Cononical Maintained ....**[/B]

It's the next tab over: Other Software.

Please look into /var/log/apt/term.log for the day you had the very first problem, and show us that section of the log.

---

### Post by Bashing-om on 2017-11-07
Gnusboy; Well[

I read:
> 
Ign:1 cdrom://Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719) xenial InRelease
Err:2 cdrom://Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719) xenial Release


And the only way I know of for that condition is that the CD source is enabled . OR that the install medium is present .
Other than that ,, I am stuck .

Maybe take a look at what sources are set :
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

[INDENT][INDENT]however, amazing what I do not know
[/INDENT][/INDENT]

---

### Post by Gnusboy on 2017-11-08
Bash 

Sorry for the delay

The CD box WAS checked. I looked at it a dozen times and missed it. Doh!

I unchecked it and ran the log. Here's that result. I haven't rebooted yet. Do you want the output for the other 2 commands you asked for?


 ```
 jess@ranha-system:~$ cat -n /etc/apt/sources.list
     1	# deb cdrom:[Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main restricted
     2	
     3	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4	# newer versions of the distribution.
     5	# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
     6	
     7	## Major bug fix updates produced after the final release of the
     8	## distribution.
     9	# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
    10	
    11	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    12	## team, and may not be under a free licence. Please satisfy yourself as to
    13	## your rights to use the software. Also, please note that software in
    14	## universe WILL NOT receive any review or updates from the Ubuntu security
    15	## team.
    16	deb http://us.archive.ubuntu.com/ubuntu/ xenial universe main
    17	# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe
    18	deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe main
    19	# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
    20	
    21	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22	## team, and may not be under a free licence. Please satisfy yourself as to 
    23	## your rights to use the software. Also, please note that software in 
    24	## multiverse WILL NOT receive any review or updates from the Ubuntu
    25	## security team.
    26	# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
    27	# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
    28	
    29	## N.B. software from this repository may not have been tested as
    30	## extensively as that contained in the main release, although it includes
    31	## newer versions of some applications which may provide useful features.
    32	## Also, please note that software in backports WILL NOT receive any review
    33	## or updates from the Ubuntu security team.
    34	# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
    35	
    36	## Uncomment the following two lines to add software from Canonical's
    37	## 'partner' repository.
    38	## This software is not part of Ubuntu, but is offered by Canonical and the
    39	## respective vendors as a service to Ubuntu users.
    40	deb http://archive.canonical.com/ubuntu xenial partner
    41	# deb-src http://archive.canonical.com/ubuntu xenial partner
    42	
    43	# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
    44	deb http://security.ubuntu.com/ubuntu xenial-security universe main
    45	# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
    46	# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
```
```

jess@ranha-system:~$ 
jess@ranha-system:~$ sudo dpkg-reconfigure linux-image-extra-4.4.0-98-generic

```

---

### Post by Gnusboy on 2017-11-08
When I followed the input code you requested I got some strange result. I high lighted the first line (jess@ranha-system:~$ cat -n /etc/apt/sources.list

It pulled up the console. Don't know the console at all. I've been curious about how that works, but haven't had time to learn. I'll see if I can find a tutorial to learn a bit.
Anyway, here's what came up from that:

     1	# deb cdrom:[Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main restricted
     2	
     3	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4	# newer versions of the distribution.
     5	# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted
     6	
     7	## Major bug fix updates produced after the final release of the
     8	## distribution.
     9	# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
    10	
    11	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    12	## team, and may not be under a free licence. Please satisfy yourself as to
    13	## your rights to use the software. Also, please note that software in
    14	## universe WILL NOT receive any review or updates from the Ubuntu security
    15	## team.
    16	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe main
    17	# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
    18	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe main
    19	# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe
    20	
    21	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22	## team, and may not be under a free licence. Please satisfy yourself as to 
    23	## your rights to use the software. Also, please note that software in 
    24	## multiverse WILL NOT receive any review or updates from the Ubuntu
    25	## security team.
    26	# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
    27	# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
    28	
    29	## N.B. software from this repository may not have been tested as
    30	## extensively as that contained in the main release, although it includes
    31	## newer versions of some applications which may provide useful features.
    32	## Also, please note that software in backports WILL NOT receive any review
    33	## or updates from the Ubuntu security team.
    34	# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
    35	
    36	## Uncomment the following two lines to add software from Canonical's
    37	## 'partner' repository.
    38	## This software is not part of Ubuntu, but is offered by Canonical and the
    39	## respective vendors as a service to Ubuntu users.
    40	deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
    41	# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
    42	
    43	# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
    44	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe main
    45	# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
    46	# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
jess@ranha-system:~$ 
jess@ranha-system:~$ sudo dpkg-reconfigure linux-image-extra-4.4.0-98-generic
[sudo] password for jess: 
/usr/sbin/dpkg-reconfigure: linux-image-extra-4.4.0-98-generic is broken or not fully installed



jess@ranha-system:~$ sudo dpkg-reconfigure linux-image-extra-4.4.0-98-generic
/usr/sbin/dpkg-reconfigure: linux-image-extra-4.4.0-98-generic is broken or not fully installed
jess@ranha-system:~$ cat -n /etc/apt/sources.listsudo dpkg-reconfigure linux-image-extra-4.4.0-98-generic

---

### Post by Gnusboy on 2017-11-08
One minor question: How can I cut something in the terminal?
Say, I enter a command, get the output, but I either made a mistake or something and I want to erase
that piece of code before sending it to you. I want to shorten a piece of the output, but not the entire piece. I tried using the delete and backspace keys w/o results. I looked
for the command, but found the RM code, and the "pipe" but those appear to remove the entire file and used wrong, can really damage the whole system.
Is there a better/safer way to do this?

Thanks

---

### Post by Bashing-om on 2017-11-08
Gnusboy; Making progress :)

As to the query of copy/paste in terminal - that depends on the terminal emulator that you are using .

I run a variant of xterm that supports a wide range of keyboard shortcuts.
Once written the finger moves on and what is the result in a terminal is not editable, What one can do if edits are desired is re-direct the output to a text file; and in the created text file make the edits.
For example the output of the cat command:
```

cat -n /etc/apt/sources.list > sources.txt

```
will re-direct the output of the cat command to the created file sources.txt. In your favorite text editor one can edit the contents of sources.list.

By the way, at some point you will want to re-enable the multiverse repo .

And a huge YES on being very very aware of what you are doing with a 'rm' command . Most often there is no forgiveness of an error ,

Back to the issue at hand:
> 
/usr/sbin/dpkg-reconfigure: linux-image-extra-4.4.0-98-generic is broken or not fully installed

though I have no direct reason to be concerned, I do want to be assured that this is not a no-disk-space issue.

post back - code tags ! -
```

df -h
df -i

```

and we go back to getting that -98 kernel installed.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Gnusboy on 2017-11-08
OK, here's the data from those cmds. Do you see anything that is stopping a backup for my system?

jess@ranha-system:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1.8G     0  1.8G   0% /dev
tmpfs           370M   11M  360M   3% /run
/dev/sda9        73G  8.5G   60G  13% /
tmpfs           1.9G   80M  1.8G   5% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
tmpfs           370M   88K  370M   1% /run/user/1000
/dev/sdb1       976M   60K  976M   1% /media/jess/897fbe47-71a3-4afa-9722-109fc80bc2a4
/dev/sdb3       431G   75G  356G  18% /media/jess/205504c6-6bf7-4fc0-a732-4ea634c2d00a
/dev/sdb2       500G   78G  423G  16% /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3
jess@ranha-system:~$ df -i
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
udev            460202    555  459647    1% /dev
tmpfs           473518    794  472724    1% /run
/dev/sda9      4808704 320176 4488528    7% /
tmpfs           473518    185  473333    1% /dev/shm
tmpfs           473518      5  473513    1% /run/lock
tmpfs           473518     16  473502    1% /sys/fs/cgroup
tmpfs           473518     37  473481    1% /run/user/1000
/dev/sdb1       131072     11  131061    1% /media/jess/897fbe47-71a3-4afa-9722-109fc80bc2a4
/dev/sdb3       110240 110240       0  100% /media/jess/205504c6-6bf7-4fc0-a732-4ea634c2d00a
/dev/sdb2       128000 128000       0  100% /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3

---

### Post by Bashing-om on 2017-11-08
Gnusboy; Welp;

Not space constraints causing " or not fully installed " ; so we move on.

By the way as you do know sdb2 and sdb3 are no longer writable . Might consider archiving a lot of files there .

> 
 stopping a backup for my system?

inodes (df -i) 100% used up : no longer able to make up pointers (addressing) to any new files .


as to next here:
```

sudo apt install --reinstall linux-image-extra-4.4.0-98-generic

```
see what the package manager relates .. screaming and hollering ?

And please for the last time use code tags for your outputs . Maintains formatting and makes it so much easier for us to read .
What we do is tough enough as is .

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by Yellow Pasque on 2017-11-08
```
Errors were encountered while processing:
 linux-image-4.4.0-98-generic
 linux-image-extra-4.4.0-98-generic
 linux-image-generic
 linux-generic
```

It could be a corrupted download of a package. I would purge problematic packages, clean apt's cache, and attempt reinstall (this would force the packages to be downloaded again):
```
sudo apt-get purge linux-image-4.4.0-98-generic linux-image-extra-4.4.0-98-generic linux-image-generic linux-generic
sudo apt-get clean
sudo apt-get install linux-image-4.4.0-98-generic linux-image-extra-4.4.0-98-generic linux-image-generic linux-generic
```
If that goes successfully without spitting out errors, then you can reboot and there should be no crash dialog.

---

### Post by Gnusboy on 2017-11-09
Yeah, I knew as soon as I hit send, that I'd forgotten the code tags. Sorry.

As for this: 
[B][COLOR=#000000]"know sdb2 and sdb3 are no longer writable . Might consider archiving a lot of files there ."
[/COLOR][/B]I didn't know that. And I'm not sure, how or why, but after I added the external 1TBD, the system went from the 2 original partitions to 7 partitions. Then a few months ago, there were 9 partitions - without any input from me.

[FONT=arial][FONT=Verdana]It appears that I have loads of space on my internal 650 GB HDD. I also have an external 1 TBD added about 2 years ago. [/FONT][FONT=Verdana]Everything worked fine (after a huge learning curve for a geezer.) At the time I set up the internal 650-GB drive with 2 partitions. I went through the regular releases up to 14.04. Later, I was needing to back up the system, but that became a problem. I always got the no space left on drive error. 

When I couldn't make a backup, despite a lot of help from fellow Ubuntu-ers -I was finally able to copy some of my most important files - mainly the document files - then I installed Ubuntu 16.04 - hoping that I would create another partition to do a clean install of 16.04. That worked well. I now have 14.04 on 1 partition and 16.04 on the other partition. Initially, there were 2 partitions on the internal drive and 2 on the 1 TBD drive. [/FONT]**those 4 partitions now show up as 9 partitions! **[FONT=Verdana] And one is a 156 GB partition that is tagged as **"unusable"** [/FONT][FONT=Verdana]I don't know how / why. 
I was going to paste the info from both of those drives here, but I can't remember the disk partition app. and I couldn't figure out how to show it to you. The info won't cut & paste. And the long strange trip continues.
P.S. I really appreciate your help. Thank you.[/FONT][/FONT]


```
jess@ranha-system:~$ sudo apt install --reinstall linux-image-extra-4.4.0-98-generic
sudo: unable to resolve host ranha-system
[sudo] password for jess: 
```



```
 jess@ranha-system:~$ sudo apt install --reinstall linux-image-extra-4.4.0-98-generic
sudo: unable to resolve host ranha-system
[sudo] password for jess: 
```

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-93 linux-headers-4.4.0-93-generic
  linux-image-4.4.0-93-generic linux-image-extra-4.4.0-93-generic 
```

```
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for linux-image-extra-4.4.0-98-generic:amd64 
```

---

### Post by Yellow Pasque on 2017-11-09
Please try the advice/commands I gave you in my last post, or let us know why you can't.

---

### Post by Bashing-om on 2017-11-09
Gnusboy; Hey;

+1 as Temüjin advises.

The focus  of this thread is to get the -98 kernel installed - help is what we do and we will address these other issues in new threads.
For now my concern is:
> 
jess@ranha-system:~$ sudo apt install --reinstall linux-image-extra-4.4.0-98-generic
sudo: unable to resolve host ranha-system
[sudo] password for jess:

that we must address in order to install the kernel.

Administration actions to the system must be done from the primary account . What user are you in the above action - is jess that primary account ? 

Do we need to look at your authorization file to determine what user has admin rights ?
```

cat  /etc/group

```

[INDENT][INDENT]all in that process
[/INDENT][/INDENT]

---

### Post by Gnusboy on 2017-11-09
Guys,
This has been interesting. I'm feeling better with the terminal and getting used to cmd syntax.
And ... I especially know why code tags are necessary. I spent a lot of time, I mean a lot, trying to make sure the various pieces of output
married the right way.
Thanks. What's next?

Here is the output from this cmd: 


sudo apt-get purge linux-image-4.4.0-98-generic linux-image-extra-4.4.0-98-generic linux-image-generic linux-generic


```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-93 linux-headers-4.4.0-93-generic linux-headers-4.4.0-98
  linux-headers-4.4.0-98-generic linux-headers-generic
  linux-image-4.4.0-93-generic linux-image-extra-4.4.0-93-generic thermald
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  linux-generic* linux-image-4.4.0-98-generic*
  linux-image-extra-4.4.0-98-generic* linux-image-generic*
0 upgraded, 0 newly installed, 4 to remove and 6 not upgraded.
4 not fully installed or removed.
After this operation, 220 MB disk space will be freed.

Do you want to continue? [Y/n] y 
```

```

(Reading database ... 273789 files and directories currently installed.)
Removing linux-generic (4.4.0.98.103) ...
Removing linux-image-generic (4.4.0.98.103) ...
Removing linux-image-extra-4.4.0-98-generic (4.4.0-98.121) ...
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/cmac.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/md4.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/tgr192.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/cts.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/chacha20poly1305.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/blowfish_common.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/twofish_generic.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/tea.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/anubis.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/lz4.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/842.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/tcrypt.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/async_tx/async_tx.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/async_tx/async_memcpy.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/async_tx/async_xor.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/async_tx/async_pq.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/async_tx/async_raid6_recov.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/async_tx/raid6test.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/drivers/net/bonding/bonding.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/drivers/net/macvtap.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/drivers/net/caif/caif_virtio.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/drivers/net/vmxnet3/vmxnet3.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/drivers/md/raid1.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/drivers/md/raid456.ko: Exec format error
Bus error (core dumped) 
```

```

run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-98-generic /boot/vmlinuz-4.4.0-98-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-98-generic /boot/vmlinuz-4.4.0-98-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-98-generic
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/cmac.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/md4.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/tgr192.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/cts.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/chacha20poly1305.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/blowfish_common.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/twofish_generic.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/tea.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/anubis.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/lz4.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/842.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/tcrypt.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/async_tx/async_tx.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/async_tx/async_memcpy.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/async_tx/async_xor.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/async_tx/async_pq.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/async_tx/async_raid6_recov.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/crypto/async_tx/raid6test.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/drivers/net/bonding/bonding.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/drivers/net/macvtap.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/drivers/net/caif/caif_virtio.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/drivers/net/vmxnet3/vmxnet3.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/drivers/md/raid1.ko: Exec format error
depmod: ERROR: failed to load symbols from /lib/modules/4.4.0-98-generic/kernel/drivers/md/raid456.ko: Exec format error
Bus error (core dumped) 
```

(the following symbols came up when I entered the first line of code to  [COLOR=#000000][FONT=&quot]sudo apt update. Just when I typed it, the console opened on the left half of the screen. Wouldn't close at an attempt to close - flickered and disabled the X close and terminal. I figured it out. The symbols below is how the output looked with the console open, and the following display is what showed after I got the consoled closed.)

 onit continued in the terminal the console was flashing and the weird symbols showed.
But after I figured out how to bypass the console, it output normally.) [/FONT][/COLOR]

sudo apt update
sudo apt full-upgrade
sudo apt -f install


```

depmod: ERROR: Invalid modules.builtin line: &#65533;`Ng&#65533;&#65533;&#65533;&#65533;&#65533;>&#65533;?\&#65533;&#1962;&#65533;x&#65533;cJn?)_&#1717;&#65533;&#65533;J&#65533;&#65533;v&#65533;&#65533;S&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;D&#65533;&#65533;&#65533;X	&#65533;&#65533;)&#877;&#65533;&#65533;an&#1683;&#65533;&#65533;&#65533;bE&#65533;
                              &#65533;o&#65533;7&#65533;&#65533;&#65533;X&#65533;&#65533;&#65533;&#65533;Dz&#65533;&#65533;&#2039;&#65533;&#65533;9&#65533;&#65533;&#65533;>&#65533;J&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;<&#65533;*&#65533;x&#65533;&#65533;&#65533;
                                                                          &#616;&#65533;k&#65533;=&#65533;q&#724;o&#65533;&#65533;d&#65533;&#65533;_&#65533;&#65533;L&#65533;&#65533;&#65533;&#65533;&#65533;o&#65533;E&#65533;&#65533;&#65533;&#65533;&#65533;u&#65533;&#65533;NO&#65533;[&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;#&#65533;z&#65533;&#65533;&#65533;&#65533;&#65533;6 
depmod: ERROR: Invalid modules.builtin line: \`&#65533;E&#65533;&#65533;_	&#65533;92&#65533;&#65533;
                                                             y}\&#65533;;&#65533;;5&#65533;~0}&#65533;n+&#65533;X>!&#65533;~y&#65533;n&#65533;}4&#65533;
          &#65533;+wg&#65533;s&#65533;&#65533;&#65533;1&#65533;&#65533;yL&#65533;rl&#65533;a_&#65533;li&#65533;T&#65533;&#65533;&#65533;&#65533;h&#65533;&#65533;2&#65533;wE&#65533;&&#983;d&#65533;Q|F<&#65533;l&#65533;5NH&#65533;&#65533;&#65533;3&#65533;&#65533;1&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;S&#65533;&#65533;&#65533;&#65533;~&#65533;&#65533;&#65533;&#65533;&#65533;&#679;&#1742;&#65533;&#65533;&#65533;Z&#65533;V&#65533;y&#65533;&#65533;&#65533;<&#65533;&#65533;~~&#65533;&#65533;&#65533;$&#65533;&#65533;{&#65533;&#65533;&#65533;&#65533;.&#65533;&#65533;F&#273;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;r&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;7&#65533;&#65533;mq&#65533;k&#65533;P&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;:&#65533;&#65533;Q¤&#65533;&#65533;Vc&#65533;!1&#65533;&#65533;&#65533;&#65533;&#1203;:&#65533;`1y&#65533;&#65533;&#65533;&#65533;&#65533;'&#65533;e&#1338;&#65533;{?~W&#1023;A&#65533;&#811;m&#65533;&#65533;&#65533;"&#65533;8&#65533;/&#65533;P&#1787;K&#65533;&#65533;0@&#65533;&#65533;&#65533;)_&#65533;&#65533;&#921;km'm(^&#65533;&#807;&#65533;<}%&#65533;&#65533;&#65533;y&#65533;&#65533;gJ&#65533;&#65533;;&#65533;@&#65533;&#593;&#65533;TE&#65533;iW&#830;&#65533;&#65533;&#65533;&#65533;#&#65533;&#65533;Y&#65533;&#65533;&#65533;>&#65533;q&#65533;J&#65533;&#65533;5&#65533;&#65533;&#65533;&#1671;&#65533;z&#65533;+&#65533;&#65533;~g/&#65533;E,&#65533;&#65533;&#65533;&#1926;X=.8&#65533;\&#65533;&#65533;&#65533;
 '&#65533;#&#65533;I&#65533;
        &#406;&#65533;5D&#65533;&#65533;Q&#65533;6&#65533;&#65533;h
                    &#65533;#&#65533;k_;&#65533;P$&#65533;&#65533;t&#65533;q&#65533;Mx&#65533;4&#65533;&#65533;&#327;	
                                                fzGz5&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;?!&#65533;UU&#65533;&#65533;ok&#65533;O&#65533;?!&#65533;W&#65533;&#65533;r?-&#65533;N;&#65533;&#447;&#65533;&#65533;Q.&#65533;e{m	7&#65533;&#65533;&#65533;&#1964;&#65533;tr&#65533;&#65533;&#65533;&#65533;&#65533;2^&#65533;=&#65533;
                                      &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&&#65533;&#65533;f/G&#65533;&#65533;&#65533;-s&#65533;&#65533;+&#65533;U&#65533;&#65533;E&#65533;Q:&#65533;S&#65533;l&#65533;#&#65533;*n&#65533;5&#65533;9&#65533;X|&#65533;9&#65533;r&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;qTL&#65533;&#1277;&#65533;&#65533;z&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;yAf&#65533;L&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;(&#1532;O8&#65533;M&#65533;H&#65533;&#65533;&#65533;n&#65533;u&#65533;&#65533;&#65533;qg&#65533;&#65533;&#65533;u!&#65533;&#65533;.&#65533;&#65533;&#65533;&#65533;Y&#37231;&#65533;&#1716;&#65533;x&#65533;W&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;w&#65533;&#65533;?&>&#65533;&#65533;&#65533;2&#65533;&#65533;&#65533;+&#65533;&#65533;`m&#65533;


depmod: ERROR: Invalid modules.builtin line:  :Ld}&#65533;&#774;&#1763;&#1902;&#65533;kc&#65533;y!&#65533;&#65533;&#65533;hH&#65533;&#65533;}{&#65533;&#65533;&#65533;Ke'pl&#65533;	&#65533;&#65533;<sm&#65533;}&#65533;&#65533; d&#65533; X&#1183;|&#65533;T&#65533;p&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;y&#65533;&#65533;&#65533;&#65533;{nP#&#65533;w&#65533;&#65533;0&#65533;O&#65533;h&#65533;&#65533;&#65533;0&#65533;&#65533;&#826;&#65533;&#65533;B&#65533;&#65533;&#65533;l7&#65533;_&#65533;O&#65533;0&#65533;&#65533;&#949;&#65533;&#65533;&#65533;&#65533;


&#65533;1aQy&#65533;B{W<[&#65533;*&#65533;&#65533;&#65533;&#65533;&#65533;\&#65533;&#65533;n&#65533;&#65533;?&#65533;'D_&#65533;&#65533;&#65533;E;Y&#65533;S&#65533;&#65533;Wl&#65533;&#65533;&#65533;O3--Y&#65533;&#65533;&#65533;R$&#65533;&#65533;&#65533;,;m&#65533;7-&#65533;&#65533;{&#65533;g&#65533;&#65533;a &#65533;?&#65533;&#65533;N&#65533;ftw&#65533;&#65533;&#65533;&#65533;&#65533;


depmod: ERROR: Invalid modules.builtin line: OJc&#65533;&#373;&#65533;&#65533;)&#65533;&#65533;&#65533;&#65533;h&#65533;w&#65533;&#65533;3M&#65533;Sw1&#65533;p&#65533;V;2z&#65533;1&#65533;K&#65533;&#65533;?F&#65533;&#65533;&#65533;^&#65533;z&#65533;&#1712;*&#65533;&#65533;&#65533;&#65533;
&#65533;Uo&#65533;&#65533;&#65533;&#65533;MM'/&#1633;d&#65533;&#65533;&#65533;_5&#65533;&#1635;&#65533;&#65533;&#65533;ZO&#65533;22\C&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#52550;|&#65533;b&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;^C&#65533;&#65533;&#65533;&#65533;&#65533;aG&#65533;^!
                                                                    &#65533;h&#65533;&#65533;6,{&#65533;}&#65533;_&#65533;3|&#65533;&#65533;&#65533;'G&#65533;&#65533;&#65533;&#65533;-Yu&#65533;&#65533;i&#65533;&#65533;Q&#65533;&#65533;&#65533;Pm&#65533;.\&#65533;&#65533;&#65533;&#65533;'&#65533;r&#65533;5&#65533;A&#65533;X&#65533;&#65533;&#65533;?e&#65533;F&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;c3;|&#65533;&#65533;&#65533;f&#65533;T&#65533;*&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;S&#1745;&#65533;<&#65533;;&#65533;&#65533;L&#65533; 9&#65533;&#65533;&#65533;&#65533;]&#65533;&#65533;&#65533;zH&#65533;i&#65533;O&#65533;&#65533;&#65533;&#1798;g&#649;w&#65533;&#65533;&#65533;-&#65533;R&#65533;&#65533;._&#65533;otVRbcæ&#65533;&#65533;u&#65533;&#65533;].C&#65533;&#751;&#65533;&#65533;S<e&#65533;&#65533;OP&#65533;x&#65533;K&#65533;x&#65533;&#65533;&#65533;&#65533;&#65533;tj&#65533;&#65533;&#65533;\&#65533;&#65533;&#65533;


depmod: ERROR: Invalid modules.builtin line: _&#65533;V&#65533;,W&#65533;w&#65533;1&#65533;&#65533;&#65533;
                                                            <&#65533;&#65533;&#65533;z&#65533;&#65533;(&#65533;7&#65533;&#65533;&#65533;
                                                                         &#65533;&#65533;&#65533;3&#65533;To|&#65533;&#65533;&n&#65533;&#65533;&#65533;#;?&#65533;&&#65533;5u^/&#65533;&#65533;&#65533;&#65533;n&#65533;9&#65533;&#65533;=&#65533;&#65533;|C{&#65533;kY&#65533;^&#65533;MW&#65533;&#65533;}&#65533;h&#65533;&#65533;&#65533;&#65533;@T&#391;&#1071;&#65533;aO&#65533;u&#65533;O&#65533;&#65533;&#65533;&#65533;r


depmod: ERROR: Invalid modules.builtin line: &#65533;7&#65533;&#65533;A&#65533;&#65533;~&#65533;&#65533;d
                                                        j&#65533;M&#65533;%&#65533;&#65533;4&#65533;&#65533;j\UC}9&#65533;&#65533;mZÖw&#65533;&#65533;_&#65533;s&#65533;d&#65533;&#65533;&#65533;&#65533;'U&#65533;&#65533;&#65533;6&#65533;&#65533;&#65533;+&#65533;`&#65533;&#65533;&#65533;z&#991;&#65533;o&#65533;&#65533;{S*&#65533;&#65533;&#65533;?&#65533;&#65533;&#65533;W&#65533;&#65533;&#65533;K&#65533;&#65533;8&#65533;&#65533;&#65533;1W|,&#65533;-=w&#65533;&#65533;&#65533;&#541;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;-)mr&#65533;`&#65533;<&#65533;Ð&#65533;&#65533;&#65533;c&#65533;e&#65533;n&#65533;ep&#65533;{9&#65533;&#65533;&#65533;$PL&#65533;&#65533;&#1091;</&#65533;[&#65533;A&#65533;}&#1767;&#65533;\&#65533;&#65533;Q&#65533;&#65533;&#65533;&#65533;ME&#65533;&#65533;&#65533;d&#65533;W&#65533;&#65533;-8wb&#65533;7&#65533;&#65533;&#65533;&#65533;&#65533;M&#65533;&#65533;&#65533;z&#65533;&#65533;lX/^&#65533;&#65533;&#65533;&#65533;C&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;N&#65533;Q&#65533;=&#65533;&#65533;z&#65533;0m<*7&#50842;,&#65533;?&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;6&#65533;)&#65533;f&#65533;&#65533;&#65533;1&#65533;&#65533;C&#65533;&#65533;0W&#65533;EM&#65533;&#65533;&#65533;&#65533;&#65533;6R&#65533;=N&#65533;5|&#65533;Sr&#65533;'J&#65533;v&#65533;7&#65533;{J&#65533;&#65533;&#65533;&#65533;J&#51855;&#1947;&#65533;)&#65533;&#65533;'b&#65533;&#65533;&#65533;2&#65533;&#65533;&#65533;o7Lw&#65533;o&#65533;U&#65533;&#65533;“&#65533;"&#65533;&#65533;&#65533;&#65533;TN&#1511;=&#65533;2&#65533;u&#65533;&#65533;&#65533;&#65533;&#764;s&#65533;&#264;KTM&#65533;&#65533;&&#65533;&#65533;&#65533;&#65533;O-&#65533;ss&#65533;&#65533;&#65533;`KS&#65533;&#65533;&#65533;Y&#65533;&#65533; &#65533;&#65533;
                                &#65533;&#65533;&#65533;Q&#65533;E&#65533;	&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#472;&#65533;#&#65533;&#65533;N&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
depmod: ERROR: Invalid modules.builtin line: &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;6$&#65533;&#65533;&#65533;&#65533;&#65533;7&#65533;&#65533;<&#65533;&#65533;&#65533;~&#65533;&#65533;f&#65533;&#65533;&#65533;&#65533;3}&#65533;I&#65533;&#65533;&#65533;jB|.j&#65533;G&#65533;p&#65533;&#65533;7&#65533;&#65533;&#65533;&#65533;61h&#65533;o&#65533;l`_&#65533;J&#65533;t&#65533;jy&#65533;NF&#65533;}Z'&#65533;&#65533;&#65533;>&#65533;1&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;r^&#65533;&#65533;&#65533;&#65533;&#65533;\&#65533;C&#65533;?*L&#1518;&#65533;]u&#65533;&#65533;&#65533;&#65533;U&#65533;f&#65533;/&#65533;V>&#65533;1&#907;&#65533;&#65533;:&#65533;&#65533;&#65533;&#65533;(&#65533;&#65533;?!&#65533;VBX:&#65533;&#1997;5&
                                      &#65533;1 &#65533;,H&#65533;&#65533;&#65533;_=&#65533;&#65533;3n&#65533;m&#65533;&&#65533;&#1075;&#65533;>&#65533;&#65533;{&#65533;&#65533;U&#65533;&#65533;s&#65533;&#65533;&#65533;3;p&#65533;&#65533;4&#65533;)Gw&#65533;&#65533;&#65533;&#65533;bS&#65533;&#65533;X&#65533;E&#65533;7k&#65533;&#65533;&#2039;&#65533;&#65533;Jb?.&#1963;mZSC&#65533;T4G&#65533;&#1959;&#65533;EvU7&#65533;S&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;$<l&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;rc&#65533;&#65533;&#65533;k^&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;K&#65533;&#65533;N?&#65533;&#65533;"x-:&#65533;}Iy&#65533;8&#65533;&#65533;b&#65533;&#65533;>&#65533;&#65533;&#65533;&#65533;T&#65533;&#65533;&#393;+7&#65533;&#65533;&#65533;<c&#65533;&#65533;


depmod: ERROR: Invalid modules.builtin line: &#65533;mb&#65533;&#65533;Y^&#65533;-w&#65533; &#65533;&#65533;K?&#65533;&#647;:&#65533;&#65533;}&#65533;&#65533;&#420;`&#65533;&#65533;&#65533;@b&#65533;y2j1&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;uKN&#65533;&#65533;-&#65533;&#65533;&#65533;&#65533;&#65533;q&#65533;&#65533;&#65533;&#65533;[S&#65533;TM&#65533;L&#65533;&#65533;&#65533;8R&#65533;	&#65533;&#65533;&#65533;&&#65533;&#1222;Y&#65533;&#65533;jmV&#65533;{]&#65533;wz+&#65533;j&#1340;&#65533;&#1427;&#65533;&#65533;bm&#65533;>&#65533;&#65533;&#65533;y&#65533;&#65533;{
       &#65533;N~|T&#65533;qw&#32077;Y&#65533;Q&#65533;\&#65533;(&#65533;&#65533;&#65533;;g&#53713;&#65533;{q5&#65533;&#65533;]%0M&#65533;&#494;!&#65533;&#65533;&#65533;?&#65533;^&#65533;Q&#65533;&#360;ƒ_f&#65533;gP&#770;IC[&#65533;_&#65533;&#65533;Yi&#65533;&#65533;K|-ug&#65533;s&#65533;<&#65533;&#65533;&#65533;


depmod: ERROR: Invalid modules.builtin line: "(&#65533;V&#65533;h%&#65533;&#65533;0&#65533;!;P&#65533;&#65533;btt&#65533;$o&#65533;&#65533;w&#65533;[&#65533;&#65533;O&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;O&#65533;Lv&#65533;+&#65533;X&#65533;&#65533;sQ%J&#7109;&#65533;}e&#65533;1&#65533;&#65533;8&#65533;G&#65533;ö&#65533;:/&#65533;&#65533;J&#65533;+&#65533;R&#65533;&#65533;o&#65533;&#65533;C&#65533;^&#65533;&#65533;&#65533;&#65533;&#65533;<&#65533;&#65533;&#65533;4&#65533;K&#65533;&#65533;&#65533;&#65533;[&#65533;&#65533;&#65533;	&#65533;&#65533;&#65533;Mz8&#65533;&#65533;&#65533;Ae&#65533;<&#65533;Fe&#65533;}&#65533;G&#65533;w&#65533;Q&#65533;&#65533;F&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;v(&#65533;&#65533;&#65533;&#65533;!&#65533;n&#65533;&#65533;V&#65533;&#65533;&#65533;&#65533;&#65533;P&#65533;gs&#65533;&#1172;&#65533;p&#65533;&#65533;&#65533;&#65533;%&#65533;E&#65533;&#65533;#&#65533;+*:N&#65533;&#65533;m&#65533;&#65533;j&#65533;?&#65533;)$@\&#65533;&#65533;&#65533;&#65533;W&#65533;]z&#65533;?%TX&#65533;&#65533;z&#65533;&#65533;&#65533;}


depmod: ERROR: Invalid modules.builtin line: &#65533;Zi&#1263;&#65533;5&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;%{&#65533;&#65533;&#958;&#37990;&#65533;	&#65533;&#500;)g&#65533;&#65533;&#65533;&#65533;&#65533;whP&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;2V&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;,
depmod: ERROR: Invalid modules.builtin line: &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;B&#65533;&#65533;&#65533;Sf&#1818;&#65533;w&#65533;&#65533;SV&#65533;y&#65533;&#65533;&#65533;&#65533;&#65533;{&#65533;M&#65533;&#65533;/r&#65533;&#65533;}S_&#922;y}&#65533;&#65533;&#65533;&#65533;&#65533;#&#65533;&#65533;&#65533;>&#65533;=&#65533;?V&#65533;&#65533;&#65533;&#65533;rE&#65533;&#65533;&#1736;.&#65533;&#65533;&#65533;E&#1889;=f&#65533;&#65533;R9&#65533;&#65533;&#65533;&#65533;y&#65533;&#991;t&#65533;&#65533;&#65533;7+We\&#793;


depmod: ERROR: Invalid modules.builtin line: }&#65533;S&#65533;
am&#65533;F&#60761;&#65533;U#u&#65533;o>&#65533;&#65533;&#65533;&#65533;t&#65533;&#65533;&#65533;v&#65533;&#65533;d&#65533;&#65533;W&#65533;`&#451;&#65533;v.]&#65533;&#65533;&#65533;KE&#65533;&#65533;&#65533;0&#65533;&#65533;&#65533;[&#65533;*&#65533;&#65533;Z&#65533;CY&#65533;&#65533;&#65533;&#65533;sKU&#65533;&#65533;:&#65533;&#65533;&#65533;&#65533;Z&#65533;&#65533;|9]&#65533;&#65533;&#65533;&#65533;&#65533;&#1202;h&#65533;&#65533;}&#65533;&#1863;&#65533;D=&#65533;&#65533;Xo&#65533;"~+&#65533;o&#65533;O&#65533;&#65533;e&#39657;&#65533;j&#65533;&#65533;M&#65533;6&#65533;&#351;&#65533;&#65533;,&#65533;m&#65533;&#65533;Q&#65533;H&#65533;o&#65533;&#65533;&#65533;&#65533;&#41629;*&#65533;#z&#65533;&#65533;6/&#65533;&#65533;&#65533;%&#65533;&#65533;e&#65533;&#65533;+&#65533;!&#65533;[&#65533;&#65533;&#65533;&#65533;R&#65533;&#65533;q&#65533;&#65533;&#65533;&#65533;&#65533;6&#44890;&#65533;&#65533;&&#65533;&#65533;V&#65533;i&#65533;s&#65533;S&#65533;>&#65533;&#109917;&


depmod: ERROR: Invalid modules.builtin line: &#65533;&#65533;cO&#65533;&#65533;U&#65533;&#65533;&#65533;&#65533;r&#65533;&#65533;&#65533;D&#1309;&#65533;&#65533;/&#65533;tS&#65533;&#65533;<p!&#65533;&#65533;AR_&#65533;X_u&#65533;S(&#65533;w&#65533;&#65533;&#65533;D&#65533;KS&#65533;&#65533;&#65533;&#65533;$&#65533;Xg&#65533;&#65533;&#683;=&#65533;#;s&#65533;o&#65533;&#65533;s&#65533;&#65533;F&#65533;.&#65533;D


depmod: ERROR: Invalid modules.builtin line: &#65533;&#65533;N&#65533;>&#65533;n&#65533;mK

```


```

run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-98-generic /boot/vmlinuz-4.4.0-98-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-98-generic /boot/vmlinuz-4.4.0-98-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-98-generic /boot/vmlinuz-4.4.0-98-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-98-generic /boot/vmlinuz-4.4.0-98-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-98-generic
Found initrd image: /boot/initrd.img-4.4.0-98-generic
Found linux image: /boot/vmlinuz-4.4.0-97-generic
Found initrd image: /boot/initrd.img-4.4.0-97-generic
Found linux image: /boot/vmlinuz-4.4.0-96-generic
Found initrd image: /boot/initrd.img-4.4.0-96-generic
Found linux image: /boot/vmlinuz-4.4.0-93-generic
Found initrd image: /boot/initrd.img-4.4.0-93-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 11.10 (11.10) on /dev/sda1
Found Ubuntu 12.04.5 LTS (12.04) on /dev/sda6
Found Ubuntu 14.04.5 LTS (14.04) on /dev/sda8
done
Purging configuration files for linux-image-extra-4.4.0-98-generic (4.4.0-98.121) ...
Removing linux-image-4.4.0-98-generic (4.4.0-98.121) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-98-generic /boot/vmlinuz-4.4.0-98-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-98-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-98-generic /boot/vmlinuz-4.4.0-98-generic

```

```

Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-97-generic
Found initrd image: /boot/initrd.img-4.4.0-97-generic
Found linux image: /boot/vmlinuz-4.4.0-96-generic
Found initrd image: /boot/initrd.img-4.4.0-96-generic
Found linux image: /boot/vmlinuz-4.4.0-93-generic
Found initrd image: /boot/initrd.img-4.4.0-93-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 11.10 (11.10) on /dev/sda1
Found Ubuntu 12.04.5 LTS (12.04) on /dev/sda6
Found Ubuntu 14.04.5 LTS (14.04) on /dev/sda8
done
Purging configuration files for linux-image-4.4.0-98-generic (4.4.0-98.121) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-98-generic /boot/vmlinuz-4.4.0-98-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-98-generic /boot/vmlinuz-4.4.0-98-generic

```

Then this cmd: sudo apt full-upgrade

```

jess@ranha-system:~$ sudo apt full-upgrade
[sudo] password for jess: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-93 linux-headers-4.4.0-93-generic linux-headers-4.4.0-96 linux-headers-4.4.0-96-generic linux-headers-generic linux-image-4.4.0-93-generic linux-image-4.4.0-96-generic
  linux-image-extra-4.4.0-93-generic linux-image-extra-4.4.0-96-generic thermald
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  libnm-gtk-common libnm-gtk0 libnma-common libnma0 network-manager-gnome snapd
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 13.1 MB of archives.
After this operation, 8,385 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y


```
```
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libnm-gtk0 amd64 1.2.6-0ubuntu0.16.04.4 [70.3 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libnm-gtk-common all 1.2.6-0ubuntu0.16.04.4 [5,694 B]
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 network-manager-gnome amd64 1.2.6-0ubuntu0.16.04.4 [291 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libnma0 amd64 1.2.6-0ubuntu0.16.04.4 [66.5 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libnma-common all 1.2.6-0ubuntu0.16.04.4 [5,684 B]
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 snapd amd64 2.28.5 [12.6 MB]
Fetched 13.1 MB in 22s (580 kB/s)                                                                                                                                                                          
(Reading database ... 273784 files and directories currently installed.)
Preparing to unpack .../libnm-gtk0_1.2.6-0ubuntu0.16.04.4_amd64.deb ...
Unpacking libnm-gtk0:amd64 (1.2.6-0ubuntu0.16.04.4) over (1.2.6-0ubuntu0.16.04.3) ...
Preparing to unpack .../libnm-gtk-common_1.2.6-0ubuntu0.16.04.4_all.deb ...
Unpacking libnm-gtk-common (1.2.6-0ubuntu0.16.04.4) over (1.2.6-0ubuntu0.16.04.3) ...
Preparing to unpack .../network-manager-gnome_1.2.6-0ubuntu0.16.04.4_amd64.deb ...
Unpacking network-manager-gnome (1.2.6-0ubuntu0.16.04.4) over (1.2.6-0ubuntu0.16.04.3) ...
Preparing to unpack .../libnma0_1.2.6-0ubuntu0.16.04.4_amd64.deb ...
Unpacking libnma0:amd64 (1.2.6-0ubuntu0.16.04.4) over (1.2.6-0ubuntu0.16.04.3) ...
Preparing to unpack .../libnma-common_1.2.6-0ubuntu0.16.04.4_all.deb ...
Unpacking libnma-common (1.2.6-0ubuntu0.16.04.4) over (1.2.6-0ubuntu0.16.04.3) ...
Preparing to unpack .../snapd_2.28.5_amd64.deb ...
Warning: Stopping snapd.service, but it can still be activated by:
  snapd.socket 
```

```

Unpacking snapd (2.28.5) over (2.27.5) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for gconf2 (3.2.6-3ubuntu6) ...
Processing triggers for libglib2.0-0:amd64 (2.48.2-0ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Setting up libnm-gtk-common (1.2.6-0ubuntu0.16.04.4) ...
Setting up libnm-gtk0:amd64 (1.2.6-0ubuntu0.16.04.4) ...
Setting up libnma-common (1.2.6-0ubuntu0.16.04.4) ...
Setting up libnma0:amd64 (1.2.6-0ubuntu0.16.04.4) ...
Setting up network-manager-gnome (1.2.6-0ubuntu0.16.04.4) ...
Setting up snapd (2.28.5) ...
Installing new version of config file /etc/apparmor.d/usr.lib.snapd.snap-confine.real ...
Installing new version of config file /etc/profile.d/apps-bin-path.sh ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
jess@ranha-system:~$ 
```

```

jess@ranha-system:~$ sudo apt -f install
sudo: unable to resolve host ranha-system
[sudo] password for jess: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-93 linux-headers-4.4.0-93-generic linux-headers-4.4.0-96 linux-headers-4.4.0-96-generic linux-headers-generic linux-image-4.4.0-93-generic linux-image-4.4.0-96-generic
  linux-image-extra-4.4.0-93-generic linux-image-extra-4.4.0-96-generic thermald
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jess@ranha-system:~$ 

```

---

### Post by Yellow Pasque on 2017-11-09
Edit: nvm

---

### Post by Gnusboy on 2017-11-10
I had a problem when I logged in today. several error messages. I don't know what they mean, or if they are important.
I sent in the error reports and looked at the system logs, but I'm not sure what I'm looking at.

I also did a trial run on a backup, but still get out of space on drive msg. I'd like to fix that, as I have many important files I can't lose.

What ever help is available is appreciated. Thanks

---

### Post by Bashing-om on 2017-11-10
Gnusboy; Hey ...

Help is what we do .. but -
threads are like dead men -> one to the box :)

As this thread is now concluded :
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

And open a new thread on the new issues .

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by Gnusboy on 2017-11-10
Awesome! Thanks again.

---

