---
title: "System never gets passed Ubuntu logo loading."
date: 2013-11-15
forum: General Help
---

### Post by adellaci on 2013-11-15
Ubuntu 12.02 LTS i386
kerenel 3.2.0-56-generic-pae

When i reboot my system it gets to the logo for the desktop but doesn't go any further. Any suggestions where to look at why it will not continue?

I can boot to the recovery mode and login at coomand, but have to run mount command to get to r/w mode.

---

### Post by ajgreeny on 2013-11-15
Is this a new installation or has the change happened suddenly after being able to boot properly in the past?

---

### Post by adellaci on 2013-11-15
The system has been running for about 9 month, daul boot with windows xp. About month, maybe a month an half i add the Xubuntu, Lubuntu, and Kubuntu desks top to the system. Had run great, no problems. I had removed some desktop apps that i had installed recently, but i'm pretty sure i have rebooted since with no issues.

---

### Post by ajgreeny on 2013-11-16
Were there any specific updates just before this problem appeared.  You can find all updates to the system by using command ```
grep -iw upgrade /var/log/dpkg.log.1 && grep -iw upgrade /var/log/dpkg.log
``` which will list all of them by date.  If there is an error about **dpkg.log.1** not found remove the part of the command up to and including the &&.

---

### Post by adellaci on 2013-11-16
Check the log and the last updates were 11/08/2013, many days before i had this issue. Last was the Linux Kernel 3.2.0.55.65, and computer was rebooted after that update and was working fine at that time.

---

### Post by adellaci on 2013-11-18
Ran boot-repair. It did not fix the problem. Which logs can i look to see what maybe failing?

---

### Post by adellaci on 2013-11-18
Looking in /var/log/boot 

```
(Nothing has been logged yet.)
```

Looking in /var/log/boot.log

