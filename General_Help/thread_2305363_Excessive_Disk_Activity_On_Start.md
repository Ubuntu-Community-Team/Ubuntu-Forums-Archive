---
title: "Excessive Disk Activity On Start"
date: 2015-12-05
forum: General Help
---

### Post by philwx on 2015-12-05
After start, my pc experiences excessive disk activity. 


[LIST]
[*]The pc is unusably slow. The disk read/write light is constantly lit. 
[*]Lasts approx 10 minutes 
[*]This doesn't happen on subsequent restarts during the day. 
[/LIST]

After reading other threads on disk activity I installed iotop. The three cmds that seem active are find, flush and jbd2. Here are 2 screen grabs:
[IMG]http://houseofhaberdashery.co.uk/itop1.png[/IMG]

[IMG]http://houseofhaberdashery.co.uk/itop3.png[/IMG]

Any help to understand what this is (and stop  if not essential) much appreciated. 

I am very far from an Ubuntu expert. 

Ubuntu
Release 12.04 (precise) 32-bit
Kernel Linux 3.8.0-30-lowlatency
GNOME 3.4.2

Thanks,
Phil

---

### Post by matt_symes on 2015-12-05
Hi

> **philwx said:**
> After reading other threads on disk activity I installed iotop. The three cmds that seem active are find, flush and jbd2. 

flush and jdb2 are not a problem. flush just flushes to the disk and jdb2 is the journaling daemon that ext3 and 4 file systems use.

The real culprit is find and i suspect, although i'm not sure, it may be updating the mlocate database when you start the PC.

This may be being kicked off my anacron when you start the PC the first time. On subsequent boots the mlocate database will be up to date for that day.

I'm not sure  that's what's happening but it would explain the disk activity you are seeing.

You could disable the cron job for mlocate in /etc/cron.daily and see if that fixes the problem (as a temporary fix).

Anacron is called when the PC is switched on and uses the configuration file /etc/anacrontab
```

matthew-xu-16-04:/home/matthew:3 % less /etc/anacrontab
# /etc/anacrontab: configuration file for anacron

# See anacron(8) and anacrontab(5) for details.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
HOME=/root
LOGNAME=root

# These replace cron's entries
1       5       cron.daily      run-parts --report /etc/cron.daily
7       10      cron.weekly     run-parts --report /etc/cron.weekly
@monthly        15      cron.monthly    run-parts --report /etc/cron.monthly
matthew-xu-16-04:/home/matthew:3 
```

As you can see, anacron runs all the scripts in /etc/cron.daily and one of the scripts in cron.daily runs mlocate to update the locate database.
```

matthew-xu-16-04:/home/matthew:3 % ls /etc/cron.daily/mlocate 
/etc/cron.daily/mlocate*
matthew-xu-16-04:/home/matthew:3
```

