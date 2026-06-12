---
title: "Error - Xsession: unable to write to /tmp"
date: 2007-05-02
forum: General Help
---

### Post by bobleny on 2007-05-02
System: Kubuntu Edgy Eft 6.10

Problem: I am unable to login to the system. When I enter my user info, I get the following error and then I am sent back to the login screen.

Error: “Xsession: warning: unable to write to /tmp; x session may exit with an error”
---------------------------

Possible Cause-
Something is full?

Directory: /dev/hdba2
Size: 9.4 GB
Used: 9.2 GB
Available: 0 GB
Used %: 100%
Mounted on: /
File System: ext3
---------------------------

Possible Cause-
/tmp directory full?

$root@george# ls /tmp
1064969842
$root@george# rm /tmp/1064969842
Error: can not remove: not a file or directory

$root@george# du /tmp
 4  /tmp/.X11-unix
 4  /tmp/.ICE-unix
 4  /tmp/0002672176/.qt
 8  /tmp/0002672176
24  /tmp
---------------------------

I'm not sure what to do about this. None of it makes sense to me...

If you could help, please do!

Thanks!

---

### Post by bobleny on 2007-05-08
Does any one mind if I bump this thread up a little?

Any one have any ideas?

---

### Post by taurus on 2007-05-08
Boot into recovery mode and clear up some space on /.

```
aptitude clean
df -h
```

---

### Post by bobleny on 2007-05-08
Thank you! That cleaned it enough to let me login.

However... It is still 97% full!
Directory: /dev/hdba2
Size: 9.4 GB
Used: 8.6 GB
Available: 339 MB
Used %: 97%
Mounted on: /
File System: ext3


When I installed Kubuntu I was very careful to make sure I would have enough room on my HDD. I was told I wouldn't need more than 5 gigs for my / partition. I made it 10 gigs! I don't understand why it is so full.

How do I clean it up better or something?

---

### Post by taurus on 2007-05-08
Don't forget to empty your trash bin.  

```
cd ~/.Trash
rm *
df -h
```
Otherwise, post the output of this command here.

```
sudo du -h /
```

---

### Post by bobleny on 2007-05-08
I can't give you the results of that command! I can't even see most of the results. There where so many things listed, It's only showing a little bit of what was printed.

I did get this though:
4.0K    /tmp/.X11-unix
4.0K    /tmp/.ICE-unix
4.0K    /tmp/0558781349/.qt
8.0K    /tmp/0558781349
8.0K    /tmp/kde-bob
4.0K    /tmp/1045749005/.qt
8.0K    /tmp/1045749005
4.0K    /tmp/ssh-EtpqgG4544
4.0K    /tmp/orbit-bob
8.0K    /tmp/gconfd-bob/lock
12K     /tmp/gconfd-bob
60K     /tmp
33G     /


Everything that I can see above that is 0K...

---

### Post by taurus on 2007-05-08
```
sudo du -h /  | more
```
Hit the space key for the next 24l lines.

---

### Post by bobleny on 2007-05-08
May I ask why you need all this information?

Edit:
Well, It will take me a long time to copy and paste all these, a long time!

---

### Post by taurus on 2007-05-08
So I want to see which directory (directories) takes up the most space.  Perhaps try this then.

```
sudo du -h /var
```

---

