---
title: "Ubuntu inheriting automated shutdown from Windows"
date: 2012-11-07
forum: General Help
---

### Post by Aapsis on 2012-11-07
Hello,

I am experiencing a somewhat weird problem on my Ubuntu installation. 
I recently decided to switch from Windows 7 to Ubuntu, installed a fresh copy of it - 12.0.4, removed the Windows installation entirely - formated/deleted all partitions prior to installing Ubuntu but for some reason my computer is still performing automated shutdown which on the Windows installation I had set for 03.00. It happens exactly at 03.00 on Ubuntu as well.
I didn't use any 3rd party software for the automated shutdowns but Windows task scheduler.
I have not attempted to set any shutdown timers on Ubuntu since I installed it so I must just assume it must be something inherited from the Windows installation. Or could this be just a coincidence and Ubuntu does this by default for some reason?
Is there any way to now stop the automated shutdowns on Ubuntu?

Cheers

---

### Post by SlugSlug on 2012-11-07
I'd check your BIOS first. Maybe you used a Motherboard app rather than windows task sched.

---

### Post by Aapsis on 2012-11-07
Nop, there's nothing in BIOS.

---

### Post by 1971 on 2012-11-07
> **Aapsis said:**
> Nop, there's nothing in BIOS.

Did you migrate any apps from Win 7 onto Linux using Wine? e.g copy a programs folder or program data/file. Unlikely cause but a possibility.

Are you running through a configurable UPS? Do you have one those mains power timers?

If you are sure it is none of the above it comes down to  either you have not fully removed the previous Windows installation or have missed a BIOS setting. Ubuntu does not do this by default. 

I suppose use Gparted to check. What is the mainboard?

You are right seems strange

---

### Post by dcstar on 2012-11-09
> **1971 said:**
> 
...........
If you are sure it is none of the above it comes down to  either you have not fully removed the previous Windows installation or have missed a BIOS setting. Ubuntu does not do this by default. 


+1

Reset the BIOS to default.

---

### Post by Aapsis on 2012-11-20
Is there a service on Ubuntu that controls autmoatic rebotts/shutdowns?

---

### Post by Aapsis on 2012-11-21
> **Aapsis said:**
> Is there a service on Ubuntu that controls autmoatic rebotts/shutdowns?