I suspect that the code to update the mlocate database is using the find command (although i'm not 100% sure).

On my 16.04 dev installation, ionice is being used to limit disk access.
```

# See ionice(1)
if [ -x /usr/bin/ionice ] &&
    /usr/bin/ionice -c3 true 2>/dev/null; then
    IONICE="/usr/bin/ionice -c3"
flock --nonblock /run/mlocate.daily.lock $IONICE /usr/bin/updatedb.mlocate
matthew-xu-16-04:/home/matthew:3 % 
```

To see if it is the problem you can disable the mlocate cronjob.

```
sudo chmod 000 /etc/cron.daily/mlocate
```

If you don't have the same disk activity problem after that running command when you would usually expect it, post back and we'll try to come up with a better approach than the sledgehammer of disabling the cronjob completely.

**EDIT:**

It may also be updating the package database, looking for updates.

Kind regards

---

### Post by philwx on 2015-12-06
Hello Matt

Thanks very much for your help. I have just run the cmd to disable the mlocate cronjob. I'll post back the result in a couple of days.

Phil

---

### Post by philwx on 2015-12-07
Hello Matt

This morning the excessive disk activity happened exactly the same as before. It appears the cmd to disable the mlocate cronjob had no effect.

Phil

---

### Post by matt_symes on 2015-12-07
Hi

> **philwx said:**
> Hello Matt

This morning the excessive disk activity happened exactly the same as before. It appears the cmd to disable the mlocate cronjob had no effect.

Phil

Hmm. 

In the first screen shot you posted, it shows *run-parts* being called on the files in */etc/cron.daily*. That, along with the find command, is why i suspected the mlocate cronjob.

I'm still not convinced it's not a cron job.

Can you post the output of these commands.

```
ls -l /etc/cron.daily
```

I would like to see the parent processes of that find command so, when the find command is running, please post the output of this command.

```
pstree -s $(pgrep find)
```

If pstree is not installed on your system 

(you can check with ```
dpkg -l psmisc
``` )

then

```
sudo apt-get install psmisc
```

Also, let's put things back the way they were.

```
sudo chmod 755 /etc/cron.daily/mlocate
```

Kind regards

---

### Post by philwx on 2015-12-08
Hello Matt

Here's the first output:

```
phil@phil-G41D3:~$ ls -l /etc/cron.daily
total 84
-rwxr-xr-x 1 root root   311 Jun 20  2010 0anacron
-rwxr-xr-x 1 root root   633 Mar  8  2013 apache2
-rwxr-xr-x 1 root root   219 Apr 10  2012 apport
-rwxr-xr-x 1 root root 15399 Dec 12  2012 apt
-rwxr-xr-x 1 root root   314 Oct  5  2012 aptitude
-rwxr-xr-x 1 root root   502 Jun  8  2011 bsdmainutils
-rwxr-xr-x 1 root root   256 Oct  6  2011 dpkg
lrwxrwxrwx 1 root root    37 Nov 24 05:09 google-chrome -> /opt/google/chrome/cron/google-chrome
-rwxr-xr-x 1 root root  7613 Oct  7  2013 google-earth
-rwxr-xr-x 1 root root  2211 Jan 23  2012 locate
-rwxr-xr-x 1 root root   372 Oct  4  2011 logrotate
-rwxr-xr-x 1 root root  1365 Mar 31  2012 man-db
---------- 1 root root   606 Aug 17  2011 mlocate
-rwxr-xr-x 1 root root   249 Jun 24  2011 passwd
-rwxr-xr-x 1 root root  2417 Jul  1  2011 popularity-contest
-rwxr-xr-x 1 root root   982 Nov 14  2011 rkhunter
-rwxr-xr-x 1 root root  2947 Jun 19  2012 standard
-rwxr-xr-x 1 root root   214 Sep 10  2012 update-notifier-common
```

I then ran the reset mlocate perms cmd.

This morning as the excessive disk activity was happeing I ran your cmd suggestion but it wasn't understood:
```
phil@phil-G41D3:~$ pstree -s $(pgrep find)
Usage: pstree [ -a ] [ -c ] [ -h | -H PID ] [ -l ] [ -n ] [ -p ] [ -u ]
              [ -A | -G | -U ] [ PID | USER ]
       pstree -V
Display a tree of processes.

  -a, --arguments     show command line arguments
  -A, --ascii         use ASCII line drawing characters
  -c, --compact       don't compact identical subtrees
  -h, --highlight-all highlight current process and its ancestors
  -H PID,
  --highlight-pid=PID highlight this process and its ancestors
  -G, --vt100         use VT100 line drawing characters
  -l, --long          don't truncate long lines
  -n, --numeric-sort  sort output by PID
  -p, --show-pids     show PIDs; implies -c
  -s, --show-parents  show parents of the selected process
  -u, --uid-changes   show uid transitions
  -U, --unicode       use UTF-8 (Unicode) line drawing characters
  -V, --version       display version information
  PID    start at this PID; default is 1 (init)
  USER   show only trees rooted at processes of this user
```
Unfortunately my lack of experience with bash means I was unable to make sense of the cmd. So I simply split it and got:
```
phil@phil-G41D3:~$ pstree -s
init&#9472;&#9516;&#9472;NetworkManager&#9472;&#9516;&#9472;dhclient
     &#9474;                &#9500;&#9472;dnsmasq
     &#9474;                &#9492;&#9472;2*[{NetworkManager}]
     &#9500;&#9472;a2jmidid
     &#9500;&#9472;accounts-daemon&#9472;&#9472;&#9472;{accounts-daemon}
     &#9500;&#9472;acpid
     &#9500;&#9472;anacron&#9472;&#9472;&#9472;sh&#9472;&#9472;&#9472;run-parts&#9472;&#9472;&#9472;locate&#9472;&#9472;&#9472;updatedb.findut&#9472;&#9516;&#9472;frcode
     &#9474;                                                     &#9500;&#9472;sort
     &#9474;                                                     &#9492;&#9472;updatedb.findut&#9472;&#9472;&#9472;+
     &#9500;&#9472;apache2&#9472;&#9472;&#9472;5*[apache2]
     &#9500;&#9472;at-spi-bus-laun&#9472;&#9472;&#9472;2*[{at-spi-bus-laun}]
     &#9500;&#9472;atd
     &#9500;&#9472;avahi-daemon&#9472;&#9472;&#9472;avahi-daemon
     &#9500;&#9472;bamfdaemon&#9472;&#9472;&#9472;2*[{bamfdaemon}]
     &#9500;&#9472;bluetoothd
     &#9500;&#9472;colord&#9472;&#9472;&#9472;2*[{colord}]
     &#9500;&#9472;console-kit-dae&#9472;&#9472;&#9472;64*[{console-kit-dae}]
     &#9500;&#9472;cron
     &#9500;&#9472;cupsd
     &#9500;&#9472;2*[dbus-daemon]
     &#9500;&#9472;dbus-launch
     &#9500;&#9472;dconf-service&#9472;&#9472;&#9472;2*[{dconf-*********]
     &#9500;&#9472;e-addressbook-f&#9472;&#9472;&#9472;2*[{e-addressbook-f}]
     &#9500;&#9472;e-calendar-fact&#9472;&#9472;&#9472;2*[{e-calendar-fact}]
     &#9500;&#9472;firefox&#9472;&#9472;&#9472;42*[{firefox}]
     &#9500;&#9472;freshclam
     &#9500;&#9472;gconfd-2
     &#9500;&#9472;gedit&#9472;&#9472;&#9472;2*[{gedit}]
     &#9500;&#9472;geoclue-master
     &#9500;&#9472;6*[getty]
     &#9500;&#9472;gnome-keyring-d&#9472;&#9472;&#9472;6*[{gnome-keyring-d}]
     &#9500;&#9472;gnome-terminal&#9472;&#9516;&#9472;bash&#9472;&#9472;&#9472;sudo&#9472;&#9472;&#9472;iotop
     &#9474;                &#9500;&#9472;bash&#9472;&#9472;&#9472;pstree
     &#9474;                &#9500;&#9472;gnome-pty-helpe
     &#9474;                &#9492;&#9472;4*[{gnome-terminal}]
     &#9500;&#9472;goa-daemon&#9472;&#9472;&#9472;{goa-daemon}
     &#9500;&#9472;gvfs-afc-volume&#9472;&#9472;&#9472;{gvfs-afc-volume}
     &#9500;&#9472;gvfs-fuse-daemo&#9472;&#9472;&#9472;3*[{gvfs-fuse-daemo}]
     &#9500;&#9472;gvfs-gdu-volume
     &#9500;&#9472;gvfs-gphoto2-vo
     &#9500;&#9472;gvfsd
     &#9500;&#9472;gvfsd-burn
     &#9500;&#9472;gvfsd-metadata
     &#9500;&#9472;gvfsd-trash
     &#9500;&#9472;hud-service&#9472;&#9472;&#9472;3*[{hud-*********]
     &#9500;&#9472;indicator-appli&#9472;&#9472;&#9472;{indicator-appli}
     &#9500;&#9472;indicator-datet&#9472;&#9472;&#9472;2*[{indicator-datet}]
     &#9500;&#9472;indicator-messa&#9472;&#9472;&#9472;{indicator-messa}
     &#9500;&#9472;indicator-print&#9472;&#9472;&#9472;2*[{indicator-print}]
     &#9500;&#9472;indicator-sessi&#9472;&#9472;&#9472;2*[{indicator-sessi}]
     &#9500;&#9472;indicator-sound&#9472;&#9472;&#9472;2*[{indicator-sound}]
     &#9500;&#9472;jackdbus
     &#9500;&#9472;lightdm&#9472;&#9516;&#9472;Xorg
     &#9474;         &#9500;&#9472;lightdm&#9472;&#9516;&#9472;gnome-session&#9472;&#9516;&#9472;bluetooth-apple&#9472;&#9472;&#9472;2*[{bluetooth-appl+
     &#9474;         &#9474;         &#9474;               &#9500;&#9472;deja-dup-monito&#9472;&#9472;&#9472;2*[{deja-dup-monit+
     &#9474;         &#9474;         &#9474;               &#9500;&#9472;evolution-alarm&#9472;&#9472;&#9472;2*[{evolution-alar+
     &#9474;         &#9474;         &#9474;               &#9500;&#9472;gdu-notificatio&#9472;&#9472;&#9472;2*[{gdu-notificati+
     &#9474;         &#9474;         &#9474;               &#9500;&#9472;gnome-fallback-&#9472;&#9472;&#9472;2*[{gnome-fallback+
     &#9474;         &#9474;         &#9474;               &#9500;&#9472;gnome-screensav&#9472;&#9472;&#9472;2*[{gnome-screensa+
     &#9474;         &#9474;         &#9474;               &#9500;&#9472;gnome-settings-&#9472;&#9472;&#9472;2*[{gnome-settings+
     &#9474;         &#9474;         &#9474;               &#9500;&#9472;metacity&#9472;&#9472;&#9472;2*[{metacity}]
     &#9474;         &#9474;         &#9474;               &#9500;&#9472;nautilus&#9472;&#9472;&#9472;2*[{nautilus}]
     &#9474;         &#9474;         &#9474;               &#9500;&#9472;nm-applet&#9472;&#9472;&#9472;2*[{nm-applet}]
     &#9474;         &#9474;         &#9474;               &#9500;&#9472;polkit-gnome-au&#9472;&#9472;&#9472;2*[{polkit-gnome-a+
     &#9474;         &#9474;         &#9474;               &#9500;&#9472;python3
     &#9474;         &#9474;         &#9474;               &#9500;&#9472;ssh-agent
     &#9474;         &#9474;         &#9474;               &#9500;&#9472;telepathy-indic&#9472;&#9472;&#9472;2*[{telepathy-indi+
     &#9474;         &#9474;         &#9474;               &#9500;&#9472;unity-2d-panel&#9472;&#9472;&#9472;2*[{unity-2d-panel}+
     &#9474;         &#9474;         &#9474;               &#9500;&#9472;unity-2d-shell&#9472;&#9472;&#9472;4*[{unity-2d-shell}+
     &#9474;         &#9474;         &#9474;               &#9500;&#9472;update-notifier&#9472;&#9472;&#9472;2*[{update-notifie+
     &#9474;         &#9474;         &#9474;               &#9500;&#9472;zeitgeist-datah&#9472;&#9472;&#9472;{zeitgeist-datah}
     &#9474;         &#9474;         &#9474;               &#9492;&#9472;3*[{gnome-session}]
     &#9474;         &#9474;         &#9492;&#9472;{lightdm}
     &#9474;         &#9492;&#9472;2*[{lightdm}]
     &#9500;&#9472;master&#9472;&#9516;&#9472;pickup
     &#9474;        &#9492;&#9472;qmgr
     &#9500;&#9472;mission-control&#9472;&#9472;&#9472;2*[{mission-control}]
     &#9500;&#9472;modem-manager
     &#9500;&#9472;mysqld&#9472;&#9472;&#9472;17*[{mysqld}]
     &#9500;&#9472;polkitd&#9472;&#9472;&#9472;{polkitd}
     &#9500;&#9472;rsyslogd&#9472;&#9472;&#9472;3*[{rsyslogd}]
     &#9500;&#9472;rtkit-daemon&#9472;&#9472;&#9472;2*[{rtkit-daemon}]
     &#9500;&#9472;sshd
     &#9500;&#9472;system-service-
     &#9500;&#9472;thunderbird&#9472;&#9472;&#9472;33*[{thunderbird}]
     &#9500;&#9472;tor
     &#9500;&#9472;ubuntu-geoip-pr&#9472;&#9472;&#9472;2*[{ubuntu-geoip-pr}]
     &#9500;&#9472;ubuntuone-syncd&#9472;&#9472;&#9472;2*[{ubuntuone-syncd}]
     &#9500;&#9472;udevd&#9472;&#9472;&#9472;2*[udevd]
     &#9500;&#9472;udisks-daemon&#9472;&#9516;&#9472;udisks-daemon
     &#9474;               &#9492;&#9472;2*[{udisks-daemon}]
     &#9500;&#9472;unity-applicati&#9472;&#9472;&#9472;2*[{unity-applicati}]
     &#9500;&#9472;unity-files-dae&#9472;&#9472;&#9472;2*[{unity-files-dae}]
     &#9500;&#9472;unity-lens-vide&#9472;&#9472;&#9472;{unity-lens-vide}
     &#9500;&#9472;unity-music-dae&#9472;&#9472;&#9472;{unity-music-dae}
     &#9500;&#9472;unity-musicstor&#9472;&#9472;&#9472;{unity-musicstor}
     &#9500;&#9472;unity-panel-ser&#9472;&#9472;&#9472;3*[{unity-panel-ser}]
     &#9500;&#9472;unity-scope-vid&#9472;&#9472;&#9472;2*[{unity-scope-vid}]
     &#9500;&#9472;update-manager&#9472;&#9472;&#9472;3*[{update-manager}]
     &#9500;&#9472;upowerd&#9472;&#9472;&#9472;2*[{upowerd}]
     &#9500;&#9472;upstart-socket-
     &#9500;&#9472;upstart-udev-br
     &#9500;&#9472;winbindd&#9472;&#9472;&#9472;winbindd
     &#9500;&#9472;xfconfd
     &#9500;&#9472;zeitgeist-daemo&#9472;&#9472;&#9472;{zeitgeist-daemo}
     &#9492;&#9472;zeitgeist-fts&#9472;&#9516;&#9472;cat
                     &#9492;&#9472;{zeitgeist-fts}

```

and:
```
phil@phil-G41D3:~$ $(pgrep find)
4974: command not found
```

UPDATE
I was up earlier than normal this morning and noticed the excessive disk activity didn't happen upon starting the pc. It happened about 7.55am, approx half an hour after starting. Just thought I would mention this.

---

### Post by matt_symes on 2015-12-08
Hi
```

-rwxr-xr-x 1 root root  2211 Jan 23  2012 locate
...
---------- 1 root root   606 Aug 17  2011 mlocate
```

```

     &#9500;&#9472;anacron&#9472;&#9472;&#9472;sh&#9472;&#9472;&#9472;run-parts&#9472;&#9472;&#9472;locate&#9472;&#9472;&#9472;updatedb.findut&#9472;&#9516;&#9472;frcode
     &#9474;                                                     &#9500;&#9472;sort
     &#9474;                                                     &#9492;&#9472;updatedb.findut&#9472;&#9472;&#9472;+

```

You have locate from the package findutils (i thought that had been split off from findutils and into mlocate) and mlocate ? Any idea why ?

Firstly can you post the contents of the locate cron file.

```
cat /etc/cron.daily/locate
```

Then the sledgehammer again for locate instead.

```
sudo chmod 000 /etc/cron.daily/locate
```

Post back tomorrow on whether you have excessive disk activity or not and we can take it from there.

**EDIT:**

```
phil@phil-G41D3:~$ pstree -s $(pgrep find)
Usage: pstree [ -a ] [ -c ] [ -h | -H PID ] [ -l ] [ -n ] [ -p ] [ -u ]
              [ -A | -G | -U ] [ PID | USER ]
......
```

For my own curiosity can you post the output of

```
cat /etc/issue; dkpg -l procps
```

Kind regards

---

### Post by philwx on 2015-12-09
Hello Matt
> **matt_symes said:**
> Hi
You have locate from the package findutils (i thought that had been split off from findutils and into mlocate) and mlocate ? Any idea why ?

Sorry, I have no idea. That is way beyond my level of understanding.

```

phil@phil-G41D3:~$ cat /etc/cron.daily/locate
#! /bin/sh

set -e

# cron script to update the `locatedb' database.
#
# Written by Ian A. Murdock <imurdock@debian.org> and 
#            Kevin Dalley <kevin@aimnet.com>

# Please consult updatedb(1) and /usr/share/doc/locate/README.Debian

[ -e /usr/bin/updatedb.findutils ] || exit 0

if [ "$(id -u)" != "0" ]; then
    echo "You must be root."
    exit 1
fi
 
# Global options for invocations of find(1)
FINDOPTIONS='-ignore_readdir_race'
# filesystems which are pruned from updatedb database
PRUNEFS="NFS nfs nfs4 afs binfmt_misc proc smbfs autofs iso9660 ncpfs coda devpts ftpfs devfs mfs shfs sysfs cifs lustre_lite tmpfs usbfs udf ocfs2"
# paths which are pruned from updatedb database
PRUNEPATHS="/tmp /usr/tmp /var/tmp /afs /amd /alex /var/spool /sfs /media /var/lib/schroot/mount"
# netpaths which are added
NETPATHS=""
# run find as this user
LOCALUSER="nobody"
# cron.daily/find: run at this priority -- higher number means lower priority
# (this is relative to the default which cron sets, which is usually +5)
NICE=10

# I/O priority
# 1 for real time, 2 for best-effort, 3 for idle ("3" only allowed for root)
IONICE_CLASS=3
# 0-7 (only valid for IONICE_CLASS 1 and 2), 0=highest, 7=lowest 
IONICE_PRIORITY=7

# allow keeping local customizations in a separate file
if [ -r /etc/updatedb.findutils.cron.local ] ; then
    . /etc/updatedb.findutils.cron.local
fi
export FINDOPTIONS PRUNEFS PRUNEPATHS NETPATHS LOCALUSER

# Set the task to run with desired I/O priority if possible
# Linux supports io scheduling priorities and classes since
# 2.6.13 with the CFQ io scheduler
if [ -x /usr/bin/ionice ] && [ "${UPDATDB_NO_IONICE}" = "" ]; then
    # don't run ionice if kernel version < 2.6.13
    KVER=$(uname -r)
    case "$KVER" in
        2.[012345]*) ;;
        2.6.[0-9]) ;;
        2.6.[0-9].*) ;;
        2.6.1[012]*) ;;
        *)
        # Avoid providing "-n" when IONICE_CLASS isn't 1 or 2
        case "$IONICE_CLASS" in
            1|2) priority="-n ${IONICE_PRIORITY:-7}" ;;
            *) priority="" ;;
        esac
        ionice -c $IONICE_CLASS $priority -p $$ > /dev/null 2>&1 || true
        ;;
    esac
