---
title: "autostart at boot programs"
date: 2012-12-24
forum: General Help
---

### Post by sdowney717 on 2012-12-24
2 programs i want to start up.

frome commandline i do it like this

rygel
sudo service minidlna restart


I want to let these start at boot
so what to do?

---

### Post by sdowney717 on 2012-12-24
run gnome-session-properties for rygel
not in the menus'

but the service startup?????????????????????????????????????

---

### Post by sdowney717 on 2012-12-24
run this will give bigger list

sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop

[http://www.muktware.com/4179/display-hidden-startup-applications-ubuntu-1204#.UNjH7mJQAsE](http://www.muktware.com/4179/display-hidden-startup-applications-ubuntu-1204#.UNjH7mJQAsE)

---

### Post by fdrake on 2012-12-24
> **sdowney717 said:**
> run gnome-session-properties for rygel
not in the menus'

but the service startup?????????????????????????????????????

the commands differ for permission one needs the sudo the other doesnt. I sugget to use the cron
check [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

teh seccond command willl need root priv so you have otk run it as 
"sudo cron -e"

for time you have to use the "@reboot" followed by the command.
[http://www.cyberciti.biz/faq/linux-execute-cron-job-after-system-reboot/](http://www.cyberciti.biz/faq/linux-execute-cron-job-after-system-reboot/)

---

### Post by sdowney717 on 2012-12-24
chron?
I need some help with the suggestion

i put the minildlna command into startup
here is a reboot
minidlna shuts down
[2012/12/24 16:30:30] minidlna.c:155: warn: received signal 15, good-bye

here i commandline told it to restart
[2012/12/24 16:39:26] minidlna.c:907: warn: Starting MiniDLNA version 1.0.21 [SQLite 3.7.9].
[2012/12/24 16:39:26] minidlna.c:1002: warn: HTTP listening on port 8200


> ```
[2012/12/24 12:53:01] minidlna.c:907: warn: Starting MiniDLNA version 1.0.21 [SQLite 3.7.9].
[2012/12/24 12:53:01] minidlna.c:935: warn: Creating new database...
[2012/12/24 12:53:01] minidlna.c:1002: warn: HTTP listening on port 8200
[2012/12/24 12:53:01] scanner.c:719: warn: Scanning /opt
[2012/12/24 12:53:02] scanner.c:790: warn: Scanning /opt finished (0 files)!
[2012/12/24 12:59:40] minidlna.c:155: warn: received signal 15, good-bye
[2012/12/24 12:59:41] minidlna.c:907: warn: Starting MiniDLNA version 1.0.21 [SQLite 3.7.9].
[2012/12/24 12:59:41] minidlna.c:1002: warn: HTTP listening on port 8200
[2012/12/24 12:59:56] minidlna.c:155: warn: received signal 15, good-bye
[2012/12/24 12:59:56] minidlna.c:907: warn: Starting MiniDLNA version 1.0.21 [SQLite 3.7.9].
[2012/12/24 12:59:56] minidlna.c:935: warn: Creating new database...
[2012/12/24 12:59:56] minidlna.c:1002: warn: HTTP listening on port 8200
[2012/12/24 12:59:56] scanner.c:719: warn: Scanning /opt
[2012/12/24 12:59:56] scanner.c:790: warn: Scanning /opt finished (0 files)!
[2012/12/24 12:59:56] scanner.c:719: warn: Scanning /home/daviddowney/Videos
[2012/12/24 12:59:56] scanner.c:790: warn: Scanning /home/daviddowney/Videos finished (0 files)!
[2012/12/24 14:20:06] metadata.c:677: warn: Opening /home/daviddowney/Videos/Untitled 55.avi failed!
[2012/12/24 14:20:06] scanner.c:498: warn: Unsuccessful getting details for /home/daviddowney/Videos/Untitled 55.avi!
[2012/12/24 15:22:07] minidlna.c:155: warn: received signal 15, good-bye
[2012/12/24 15:50:17] minidlna.c:907: warn: Starting MiniDLNA version 1.0.21 [SQLite 3.7.9].
[2012/12/24 15:50:17] minidlna.c:1002: warn: HTTP listening on port 8200
[2012/12/24 16:30:30] minidlna.c:155: warn: received signal 15, good-bye
[2012/12/24 16:39:26] minidlna.c:907: warn: Starting MiniDLNA version 1.0.21 [SQLite 3.7.9].
[2012/12/24 16:39:26] minidlna.c:1002: warn: HTTP listening on port 8200
```

---

### Post by NikTh on 2012-12-24
> **sdowney717 said:**
> 
but the service startup?????????????????????????????????????

Is this startup service must begin to a specific time ? after rygel ? 

As now you have added the rygel to startup applications.. you can add the restart of service to rc.local with a specific delay.. 

```
sudo nano rc.local
```and after exit 0 , add 
```
(sleep 15 ;  sudo service minidlna restart) &
```see if 15 seconds are ok , if not , you can increase the time.. 

Thanks

---

### Post by sdowney717 on 2012-12-24
hi, I have several rc.local,  which one to edit?

also what does  15 seconds do?

---

### Post by sdowney717 on 2012-12-24
OK, I edited the one at /etc
I rebooted and minidlna was not started

so i ran command in terminal manually and it starts.
20:18 is the manual start
20:15 is the boot


log shows this
```
[2012/12/24 20:04:40] minissdp.c:325: error: sendto(udp_notify=8, 192.168.5.142): Invalid argument
[2012/12/24 20:15:38] minidlna.c:155: warn: received signal 15, good-bye
[2012/12/24 20:15:38] minissdp.c:738: error: sendto(udp_shutdown=8): Invalid argument
[2012/12/24 20:15:38] minidlna.c:1266: error: Failed to broadcast good-bye notifications
[2012/12/24 20:18:10] minidlna.c:907: warn: Starting MiniDLNA version 1.0.21 [SQLite 3.7.9].
[2012/12/24 20:18:10] minidlna.c:1002: warn: HTTP listening on port 8200
```

---

### Post by sdowney717 on 2012-12-24
set to 30 but still getting a goodbye notification on a boot up

```
[2012/12/24 20:15:38] minidlna.c:1266: error: Failed to broadcast good-bye notifications
[2012/12/24 20:18:10] minidlna.c:907: warn: Starting MiniDLNA version 1.0.21 [SQLite 3.7.9].
[2012/12/24 20:18:10] minidlna.c:1002: warn: HTTP listening on port 8200
[2012/12/24 20:28:52] minidlna.c:155: warn: received signal 15, good-bye
```

---

### Post by sdowney717 on 2012-12-24
do you think the delay needs to be much longer??

found this on auto starting
```
# Change db_dir so that the database is saved across reboots
db_dir=/home/pi/.minidlna
 
# Uncomment log_dir for now in case we hit problems
log_dir=/var/log
 
# Start MiniDLNA at boot
sudo update-rc.d minidlna defaults
 
# Start MiniDLNA now
sudo service minidlna start
```

so i ran and it gives me this
```
daviddowney@scott-P5QCusb:~$ sudo update-rc.d minidlna defaults
[sudo] password for daviddowney: 
 System start/stop links for /etc/init.d/minidlna already exist.
daviddowney@scott-P5QCusb:~$ 


```

---

### Post by NikTh on 2012-12-25
If you want to start manual the miniDLNA , then remove it from startup .. and keep only the rc.local entry. 

```
sudo update-rc.d -f minidlna remove
``` 

Then change the entry in rc.local (yes , etc/rc.local is the correct) to 
```
(sleep 30 ; sudo service minidlna start) & 
``` 

Thanks

---

### Post by sdowney717 on 2012-12-25
It is starting i think at boot, but fails with error code 15

Now this may have to do with where I am right now. 
Using an adhoc network. Maybe the connections are not ready in time??

Anyway maybe this will be moot after I get home from Christmas.

---