I`ve reset BIOS just to be safe though there wasn't anything in there related to automatic shutdowns.

I didn't copy anything from the previous installation of windows. 

My machine still keeps shutting down. I'm a first time Linux user so could use as much info as possible. And since I often work nights, this is really annoying having to drop everything at 3.00.

 Is there any way to log what causes it? Like see what service calls for the shutdown?

---

### Post by jlangvand on 2012-11-21
Try "dmesg | tail", it might give you a hint. You can find all logs under /var/log/

---

### Post by Aapsis on 2012-11-21
> **jlangvand said:**
> Try "dmesg | tail", it might give you a hint. You can find all logs under /var/log/


This is what I found in /var/log/syslog.1

Nov 21 03:00:01 Aapbuntu CRON[4632]: (root) CMD (/sbin/poweroff # JOB_ID_1)
Nov 21 03:00:02 Aapbuntu kernel: Kernel logging (proc) stopped.
Nov 21 03:00:02 Aapbuntu rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="779" x-info="http://www.rsyslog.com"] exiting on signal 15.

Any idea what that means?

dmesg | tail just spews some random stuff about wineserver

---

### Post by Aapsis on 2012-11-21
> **Aapsis said:**
> This is what I found in /var/log/syslog.1

Nov 21 03:00:01 Aapbuntu CRON[4632]: (root) CMD (/sbin/poweroff # JOB_ID_1)
Nov 21 03:00:02 Aapbuntu kernel: Kernel logging (proc) stopped.
Nov 21 03:00:02 Aapbuntu rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="779" x-info="http://www.rsyslog.com"] exiting on signal 15.

Any idea what that means?

dmesg | tail just spews some random stuff about wineserver


From the day before:

Nov 20 03:00:01 Aapbuntu CRON[24472]: (root) CMD (/sbin/poweroff # JOB_ID_1)
Nov 20 03:00:03 Aapbuntu kernel: [86365.624047] init: tty4 main process (859) killed by TERM signal
Nov 20 03:00:03 Aapbuntu kernel: [86365.624297] init: tty5 main process (868) killed by TERM signal
Nov 20 03:00:03 Aapbuntu kernel: [86365.624530] init: tty2 main process (883) killed by TERM signal
Nov 20 03:00:03 Aapbuntu kernel: [86365.624759] init: tty3 main process (886) killed by TERM signal
Nov 20 03:00:03 Aapbuntu kernel: [86365.625000] init: tty6 main process (888) killed by TERM signal
Nov 20 03:00:03 Aapbuntu kernel: [86365.625431] init: cron main process (904) killed by TERM signal
Nov 20 03:00:03 Aapbuntu kernel: [86365.625836] init: irqbalance main process (913) killed by TERM signal
Nov 20 03:00:03 Aapbuntu kernel: [86365.626057] init: tty1 main process (1145) killed by TERM signal
Nov 20 03:00:05 Aapbuntu kernel: Kernel logging (proc) stopped.
Nov 20 03:00:05 Aapbuntu rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="673" x-info="http://www.rsyslog.com"] exiting on signal 15.

---

### Post by JKyleOKC on 2012-11-21
> **Aapsis said:**
> 
Nov 20 03:00:01 Aapbuntu CRON[24472]: (root) CMD (/sbin/poweroff # JOB_ID_1)This is your culprit. It's a "cron" job that's probably launched from the directory /etc/cron.daily but that's not a part of normal Ubuntu setup, so it most likely got created in the process of installing Wine -- probably via the configuration file of some application that you brought over from the old Windows installation. (EDIT: The installation of Wine might have picked it up from the Windows registry, if it was still in existence when you installed Wine.)

To pin it down, use a terminal window to issue the command "ls -la /etc/cron.daily", then copy the results and paste into a message. After you paste the result in, highlight it and click the "#" icon in the top margin of the message editor, which will put "code" tags around the result and make it much easier for us to read. Some of us can then probably tell you specifically which file is doing it, and how to disable it.

Hope this helps!

SECOND EDIT: It might also be caused by a line in the file "/etc/crontab" which you can view, but not edit, from any text editor. If it's there we can tell you how to do the edit and inactivate that line.

---

### Post by Aapsis on 2012-11-22
Herewith contents of the cron.daily folder:

```
aapsis@Aapbuntu:~$ ls -la /etc/cron.daily
total 92
drwxr-xr-x   2 root root  4096 nov 15 11:06 .
drwxr-xr-x 144 root root 12288 nov 22 14:01 ..
-rwxr-xr-x   1 root root   311 j&#363;n 20  2010 0anacron
-rwxr-xr-x   1 root root   219 apr 10  2012 apport
-rwxr-xr-x   1 root root 15399 apr 20  2012 apt
-rwxr-xr-x   1 root root   502 mar 31  2012 bsdmainutils
-rwxr-xr-x   1 root root   256 apr 13  2012 dpkg
-rwxr-xr-x   1 root root  7623 okt 31 20:49 google-chrome
-rwxr-xr-x   1 root root   372 okt  4  2011 logrotate
-rwxr-xr-x   1 root root  1365 mar 31  2012 man-db
-rwxr-xr-x   1 root root   606 aug 17  2011 mlocate
-rwxr-xr-x   1 root root   249 apr  9  2012 passwd
-rw-r--r--   1 root root   102 apr  2  2012 .placeholder
-rwxr-xr-x   1 root root  2417 j&#363;l  2  2011 popularity-contest
-rwxr-xr-x   1 root root  2379 feb  3  2010 prelink
-rwxr-xr-x   1 root root  2947 apr  2  2012 standard
-rwxr-xr-x   1 root root   214 aug  9 09:00 update-notifier-common

```And the crontab file:

```
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user    command
17 *    * * *    root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#
```Thanks for your help.

---

### Post by JKyleOKC on 2012-11-22
Unfortunately I don't see anything in either report that correlates with the time and command shown in your logs!

The cron.daily job runs at 6:25 a.m. each day, so my suggesting it was actually a bit of a red herring. There must be a cron job somewhere that's launched at 3 a.m. every day, but I'm a bit short of ideas as to other places to look for it. Perhaps in /etc/cron.d -- and hopefully other folk will think of other places to look for it. That "JOB_ID_1" comment in your log entries is definitely a clue. It might even be a backgrounded job launched as part of your login, but I don't know how to follow it up...

---

### Post by Aapsis on 2012-11-22
[LEFT]/etc/default/cron lead me to this file: /etc/init/cron.conf which only contains the following:

```
# cron - regular background program processing daemon
#
# cron is a standard UNIX program that runs user-specified programs at
# periodic scheduled times