fi

if getent passwd $LOCALUSER > /dev/null ; then
  cd / && nice -n ${NICE:-10} updatedb.findutils 2>/dev/null
else
  echo "User $LOCALUSER does not exist."
  exit 1
fi

```

I ran the locate sledgehammer cmd. And this morning there was no excessive disk activity! Great. 

For your curiosity:
```

phil@phil-G41D3:~$ cat /etc/issue; dkpg -l procps
Ubuntu 12.04.5 LTS \n \l

No command 'dkpg' found, did you mean:
 Command 'dpkg' from package 'dpkg' (main)
dkpg: command not found

```

I guess so:
```

phil@phil-G41D3:~$ cat /etc/issue; dpkg -l procps
Ubuntu 12.04.5 LTS \n \l

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  procps         1:3.2.8-11ubun /proc file system utilities


```

---

### Post by matt_symes on 2015-12-09
> **philwx said:**
> Hello Matt

Sorry, I have no idea. That is way beyond my level of understanding.

```

phil@phil-G41D3:~$ cat /etc/cron.daily/locate
#! /bin/sh

set -e

# cron script to update the `locatedb' database.
#
# Written by Ian A. Murdock <imurdock@debian.org> and 
#            Kevin Dalley <kevin@aimnet.com>

# Please consult updatedb(1) and /usr/share/doc/locate/README.Debian

