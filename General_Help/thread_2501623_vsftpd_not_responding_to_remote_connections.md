---
title: "vsftpd not responding to remote connections"
date: 2024-10-15
forum: General Help
---

### Post by doublejz on 2024-10-15
I just spun up a new host and attempted to setup vsftpd. Config as follows

```
root@mail:~# cat /etc/vsftpd.conf
listen=YES
listen_ipv6=NO
anonymous_enable=NO
local_enable=YES
write_enable=YES
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
xferlog_file=/var/log/vsftpd.log
log_ftp_protocol=YES
chroot_local_user=YES
allow_writeable_chroot=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
ssl_enable=NO
pasv_enable=YES
pasv_min_port=30000
pasv_max_port=31000
user_sub_token=$USER
local_root=/home/$USER/ftp
userlist_file=/etc/vsftpd.user_list
userlist_deny=NO
root@mail:~#

```

```
root@mail:~# cat /etc/vsftpd.user_list
charlie
wild
double
root@mail:~#

```

Its up and running and listening

```
root@mail:~# netstat -anp | grep :21
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      17699/vsftpd
root@mail:~#

```

The firewall is allowing the Passive ports as well as 20/21.

```
root@mail:~# ufw status | egrep '(20/tcp|21/tcp|31000/tcp)'
30000:31000/tcp            ALLOW       Anywhere
20/tcp                     ALLOW       Anywhere
21/tcp                     ALLOW       Anywhere
root@mail:~#

```

However, when I try to connect to the server via 21, vsftpd never responds.

```
root@mail:~# tcpdump -nnn -i any port 21
tcpdump: data link type LINUX_SLL2
tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
listening on any, link-type LINUX_SLL2 (Linux cooked v2), snapshot length 262144 bytes
17:20:16.713491 eth0  In  IP 71.210.23.15.59507 > 102.46.52.23.21: Flags [S], seq 2260655885, win 64240, options [mss 1460,nop,wscale 8,nop,nop,sackOK], length 0
17:20:17.721050 eth0  In  IP 71.210.23.15.59507 > 102.46.52.23.21: Flags [S], seq 2260655885, win 64240, options [mss 1460,nop,wscale 8,nop,nop,sackOK], length 0
17:20:19.721252 eth0  In  IP 71.210.23.15.59507 > 102.46.52.23.21: Flags [S], seq 2260655885, win 64240, options [mss 1460,nop,wscale 8,nop,nop,sackOK], length 0
17:20:23.723941 eth0  In  IP 71.210.23.15.59507 > 102.46.52.23.21: Flags [S], seq 2260655885, win 64240, options [mss 1460,nop,wscale 8,nop,nop,sackOK], length 0

```

If I try to connect via localhost, it works. same with its own interface IP address.

```
root@mail:~# ftp localhost
Connected to mail
220 (vsFTPd 3.0.5)
Name (localhost:root):

```

```
root@mail:~# cat /var/log/vsftpd.log
Tue Oct 15 17:21:23 2024 [pid 17015] CONNECT: Client "::ffff:127.0.0.1"
Tue Oct 15 17:21:23 2024 [pid 17015] FTP response: Client "::ffff:127.0.0.1", "220 (vsFTPd 3.0.5)"
root@mail:~#


```

I even removed tcp_wrappers from the config but still this should have allowed it
```
root@mail:~# cat /etc/hosts.allow
vsftpd: ALL
root@mail:~# cat /etc/hosts.deny

```

I also disabled ufw as a whole and still no difference. I'm out of ideas here, any thoughts? TIA

---

