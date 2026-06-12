---
title: "Problems with transmission-daemon and permission on headless install"
date: 2012-12-14
forum: General Help
---

### Post by MadsRC on 2012-12-14
I've got a headless install of 12.04 in my house, and I've encountered some problems with the transmission-daemon package.

I can only get it to download to locations, other than the default /var/lib/blablabla, if I run transmission-daemon as root (Which is bad...)

Here's a cutout from my syslog:
```
Dec 14 13:12:04 serv01 transmission-daemon[23238]: Couldn't create "/mnt/storage/transmission-daemon/downloads": Permission denied (fdlimi
t.c:360)
Dec 14 13:12:04 serv01 transmission-daemon[23238]: ubuntu-12.04.1-desktop-i386.iso tr_fdFileCheckout failed for "/mnt/storage/transmission
-daemon/downloads/ubuntu-12.04.1-desktop-i386.iso.part": Permission denied (inout.c:100)
Dec 14 13:12:04 serv01 transmission-daemon[23238]: ubuntu-12.04.1-desktop-i386.iso Permission denied (/mnt/storage/transmission-daemon/dow
nloads/ubuntu-12.04.1-desktop-i386.iso) (torrent.c:487)
Dec 14 13:12:04 serv01 transmission-daemon[23238]: ubuntu-12.04.1-desktop-i386.iso Pausing (torrent.c:1763)
Dec 14 13:12:04 serv01 transmission-daemon[23238]: Couldn't create "/mnt/storage/transmission-daemon": Permission denied (utils.c:569)
Dec 14 13:12:04 serv01 transmission-daemon[23238]: Couldn't create "/mnt/storage/transmission-daemon/downloads": Permission denied (fdlimi
t.c:360)
Dec 14 13:12:04 serv01 transmission-daemon[23238]: ubuntu-12.04.1-desktop-i386.iso tr_fdFileCheckout failed for "/mnt/storage/transmission
-daemon/downloads/ubuntu-12.04.1-desktop-i386.iso.part": Permission denied (inout.c:100)

```

And here is the EXACT steps I used to install & configure transmission-daemon:
```
apt-get install transmission-daemon

service transmission-daemon stop

vi /etc/transmision-daemon/settings.json
     Change "downloads dir" to /mnt/storage/transmission-daemon/downloads from /var7liv/transmission-daemon/downloads
     Also changed the password
     Changed "rpc-whitelist-enabled" to false

cp -p /var/lib/transmission-daemon /mnt/storage/
     Got an error: omitting directory `/var/lib/transmission-daemon' - I forgot to use -r

cp -R -p /var/lib/transmission-daemon /mnt/storage/

ls -l /var/lib/transmission-daemon/
total 8
drwsrwxr-x 2 debian-transmission debian-transmission 4096 Sep 24 21:23 downloads
drwsr-x--- 5 debian-transmission debian-transmission 4096 Dec 14 13:46 info

ls -l /mnt/storage/transmission-daemon/
total 0
drwsrwxr-x 2 debian-transmission debian-transmission  48 Sep 24 21:23 downloads
drwsr-x--- 5 debian-transmission debian-transmission 160 Dec 14 13:46 info

ls -l /etc/transmission-daemon/
total 8
-rw-r--r-- 1 root                root                 303 Feb 15  2012 README.json
-rw------- 1 debian-transmission debian-transmission 2295 Dec 14 13:49 settings.json

