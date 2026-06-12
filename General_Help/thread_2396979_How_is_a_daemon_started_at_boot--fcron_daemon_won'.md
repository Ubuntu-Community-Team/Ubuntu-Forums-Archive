---
title: "How is a daemon started at boot--fcron daemon won't startup"
date: 2018-07-23
forum: General Help
---

### Post by Ralph L on 2018-07-23
I am trying to get the fcron-3.3.0 scheduler working. It has features that cron/anacron don't have. Its web sites are [http://fcron.free.fr/doc/en/index.html](http://fcron.free.fr/doc/en/index.html) and [http://fcron.free.fr/download.php#fcron3.3.0](http://fcron.free.fr/download.php#fcron3.3.0), with this site giving several hints [http://www.linuxfromscratch.org/blfs/view/svn/general/fcron.html](http://www.linuxfromscratch.org/blfs/view/svn/general/fcron.html) . Everything seems to run ok, except the daemon (fcron) won't start at boot or suspend-resume time. I don't understand how daemons are normally initiated, but I see that the following file is in /lib/systemd/system/fcron.service:```
#systemd service configuration file for fcron

[Unit]
Description=fcron periodical command scheduler
After=remote-fs.target syslog.target time-sync.target
Before=shutdown.target

[Service]
Type=forking
PIDFile=/usr/local/var/run/fcron.pid
ExecStart=/usr/local/sbin/fcron -b
ExecReload=/bin/kill -USR1 $MAINPID
Restart=always
KillMode=process
# 128MB
LimitCORE=134217728

[Install]
WantedBy=multi-user.target

```
This looks like it should start the fcron daemon with the statement "ExecStart=/usr/local/sbin/fcron -b".  Indeed if I type into a Terminal /usr/local/sbin/fcron -b, the fcron daemon starts and everything runs fine.
I would much appreciate someone telling me how daemons are normally started, and also give me any hints as to why this one isn't starting.
Any help appreciated.......

---

### Post by Ralph L on 2018-07-25
A little help is needed on how to start a daemon.  
Somebody must know how to do this..................................

---

### Post by Ralph L on 2018-07-27
I figured out a way to start the fcron daemon at boot and at resume (from suspend). I don't think I did it completely correctly, since I had to put in a seemingly redundant symbolic link, but at least it works. I followed the instructions in this web site, under the section "For 15.04 and later": [https://askubuntu.com/questions/814/how-to-run-scripts-on-start-up](https://askubuntu.com/questions/814/how-to-run-scripts-on-start-up) .

In addition, I installed Fcronq--the GUI for fcron.  It gave error messages when I ran it. The author of fcronq (Xavion) replied to my email for help so I solved my fcronq problems first.  The solution to the fcronq problems may have also fixed some of my fcron daemon problems so I am going to discuss the changes I made for fcronq first. Apparently fcronq expects the file fcron.conf to be in one of these places:
1. /etc/fcron.conf
2. /usr/etc/fcron.cong
3. /etc/fcron/fcron.conf
However, the fcron installation installed it, and 2 other files, in /usr/local/etc/.  So I installed the following symbolic links targetted to the fcron files in /usr/local/etc/;
1. /etc/fcron/fcron.allow
2. /etc/fcron/fcron.conf
3. /etc/fcron/fcron.deny
Fcron requires that a User account and a Group be set up (Users and Groups or some other way) called (User account name=fcron; Group name=fcron) and Fcronq requires that each user that schedules jobs be a member of Group fcron. So I put my User name in Group fcron using Users and Groups.
Doing the 2 things above allowed Fcronq to run without error.  Whether these items contributed to getting the fcron daemon running, I don't know.

To get fcron daemon to start at boot and resume (following the website listed above):
1. Fcron installation installed /lib/systemd/system/fcron.service with the startup statement &#8220;ExecStart=/usr/local/sbin/fcron -b&#8221;.  However, apparently nothing called it.  Fcron installation also intalled the daemon itself in /usr/local/sbin/fcron.
2. In accordance with the website I created a symbolic link /etc/systemd/system/fcron.service pointing to /lib/systemd/system/fcron.service.  I then ran in a Terminal at /home/ralph (just brought up Terminal without any special setting):
               sudo systemctl daemon-reload
               sudo systemctl enable fcron.service
3. This put out a message in Terminal that said something about creating a symbolic link /etc/systemd/system/multi-user.target.wants/fcron.service (a symbolic link to /lib/systemd/system/fcron.service)
4. Apparently the results of the two commands above made /lib/systemd/system/fcron.service execute and now fcron daemon starts running at system boot and resume.

Hope this helps somebody...........

---

