---
title: "Samba Help - All setup but cannot access."
date: 2015-12-31
forum: General Help
---

### Post by max134 on 2015-12-31
Morning all,

Struggling with Samba a little and wondering if I could have some help please. I am fairly new to Linux so please be easy on me. I have set everything up and all the AD stuff seems setup and its connected to my AD can list all users and groups etc etc. When I try to access a share it just keeps asking for username and password Here is what is contained in samba.log:

```
media@TVSERVER:/var/log/samba$ tail -f samba.log
[2015/12/31 10:50:21.003577,  2] ../source3/smbd/server.c:437(remove_child_pid)
  Could not find child 1861 -- ignoring
[2015/12/31 10:51:21.049662,  2] ../source3/smbd/server.c:437(remove_child_pid)
  Could not find child 1864 -- ignoring
[2015/12/31 10:52:21.068647,  2] ../source3/smbd/server.c:437(remove_child_pid)
  Could not find child 1866 -- ignoring
[2015/12/31 10:53:21.095951,  2] ../source3/smbd/server.c:437(remove_child_pid)
  Could not find child 1867 -- ignoring
[2015/12/31 10:54:21.157882,  2] ../source3/smbd/server.c:437(remove_child_pid)
  Could not find child 1881 -- ignoring
[2015/12/31 10:55:21.219866,  2] ../source3/smbd/server.c:437(remove_child_pid)
  Could not find child 1883 -- ignoring
[2015/12/31 10:55:24.548859,  1] ../source3/param/loadparm.c:3178(lp_do_parameter)
  WARNING: The "idmap backend" option is deprecated
[2015/12/31 10:55:24.549016,  1] ../source3/param/loadparm.c:3178(lp_do_parameter)
  WARNING: The "idmap uid" option is deprecated
[2015/12/31 10:55:24.549101,  1] ../source3/param/loadparm.c:3178(lp_do_parameter)
  WARNING: The "idmap gid" option is deprecated
[2015/12/31 10:55:24.549349,  2] ../source3/param/loadparm.c:3581(do_section)
  Processing section "[TV Shows]"
[2015/12/31 10:55:24.549512,  2] ../source3/param/loadparm.c:3581(do_section)
  Processing section "[Movies]"
[2015/12/31 10:55:24.549658,  2] ../source3/param/loadparm.c:3581(do_section)
  Processing section "[Photos]"
[2015/12/31 10:55:24.549965,  2] ../source3/lib/interface.c:341(add_interface)
  added interface eth0 ip=192.168.1.10 bcast=192.168.1.255 netmask=255.255.255.0
[2015/12/31 10:55:24.779827,  1] ../source3/param/loadparm.c:3178(lp_do_parameter)
  WARNING: The "idmap backend" option is deprecated
[2015/12/31 10:55:24.779938,  1] ../source3/param/loadparm.c:3178(lp_do_parameter)
  WARNING: The "idmap uid" option is deprecated
[2015/12/31 10:55:24.780041,  1] ../source3/param/loadparm.c:3178(lp_do_parameter)
  WARNING: The "idmap gid" option is deprecated
[2015/12/31 10:55:24.780304,  2] ../source3/param/loadparm.c:3581(do_section)
  Processing section "[TV Shows]"
[2015/12/31 10:55:24.780447,  2] ../source3/param/loadparm.c:3581(do_section)
  Processing section "[Movies]"
[2015/12/31 10:55:24.780615,  2] ../source3/param/loadparm.c:3581(do_section)
  Processing section "[Photos]"
[2015/12/31 10:55:24.794157,  2] ../source3/smbd/service.c:418(create_connection_session_info)
  user 'MYDOMAIN\MYUSER' (from session setup) not permitted to access this share (Movies)
[2015/12/31 10:55:24.794230,  1] ../source3/smbd/service.c:550(make_connection_snum)
  create_connection_session_info failed: NT_STATUS_ACCESS_DENIED
[2015/12/31 10:55:24.800090,  2] ../source3/smbd/service.c:418(create_connection_session_info)
  user 'MYDOMAIN\MYUSER' (from session setup) not permitted to access this share (Movies)
[2015/12/31 10:55:24.800174,  1] ../source3/smbd/service.c:550(make_connection_snum)
  create_connection_session_info failed: NT_STATUS_ACCESS_DENIED
[2015/12/31 10:55:24.806124,  2] ../source3/smbd/service.c:418(create_connection_session_info)
  user 'MYDOMAIN\MYUSER' (from session setup) not permitted to access this share (Movies)
[2015/12/31 10:55:24.806173,  1] ../source3/smbd/service.c:550(make_connection_snum)
  create_connection_session_info failed: NT_STATUS_ACCESS_DENIED
[2015/12/31 10:55:24.809358,  2] ../source3/smbd/service.c:418(create_connection_session_info)
  user 'MYDOMAIN\MYUSER' (from session setup) not permitted to access this share (Movies)
[2015/12/31 10:55:24.809402,  1] ../source3/smbd/service.c:550(make_connection_snum)
  create_connection_session_info failed: NT_STATUS_ACCESS_DENIED
[2015/12/31 10:55:24.817287,  2] ../source3/smbd/service.c:418(create_connection_session_info)
  user 'MYDOMAIN\MYUSER' (from session setup) not permitted to access this share (Movies)
[2015/12/31 10:55:24.817332,  1] ../source3/smbd/service.c:550(make_connection_snum)
  create_connection_session_info failed: NT_STATUS_ACCESS_DENIED
[2015/12/31 10:55:24.821921,  2] ../source3/smbd/service.c:418(create_connection_session_info)
  user 'MYDOMAIN\MYUSER' (from session setup) not permitted to access this share (Movies)
[2015/12/31 10:55:24.821964,  1] ../source3/smbd/service.c:550(make_connection_snum)
  create_connection_session_info failed: NT_STATUS_ACCESS_DENIED
[2015/12/31 10:55:24.846209,  2] ../source3/smbd/service.c:418(create_connection_session_info)
  user 'MYDOMAIN\MYUSER' (from session setup) not permitted to access this share (Movies)
[2015/12/31 10:55:24.846264,  1] ../source3/smbd/service.c:550(make_connection_snum)
  create_connection_session_info failed: NT_STATUS_ACCESS_DENIED


```
Replaced my domain and username

