---
title: "/var/run/freeradius/freeradius.pid not found..."
date: 2015-02-15
forum: General Help
---

### Post by mark198 on 2015-02-15
I've had Freeradius up and running for about 2 months now without issue.  Today I intalled vsftpd and now I can't get it to run properly.  I've even gone as far as doing a clean Ubuntu and Freeradius install.  When I boot the server doing a "service freeradius status" shows it as running.  However once I restart the service I get this error "/var/run/freeradius/freeradius.pid not found..."  I checked to ensure that the directory exists and it does.  I'm new to Ubuntu and Linux in general.  Anyone have a suggestion to address this?  Thanks.

---

### Post by mark198 on 2015-02-15
ok..playing around this is what I've discovered.  I can start/stop the service and it responds as it should until I edit the users and clients.conf files.  after that if I do a restart then do a status it says its stop/waiting.  If I do a stop command it says "Unknown Instance".  don't know if it makes a difference but I'm using WinSCP to access and edit the files.  I've done it this way in the past without issue.

---

### Post by mark198 on 2015-02-15
update.....did apt-get purge freeradius and re-installed it.  After adding about 25 clients (stopping and restarting after each) I'm getting the same error again.

---