### Post by bobleny on 2007-05-08
root@George:/# du -h /var
0       /var/lock/apache2
0       /var/lock
0       /var/run/sudo/bob
0       /var/run/sudo
0       /var/run/console
0       /var/run/apache2
4.0K    /var/run/hal
4.0K    /var/run/dbus
4.0K    /var/run/mysqld
16K     /var/run/hplip
0       /var/run/cups/certs
4.0K    /var/run/cups
4.0K    /var/run/xauth
0       /var/run/xdmctl/dmctl-:0
0       /var/run/xdmctl/dmctl
0       /var/run/xdmctl
8.0K    /var/run/klogd
0       /var/run/screen
4.0K    /var/run/network
92K     /var/run
2.5M    /var/backups
4.0K    /var/cache/apt/archives/partial
24K     /var/cache/apt/archives
20M     /var/cache/apt
20M     /var/cache/apt-index-watcher
4.0K    /var/cache/cups/ppd
16K     /var/cache/cups
3.1M    /var/cache/debconf
4.0K    /var/cache/debtags/partial
8.0K    /var/cache/debtags
28K     /var/cache/dictionaries-common
4.0K    /var/cache/locate
4.0K    /var/cache/man/X11R6
4.0K    /var/cache/man/cat1
4.0K    /var/cache/man/cat2
4.0K    /var/cache/man/cat3
4.0K    /var/cache/man/cat4
4.0K    /var/cache/man/cat5
4.0K    /var/cache/man/cat6
4.0K    /var/cache/man/cat7
4.0K    /var/cache/man/cat8
4.0K    /var/cache/man/cat9
4.0K    /var/cache/man/fsstnd
4.0K    /var/cache/man/local
4.0K    /var/cache/man/oldlocal
4.0K    /var/cache/man/opt
356K    /var/cache/man
4.0K    /var/cache/pppconfig
16K     /var/cache/setup-tool-backends/debug/network/1
36K     /var/cache/setup-tool-backends/debug/network/2
8.0K    /var/cache/setup-tool-backends/debug/network/3
64K     /var/cache/setup-tool-backends/debug/network
68K     /var/cache/setup-tool-backends/debug
16K     /var/cache/setup-tool-backends/backup/network/First/etc/samba
8.0K    /var/cache/setup-tool-backends/backup/network/First/etc/network
40K     /var/cache/setup-tool-backends/backup/network/First/etc
44K     /var/cache/setup-tool-backends/backup/network/First
8.0K    /var/cache/setup-tool-backends/backup/network/1/etc/network
28K     /var/cache/setup-tool-backends/backup/network/1/etc
32K     /var/cache/setup-tool-backends/backup/network/1
80K     /var/cache/setup-tool-backends/backup/network
84K     /var/cache/setup-tool-backends/backup
156K    /var/cache/setup-tool-backends
4.0K    /var/cache/apache2/proxy
8.0K    /var/cache/apache2
43M     /var/cache
20K     /var/lib/acpi-support
12K     /var/lib/alsa
4.0K    /var/lib/apt/lists/partial
46M     /var/lib/apt/lists
4.0K    /var/lib/apt/periodic
46M     /var/lib/apt
4.0K    /var/lib/aptitude
3.5M    /var/lib/aspell
52K     /var/lib/belocs
1.2M    /var/lib/debtags
16K     /var/lib/defoma/fontconfig.d/A
20K     /var/lib/defoma/fontconfig.d/B
16K     /var/lib/defoma/fontconfig.d/C
96K     /var/lib/defoma/fontconfig.d/D
8.0K    /var/lib/defoma/fontconfig.d/E
24K     /var/lib/defoma/fontconfig.d/F
24K     /var/lib/defoma/fontconfig.d/G
12K     /var/lib/defoma/fontconfig.d/H
8.0K    /var/lib/defoma/fontconfig.d/J
16K     /var/lib/defoma/fontconfig.d/K
12K     /var/lib/defoma/fontconfig.d/L
68K     /var/lib/defoma/fontconfig.d/M
24K     /var/lib/defoma/fontconfig.d/N
8.0K    /var/lib/defoma/fontconfig.d/O
16K     /var/lib/defoma/fontconfig.d/P
8.0K    /var/lib/defoma/fontconfig.d/R
8.0K    /var/lib/defoma/fontconfig.d/S
16K     /var/lib/defoma/fontconfig.d/T
16K     /var/lib/defoma/fontconfig.d/U
8.0K    /var/lib/defoma/fontconfig.d/V
12K     /var/lib/defoma/fontconfig.d/a
12K     /var/lib/defoma/fontconfig.d/j
12K     /var/lib/defoma/fontconfig.d/m
8.0K    /var/lib/defoma/fontconfig.d/u
600K    /var/lib/defoma/fontconfig.d
4.0K    /var/lib/defoma/gs.d/dirs/CMap
188K    /var/lib/defoma/gs.d/dirs/fonts
196K    /var/lib/defoma/gs.d/dirs
304K    /var/lib/defoma/gs.d
140K    /var/lib/defoma/pango.d
68K     /var/lib/defoma/scripts
4.0K    /var/lib/defoma/x-ttcidfont-conf.d/dirs/CID
200K    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
208K    /var/lib/defoma/x-ttcidfont-conf.d/dirs
532K    /var/lib/defoma/x-ttcidfont-conf.d
152K    /var/lib/defoma/libwmf0.2-7.d
2.2M    /var/lib/defoma
8.0K    /var/lib/dhcp3
8.0K    /var/lib/dictionaries-common/aspell
12K     /var/lib/dictionaries-common/wordlist
24K     /var/lib/dictionaries-common
4.0K    /var/lib/apache2
236K    /var/lib/doc-base/info
240K    /var/lib/doc-base
232K    /var/lib/dpkg/alternatives
27M     /var/lib/dpkg/info
4.0K    /var/lib/dpkg/methods/disk
4.0K    /var/lib/dpkg/methods/floppy
4.0K    /var/lib/dpkg/methods/mnt
16K     /var/lib/dpkg/methods
4.0K    /var/lib/dpkg/parts
4.0K    /var/lib/dpkg/updates
31M     /var/lib/dpkg
1.4M    /var/lib/gcj-4.1
8.0K    /var/lib/gconf/debian.defaults
4.7M    /var/lib/gconf/defaults
4.7M    /var/lib/gconf
4.0K    /var/lib/gstreamer/0.10
8.0K    /var/lib/gstreamer
8.0K    /var/lib/guidance
8.0K    /var/lib/initramfs-tools
4.0K    /var/lib/initscripts
8.0K    /var/lib/kdm
12K     /var/lib/locales/supported.d
16K     /var/lib/locales
8.0K    /var/lib/logrotate
160K    /var/lib/misc
8.0K    /var/lib/mozilla-firefox/extensions.d
12K     /var/lib/mozilla-firefox
8.0K    /var/lib/mozilla-thunderbird/extensions.d
4.0K    /var/lib/mozilla-thunderbird/components
16K     /var/lib/mozilla-thunderbird
68K     /var/lib/scrollkeeper/C
60K     /var/lib/scrollkeeper/af
60K     /var/lib/scrollkeeper/am
60K     /var/lib/scrollkeeper/an
60K     /var/lib/scrollkeeper/ar
60K     /var/lib/scrollkeeper/as
60K     /var/lib/scrollkeeper/az
68K     /var/lib/scrollkeeper/be
60K     /var/lib/scrollkeeper/bg
60K     /var/lib/scrollkeeper/bn
60K     /var/lib/scrollkeeper/br
60K     /var/lib/scrollkeeper/bs
60K     /var/lib/scrollkeeper/ca
60K     /var/lib/scrollkeeper/co
60K     /var/lib/scrollkeeper/cs
60K     /var/lib/scrollkeeper/cy
60K     /var/lib/scrollkeeper/da
60K     /var/lib/scrollkeeper/de
60K     /var/lib/scrollkeeper/el
60K     /var/lib/scrollkeeper/en
60K     /var/lib/scrollkeeper/en_GB
60K     /var/lib/scrollkeeper/eo
60K     /var/lib/scrollkeeper/es
60K     /var/lib/scrollkeeper/et
60K     /var/lib/scrollkeeper/eu
60K     /var/lib/scrollkeeper/fa
60K     /var/lib/scrollkeeper/fi
60K     /var/lib/scrollkeeper/fo
60K     /var/lib/scrollkeeper/fr
60K     /var/lib/scrollkeeper/ga
60K     /var/lib/scrollkeeper/gl
60K     /var/lib/scrollkeeper/gu
60K     /var/lib/scrollkeeper/he
60K     /var/lib/scrollkeeper/hr
60K     /var/lib/scrollkeeper/hu
60K     /var/lib/scrollkeeper/hy
60K     /var/lib/scrollkeeper/ia
60K     /var/lib/scrollkeeper/id
60K     /var/lib/scrollkeeper/is
60K     /var/lib/scrollkeeper/it
60K     /var/lib/scrollkeeper/ja
60K     /var/lib/scrollkeeper/ka
60K     /var/lib/scrollkeeper/kk
60K     /var/lib/scrollkeeper/kn
60K     /var/lib/scrollkeeper/ko
60K     /var/lib/scrollkeeper/ku
60K     /var/lib/scrollkeeper/ky
60K     /var/lib/scrollkeeper/lb
60K     /var/lib/scrollkeeper/lg
60K     /var/lib/scrollkeeper/li
60K     /var/lib/scrollkeeper/lo
60K     /var/lib/scrollkeeper/lt
60K     /var/lib/scrollkeeper/lv
60K     /var/lib/scrollkeeper/mg
60K     /var/lib/scrollkeeper/mi
60K     /var/lib/scrollkeeper/ml
60K     /var/lib/scrollkeeper/mn
60K     /var/lib/scrollkeeper/mr
60K     /var/lib/scrollkeeper/ms
60K     /var/lib/scrollkeeper/my
60K     /var/lib/scrollkeeper/nb
60K     /var/lib/scrollkeeper/ne
60K     /var/lib/scrollkeeper/nl
60K     /var/lib/scrollkeeper/nn
60K     /var/lib/scrollkeeper/no
60K     /var/lib/scrollkeeper/oc
60K     /var/lib/scrollkeeper/or
60K     /var/lib/scrollkeeper/pa
60K     /var/lib/scrollkeeper/pl
60K     /var/lib/scrollkeeper/pt
60K     /var/lib/scrollkeeper/pt_BR
60K     /var/lib/scrollkeeper/rm
60K     /var/lib/scrollkeeper/ro
68K     /var/lib/scrollkeeper/ru
60K     /var/lib/scrollkeeper/rw
60K     /var/lib/scrollkeeper/se
60K     /var/lib/scrollkeeper/si
60K     /var/lib/scrollkeeper/sk
60K     /var/lib/scrollkeeper/sl
60K     /var/lib/scrollkeeper/sq
68K     /var/lib/scrollkeeper/sr
60K     /var/lib/scrollkeeper/sr@Latn
60K     /var/lib/scrollkeeper/sv
60K     /var/lib/scrollkeeper/sw
60K     /var/lib/scrollkeeper/ta
60K     /var/lib/scrollkeeper/te
60K     /var/lib/scrollkeeper/tg
60K     /var/lib/scrollkeeper/th
60K     /var/lib/scrollkeeper/tk
60K     /var/lib/scrollkeeper/tl
60K     /var/lib/scrollkeeper/tr
60K     /var/lib/scrollkeeper/ug
68K     /var/lib/scrollkeeper/uk
60K     /var/lib/scrollkeeper/ur
60K     /var/lib/scrollkeeper/uz
60K     /var/lib/scrollkeeper/vi
60K     /var/lib/scrollkeeper/wa
60K     /var/lib/scrollkeeper/wo
60K     /var/lib/scrollkeeper/xh
60K     /var/lib/scrollkeeper/yi
60K     /var/lib/scrollkeeper/yo
60K     /var/lib/scrollkeeper/zh_CN
60K     /var/lib/scrollkeeper/zh_TW
60K     /var/lib/scrollkeeper/zu
8.0K    /var/lib/scrollkeeper/TOC
8.0K    /var/lib/scrollkeeper/index
6.2M    /var/lib/scrollkeeper
8.0K    /var/lib/pango
4.0K    /var/lib/php5
84K     /var/lib/python-support/python2.4/dbus
120K    /var/lib/python-support/python2.4/elementtree
20K     /var/lib/python-support/python2.4/elementtree-1.2.6_20050316.egg-info
1.5M    /var/lib/python-support/python2.4
1.6M    /var/lib/python-support
2.5M    /var/lib/dlocate
4.0K    /var/lib/sgml-base
2.0M    /var/lib/slocate
4.0K    /var/lib/snmp
32K     /var/lib/ucf/cache
72K     /var/lib/ucf
8.0K    /var/lib/urandom
4.0K    /var/lib/vim/addons
8.0K    /var/lib/vim
28K     /var/lib/x11
4.0K    /var/lib/xkb
32K     /var/lib/xml-core
680K    /var/lib/mysql/mysql
180K    /var/lib/mysql/PBB
344K    /var/lib/mysql/bobleny_site
28K     /var/lib/mysql/testy
56K     /var/lib/mysql/medieval
64K     /var/lib/mysql/bobleny_crow
68K     /var/lib/mysql/bobleny_acc
22M     /var/lib/mysql
128K    /var/lib/site
8.0K    /var/lib/phpmyadmin
4.0K    /var/lib/mysql-cluster
123M    /var/lib
4.0K    /var/local
64K     /var/log/cups
12K     /var/log/fsck
4.0K    /var/log/news
524K    /var/log/installer
20K     /var/log/mysql
96K     /var/log/apache2
3.0M    /var/log
4.0K    /var/mail
4.0K    /var/opt
16K     /var/spool/anacron
8.0K    /var/spool/cron/atjobs
4.0K    /var/spool/cron/atspool
4.0K    /var/spool/cron/crontabs
20K     /var/spool/cron
4.0K    /var/spool/cups/tmp
72K     /var/spool/cups
4.0K    /var/spool/openoffice/uno_packages/cache
8.0K    /var/spool/openoffice/uno_packages
12K     /var/spool/openoffice
124K    /var/spool
4.0K    /var/tmp/kdecache-root/background
1.1M    /var/tmp/kdecache-root
60K     /var/tmp/kdecache-bob/background
76K     /var/tmp/kdecache-bob/favicons
8.0K    /var/tmp/kdecache-bob/http/g
16K     /var/tmp/kdecache-bob/http/u
16K     /var/tmp/kdecache-bob/http/i
4.0K    /var/tmp/kdecache-bob/http/h
12K     /var/tmp/kdecache-bob/http/e
4.0K    /var/tmp/kdecache-bob/http/d
4.0K    /var/tmp/kdecache-bob/http/q
4.0K    /var/tmp/kdecache-bob/http/s
4.0K    /var/tmp/kdecache-bob/http/a
8.0K    /var/tmp/kdecache-bob/http/n
20K     /var/tmp/kdecache-bob/http/p
12K     /var/tmp/kdecache-bob/http/m
40K     /var/tmp/kdecache-bob/http/f
8.0K    /var/tmp/kdecache-bob/http/k
4.0K    /var/tmp/kdecache-bob/http/x
4.0K    /var/tmp/kdecache-bob/http/y
12K     /var/tmp/kdecache-bob/http/r
4.0K    /var/tmp/kdecache-bob/http/b
12K     /var/tmp/kdecache-bob/http/l
8.0K    /var/tmp/kdecache-bob/http/c
12K     /var/tmp/kdecache-bob/http/o
8.0K    /var/tmp/kdecache-bob/http/t
4.0K    /var/tmp/kdecache-bob/http/v
4.0K    /var/tmp/kdecache-bob/http/j
236K    /var/tmp/kdecache-bob/http
4.0K    /var/tmp/kdecache-bob/help
4.0K    /var/tmp/kdecache-bob/krun
1.5M    /var/tmp/kdecache-bob
2.6M    /var/tmp
152K    /var/www/apache2-default
160K    /var/www
173M    /var