[ -e /usr/bin/updatedb.findutils ] || exit 0

if [ "$(id -u)" != "0" ]; then
    echo "You must be root."
    exit 1
fi
 
# Global options for invocations of find(1)
FINDOPTIONS='-ignore_readdir_race'
# filesystems which are pruned from updatedb database
PRUNEFS="NFS nfs nfs4 afs binfmt_misc proc smbfs autofs iso9660 ncpfs coda devpts ftpfs devfs mfs shfs sysfs cifs lustre_lite tmpfs usbfs udf ocfs2"
# paths which are pruned from updatedb database
PRUNEPATHS="/tmp /usr/tmp /var/tmp /afs /amd /alex /var/spool /sfs /media /var/lib/schroot/mount"
# netpaths which are added
NETPATHS=""
# run find as this user
LOCALUSER="nobody"
# cron.daily/find: run at this priority -- higher number means lower priority
# (this is relative to the default which cron sets, which is usually +5)
NICE=10

# I/O priority
# 1 for real time, 2 for best-effort, 3 for idle ("3" only allowed for root)
IONICE_CLASS=3
# 0-7 (only valid for IONICE_CLASS 1 and 2), 0=highest, 7=lowest 
IONICE_PRIORITY=7

# allow keeping local customizations in a separate file
if [ -r /etc/updatedb.findutils.cron.local ] ; then
    . /etc/updatedb.findutils.cron.local
