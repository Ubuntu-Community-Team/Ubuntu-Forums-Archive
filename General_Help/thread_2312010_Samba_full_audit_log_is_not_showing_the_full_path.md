---
title: "Samba full audit log is not showing the full path"
date: 2016-02-01
forum: General Help
---

### Post by Devil727 on 2016-02-01
Hi All,

I am using ubuntu server 12.04 .

I have configured the samba for full audit log for a share.

Below is my samba configuration for audit log

# Audit settings
vfs object = full_audit
full_audit:prefix = %u|%I|%S
full_audit:failure = connect
full_audit:success = opendir mkdir rmdir open close read pread write pwrite rename
full_audit:facility = local7
full_audit:priority = notice

and below is the share config in samba

[share]
        comment = Ubuntu File Server Share
        writeable = yes
        create mode = 0755
        valid users = local, itadmin
        browsable = yes
        public = yes
        path = /home/local/
        force user = local
        vfs objects = full_audit
        vfs objects = recycle
        recycle:repository = .recycle
        recycle:keeptree = yes
        recycle:versions = yes


Below is my syslog configuration.

auth,authpriv.*                 /var/log/auth.log
#*.*;local7,auth,authpriv.none          -/var/log/syslog
local7.notice                       /var/log/samba-audit.log


Now when I check the samba-audit.log

It shows me the below lines where I can't see the full path

Feb  1 14:29:32  smbd[8294]: local|192.168.x.xx IPC_|chdir|ok|chdir|/tmp
Feb  1 14:29:33  smbd[7718]: local|192.168.x.xx|IPC_|chdir|ok|chdir|/tmp
Feb  1 14:29:33  smbd[8294]: local|192.168.x.xx|IPC_|chdir|ok|chdir|/tmp
Feb  1 14:29:38  smbd[8294]: last message repeated 6 times
Feb  1 14:29:38  smbd[8378]: local|192.168.x.xx|IPC_|chdir|ok|chdir|/tmp
Feb  1 14:29:38  smbd[8378]: local|192.168.x.xx|IPC_|chdir|ok|chdir|/
Feb  1 14:29:40  smbd[8294]: local|192.168.x.xx|IPC_|chdir|ok|chdir|/tmp
Feb  1 14:29:48  smbd[8294]: last message repeated 4 times
Feb  1 14:29:48  smbd[7718]: local|192.168.x.xx|IPC_|chdir|ok|chdir|/tmp
Feb  1 14:29:48  smbd[7718]: local|192.168.x.xx|IPC_|chdir|ok|chdir|/


I am not able to get what I am putting wrong Please suggest.

---