---

### Post by bobleny on 2007-05-08
Here where the folders in my / directory that really stood out as a large file!

/lib - 102 MB
/proc - 2056 MB
/sys - 592 MB
/usr - 2.3 GB
/var - 153 MB
/home - 22 GB

---

### Post by taurus on 2007-05-10
You must have a separate /home then!  

```
sudo aptitude autoclean
df -h
```

---

### Post by bobleny on 2007-05-10
I do have a separate /home!

df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             9.4G  8.6G  339M  97% /
varrun                126M   92K  125M   1% /var/run
varlock               126M     0  126M   0% /var/lock
procbususb             10M  120K  9.9M   2% /proc/bus/usb
udev                   10M  120K  9.9M   2% /dev
devshm                126M     0  126M   0% /dev/shm
lrm                   126M   18M  108M  14% /lib/modules/2.6.17-10-generic/volatile
/dev/hda5              52M  8.1M   41M  17% /boot
[COLOR="Red"]/dev/hda4             191G   23G  159G  13% /home[/COLOR]
/dev/hda3              29G  2.7G   25G  10% /usr


Edit:

And every time I run, "sudo aptitude autoclean", It frees 0MB of space...

---

### Post by taurus on 2007-05-10
Now, this is interesting.  You have /, /boot, /usr, & /home and your 10GB in / is almost filled up.  Can you boot your machine with a LiveCD?  Then run