fi
export FINDOPTIONS PRUNEFS PRUNEPATHS NETPATHS LOCALUSER

# Set the task to run with desired I/O priority if possible
# Linux supports io scheduling priorities and classes since
# 2.6.13 with the CFQ io scheduler
if [ -x /usr/bin/ionice ] && [ "${UPDATDB_NO_IONICE}" = "" ]; then
    # don't run ionice if kernel version < 2.6.13
    KVER=$(uname -r)
    case "$KVER" in
        2.[012345]*) ;;
        2.6.[0-9]) ;;
        2.6.[0-9].*) ;;
        2.6.1[012]*) ;;
        *)
        # Avoid providing "-n" when IONICE_CLASS isn't 1 or 2
        case "$IONICE_CLASS" in
            1|2) priority="-n ${IONICE_PRIORITY:-7}" ;;
            *) priority="" ;;
        esac
        ionice -c $IONICE_CLASS $priority -p $$ > /dev/null 2>&1 || true
        ;;
    esac
fi

if getent passwd $LOCALUSER > /dev/null ; then
  cd / && nice -n ${NICE:-10} updatedb.findutils 2>/dev/null
else
  echo "User $LOCALUSER does not exist."
  exit 1
fi

```

I ran the locate sledgehammer cmd. And this morning there was no excessive disk activity! Great.


That's good. It was a cron job then like i suspected. So the question is how do we fix it.

If we edit the cron job then there's a chance it will be overwritten if locate get upgraded during an update.

I'm interested in why it's installed and what pulled it in. I don't really want to disable it or edit its cron job until I understand that.

Are you willing to spend a couple more days at this and see if you can find a better solution ?

If you are then if we can find the date it was installed, maybe we can see what else was also installed on that date. 

Please *copy and paste* this into the terminal, as the spaces inside the quotes are important, and copy and paste any output into you next post.

```

