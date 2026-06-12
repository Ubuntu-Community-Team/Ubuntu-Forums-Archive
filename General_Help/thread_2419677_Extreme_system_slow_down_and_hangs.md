---
title: "Extreme system slow down and hangs"
date: 2019-05-24
forum: General Help
---

### Post by Gnusboy on 2019-05-24
Hi all

I'm running Ubuntu 16.04 on AMD 9250 



I  had a strange problem with Ubuntu today that I've never seen before. I  had scanned a couple of photos and was closing the Simple Scan program  when my system started getting slower and slower. 

All  I had open was Firefox, Simple Scan,  and the file manager open. I was  trying to save two photo scans. The system kept hanging, at one point  for more than a minute. At that point, 

I started closing all the open files, a couple of pages in Firefox and Deja Dup notice that was set for a scheduled backup. As I did this, the system did not get better so I disconnected the 1 TB external drive. 

And did a reboot. Even that was slow and it took nearly a minute for the splash page to load.


I  checked the system logwhich showed numerous repeating lines of the  usual startup code until itwas finally running.  The system seems to  working pretty well now, but I'd like to know what caused the problem. 

I don't know why pulseaudio shows here, I seldom use it and it wasn't open.



I've posted some of what shows on the syslog after the reboot. I don't know if it's relevant but here's some of what I see. There were many time-outs  and alot of it of this repeates, but I don't know its   significance.  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------



 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


.




Thank you

---

### Post by TheFu on 2019-05-24
Systems that get slow, usually have 1 of 3 issues.
* failing hardware
* incorrect software configuration
* low RAM

Some data would be helpful:```


$ inxi -bz
$ free -h
$ swapon -s
$ sudo egrep -i 'warn|error' /var/log/*g
```
Provides some system information.
Current RAM used and buffer info.
Swap setup
Looks in all log files for warnings and errors. I have some for pm-suspend things, but nothing else.

Looks like the system is having network issues from the logs. That can make things really slow until the network request times out.  Is there an explanation?

Posting so many log lines, especially when they are the same isn't really needed.  Would be good to remove any sensitive identifying data and use a text posting service like pastebin or sprung. IPs are NOT sensitive, but MAC addresses and perhaps userids are.  How?
```
cat file-that-you've-edited | curl -F '*******=<-' http://*******.us
```
Wow - guess the service I use, s-p-r-u-n-g-e, isn't allowed here (the BB system converted the name to *****). Ubuntu has a pastebin, but I don't know how to use it.

---

### Post by HermanAB on 2019-05-25
It looks like a dud internet connection to me. Check your ISP router.

---

### Post by Gnusboy on 2019-05-25
TheFu,
I can use some help figuring this out.

 I looked at the system monitor before entering the commands you posted. 
There are many lines with entries I have never seen before. In this sample there are 36 lines showing in these columns 
PROCESS NAME    bioset  
USER    root  
0% CPU 0
ID numbers for each line (none repeat) 
MEMORY   *N*/A 
PRIORITY Very High

An Authenticate box popped up 
Asking for a password  "Privileges are required to control other user's processes"
"An application is attempting to perform an action that requires privileges. Authentication is required to perform this action"

Details
Action: org.gnome.gnome-system-monitor.kill
The GNOME Project
 The authenticate box shows "Privileges are required to control other users' processes"
 "An application is required to perform an action that requires privileges. Authentication is required to perform this action"

I don't know what to do at this point. I have never seen entries like this and I don't know how to proceed. I have not yet tried a reboot. I'd like know more info before trying that.

---

### Post by Gnusboy on 2019-05-26
I may be posting this in the wrong area, but its a follow up to my system problems

A couple of days ago my system started running at an extreme slowdown. 
I went through my system logs and found many curious entries and multiple warnings

There are many lines with entries I have never seen before. In this sample there are 36 lines showing in these columns 
PROCESS NAME    bioset  
USER    root  
0% CPU 0
ID numbers for each line (none repeat) 
MEMORY   *N*/A 
PRIORITY Very High

The system kept hanging, at one point  for more than a minute. At that point, 

I started closing all the open files, a couple of pages in Firefox and  Deja Dup notice that was set for a scheduled backup. As I did this, the  system did not get better so I disconnected the 1 TB external drive. 

And did a reboot. Even that was slow and it took nearly a minute for the splash page to load.
I  checked the system log which showed numerous repeating lines of startup code:
There are many lines with entries I have never seen before. In this sample there are 36 lines showing in these columns 
PROCESS NAME    bioset  
USER    root  
0% CPU 0
ID numbers for each line (none repeat) 
MEMORY   *N*/A 
PRIORITY Very High
I am concerned about an authenticate popup that requires a password.