Here is whats in mt smb.conf:

```
[global]
    # No .tld
    workgroup = MYDOMAIN
    # Active Directory System
    security = ads
    # With .tld
    realm = MYDOMAIN.CO.UK
    # Just a member server
    domain master = no
    local master = no
    preferred master = no
    # Disable printing error log messages when CUPS is not installed.
    printcap name = /etc/printcap
    load printers = no
    # Works both in samba 3.2 and 3.6.
    idmap backend = tdb
    idmap uid = 10000-999999
    idmap gid = 10000-999999
    # no .tld
    idmap config MYDOMAIN:backend = rid
    idmap config MYDOMAIN:range = 10000-99999
    winbind enum users = yes
    winbind enum groups = yes
    # This way users log in with username instead of username@example.org
    winbind use default domain = yes
    # Inherit groups in groups
    winbind nested groups = yes
    winbind refresh tickets = yes
    winbind offline logon = true
    # Becomes /home/example/username
    template homedir = /home/%D/%U
    # No shell access
    template shell = /bin/false
    client use spnego = yes
    client ntlmv2 auth = yes
    encrypt passwords = yes
    restrict anonymous = 2
    log file = /var/log/samba/samba.log
    log level = 2

[TV Shows]
    comment = TV Shows
    path = /media/Data/TV_SHOWS
    valid users = any
    writable = yes
    read only = no
    force create mode = 0660
    create mask = 0777
    directory mask = 0777
    force directory mode = 0770
    access based share enum = yes
    hide unreadable = yes
    browseable = yes


```


Please help! What else do you need to know?

---

### Post by Elishasmantle on 2016-01-01
Hello,

Is this the documentation you are using for your setup?
[https://wiki.samba.org/index.php/Setup_Samba_as_an_AD_Domain_Member](https://wiki.samba.org/index.php/Setup_Samba_as_an_AD_Domain_Member)
[https://wiki.samba.org/index.php/User_home_drives](https://wiki.samba.org/index.php/User_home_drives)

Just a thought... Looks pretty complicated and you might have accidentally missed a step or made a type-0 some where.

Thank You,

Elishasmantle

---

### Post by max134 on 2016-01-01
Thanks for the reply. I didn't use that guide used another but and it  was all working perfectly apart from not giving me access to the share.  As it turns out it was something to do with permissions on the  filesystem. I gave ownership to a new group I created and I added all  the users to that group I also applied permission 777 to the folders.  and now its working. Thats opening it up alot but then again in the  Samba configuration the share is limited to an AD group so pending  testing it should only allow domain users of that group in. I will have  to test locking it down slowly maybe at some point.

---