Applications -> Accessories -> Terminal
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda2 /mnt/ubuntu
sudo du -h /mnt/ubuntu
```
and post the complete output of the last command here.

---

### Post by bobleny on 2007-05-10
Uhm, no, my live CD was destroyed. The back of it got riped off some how. It wont even start....

Is there an ISO of the system that I installed on here some where? Like, I installed Kubuntu 6.10, I was just wondering if the ISO is on here as well.

---

### Post by bobleny on 2007-05-10
OK, I got a new CD made and I tried the command. It wouldn't give me all of them, they where cut off...

Also, are you sure you want me to post all of them? There are hundreds of lines that are printed.... It will take me a long time to get all of them too...

---

### Post by bobleny on 2007-05-11
Going trough the list of files produced by, "du -h /mnt/ubuntu", I noticed a lot of files that where deleted a long time ago. The files where stored at, "/root/.local/share/Trash/".

I deleted the files in there and my system went from this:
```

root@George:/# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             9.4G  8.6G  338M  97% /
varrun                126M   96K  125M   1% /var/run
varlock               126M     0  126M   0% /var/lock
procbususb             10M  132K  9.9M   2% /proc/bus/usb
udev                   10M  132K  9.9M   2% /dev
devshm                126M     0  126M   0% /dev/shm
lrm                   126M   18M  108M  14% /lib/modules/2.6.17-10-generic/volatile
/dev/hda5              52M  8.1M   41M  17% /boot
/dev/hda4             191G   24G  158G  14% /home
/dev/hda3              29G  2.7G   25G  10% /usr
/dev/sda1             2.0G  1.9G   62M  97% /media/MY USB DISK

```


To this:
```

root@George:/# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             9.4G  426M  8.6G   5% /
varrun                126M   96K  125M   1% /var/run
varlock               126M     0  126M   0% /var/lock
procbususb             10M  132K  9.9M   2% /proc/bus/usb
udev                   10M  132K  9.9M   2% /dev
devshm                126M     0  126M   0% /dev/shm
lrm                   126M   18M  108M  14% /lib/modules/2.6.17-10-generic/volatile
/dev/hda5              52M  8.1M   41M  17% /boot
/dev/hda4             191G   24G  158G  14% /home
/dev/hda3              29G  2.7G   25G  10% /usr
/dev/sda1             2.0G  1.9G   62M  97% /media/MY USB DISK

```


That is a huge change, 97% to 5%!

Than you so much! Every thing seems fine now, thanks!

---

