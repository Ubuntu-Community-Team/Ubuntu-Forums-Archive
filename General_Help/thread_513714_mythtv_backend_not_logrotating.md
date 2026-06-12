---
title: "mythtv backend not logrotating"
date: 2007-07-30
forum: General Help
---

### Post by mvsjes2 on 2007-07-30
I have a strange problem I'm trying to figure out. My mythtv backend log has not been rotating since I upgraded to feisty back in April. Everything else seems to be rotating fine.

My /etc/logrotate.d/mythtv-backend
/var/log/mythtv/mythbackend.log {
        daily
        rotate 7
        notifempty
        copytruncate
}

If I enter sudo logrotate -f -s /var/lib/logrotate/status /etc/logrotate.d/mythtv-backend, the log rotates with no errors.

My /var/lib/logrotate/status shows:
logrotate state -- version 2
"/var/log/acpid" 2007-4-8
"/var/log/aptitude" 2007-4-1
"/var/log/cups/access_log" 2007-4-1
"/var/log/cups/error_log" 2007-4-7
"/var/log/cups/page_log" 2007-4-1
"/var/log/dpkg.log" 2007-4-1
"/var/log/kdm.log" 2007-4-7
"/var/log/lvm" 2007-4-1
"/var/log/ppp-connect-errors" 2007-4-1
"/var/log/scrollkeeper.log" 2007-4-8
"/var/log/wpa_action.log" 2007-4-1
"/var/log/wtmp" 2007-4-1
"/var/log/btmp" 2007-4-1
"/var/log/mysql.log" 2007-4-12
"/var/log/mysql/mysql.log" 2007-4-2
"/var/log/mysql/mysql-slow.log" 2007-4-2
"/var/lib/myth/mythdatabase-backup.txt" 2007-4-2
"/var/log/mythtv/mythbackend.log" 2007-7-30
"/var/log/samba/log.smbd" 2007-4-8
"/var/log/samba/log.nmbd" 2007-4-8
"/var/log/apache2/access.log" 2007-4-12
"/var/log/apache2/error.log" 2007-4-12

I'm not sure why these all have dates in April. As I said, my other logs seem to be rotating properly.

My /etc/logrotate.conf:
# rotate log files weekly
weekly

# keep 4 weeks worth of backlogs
rotate 4

# create new (empty) log files after rotating old ones
create

# uncomment this if you want your log files compressed
#compress

# packages drop log rotation information into this directory
include /etc/logrotate.d

# no packages own wtmp, or btmp -- we'll rotate them here
/var/log/wtmp {
    missingok
    monthly
    create 0664 root utmp
    rotate 1
}

/var/log/btmp {
    missingok
    monthly
    create 0664 root utmp
    rotate 1
}

---

