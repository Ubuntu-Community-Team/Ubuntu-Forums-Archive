---
title: "Cannot get vsftpd to work"
date: 2012-10-14
forum: General Help
---

### Post by TechGuyAlabama on 2012-10-14
I have installed vsftpd on my server. I am running Ubuntu 12.04 LTS. 

When I try to connect using FileZilla I am getting this message:

Status:    Connection attempt failed with "ECONNREFUSED - Connection refused by server".

I have set this in my `/etc/vsftpd.conf`:

    anonymous_enable=NO
    local_enable=YES
    write_enable=YES
    connect_from_port_20=YES

ftp allowed users list: `/etc/vsftpd.chroot_list` 

in this list I have:

    testuser

ftp disallowed users list: `/etc/ftpusers`

    root
    daemon
    bin
    sys
    sync
    games
    man
    lp
    mail
    news
    uucp
    nobody

in my `/etc/shells` I have:

    /bin/sh
    /bin/dash
    /bin/bash
    /bin/rbash
    /usr/bin/screen
    /bin/tcsh

I am able to login to this account via ssh.

What am I missing?!

---