zgrep " installed locate" /var/log/dpkg.log.*.gz; grep " installed locate" /var/log/dpkg.log{,.1}
```

> 
For your curiosity:
```

phil@phil-G41D3:~$ cat /etc/issue; dkpg -l procps
Ubuntu 12.04.5 LTS \n \l

No command 'dkpg' found, did you mean:
 Command 'dpkg' from package 'dpkg' (main)
dkpg: command not found

```

I guess so:
```

phil@phil-G41D3:~$ cat /etc/issue; dpkg -l procps
Ubuntu 12.04.5 LTS \n \l

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  procps         1:3.2.8-11ubun /proc file system utilities


```

I fat fingered that last command then :). 

I see you're on Precise. It's been a couple of years since i ran Precise.

Kind regards

---

### Post by philwx on 2015-12-09
Hello Matt

Thanks very much for your continued help. I copied and pasted the cmd but it output nothing:

```
phil@phil-G41D3:~$ zgrep " installed locate" /var/log/dpkg.log.*.gz; grep " installed locate" /var/log/dpkg.log{,.1}
phil@phil-G41D3:~$ 
```

Phil

---

### Post by matt_symes on 2015-12-09
Hi

> **philwx said:**
> Hello Matt

Thanks very much for your continued help. I copied and pasted the cmd but it output nothing:

```
phil@phil-G41D3:~$ zgrep " installed locate" /var/log/dpkg.log.*.gz; grep " installed locate" /var/log/dpkg.log{,.1}
phil@phil-G41D3:~$ 
```

Phil

Hmm. How long have you had the excessive disk activity ?

Maybe we should broaden the search. Does this return anything ?

```
zgrep "locate" /var/log/dpkg.log.*.gz; grep "locate" /var/log/dpkg.log{,.1}
```

Can you also post the output of this please.

```
ls -l /var/log/dpkg*
```

Kind regards

---

### Post by philwx on 2015-12-09
Hello Matt

Nothing again:
```
phil@phil-G41D3:~$ zgrep "locate" /var/log/dpkg.log.*.gz; grep "locate" /var/log/dpkg.log{,.1}
phil@phil-G41D3:~$
```

Here's the other:
```
phil@phil-G41D3:~$ ls -l /var/log/dpkg*
-rw-r--r-- 1 root root 22991 Dec  2 21:40 /var/log/dpkg.log
-rw-r--r-- 1 root root 71768 Nov 26 22:26 /var/log/dpkg.log.1
-rw-r--r-- 1 root root 23869 Mar  1  2015 /var/log/dpkg.log.10.gz
-rw-r--r-- 1 root root 15616 Dec 26  2014 /var/log/dpkg.log.11.gz
-rw-r--r-- 1 root root 12788 Nov 29  2014 /var/log/dpkg.log.12.gz
-rw-r--r-- 1 root root  9716 Oct 30 08:33 /var/log/dpkg.log.2.gz
-rw-r--r-- 1 root root   485 Sep  6 18:07 /var/log/dpkg.log.3.gz
-rw-r--r-- 1 root root 10249 Aug 28 00:42 /var/log/dpkg.log.4.gz
-rw-r--r-- 1 root root  4435 Jul 31 00:25 /var/log/dpkg.log.5.gz
-rw-r--r-- 1 root root  5590 Jun 30 20:40 /var/log/dpkg.log.6.gz
-rw-r--r-- 1 root root 18413 May 31  2015 /var/log/dpkg.log.7.gz
-rw-r--r-- 1 root root  4302 Apr 12  2015 /var/log/dpkg.log.8.gz
-rw-r--r-- 1 root root 14170 Apr  1  2015 /var/log/dpkg.log.9.gz

