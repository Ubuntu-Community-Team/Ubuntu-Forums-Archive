---
title: "Trouble syncing large files to box.com on Ubuntu 13.10 using WebDav and davfs2"
date: 2014-02-14
forum: General Help
---

### Post by Dr3x1 on 2014-02-14
[COLOR=#333333][FONT=Helvetica]On my VPS I'm running Ubuntu 13.10 and I've mounted box.com as a WebDav drive using davfs2. I appear to have configured it properly because all of my existing content has been synced to my VPS and I can upload small files just fine. For example, from my box directory I can "touch test" and it uploads "test" to box.com no problem. I can then edit the file in VIM and the changes propagate to the cloud. However when I attempt to upload large zip files they end up in lost+found and not uploaded to box at all.

```
Contents of /etc/fstab
---
proc  /proc       proc    defaults    0    0
none  /dev/pts    devpts  rw,gid=5,mode=620    0    0
none  /run/shm    tmpfs   defaults    0    0
https://dav.box.com/dav    /root/box    davfs    _netdev,rw,user,noexec 0 0

```
[/FONT][/COLOR]
```
Contents of /etc/davfs2/davfs2.conf
---
# davfs2 configuration file 2009-04-12
# version 9
# ------------------------------------


# Copyright (C) 2006, 2007, 2008, 2009 Werner Baumann


# Copying and distribution of this file, with or without modification, are
# permitted in any medium without royalty provided the copyright notice
# and this notice are preserved.




# Please read the davfs2.conf (5) man page for a description of the
# configuration options and syntax rules.




# Available options and default values
# ====================================


# General Options
# ---------------


# dav_user        davfs2            # system wide config file only
# dav_group       davfs2            # system wide config file only
ignore_home       kernoops,distccd  # system wide config file only
# kernel_fs       fuse
# buf_size        16                 # KiByte


# WebDAV Related Options
# ----------------------


# use_proxy       1                 # system wide config file only
# proxy                             # system wide config file only
# servercert
# clientcert
# secrets         ~/.davfs2/secrets # user config file only
# ask_auth        1
use_locks       0
# lock_owner      <user-name>
# lock_timeout    1800              # seconds
# lock_refresh    60                # seconds
# use_expect100   0
# if_match_bug    0
# drop_weak_etags 0
# allow_cookie    0
# precheck        1
# ignore_dav_header 0
# server_charset
# connect_timeout 10                # seconds
# read_timeout    30                # seconds
# retry           30                # seconds
# max_retry       300               # seconds
# add_header


# Cache Related Options
# ---------------------


# backup_dir      lost+found
# cache_dir       /var/cache/davfs2 # system wide cache
#                 ~/.davfs2/cache   # per user cache
# cache_size      50                # MiByte
# table_size      1024
# dir_refresh     60                # seconds
# file_refresh    1                 # second
# delay_upload    10
# gui_optimize    0
# Debugging Options
# -----------------


# debug           # possible values: config, kernel, cache, http, xml,
                  #      httpauth, locks, ssl, httpbody, secrets, most

```[COLOR=#333333][FONT=Helvetica]
[/FONT][/COLOR]

---

### Post by Dr3x1 on 2014-02-16
I don't know what the rules for bumping are, but it has been over 24hrs. I have been unable to resolve this problem so far. Any guidance is very much appreciated.

---

### Post by andrew102 on 2014-04-02
I'd like to know the answer:

IS THERE A FILE SIZE LIMIT?

A week or two ago I uploaded  some 200MB sized files from a WIndows PC. Since then my Box drive will mount, however, 80% of the time when I try to browse the files, the /home/ folder hangs ("loading...")
The trouble is it ends up causing the whole UI to hang and I have to reset PC.

I have tried two different PC's, one running 32-bit Ubuntu 12.04LTS, and another running 64-bit 13.10.


I'm thinking of switching to another service with native Linux software.

---

### Post by Sven_Sorrell on 2014-04-07
The free version of Box has a 250MB file size limit.
Also, for me, the Davfs2 interface is excruciatingly slow. I used to use Box back on Windows, but now I have mostly switched to Copy.com; they start you off with 15GB, or 20GB if you use a referral, and they have a fully-integrated Linux client.
If you fancy trying it out, use my link and you get the bonus 5GB (as do I): [https://copy.com?r=CdoQai](https://copy.com?r=CdoQai)

---

### Post by kicelo on 2014-04-19
Copy looks good on the outside, but has issues syncing on the fly. YMMV
Also their forum is not moderated or read. It is starting to become cluttered with complaints and spam. This is an early warning sign to me.  I wish Box's webdav wasn't unbearably slow or they cared about Linux.

---