"Privileges are required to control other user's processes"
"An application is attempting to perform an action that requires privileges. Authentication is required to perform this action"
It  has option to authenticate or cancel, but if I hit the cancel it just  reopens the box. I haven't authenticated the issue because I don't know  what might happen. I in an attempt to figure out the problem, 
 I ran a couple of tests which came back with these replies:
[B]
jess@ranha-system:~$ inxi -bz[/B]
System:    Host: ranha-system Kernel: 4.4.0-98-generic x86_64 (64 bit)
           Desktop: Unity 7.4.5  Distro: Ubuntu 16.04 xenial
Machine:   Mobo: ASUSTeK model: M3A78-EM v: Rev X.0x
           Bios: American Megatrends v: 1401 date: 01/09/2009
CPU:       Quad core AMD Phenom 9850 (-MCP-) speed/max: 1250/2500 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] RS780 [Radeon HD 3200]
           Display Server: X.Org 1.18.4 drivers: ati,radeon (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.00hz
           GLX Renderer: AMD RS780 (DRM 2.43.0 / 4.4.0-98-generic, LLVM 6.0.0)
           GLX Version: 3.0 Mesa 18.0.5
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169
Drives:    HDD Total Size: 640.1GB (7.3% used)
Info:      Processes: 260 Uptime: 1 day Memory: 2197.7/3699.4MB
           Client: Shell (bash) inxi: 2.2.35 

** sudo egrep -i 'warn|error' /var/log/*g**
```

/var/log/auth.log:May 23 11:12:15 ranha-system dbus[1196]: [system] Rejected send message, 2 matched rules; type="method_return", sender=":1.5" (uid=111 pid=1209 comm="avahi-daemon: starting up ") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.99" (uid=1000 pid=4994 comm="gedit /home/jess/Desktop/Deja Dup Screenshot 02.01")
/var/log/auth.log:May 23 11:12:15 ranha-system dbus[1196]: [system] Rejected send message, 2 matched rules; type="method_return", sender=":1.5" (uid=111 pid=1209 comm="avahi-daemon: starting up ") interface="(unset)" member="(unset)" error 
/var/log/auth.log:May 23 11:12:15 ranha-system dbus[1196]: [system] Rejected send message, 2 matched rules; type="method_return", sender=":1.5" (uid=111 pid=1209 comm="avahi-daemon: starting up ") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.99" (uid=1000 pid=4994 comm="gedit /home/jess/Desktop/Deja Dup Screenshot 02.01") 
```

```

var/log/auth.log:May 25 12:30:11 ranha-system pkexec[4319]: jess: Error executing command as another user: Request dismissed [USER=root] [TTY=unknown] [CWD=/home/jess] [COMMAND=/usr/lib/gnome-system-monitor/gnome-system-monitor/gsm-kill -s 18 71]
/var/log/auth.log:May 26 12:41:28 ranha-system sudo:     jess : TTY=pts/0 ; PWD=/home/jess ; USER=root ; COMMAND=/bin/egrep -iwarn|error /var/log/alternatives.log /var/log/apport.log /var/log/auth.log /var/log/boot.log /var/log/bootstrap.log /var/log/dmesg /var/log/dpkg.log /var/log/faillog /var/log/fontconfig.log /var/log/gpu-manager.log /var/log/kern.log /var/log/lastlog /var/log/syslog /var/log/Xorg.0.log /var/log/Xorg.1.log
/var/log/auth.log:May 26 12:47:45 ranha-system sudo:     jess : TTY=pts/0 ; PWD=/home/jess ; USER=root ; COMMAND=/bin/egrep -iwarn|error /var/log/alternatives.log /var/log/apport.log /var/log/auth.log /var/log/boot.log /var/log/bootstrap.log /var/log/dmesg /var/log/dpkg.log /var/log/faillog /var/log/fontconfig.log /var/log/gpu-manager.log /var/log/kern.log /var/log/lastlog /var/log/syslog /var/log/Xorg.0.log /var/log/Xorg.1.log
/var/log/auth.log:May 26 13:40:13 ranha-system sudo:     jess : TTY=pts/0 ; PWD=/home/jess ; USER=root ; COMMAND=/bin/egrep -i warn|error /var/log/alternatives.log /var/log/apport.log /var/log/auth.log /var/log/boot.log /var/log/bootstrap.log /var/log/dmesg /var/log/dpkg.log /var/log/faillog /var/log/fontconfig.log /var/log/gpu-manager.log /var/log/kern.log /var/log/lastlog /var/log/syslog /var/log/Xorg.0.log /var/log/Xorg.1.log

ar/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 4 package 'dpkg':
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 23 package 'dpkg':
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 23 package 'dpkg':
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 23 package 'dpkg':
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!

```

```

/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!

```
```


/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:Selecting previously unselected package libgpg-error0:amd64.
/var/log/bootstrap.log:Preparing to unpack .../libgpg-error0_1.21-2ubuntu1_amd64.deb ...
/var/log/bootstrap.log:Unpacking libgpg-error0:amd64 (1.21-2ubuntu1) ...
[B]30 identical entries follow:

```[/B]
```

 /var/log/bootstrap.log:Setting up libgpg-error0:amd64 (1.21-2ubuntu1) ...
/var/log/bootstrap.log:update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
/var/log/bootstrap.log:update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
/var/log/bootstrap.log:update-rc.d: warning: stop runlevel arguments (1) do not match cron Default-Stop values (none)
/var/log/bootstrap.log:update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults

```

```

/var/log/kern.log:May 20 10:01:12 ranha-system NetworkManager[1267]: <warn>  [1558371671.8666] (pid 15684) unhandled DHCP event for interface enp3s0
/var/log/kern.log:May 20 11:19:28 ranha-system NetworkManager[1267]: <warn>  [1558376368.1529] (pid 17605) unhandled DHCP event for interface enp3s0
/var/log/kern.log:May 21 10:04:13 ranha-system kernel: [    6.207440] EXT4-fs (sda9): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:May 21 10:04:13 ranha-system kernel: [    9.399772] ACPI Warning: SystemIO range 0x0000000000000B00-0x0000000000000B08 conflicts with OpRegion 0x0000000000000B00-0x0000000000000B0F (\SOR1) (20150930/utaddress-254)
/var/log/kern.log:May 21 10:04:14 ranha-system NetworkManager[1254]: <warn>  [1558458254.0986] SettingsPlugin-Ofono: file doesn't exist: /var/lib/ofono
/var/log/kern.log:May 21 10:04:14 ranha-system NetworkManager[1254]: <warn>  [1558458254.3892] failed to enumerate oFono devices: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
/var/log/kern.log:May 21 10:06:04 ranha-system kernel: [  137.466079] EXT4-fs (sdb1): warning: maximal mount count reached, running e2fsck is recommended
/var/log/kern.log:May 21 10:06:04 ranha-system kernel: [  137.504691] EXT4-fs (sdb3): warning: maximal mount count reached, running e2fsck is recommended
/var/log/kern.log:May 21 10:06:04 ranha-system kernel: [  137.561307] EXT4-fs (sdb2): warning: maximal mount count reached, running e2fsck is recommended
/var/log/kern.log:May 23 10:24:13 ranha-system NetworkManager[1254]: <warn>  [1558632253.1403] (pid 17435) unhandled DHCP event for interface enp3s0
/var/log/kern.log:May 23 10:25:58 ranha-system kernel: [    6.073557] EXT4-fs (sda9): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:May 23 10:25:58 ranha-system kernel: [    9.222926] ACPI Warning: SystemIO range 0x0000000000000B00-0x0000000000000B08 conflicts with OpRegion 0x0000000000000B00-0x0000000000000B0F (\SOR1) (20150930/utaddress-254)
/var/log/kern.log:May 23 10:26:00 ranha-system NetworkManager[1204]: <warn>  [1558632360.8628] SettingsPlugin-Ofono: file doesn't exist: /var/lib/ofono
/var/log/kern.log:May 23 10:26:02 ranha-system NetworkManager[1204]: <warn>  [1558632362.5952] failed to enumerate oFono devices: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files

/var/log/kern.log:May 23 10:26:28 ranha-system kernel: [   49.235246] EXT4-fs (sdb1): warning: maximal mount count reached, running e2fsck is recommended
/var/log/kern.log:May 23 10:26:28 ranha-system kernel: [   49.311648] EXT4-fs (sdb3): warning: maximal mount count reached, running e2fsck is recommended
/var/log/kern.log:May 23 10:26:28 ranha-system kernel: [   49.320982] EXT4-fs (sdb2): warning: maximal mount count reached, running e2fsck is recommended
/var/log/kern.log:May 24 12:54:05 ranha-system kernel: [    6.008459] EXT4-fs (sda9): re-mounted. Opts: errors=remount-ro

```

```

/var/log/kern.log:May 24 12:54:05 ranha-system kernel: [    9.458648] ACPI Warning: SystemIO range 0x0000000000000B00-0x0000000000000B08 conflicts with OpRegion 0x0000000000000B00-0x0000000000000B0F (\SOR1) (20150930/utaddress-254)
/var/log/kern.log:May 24 12:54:10 ranha-system NetworkManager[1254]: <warn>  [1558727650.5380] SettingsPlugin-Ofono: file doesn't exist: /var/lib/ofono
/var/log/kern.log:May 24 12:54:11 ranha-system NetworkManager[1254]: <warn>  [1558727651.8663] failed to enumerate oFono devices: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
/var/log/kern.log:May 24 12:54:38 ranha-system kernel: [   50.913775] EXT4-fs (sdb1): warning: maximal mount count reached, running e2fsck is recommended
/var/log/kern.log:May 24 12:54:38 ranha-system kernel: [   50.995597] EXT4-fs (sdb3): warning: maximal mount count reached, running e2fsck is recommended
/var/log/kern.log:May 24 12:54:38 ranha-system kernel: [   51.020038] EXT4-fs (sdb2): warning: maximal mount count reached, running e2fsck is recommended
/var/log/kern.log:May 25 09:45:42 ranha-system kernel: [    5.952589] EXT4-fs (sda9): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:May 25 09:45:42 ranha-system kernel: [   10.556320] ACPI Warning: SystemIO range 0x0000000000000B00-0x0000000000000B08 conflicts with OpRegion 0x0000000000000B00-0x0000000000000B0F (\SOR1) (20150930/utaddress-254)
/var/log/kern.log:May 25 09:45:44 ranha-system NetworkManager[1152]: <warn>  [1558802744.1412] SettingsPlugin-Ofono: file doesn't exist: /var/lib/ofono
/var/log/kern.log:May 25 09:45:44 ranha-system NetworkManager[1152]: <warn>  [1558802744.3543] failed to enumerate oFono devices: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
/var/log/syslog:May 26 10:55:08 ranha-system colord[1231]: (colord:1231): Cd-WARNING **: failed to get session [pid 7886]: No such device or address

```

```

/var/log/syslog:May 26 10:55:08 ranha-system colord[1231]: message repeated 2 times: [ (colord:1231): Cd-WARNING **: failed to get session [pid 7886]: No such device or address]
/var/log/syslog:May 26 12:36:32 ranha-system org.gnome.zeitgeist.SimpleIndexer[2109]: ** (zeitgeist-fts:2657): WARNING **: Failed to search index: Db block overwritten - are there multiple writers?
/var/log/syslog:May 26 12:36:32 ranha-system com.canonical.Unity.Scope.LocalFiles[2109]: (unity-files-daemon:3931): unity-files-daemon-WARNING **: daemon.vala:491: Error performing global search 't': GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._g_2dio_2derror_2dquark.Code36: GDBus.Error:org.gnome.zeitgeist.EngineError.DatabaseError: Db block overwritten - are there multiple writers?
/var/log/syslog:May 26 12:36:33 ranha-system org.gnome.zeitgeist.SimpleIndexer[2109]: ** (zeitgeist-fts:2657): WARNING **: Failed to search index: Db block overwritten - are there multiple writers?
/var/log/syslog:May 26 12:36:33 ranha-system com.canonical.Unity.Scope.LocalFiles[2109]: (unity-files-daemon:3931): unity-files-daemon-WARNING **: daemon.vala:491: Error performing global search 'te': GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._g_2dio_2derror_2dquark.Code36: GDBus.Error:org.gnome.zeitgeist.EngineError.DatabaseError: Db block overwritten - are there multiple writers?
/var/log/syslog:May 26 12:36:33 ranha-system org.gnome.zeitgeist.SimpleIndexer[2109]: ** (zeitgeist-fts:2657): WARNING **: Failed to search index: Db block overwritten - are there multiple writers?
/var/log/syslog:May 26 12:36:33 ranha-system com.canonical.Unity.Scope.LocalFiles[2109]: (unity-files-daemon:3931): unity-files-daemon-WARNING **: daemon.vala:491: Error performing global search 'ter': GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._g_2dio_2derror_2dquark.Code36: GDBus.Error:org.gnome.zeitgeist.EngineError.DatabaseError: Db block overwritten - are there multiple writers?
/var/log/syslog:May 26 12:36:38 ranha-system org.gnome.zeitgeist.SimpleIndexer[2109]: ** (zeitgeist-fts:2657): WARNING **: Failed to commit changes: Db block overwritten - are there multiple writers?
/var/log/syslog:May 26 13:21:32 ranha-system org.gnome.zeitgeist.SimpleIndexer[2109]: ** (zeitgeist-fts:2657): WARNING **: Failed to commit changes: Db block overwritten - are there multiple writers?
/var/log/syslog:May 26 13:22:04 ranha-system org.gnome.zeitgeist.SimpleIndexer[2109]: ** (zeitgeist-fts:2657): WARNING **: Failed to commit changes: Db block overwritten - are there multiple writers?
/var/log/Xorg.0.log:    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
/var/log/Xorg.1.log:    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.

```
[B]Indentical entries between code tags are edited out.
I don't know hw to interpret this data so I need someone to tell me if my system has a serious problem.I have not yet rebooted, nor have I filled in my password for the privileges required to control other uses' processes.
Thank you




I don't know how to interpret this data.[/B]

---

