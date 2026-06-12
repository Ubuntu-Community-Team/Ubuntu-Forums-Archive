---
title: "Problem with pam_mound and ssh-copy-id"
date: 2016-01-21
forum: General Help
---

### Post by minus3 on 2016-01-21
Hi

i have several computers with Ubuntu 14.04LTS. All are on active directory domain with OPENPBIS (ex likewise)

I mount network drives with pam_mount and i haven't any problems when i'm connect with ssh on one of theses computers with the command: ssh user@nameofPC, i write my password and everything is ok.

All the network drives (On a synology NAS) are mount when the session is opening and unmount when i close the session.

The problem is when i use ssh-copy-id for connecting to the computer without need to write my password for opening my session.

In this case, the network drives don't mount.

On auth.log i have these messages

```

Jan 19 11:29:10 Node1 sshd[20613]: Accepted publickey for testuser from 192.168.25.65 port 58914 ssh2: RSA 7f:32:23:41:81:96:98:09:6t:1b:c6:a8:0d:ec:d3:4c
Jan 19 11:29:10 Node1 sshd[20613]: pam_unix(sshd:session): session opened for user testuser by (uid=0)
Jan 19 11:29:10 Node1 sshd[20613]: (pam_mount.c:173): conv->conv(...): Conversation error
Jan 19 11:29:10 Node1 sshd[20613]: (pam_mount.c:477): warning: could not obtain password interactively either
Jan 19 11:29:11 Node1 sshd[20613]: (mount.c:72): Messages from underlying mount program:
Jan 19 11:29:11 Node1 sshd[20613]: (mount.c:76): mount error(13): Permission denied
Jan 19 11:29:11 Node1 sshd[20613]: (mount.c:76): Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
Jan 19 11:29:11 Node1 sshd[20613]: (pam_mount.c:522): mount of data failed
etc ....

```

Please how can i solve this problem ?

This is my configurations files

pam_mount.conf.xml
```

<?xml version="1.0" encoding="utf-8" ?>
<!DOCTYPE pam_mount SYSTEM "pam_mount.conf.xml.dtd">
<!-- See pam_mount.conf(5) for a description. This should go in /etc/security/ -->
<pam_mount>
<debug enable="0" />

<!-- Volume definitions -->

<volume
    fstype="cifs"
    server="172.16.15.10"
    path="data"
    mountpoint="/home/%(USER)/Data"
    user="*" 
    options="nodev,nosuid,dir_mode=0700"
    />

<volume
    fstype="cifs"
    server="172.16.15.10"
    path="archives"
    mountpoint="/home/%(USER)/Data/Archives"
    user="*" 
    options="nodev,nosuid,dir_mode=0700"
    />

<volume
    fstype="cifs"
    server="172.16.15.20"
    path="homes"
    mountpoint="/home/%(USER)/PersonalData"
    user="*" 
    options="nodev,nosuid,dir_mode=0700"
    />

<!-- pam_mount parameters: General tunables -->

<!--<luserconf name=".pam_mount.conf.xml" />-->

<!-- Note that commenting out mntoptions will give you the defaults.
You will need to explicitly initialize it with the empty string
to reset the defaults to nothing. -->
<mntoptions allow="nosuid,nodev,loop,encryption,nonempty,allow_other,sec,dir_mode,file_mode" />
<mntoptions require="nosuid,nodev,dir_mode" />
<!--
<mntoptions deny="suid,dev" />
<mntoptions allow="*" />
<mntoptions deny="*" />
-->
<logout wait="0" hup="0" term="0" kill="0" />
<!-- pam_mount parameters: Volume-related -->
<mkmountpoint enable="1" remove="true" />
</pam_mount>

```

common-session
```

#
# /etc/pam.d/common-session - session-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define tasks to be performed
# at the start and end of sessions of *any* kind (both interactive and
# non-interactive).
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
session    [default=1]            pam_permit.so
# here's the fallback if no module succeeds
session    requisite            pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
session    required            pam_permit.so
# The pam_umask module will set the umask according to the system default in
# /etc/login.defs and user settings, solving the problem of different
# umask settings with different shells, display managers, remote sessions etc.
# See "man pam_umask".
session    optional    pam_umask.so
# and here are more per-package modules (the "Additional" block)
session    required    pam_unix.so 
session    [success=ok default=ignore]    pam_lsass.so 
session    optional    pam_mount.so 
session    optional    pam_systemd.so 
session    optional            pam_ck_connector.so nox11
# end of pam-auth-update config

```

I don't modify other files in the directory /etc/pam.d/

Thank you for your help, this is the first time i use pam_mount, and i know that I do not know all the options and how using it.

---

### Post by minus3 on 2016-01-22
Nobody has idea or can help me ?

---

### Post by minus3 on 2016-01-25
up :confused:

---