service transmission-daemon start
```

Then I added the ubuntu iso, ran tail -f /var/log/syslog and this got this message in the webinterface:
Error: Permission denied (/mnt/storage/transmission-daemon/downloads/ubuntu-12.04.1-desktop-i386.iso)

This is the content of my syslog from when I logged into the webinterface:
```
Dec 14 14:00:16 serv01 transmission-daemon[24786]: DHT Attempting bootstrap from dht.transmissionbt.com (tr-dht.c:247)
Dec 14 14:00:18 serv01 transmission-daemon[24786]: Searching for web interface file "/home/debian-transmission/.local/share/transmission/web/index.html" (platform.c:540)
Dec 14 14:00:18 serv01 transmission-daemon[24786]: Searching for web interface file "/usr/share/transmission/web/index.html" (platform.c:540)
Dec 14 14:00:34 serv01 transmission-daemon[24786]: Saved "/var/lib/transmission-daemon/info/torrents/ubuntu-12.04.1-desktop-i386.iso.14ffe5dd23188fd5.torrent" (bencode.c:1731)
Dec 14 14:00:34 serv01 transmission-daemon[24786]: ubuntu-12.04.1-desktop-i386.iso Pausing (torrent.c:1763)
Dec 14 14:00:34 serv01 transmission-daemon[24786]: Saved "/var/lib/transmission-daemon/info/resume/ubuntu-12.04.1-desktop-i386.iso.14ffe5dd23188fd5.resume" (bencode.c:1731)
Dec 14 14:00:34 serv01 transmission-daemon[24786]: ubuntu-12.04.1-desktop-i386.iso Queued for verification (verify.c:260)
Dec 14 14:00:34 serv01 transmission-daemon[24786]: ubuntu-12.04.1-desktop-i386.iso Verifying torrent (verify.c:218)
Dec 14 14:00:34 serv01 transmission-daemon[24786]: ubuntu-12.04.1-desktop-i386.iso Could not connect to tracker (announcer.c:990)
Dec 14 14:00:34 serv01 transmission-daemon[24786]: ubuntu-12.04.1-desktop-i386.iso Retrying announce in 339 seconds. (announcer.c:999)
Dec 14 14:00:43 serv01 transmission-daemon[24786]: ubuntu-12.04.1-desktop-i386.iso Starting IPv4 DHT announce (poor, 20 nodes) (tr-dht.c:574)
Dec 14 14:00:51 serv01 transmission-daemon[24786]: Couldn't create "/mnt/storage/transmission-daemon": Permission denied (utils.c:569)
Dec 14 14:00:51 serv01 transmission-daemon[24786]: Couldn't create "/mnt/storage/transmission-daemon/downloads": Permission denied (fdlimit.c:360)
Dec 14 14:00:51 serv01 transmission-daemon[24786]: ubuntu-12.04.1-desktop-i386.iso tr_fdFileCheckout failed for "/mnt/storage/transmission-daemon/downloads/ubuntu-12.04.1-desktop-i386.iso.part": Permission denied (inout.c:100)
Dec 14 14:00:51 serv01 transmission-daemon[24786]: ubuntu-12.04.1-desktop-i386.iso Permission denied (/mnt/storage/transmission-daemon/downloads/ubuntu-12.04.1-desktop-i386.iso) (torrent.c:487)
Dec 14 14:00:51 serv01 transmission-daemon[24786]: Couldn't create "/mnt/storage/transmission-daemon": Permission denied (utils.c:569)
Dec 14 14:00:51 serv01 transmission-daemon[24786]: Couldn't create "/mnt/storage/transmission-daemon/downloads": Permission denied (fdlimit.c:360)
Dec 14 14:00:51 serv01 transmission-daemon[24786]: ubuntu-12.04.1-desktop-i386.iso tr_fdFileCheckout failed for "/mnt/storage/transmission-daemon/downloads/ubuntu-12.04.1-desktop-i386.iso.part": Permission denied (inout.c:100)
Dec 14 14:00:51 serv01 transmission-daemon[24786]: ubuntu-12.04.1-desktop-i386.iso Pausing (torrent.c:1763)
Dec 14 14:00:51 serv01 transmission-daemon[24786]: Couldn't create "/mnt/storage/transmission-daemon": Permission denied (utils.c:569)
Dec 14 14:00:51 serv01 transmission-daemon[24786]: Couldn't create "/mnt/storage/transmission-daemon/downloads": Permission denied (fdlimit.c:360)
Dec 14 14:00:51 serv01 transmission-daemon[24786]: ubuntu-12.04.1-desktop-i386.iso tr_fdFileCheckout failed for "/mnt/storage/transmission-daemon/downloads/ubuntu-12.04.1-desktop-i386.iso.part": Permission denied (inout.c:100)
Dec 14 14:00:51 serv01 transmission-daemon[24786]: Saved "/var/lib/transmission-daemon/info/resume/ubuntu-12.04.1-desktop-i386.iso.14ffe5dd23188fd5.resume" (bencode.c:1731)
Dec 14 14:00:53 serv01 transmission-daemon[24786]: ubuntu-12.04.1-desktop-i386.iso Could not connect to tracker (announcer.c:990)
Dec 14 14:00:53 serv01 transmission-daemon[24786]: ubuntu-12.04.1-desktop-i386.iso Retrying announce in 914 seconds. (announcer.c:999)
```

The file the interface is yawning about doesn't even exist:
```
ls -l -a /mnt/storage/transmission-daemon/downloads/
total 0
drwsrwxr-x 2 debian-transmission debian-transmission  48 Sep 24 21:23 .
drwxr-xr-x 4 root                root                104 Dec 14 13:46 ..

```

I know it's along post, But I wanted to be sure there was enough info to troubleshoot.

If I change /etc/init.d/transmission-daemon from USER=transmission-daemon to USER=root and restart transmission-daemon, it works fine... And I ALSO works fine if I tell it to download to /var/lib/transmission-daemon/downloads, which I don't understand as I did cp -p to perserve the permissions :S

---

