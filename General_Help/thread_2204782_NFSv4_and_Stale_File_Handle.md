---
title: "NFSv4 and Stale File Handle"
date: 2014-02-10
forum: General Help
---

### Post by philchambers on 2014-02-10
[SIZE=3][FONT=arial]I have Ubuntu 12.04 (64 bit desktop) installed on my desktop and my laptop.  I want my laptop to mount a couple of my desktop's directories using NFSv4.  I used the information in [https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto) to try to set it up.  However, I am getting a '[FONT=courier new]Stale NFS file handle[/FONT]' error.
[/FONT][/SIZE]
[SIZE=3][FONT=arial]
[/FONT][/SIZE]
[SIZE=3][FONT=arial]On the desktop I installed nfs-common and nfs-kernel-server (not the i386 versions) and on the laptop I installed nfs-common.  In both cases I used the Software Centre, not apt-get.[/FONT][/SIZE]

[SIZE=3][FONT=arial]
[/FONT][/SIZE]
[SIZE=3][FONT=arial]My UID (myuser:1000) and GID (myuser:1000) are the same on both computers.[/FONT][/SIZE]
[SIZE=3][FONT=arial]
[/FONT][/SIZE]
[SIZE=3][FONT=arial]I have IP addresses for 'my-laptop' and 'my-desktop' in /etc/hosts[/FONT][/SIZE]
[SIZE=3][FONT=arial]
[/FONT][/SIZE]
[SIZE=3][FONT=arial]On my desktop (as root):[/FONT][/SIZE]
[SIZE=3][FONT=arial]
[/FONT][/SIZE]
[SIZE=3][FONT=arial]I created /export and /export/myuser[/FONT][/SIZE]
[SIZE=3][FONT=arial]
[/FONT][/SIZE]
[SIZE=3][FONT=arial]I set [FONT=courier new]NEED_SVCGSSD=no in /etc/default/nfs-kernel-server[/FONT][/FONT][/SIZE]

[SIZE=3][FONT=arial]
[/FONT][/SIZE]
[SIZE=3][FONT=arial]In /etc/exports I put:[/FONT][/SIZE]
[FONT=courier new][SIZE=3] /export my-laptop(rw,sync,fsid=0,no_subtree_check)[/SIZE]
[/FONT]
[FONT=courier new][SIZE=3] /export/myuser my-laptop(rw,sync,fsid=0,no_subtree_check)[/SIZE][/FONT]
[SIZE=3][FONT=arial]
[/FONT][/SIZE]
[SIZE=3][FONT=arial]Note that I did not do any '--bind'  mounts on the desktop at this stage.[/FONT][/SIZE]
[SIZE=3][FONT=arial]
[/FONT][/SIZE]
[SIZE=3][FONT=arial]I then re-booted the desktop and exportfs shows /export and /export/myuser  exported to my-laptop.[/FONT][/SIZE]
[SIZE=3][FONT=arial]
[/FONT][/SIZE]
[SIZE=3][FONT=arial]On my-laptop (as root) I created /mnt/myuser and used:
[/FONT][/SIZE]
[FONT=courier new][SIZE=3]mount -t nfs4 -o proto=tcp,port=2049 my-desktop:/myuser /mnt/myuser[/SIZE][/FONT][SIZE=3][FONT=arial] Back as myuser I could see the mounted filespace at /mnt/myuser and had full access.  If I put files into /exports/myuser on the desktop they can be seen on the laptop and vice-versa.[/FONT][/SIZE]
[SIZE=3][FONT=arial]
[/FONT][/SIZE]
[SIZE=3][FONT=arial]One small problem on the laptop though.  If I 'umount /mnt/myuser' it fails with '/mnt/myuser was not found in /proc/mounts', so I need to reboot.[/FONT][/SIZE]
[SIZE=3][FONT=arial]
[/FONT][/SIZE]
[SIZE=3][FONT=arial]However, I need to export /home/myuser on the desktop.   So, I shut down the laptop and on the desktop I added:[/FONT][/SIZE]
[SIZE=3][FONT=arial][FONT=courier new][SIZE=3]/home/myuser    /export/myuser   none    bind  0  0[/SIZE][/FONT]

[SIZE=3]to /etc/fstab and rebooted.  I could then see the /home/myuser files in /export/myuser

When I start the laptop and re-do the mount command I can see the mount using '[FONT=courier new]df[/FONT]' and, as myuser, do '[FONT=courier new]cd /mnt/myuser[/FONT]' but when I do a '[FONT=courier new]ls[/FONT]' command I get:

[FONT=courier new]ls: cannot open directory .: Stale NFS file handle[/FONT]

Any suggestions will be appreciated.[/SIZE][/FONT][/SIZE][SIZE=3][FONT=arial] 
[/FONT][/SIZE]

---