```

[FONT=system]fsck from util-linux 2.20.1
/dev/sda3: clean, 1258383/30900224 files, 16741719/123585024 blocks
 * Stopping Enabling additional executable binary formats [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Starting  Uncomplicated firewall [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Starting  configure network device security [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Starting  configure network device security [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Starting  configure network device [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Starting  configure network device [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Starting  configure network device security [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Starting  bluetooth daemon [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Starting  Mount network filesystems [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Starting  Upstart job to start rpcbind on boot only [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Starting  SMB/CIFS File Server [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Starting  Failsafe Boot Delay [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Stopping Upstart job to start rpcbind on boot only [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Stopping Mount network filesystem  [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Starting  RPC portmapper replacment [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Starting  configure network device [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
/proc/sef/fd/9: 28: /proc/sef/fd/9: /etc/init.d/rcS: not found
 * Stopping Failsafe Boot Delay  [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Stopping load modules from /etc/modules [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Starting  modem connection manager [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Starting  configure network device security [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Starting  network connection manager [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Starting  Start this job to wait until rpcbind is started or fails to start [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Stopping rpcsec_gsss daemon [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Stopping Start this job to wait until rpcbind is started or fails to start [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Starting  Bridge socket events into upstart [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Starting  NFSv4 id <-> name mapper [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Starting  NSM status monitor [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Starting  configure network device security [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Starting  configure network device [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Starting  NetBIOS name server [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Starting  Mount network filesystems [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Stopping Mount network filesystems [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Stopping cold plug device [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Stopping log inital device creation [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Starting  load fallback graphics devices [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Starting  enable remaining boot-time encrypted bloack deives [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Starting  configure network device security [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Starting  load fallback graphicd devices [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Stopping enable remaining boot-time encrypted bloack deives [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Starting  CUPS printing spooler/server [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Starting  emergency keypress handling [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Stopping OpenSSH server [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Stopping system logging daemon  [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ][/FONT]
[FONT=system] * Stopping SMB/CIFS File Server  [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
[FONT=system] * Stopping Bridge socket events into upstart  [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
[FONT=system] * Stopping NetBIOS name server  [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
[FONT=system] * Stopping Initialize or finalize resolvconf  [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ][/FONT][/FONT][/FONT][/FONT]
[FONT=system] * Stopping [FONT=system]emergency keypress handling [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
[FONT=system] * Starting  System V runlevel compatibility [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ][/FONT][/FONT][/FONT]
[FONT=system] * Starting  save syatem clock to hardware clock [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ][/FONT]
[FONT=system] * Stopping device node and kernel event manager [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ][/FONT]
[FONT=system] * Stopping Bridge udev events into upstart [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ][/FONT]
[FONT=system][FONT=system] * Stoppng  NFSv4 id <-> name mapper [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
 * Asking all remaining processes to terminate[/FONT][/FONT] [FONT=system]           [COLOR=#0000ff]^[[/COLOR][COLOR=#000000][80[/COLOR]G [COLOR=#0000ff]^M[/COLOR][/FONT][FONT=system][FONT=system][COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
[/FONT][/FONT][FONT=system] [FONT=system][FONT=system]* Startng  Send event to indicate plymouth is up [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[FONT=system][FONT=system][FONT=system] [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][31mfail[FONT=system][FONT=system][FONT=system] [COLOR=#0000FF]^[[/COLOR][/FONT][/FONT][/FONT][/COLOR][/FONT][/FONT][/FONT][/COLOR][ OK ]
[FONT=system] * Stopping  CUPS printing spooler/server [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ][/FONT][/FONT][/FONT][/FONT]
[FONT=system] * All processes ended within 1 seconds....           [COLOR=#0000ff]^[[/COLOR][COLOR=#000000][80[/COLOR]G [COLOR=#0000ff]^M^[/COLOR][COLOR=#0000FF][[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
[COLOR=#000000][FONT=system][FONT=system][FONT=system][FONT=system] * Stopping  CUPS printing spooler/server [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
rpcbind: rpcbind terminating on signal. Restart with "rpcbind [/FONT][/FONT][/FONT][/FONT][/COLOR][/FONT]-w"[FONT=system][COLOR=#0000ff]^M
[/COLOR][/FONT][FONT=system][FONT=system] * Stoppng  NSM statuds monitor [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ][/FONT][/FONT]
[FONT=system][FONT=system] * Stoppng  RPC portmapper replacement[COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ][/FONT][/FONT]
[FONT=system][FONT=system] * Stoppng  save system clock to hardware clock [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ][/FONT][/FONT]
[FONT=system][FONT=system] * Stoppng  mDNS/DNS-SD daemon [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ][/FONT][/FONT]
[FONT=system][FONT=system] * Stoppng  bluetooth daemon [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
[FONT=system][FONT=system] * Stoppng  network connection manager [COLOR=#0000FF]^[[/COLOR][COLOR=#000000][74G[/COLOR][ OK ][/FONT][/FONT][/FONT][/FONT]
modem-manager [999]: <info> Caught siganl 15, shuting down...
[FONT=system][COLOR=#0000ff]^M
[/COLOR][/FONT][FONT=system][FONT=system][FONT=system][FONT=system] nm-dispatcher.action: Caught siganl 15, shutting down... [/FONT][/FONT][/FONT][/FONT][FONT=system][COLOR=#0000ff]^M
[/COLOR][COLOR=#000000]  * Deconfiguring network interface...[FONT=system]           [COLOR=#0000ff]^[[/COLOR][COLOR=#000000][80[/COLOR]G [COLOR=#0000ff]^M^[/COLOR][COLOR=#0000FF][[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
  *  Deactivating swap...[FONT=system]           [COLOR=#0000ff]^[[/COLOR][COLOR=#000000][80[/COLOR]G [COLOR=#0000ff]^M^[/COLOR][COLOR=#0000FF][[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
  * Stopping remaining crypto disks....[FONT=system]           [COLOR=#0000ff]^[[/COLOR][COLOR=#000000][80[/COLOR]G [COLOR=#0000ff]^M^[/COLOR][COLOR=#0000FF][[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
  * stopping early crypto disks [FONT=system]           [COLOR=#0000ff]^[[/COLOR][COLOR=#000000][80[/COLOR]G [COLOR=#0000ff]^M^[/COLOR][COLOR=#0000FF][[/COLOR][COLOR=#000000][74G[/COLOR][ OK ]
umount: /run/lock: not mounted
mount: / is busy
  * Will now restart[/FONT][/FONT][/FONT][/FONT]
[/COLOR][/FONT]
```

After rebooting system and going into the windows system the clock is all ways set UTC instead of EST -5:00

I did check for the file /etc/init.d/rcS, it is missing in that directory

---

### Post by adellaci on 2013-11-18
Looked in my laptop that was setup up just like my desktop, and saw that the file was there.

I reboot the system to recovery mode. From the menu, selected "root                 Drop to root shell prompt" Entered root password for maintenance.

Then entered following commands:

```

~# touch /etc/init.d/rcS
~# vim /etc/init.d/rcS

```

Then typed:

```

i
#! /bin/sh
#
# rcS
#
# Call all S??* scripts in /etc/rcS.d/ in numerical/alphabetical order
#

exec /etc/init.d/rc S
ECS
:wq

```

Then made it exec

```


chmod +x /etc/init.d/rcS


```

Rebooted the system and it came up. Its a little screwy, but at a point where i just need to fix a few little things. I had to have fat fingered the deletion of that file, just not sure when and how.
[URL="http://ubuntuforums.org/member.php?u=27747"]                                                      
[/URL][**[COLOR=#000000]ajgreeny[/COLOR]**]("http://ubuntuforums.org/member.php?u=27747") thank you for taking the time to help me.

---