description    "regular background program processing daemon"

start on runlevel [2345]
stop on runlevel [!2345]

expect fork
respawn

exec cron
```

I'm not exactly a wiz kid but just looking at it I doubt this describes any scheduled shutdowns? And shouldn't this be the file where scheduled tasks are listed?
/etc/cron.d only contains file called anacron, /etc/cron.hourly is empty.

Wine's Windows installation doesn't include a Taskschd.msc but if it, for some reason, is something Wine took from the previous Windows installation, where can I check? Where would it show up in registry editor?
[/LEFT]

---

### Post by JKyleOKC on 2012-11-22
I'm now down to going with wild guesses, and some of them are pretty wild. If it's being triggered by some automatically launched background job, I'd try to locate the specific process involved and then try to determine how it's getting initiated. The command "ps ax" will get you a list of all running processes, but it's not always easy to determine what each of them is actually doing. When you run this command, do it in a terminal window of which you've stretched the width to the full width of your display; some of its lines are very long and it does not wrap their content.

Note that there will be a huge number of processes listed. Right now, my system shows 170 active. Most of them are sleeping, indicated by an "S" in the status (third) column of the "ps ax" display, but they're available for wakeup on an instant's notice. Any background job will probably be in this state.

If you're lucky, the command line shown for each process will have something that relates to automatic shutdown or power, that will let you zero in on one or a few of the whole bunch to take a closer look. Also, the PID (Process IDentifier) value, which is the first column of each line, can be very helpful, since both the CRON reports in your logs showed their jobs' PID values between square brackets. One was 4632 and the other was 24472. Searching the "ps ax" report in both areas might give leads to follow up.

Here's a couple of lines from running "ps ax" on my own box, to give you an idea of what to expect:```

 1897 pts/0    Ss+    0:00 /bin/bash /home/jk/bin/watcher
 1898 pts/0    S+     0:00 inotifywait -q -e close_write --format %f received. /