```

Phil

---

### Post by matt_symes on 2015-12-09
Hi

I can only assume locate was installed a good while ago.

logrotate is configured to only keep 12 previous dkpg (apart from the current one) logs on a default installation.

When did you install this installation of Ubuntu ? As it's a Precise installation i assume it was a good while ago ?

Have you had the excessive disk activity long ?

I'm not sure if the best advice i can give you is to uninstall it, keep it installed and run the update manually when the computer is on but you're not planning to use it for 15 minutes, edit the cron job or something else.

I would really like to know if anything is actually using it.

**EDIT:**

Can you post the output of this command please.

```
apt-cache rdepends --installed locate mlocate
```

Kind regards

---

### Post by philwx on 2015-12-10
Hello Matt

The install of Precise was a few years ago. This was my first move into Ubuntu/Linux and I have installed/uninstalled many packages. The excessive disk activity has been happening a while but I have only really noticed to bother aftr a change of habit requiring me to do some pc work first thing in the morning. I do back-ups of my data and have been considering a reinstall of linux. So if this disk activity is not apparent it's not the end of the world.

Here's the cmd output:

```
phil@phil-G41D3:~$ apt-cache rdepends --installed locate mlocate
locate
Reverse Depends:
  findutils
mlocate
Reverse Depends:
  ubuntu-standard
  ubuntu-standard
 |findutils
