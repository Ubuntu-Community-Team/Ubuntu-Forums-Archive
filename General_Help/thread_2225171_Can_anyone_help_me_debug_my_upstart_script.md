---
title: "Can anyone help me debug my upstart script?"
date: 2014-05-20
forum: General Help
---

### Post by laurence2 on 2014-05-20
Hi


I'm having issues with my upstart job and I'm not sure why.


If I run the following command from the terminal all works fine:


sudo /opt/utorrent-server/utserver -settingspath /opt/utorrent-server -logfile /opt/utorrent-server/utserver.log




However my upstart script doesnt seem to work, the process is not running after I run this and no logfile has been created


I've no idea what's wrong
> loz@gravity:~$ cat /etc/init/utorrent.conf
description "utorrent startup script"

description "utserver for linux"

start on (local-filesystems and started dbus and stopped udevtrigger)
stop on runlevel [016]

# tell upstart to respawn the process if abnormal exit
respawn


script
cd /opt/utorrent
exec su -c "/opt/utorrent-server/utserver -settingspath /opt/utorrent-server -logfile /opt/utorrent-server/utserver.log" root
end script

loz@gravity:~$ ls -ltrh /etc/init.d/utorrent
lrwxrwxrwx 1 root root 21 Apr 29 19:25 /etc/init.d/utorrent -> /lib/init/upstart-job
loz@gravity:~$ ls /opt/utorrent-server/utserver.log
ls: cannot access /opt/utorrent-server/utserver.log: No such file or directory
loz@gravity:~$ sudo start utorent
[sudo] password for loz:
start: Unknown job: utorent
loz@gravity:~$ sudo start utorrent
utorrent start/running, process 9064
loz@gravity:~$ ls /opt/utorrent-server/utserver.log
ls: cannot access /opt/utorrent-server/utserver.log: No such file or directory
loz@gravity:~$ ps -ef | grep 9064
loz       9084  8863  0 20:08 pts/2    00:00:00 grep --color=auto 9064
loz@gravity:~$ sudo initctl list | grep utor
utorrent stop/waiting
loz@gravity:~$ init-checkconf /etc/init/utorrent.conf
File /etc/init/utorrent.conf: syntax ok



---

