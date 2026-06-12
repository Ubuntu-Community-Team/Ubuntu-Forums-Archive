---
title: "[ubuntu] can't access samba share"
date: 2015-04-09
forum: General Help
---

### Post by provoost2 on 2015-04-09
I have set up a SFTP which I can connect to, go to the right directory and read/write files to.

The full path is home/sftpuser/SFTP/Customer
The user "sftpuser" I am connecting with is in the group "ftpusers" which has read/write access.

That works fine.

Here is my sshd_config:
```
Match Group ftpusers ChrootDirectory /home/%u/
 ForceCommand internal-sftp
  AllowAgentForwarding no
  AllowTcpForwarding no
  X11Forwarding no
```

However, I made a samba share of the folder Customer, when I go to the IP adress on a Windows machine "\\10.0.0.1\" I can see the folder Customer, when entering it requests user/pass and afterwards gives an error: you have not the right permissions.

In Webmin:
[TABLE="class: ui_table sortable ui_columns, width: 100%"]
[TR="class: mainbody row1, bgcolor: #F8F8FA"]
[TD][C]("https://10.1.2.137:10000/samba/edit_fshare.cgi?share=Rio%20Tinto")ustomer[/TD]
[TD]/home/sftpuser/SFTP/Customer[/TD]
[TD]Read/write to everyone[/TD]
[/TR]
[/TABLE]

My smb.conf:
```
[global]
    syslog = 0
    log file = /var/log/samba/log.%m
    read raw = no
    write raw = no
    passdb backend = tdbsam
    workgroup = DOMAIN
    usershare allow guests = yes
    socket options = TCP_NODELAY
    pam password change = yes
    passwd program = /usr/bin/passwd %u
    unix password sync = yes
    obey pam restrictions = yes
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    server role = standalone server
    server string = %h server (Samba, Ubuntu)
    max log size = 1000
    map to guest = bad user
    panic action = /usr/share/samba/panic-action %d
    dns proxy = no



[Customer]
    force create mode = 755
    browsable = yes
    public = yes
    path = /home/sftpuser/SFTP/Customer
    force directory mode = 755
    writeable = yes
    valid users = @ftpusers
    force group = ftpusers
    write list = @ftpusers
```

I have been struggling for 3 days and am totally out of ideas.

LS -L for the folder:
```
total 4
drwxrwx---+ 2 sftpuser ftpusers 4096 Apr  9 11:35 Customer



```

---

### Post by provoost2 on 2015-04-09
solved adding this so smb.conf:

[COLOR=#000000][FONT=Tahoma]ntlm auth = no[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]lanman auth = no[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]client ntlmv2 auth = yes[/FONT][/COLOR]

---

