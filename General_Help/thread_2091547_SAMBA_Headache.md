---
title: "SAMBA Headache"
date: 2012-12-05
forum: General Help
---

### Post by leapinlarry on 2012-12-05
I've had a SAMBA server that's behaved itself well until this morning when I did an restart of the server.  Strange thing, it didn't entirely break - only partially...  lol

I can mount the share and read files from it fine, but I can no longer write to the share.  Here's some abbreviated info to help explain what's here.

Ubuntu Server 10.10 LTS with Samba 3.4.7

relevant pieces of smb.conf:

[global]
    workgroup = BEANIES
    server string = BEANIES File Shares
    interfaces = 192.168.10.10/24
    log level = 1
    log file = /var/log/samba/log.%m
    max log size = 50
    max xmit = 65535
    deadtime = 15
    socket options = TCP_NODELAY IPTOS_LOWDELAY
    load printers = No
    preferred master = Yes
    dns proxy = No
    wins support = Yes

[larry]
    comment = Larry's files
    path = /data/larry
    valid users = larry, bob
    admin users = larry, bob
    force user = larry
    force group = larry
    read only = No
    create mask = 0775
    browseable = No
    browsable = No

smb status notes the following:

Samba version 3.4.7
PID     Username      Group         Machine                        
-------------------------------------------------------------------
3542      larry            larry            workstation  (10.1.1.127)

Service      pid     machine       Connected at
-------------------------------------------------------
larry           3542   workstation   Wed Dec  5 05:14:58 2012

Locked files:
Pid          Uid        DenyMode   Access      R/W        Oplock           SharePath   Name   Time
--------------------------------------------------------------------------------------------------
3542         1000       DENY_NONE  0x100081    RDONLY     NONE             /data/larry   .   Wed Dec  5 05:14:59 2012

Given that larry has an entry with password and is able to mount the directory, I assume that all is well in that vein.  I can log in via smbclient from the same server and I still have no write permission.  The log file for 10.1.1.127 is empty, and the only info I see in log.smbd referrs to:

[2012/12/05 04:58:31,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option

What am I missing in this equation?

Thanks in advance for any help.

Larry

---

### Post by drdos2006 on 2012-12-05
SOunds like a write permissions problem. I found installing Webmin on the server and using a browser to change server operations a breeze, simplified a lot of things.

Logon to your server and download from your server with :
sudo wget [http://prdownloads.sourceforge.net/webadmin/webmin_1.590_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.590_all.deb)

Install with :
sudo dpkg -i webmin_1.590_all.deb

Add extra libraries with :
sudo apt-get -f install


regards

---

### Post by leapinlarry on 2012-12-06
so...  More digging resulted in some useful information that might be of use to someone later.

Turns out, SAMBA is running fine (apparently) -- the system restarted with a read-only filesystem and needed fsck run on it, which solved the problem.  However, because I was doing the work remotely via SSH, I didn't see the request for a filesystem check.

Lesson learned.

---