```

---

### Post by matt_symes on 2015-12-10
Hi

> **philwx said:**
> Hello Matt

The install of Precise was a few years ago. This was my first move into Ubuntu/Linux and I have installed/uninstalled many packages. The excessive disk activity has been happening a while but I have only really noticed to bother aftr a change of habit requiring me to do some pc work first thing in the morning. I do back-ups of my data and have been considering a reinstall of linux. So if this disk activity is not apparent it's not the end of the world.

Here's the cmd output:

```
phil@phil-G41D3:~$ apt-cache rdepends --installed locate mlocate
locate
Reverse Depends:
  findutils
mlocate
Reverse Depends:
  ubuntu-standard
  ubuntu-standard
 |findutils
```

Having both the locate and mlocate packages is duplication of functionality. 

I think you should be able to remove it without issue.

```
sudo apt-get purge locate
```

That'll get rid of it for you.

If it does want to get rid of a large number of packages, hit 'n' when you get the option, and post back the list of packages it wants to remove.

If that does fix it for you then please mark this thread as [SOLVED] using the thread tools at the top of the page. That'll help others looking for a solution as well.

If it doesn't fix it then post back and we'll investigate more.

Kind regards

---

### Post by philwx on 2015-12-12
Hello Matt

Thread marked as solved.

Thank you very much for your help.

Phil

UPDATE
Ooops! As soon as I marked this thread soled the excessive disk activity returned. Now marked unsoled. Sorry Matt!

---

### Post by philwx on 2015-12-12
Now it seems to be mlocate:
[IMG]http://houseofhaberdashery.co.uk/u2.png[/IMG]

---

### Post by matt_symes on 2015-12-12
Hi

You can disable the mlocate cron job as you did before using chmod.

You can then run it manually whenever you need to using

```
sudo updatedb
```

This is what i have done in the past.

Kind regards

---