```The PIDs here are 1897 and 1898, the jobs originated from my console, and both are in "sleeping" status. Neither has run so much as a minute since being launched. Process 1897 was launched from my desktop, through a sub-shell (/bin/bash), and its program is a script in my home directory named "watcher" that watches my FTP server's "incoming" directory for the appearance of new files. Process 1898 is what does the actual watching, using a utility named "inotifywait" with a number of options that make it do what I want. This entry was cut short because I didn't stretch the terminal window out to full display width.

If your automatic shutdown is being done by a similar script, launched automatically at start-up or login, you will probably find a similar pair of entries, one to launch the script and the second immediately afterward to launch the actual background process. However if it's not scripted, but launched by a single command line, then it would have only one entry in the report.

As I said at the beginning of this message, these are just wild guesses about what may be happening. However I'm willing to continue making them and explaining what they do, as long as you want to keep trying. I hate to have things happening that I cannot explain logically!

---

### Post by Aapsis on 2012-11-26
Unfortunately ps ax didn't show neither of those PIDs and I cannot see anything that would be responsible for shutdowns:

Herewith the full output. Sorry for the spam.

```
 PID TTY      STAT   TIME COMMAND
    1 ?        Ss     0:00 /sbin/init
    2 ?        S      0:00 [kthreadd]
    3 ?        S      0:00 [ksoftirqd/0]
    5 ?        S      0:00 [kworker/u:0]
    6 ?        S      0:00 [migration/0]
    7 ?        S      0:00 [watchdog/0]
    8 ?        S      0:00 [migration/1]
   10 ?        S      0:00 [ksoftirqd/1]
   12 ?        S      0:00 [watchdog/1]
   13 ?        S      0:00 [migration/2]
   15 ?        S      0:00 [ksoftirqd/2]
   16 ?        S      0:00 [watchdog/2]
   17 ?        S      0:01 [migration/3]
   19 ?        S      0:00 [ksoftirqd/3]
   20 ?        S      0:00 [watchdog/3]
   21 ?        S<     0:00 [cpuset]
   22 ?        S<     0:00 [khelper]
   23 ?        S      0:00 [kdevtmpfs]
   24 ?        S<     0:00 [netns]
   26 ?        S      0:00 [sync_supers]
   27 ?        S      0:00 [bdi-default]
   28 ?        S<     0:00 [kintegrityd]
   29 ?        S<     0:00 [kblockd]
   30 ?        S<     0:00 [ata_sff]
   31 ?        S      0:00 [khubd]
   32 ?        S<     0:00 [md]
   36 ?        S      0:00 [khungtaskd]
   37 ?        S      0:02 [kswapd0]
   38 ?        SN     0:00 [ksmd]
   39 ?        SN     0:00 [khugepaged]
   40 ?        S      0:00 [fsnotify_mark]
   41 ?        S      0:00 [ecryptfs-kthrea]
   42 ?        S<     0:00 [crypto]
   50 ?        S<     0:00 [kthrotld]
   52 ?        S      0:00 [scsi_eh_0]
   53 ?        S      0:00 [scsi_eh_1]
   54 ?        S      0:00 [scsi_eh_2]
   55 ?        S      0:00 [scsi_eh_3]
   56 ?        S      0:00 [kworker/u:3]
   77 ?        S<     0:00 [devfreq_wq]
  176 ?        S      0:00 [scsi_eh_4]
  178 ?        S      0:00 [scsi_eh_5]
  222 ?        S      0:01 [jbd2/sda1-8]
  223 ?        S<     0:00 [ext4-dio-unwrit]
  229 ?        S<     0:00 [firewire]
  312 ?        S      0:00 upstart-udev-bridge --daemon
  315 ?        Ss     0:00 /sbin/udevd --daemon
  449 ?        S      0:00 /sbin/udevd --daemon
  467 ?        S      0:00 /sbin/udevd --daemon
  522 ?        S<     0:00 [kpsmoused]
  565 ?        S      0:00 upstart-socket-bridge --daemon
  599 ?        S<     0:00 [hd-audio0]
  605 ?        S<     0:00 [hd-audio2]
  725 ?        Ss     0:00 dbus-daemon --system --fork --activation=upstart
  782 ?        Ss     0:00 /usr/sbin/modem-manager
  788 ?        Ss     0:00 /usr/sbin/bluetoothd
  808 ?        Sl     0:01 rsyslogd -c5
  810 ?        Ssl    0:00 NetworkManager
  824 ?        S      0:00 avahi-daemon: running [Aapbuntu.local]
  827 ?        S<     0:00 [krfcommd]
  828 ?        S      0:00 avahi-daemon: chroot helper
  875 ?        Sl     0:00 /usr/lib/policykit-1/polkitd --no-debug
  895 ?        Ss     0:00 /usr/sbin/cupsd -F
  924 tty4     Ss+    0:00 /sbin/getty -8 38400 tty4
  934 tty5     Ss+    0:00 /sbin/getty -8 38400 tty5
  948 tty2     Ss+    0:00 /sbin/getty -8 38400 tty2
  951 tty3     Ss+    0:00 /sbin/getty -8 38400 tty3
  953 tty6     Ss+    0:00 /sbin/getty -8 38400 tty6
  958 ?        Ss     0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
  963 ?        Ss     0:00 /usr/sbin/winbindd
  970 ?        Ss     0:08 /usr/sbin/irqbalance
  972 ?        Ssl    0:00 whoopsie
  975 ?        Ss     0:00 atd
  976 ?        Ss     0:00 cron
 1037 ?        S      0:00 /usr/sbin/winbindd
 1189 ?        Ssl    0:00 lightdm
 1210 tty1     Ss+    0:00 /sbin/getty -8 38400 tty1
 1214 tty7     Ss+   67:23 /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
 1222 ?        Sl     0:00 /usr/lib/accountsservice/accounts-daemon
 1239 ?        Sl     0:00 /usr/sbin/console-kit-daemon --no-daemon
 1312 ?        S      0:00 /sbin/dhclient -d -4 -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/sendsigs.omit.d/network-manager.dhclient-eth0.pid -lf /var/lib/dhcp/d
 1355 ?        Sl     0:00 /usr/lib/upower/upowerd
 1508 ?        Sl     0:00 /usr/lib/i386-linux-gnu/colord/colord
 1521 ?        Sl     0:00 lightdm --session-child 12 19
 1553 ?        SNl    0:00 /usr/lib/rtkit/rtkit-daemon
 1575 ?        S      0:00 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/var/run/sendsigs.omit.d/network-manager.dnsmasq.pid --listen-
 1680 ?        Sl     0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
 1691 ?        Ssl    0:00 gnome-session --session=ubuntu
 1726 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-session --session=ubuntu
 1729 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session gnome-session --session=ubuntu
 1730 ?        Ss     1:35 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
 1743 ?        Sl     0:21 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
 1749 ?        S      0:00 /usr/lib/gvfs/gvfsd
 1751 ?        Sl     0:00 /usr/lib/gvfs//gvfs-fuse-daemon -f /home/aapsis/.gvfs
 1759 ?        Sl    95:12 compiz
 1770 ?        S<l   17:35 /usr/bin/pulseaudio --start --log-target=syslog
 1772 ?        S      0:00 /usr/lib/i386-linux-gnu/gconf/gconfd-2
 1775 ?        Sl     0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
 1776 ?        Sl     0:00 /usr/lib/gnome-settings-daemon/gnome-fallback-mount-helper
 1779 ?        Sl     0:00 bluetooth-applet
 1782 ?        Sl     0:32 nautilus -n
 1788 ?        S      0:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
 1792 ?        Sl     0:01 /usr/lib/udisks/udisks-daemon
 1795 ?        Sl     0:00 nm-applet
 1796 ?        S      0:00 udisks-daemon: not polling any devices
 1803 ?        S      0:00 /usr/lib/pulseaudio/pulse/gconf-helper
 1807 ?        S      0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
 1809 ?        Sl     0:02 /usr/lib/gvfs/gvfs-afc-volume-monitor
 1818 ?        S      0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.6 /org/gtk/gvfs/exec_spaw/0
 1823 ?        S      0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.6 /org/gtk/gvfs/exec_spaw/1
 1827 ?        Sl     0:05 /usr/lib/bamf/bamfdaemon
 1832 ?        S      0:00 /usr/lib/gvfs/gvfsd-metadata
 1839 ?        Ss     0:00 /bin/sh -c /usr/bin/compiz-decorator
 1840 ?        Sl     0:10 /usr/bin/gtk-window-decorator
 1845 ?        Sl     4:14 /usr/lib/unity/unity-panel-service
 1847 ?        Sl     0:04 /usr/lib/indicator-appmenu/hud-service
 1860 ?        Sl     0:00 /usr/lib/indicator-printers/indicator-printers-service
 1862 ?        Sl     0:00 /usr/lib/indicator-session/indicator-session-service
 1864 ?        Sl     0:00 /usr/lib/indicator-datetime/indicator-datetime-service
 1867 ?        Sl     0:00 /usr/lib/indicator-application/indicator-application-service
 1871 ?        Sl     0:00 /usr/lib/indicator-sound/indicator-sound-service
 1874 ?        Sl     0:00 /usr/lib/indicator-messages/indicator-messages-service
 1900 ?        S      0:00 /usr/lib/geoclue/geoclue-master
 1902 ?        S      0:00 /usr/lib/ubuntu-geoip/ubuntu-geoip-provider
 1917 ?        Sl     0:00 /usr/lib/gnome-disk-utility/gdu-notification-daemon
 1951 ?        Sl     0:00 telepathy-indicator
 1955 ?        Sl     0:00 /usr/lib/telepathy/mission-control-5
 1960 ?        Sl     0:00 /usr/lib/gnome-online-accounts/goa-daemon
 1992 ?        Sl     0:07 gnome-screensaver
 1995 ?        Sl     0:00 zeitgeist-datahub
 2004 ?        Sl     0:00 /usr/bin/zeitgeist-daemon
 2019 ?        Sl     0:00 /usr/lib/zeitgeist/zeitgeist-fts
 2028 ?        S      0:00 /bin/cat
 2091 ?        SLl    0:10 /usr/bin/python /usr/bin/gwibber-service
 2120 ?        Sl     0:00 /usr/bin/python /usr/lib/ubuntuone-client/ubuntuone-syncdaemon
 2205 ?        Sl     0:01 /usr/lib/unity-lens-applications/unity-applications-daemon
 2207 ?        Sl     0:05 /usr/lib/unity-lens-files/unity-files-daemon
 2209 ?        Sl     0:00 /usr/lib/unity-lens-music/unity-music-daemon
 2211 ?        Sl     0:00 /usr/bin/python /usr/lib/unity-lens-video/unity-lens-video
 2244 ?        Sl     0:00 /usr/bin/python /usr/lib/unity-scope-video-remote/unity-scope-video-remote
 2253 ?        Sl     0:00 /usr/lib/unity-lens-music/unity-musicstore-daemon
 2272 ?        Sl     0:00 /usr/lib/dconf/dconf-service
 2294 ?        Sl     0:01 update-notifier
 2381 ?        Sl    16:45 /usr/bin/vlc
 2519 ?        S      0:00 /usr/bin/python /usr/lib/system-service/system-service-d
 2658 ?        Sl     0:00 /usr/lib/deja-dup/deja-dup/deja-dup-monitor
 2892 ?        S      0:00 /usr/lib/cups/notifier/dbus dbus:// 
 3162 ?        Sl    25:46 /usr/lib/firefox/firefox
 3179 ?        Sl     0:00 /usr/lib/at-spi2-core/at-spi-bus-launcher
 4177 ?        S      0:01 [flush-8:0]
 4195 ?        Sl    72:07 /usr/lib/firefox/plugin-container /usr/lib/flashplugin-installer/libflashplayer.so -greomni /usr/lib/firefox/omni.ja 3162 true plugin
 4743 ?        Sl     8:33 audacious
 4855 ?        Sl     8:54 skype
 5191 ?        S      0:08 [kworker/2:1]
 5225 ?        Sl     0:00 /usr/lib/telepathy/telepathy-gabble
 5326 ?        S      0:00 /bin/sh /usr/bin/xdg-screensaver suspend 0x032000cc
 5333 ?        S      0:00 /bin/sh /usr/bin/xdg-screensaver suspend 0x032000cc
 5337 ?        S      0:00 /usr/bin/xprop -id 0x032000cc -spy
 5531 ?        S      0:04 [kworker/2:2]
 5697 ?        S      0:09 [kworker/3:3]
 6445 ?        Sl     0:22 /usr/lib/thunderbird/thunderbird
 6485 ?        Sl     0:00 /usr/lib/evolution/e-addressbook-factory
 6728 ?        Sl     1:10 evince /home/aapsis/Growth-of-the-Soil-by-Knut-Hamsun.pdf
 6734 ?        Sl     0:00 /usr/lib/evince/evinced
 7458 ?        S      0:00 [kworker/3:0]
 7483 ?        S      0:02 [kworker/1:1]
 7683 ?        Ss     0:21 /usr/local/bin/wineserver
 7689 ?        Sl     0:00 C:\windows\system32\services.exe                                                  
 7695 ?        Sl     0:00 C:\windows\system32\winedevice.exe MountMgr                                                  
 7703 ?        Sl     0:00 C:\windows\system32\plugplay.exe                                                  
 7710 ?        Ss     0:00 C:\windows\system32\explorer.exe /desktop                                                  
 7793 ?        Rl    26:50 C:/Program Files/World of Warcraft/WoW.exe -launch -uid wow_engb                                                  
 7957 ?        S      0:00 [kworker/1:2]
 7962 ?        S      0:00 [kworker/0:3]
 7983 ?        Rl     0:03 gnome-terminal
 7991 ?        S      0:00 gnome-pty-helper
 7992 pts/1    Ss     0:00 bash
 9042 ?        S      0:00 [kworker/0:0]
 9089 ?        S      0:00 [kworker/0:1]
 9092 ?        S      0:00 [kworker/1:0]
 9096 ?        S      0:00 sleep 50
 9097 pts/1    R+     0:00 ps ax

```

---

### Post by Aapsis on 2012-11-26
I consulted around and turns out solution was quite simple:

sudo crontab - l

this showed the scheduled shutdown and crontab -e removed it.

I'm still baffled about where cron got the job from in the first place.

Anyway, thanks for your suggestions and help!

---

### Post by JKyleOKC on 2012-11-27
So am I, but I'm glad that you got it fixed. It's relatively easy for an installer program to add an item to crontab, but I'm amazed that it didn't show when you were searching in the /etc directory for such entries. Obviously there must be other places, also, for entries to lurk...

---

