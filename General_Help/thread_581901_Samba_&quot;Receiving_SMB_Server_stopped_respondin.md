---
title: "Samba &quot;Receiving SMB: Server stopped responding.  protocol negotiation failed&quot;"
date: 2007-10-19
forum: General Help
---

### Post by LNick on 2007-10-19
About a week ago I found that I could no longer access a Samba share from my Windows client.  I've tried to diagnose and repair this error myself, but am not having any luck.  Finally I decided I needed help from the experts.

I setup my Ubuntu box as a AD Domain member by following [Installing and Configuring Kerberos, Samba, and Winbind on Ubuntu Server 5]("http://ubuntuforums.org/showthread.php?t=91510").  This worked great!  Authentication of AD users continues to work flawlessly.

Next I decieded to add some standard Samba shares of my /var/www, /home/ftpsite, and home folders.  I did so successfuly, and had this working for a few weeks.

Here is my /etc/samba/smb.conf
```
[global]
        security = ads
        netbios name = INTRANET
        workgroup = MBDOM
        realm = MAGRATHEA.ORG
        wins server = mbmain
        idmap uid = 10000-20000
        idmap gid = 10000-20000
        winbind separator = \
        winbind enum users = yes
        winbind enum groups = yes
        winbind use default domain = yes
        template homedir = /home/%U
        template shell = /bin/bash
        client use spnego = yes
        domain master = no
        local master = no
        preferred master = no
        os level = 0
        log level = 10

[website]
        path = /var/www
        browseable = yes
        read only = no
        guest ok = no
        create mask = 0644
        directory mask = 0755
        force user = www-data
        force group = www-data

[ftpsite]
        path = /home/ftpsite
        browseable = yes
        read only = no
        guest ok = no
        create mask = 0644
        directory mask = 0755
        force user = ftpsite
        force group = ftpsite

[homes]
        comment = Home Directories
        browseable = no
        valid users = %U
        writable = yes
        create mode = 0600
        directory mode = 0755
        read only = no
        veto files = /*.{*}/.*/mail/bin/
```

I followed this fault tree in "Using Samba" from O'Reilly press [Chapter 9 Troubleshooting Samba]("http://www.oreilly.com/catalog/samba/chapter/book/ch09_02.html") and turned the log level up to 10.  I've looked at the Samba logs, but didn't see anything that seemed an error to me.  I can provide them if it will help.

The fault tree tests for IP/UDP, TCP, DNS all complete fine.  I already knew this was working as I run an intranet site off the box, but I ran the suggested tests anyway.

All the computers are on the same subnet.

"ps aux | grep mbd" shows the nmbd and smbd processes running
```
root@intranet:~# ps aux | grep mbd
root      4483  0.0  0.4  14360  2196 ?        S    11:08   0:00 /usr/sbin/smbd -D
root      4748  0.0  0.4  14356  2200 ?        S    11:34   0:00 /usr/sbin/smbd -D
root      4803  0.0  0.4  14356  2200 ?        S    13:12   0:00 /usr/sbin/smbd -D
root      4804  0.0  0.4  14356  2196 ?        S    13:13   0:00 /usr/sbin/smbd -D
root      4806  0.0  0.4  14356  2196 ?        S    13:14   0:00 /usr/sbin/smbd -D
root      4864  0.0  0.4  14356  2200 ?        S    15:28   0:00 /usr/sbin/smbd -D
root      4922  0.0  0.3   7472  1772 ?        Ss   16:01   0:00 /usr/sbin/nmbd -D
root      4947  0.0  0.1   2976   764 pts/0    S+   16:17   0:00 grep mbd
root@intranet:~#
```

"netstat -a" seems to show the daemons are bound to ports
```
root@intranet:~# netstat -a
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 intranet.mcgohanb:mysql *:*                     LISTEN
tcp        0      0 *:ftp                   *:*                     LISTEN
tcp        0      0 *:smtp                  *:*                     LISTEN
tcp        1      0 intranet.m:microsoft-ds 10.1.2.179:4715         CLOSE_WAIT
tcp        1      0 intranet.mcgohanb:45114 mbmain.mcgohanbrab:ldap CLOSE_WAIT
tcp        0      0 intranet.mcgohanb:45113 mbmain.mcgohanbrab:ldap ESTABLISHED
tcp        1      0 intranet.m:microsoft-ds 10.1.2.179:4720         CLOSE_WAIT
tcp        0      0 intranet.mcgohanb:33004 mbmain.mcg:microsoft-ds ESTABLISHED
tcp        0      0 intranet.mcgohanb:40676 mbmain.mcg:microsoft-ds ESTABLISHED
tcp        1      0 intranet.m:microsoft-ds intranet.mcgohanb:56199 CLOSE_WAIT
tcp6       0      0 *:www                   *:*                     LISTEN
tcp6       0      0 *:ssh                   *:*                     LISTEN
tcp6       0    264 intranet.mcgohanbra:ssh ::ffff:10.1.2.179%:3869 ESTABLISHED
udp        0      0 intranet.mcgohanb:32768 10.1.1.200:1514         ESTABLISHED
udp        0      0 intranet.mcg:netbios-ns *:*
udp        0      0 *:netbios-ns            *:*
udp        0      0 intranet.mc:netbios-dgm *:*
udp        0      0 *:netbios-dgm           *:*
udp        0      0 intranet.mcgohanbra:ntp *:*
udp        0      0 intranet.mcgohanbra:ntp *:*
udp        0      0 *:ntp                   *:*
udp6       0      0 fe80::20d:56ff:fe24:ntp *:*
udp6       0      0 ip6-localhost:ntp       *:*
udp6       0      0 *:ntp                   *:*
Active UNIX domain sockets (servers and established)
Proto RefCnt Flags       Type       State         I-Node Path
unix  2      [ ACC ]     STREAM     LISTENING     14220    public/cleanup
unix  2      [ ACC ]     STREAM     LISTENING     14227    private/tlsmgr
unix  2      [ ACC ]     STREAM     LISTENING     14236    private/rewrite
unix  2      [ ACC ]     STREAM     LISTENING     14240    private/bounce
unix  2      [ ACC ]     STREAM     LISTENING     14244    private/defer
unix  3      [ ]         DGRAM                    14078    /var/ossec/queue/alerts/execq
unix  5      [ ]         DGRAM                    14080    /queue/ossec/queue
unix  2      [ ]         DGRAM                    7953     @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     13887    /var/run/mysqld/mysqld.sock
unix  2      [ ACC ]     STREAM     LISTENING     14248    private/trace
unix  2      [ ACC ]     STREAM     LISTENING     14252    private/verify
unix  2      [ ACC ]     STREAM     LISTENING     14256    public/flush
unix  2      [ ACC ]     STREAM     LISTENING     14260    private/proxymap
unix  2      [ ACC ]     STREAM     LISTENING     14264    private/smtp
unix  2      [ ACC ]     STREAM     LISTENING     14268    private/relay
unix  2      [ ACC ]     STREAM     LISTENING     14272    public/showq
unix  2      [ ACC ]     STREAM     LISTENING     14276    private/error
unix  2      [ ACC ]     STREAM     LISTENING     14280    private/discard
unix  2      [ ]         DGRAM                    8215     @/org/kernel/udev/udevd
unix  2      [ ACC ]     STREAM     LISTENING     14494    /tmp/.winbindd/pipe
unix  2      [ ACC ]     STREAM     LISTENING     14284    private/local
unix  2      [ ACC ]     STREAM     LISTENING     14288    private/virtual
unix  2      [ ACC ]     STREAM     LISTENING     14292    private/lmtp
unix  2      [ ACC ]     STREAM     LISTENING     14296    private/anvil
unix  2      [ ACC ]     STREAM     LISTENING     14300    private/scache
unix  11     [ ]         DGRAM                    13701    /dev/log
unix  2      [ ACC ]     STREAM     LISTENING     14304    private/maildrop
unix  2      [ ACC ]     STREAM     LISTENING     14308    private/uucp
unix  2      [ ACC ]     STREAM     LISTENING     14312    private/ifmail
unix  2      [ ACC ]     STREAM     LISTENING     14496    /var/run/samba/winbindd_privileged/pipe
unix  2      [ ACC ]     STREAM     LISTENING     14316    private/bsmtp
unix  2      [ ACC ]     STREAM     LISTENING     14320    private/scalemail-backend
unix  2      [ ACC ]     STREAM     LISTENING     14324    private/mailman
unix  3      [ ]         STREAM     CONNECTED     165002   /var/run/samba/winbindd_privileged/pipe
unix  3      [ ]         STREAM     CONNECTED     165001
unix  2      [ ]         DGRAM                    164993
unix  3      [ ]         STREAM     CONNECTED     163974   /var/run/samba/winbindd_privileged/pipe
unix  3      [ ]         STREAM     CONNECTED     163973
unix  3      [ ]         STREAM     CONNECTED     160330   /var/run/samba/winbindd_privileged/pipe
unix  3      [ ]         STREAM     CONNECTED     160329
unix  3      [ ]         STREAM     CONNECTED     160033   /var/run/samba/winbindd_privileged/pipe
unix  3      [ ]         STREAM     CONNECTED     160032
unix  3      [ ]         STREAM     CONNECTED     15282    /var/run/samba/winbindd_privileged/pipe
unix  3      [ ]         STREAM     CONNECTED     15281
unix  3      [ ]         STREAM     CONNECTED     15278    /var/run/samba/winbindd_privileged/pipe
unix  3      [ ]         STREAM     CONNECTED     15277
unix  3      [ ]         STREAM     CONNECTED     15261    /var/run/samba/winbindd_privileged/pipe
unix  3      [ ]         STREAM     CONNECTED     15260
unix  3      [ ]         STREAM     CONNECTED     15211    /var/run/samba/winbindd_privileged/pipe
unix  3      [ ]         STREAM     CONNECTED     15210
unix  3      [ ]         STREAM     CONNECTED     15084    /tmp/.winbindd/pipe
unix  3      [ ]         STREAM     CONNECTED     15083
unix  2      [ ]         DGRAM                    15075
unix  3      [ ]         STREAM     CONNECTED     15073
unix  3      [ ]         STREAM     CONNECTED     15072
unix  3      [ ]         STREAM     CONNECTED     15071    /var/run/samba/winbindd_privileged/pipe
unix  3      [ ]         STREAM     CONNECTED     15070
unix  3      [ ]         STREAM     CONNECTED     15065
unix  3      [ ]         STREAM     CONNECTED     15064
unix  3      [ ]         STREAM     CONNECTED     15053    /var/run/samba/winbindd_privileged/pipe
unix  3      [ ]         STREAM     CONNECTED     15052
unix  3      [ ]         STREAM     CONNECTED     15019
unix  3      [ ]         STREAM     CONNECTED     15018
unix  3      [ ]         STREAM     CONNECTED     14973    /var/run/samba/winbindd_privileged/pipe
unix  3      [ ]         STREAM     CONNECTED     14971
unix  2      [ ]         STREAM     CONNECTED     14972    /var/run/samba/winbindd_privileged/pipe
unix  3      [ ]         STREAM     CONNECTED     14970    /var/run/samba/winbindd_privileged/pipe
unix  3      [ ]         STREAM     CONNECTED     14968
unix  2      [ ]         STREAM     CONNECTED     14966    /var/run/samba/winbindd_privileged/pipe
unix  3      [ ]         STREAM     CONNECTED     14963    /var/run/samba/winbindd_privileged/pipe
unix  3      [ ]         STREAM     CONNECTED     14962
unix  3      [ ]         STREAM     CONNECTED     14961
unix  3      [ ]         STREAM     CONNECTED     14960
unix  3      [ ]         STREAM     CONNECTED     14959    /var/run/samba/winbindd_privileged/pipe
unix  3      [ ]         STREAM     CONNECTED     14958
unix  2      [ ]         STREAM     CONNECTED     14955    /tmp/.winbindd/pipe
unix  2      [ ]         STREAM     CONNECTED     14954    /tmp/.winbindd/pipe
unix  2      [ ]         STREAM     CONNECTED     14953    /tmp/.winbindd/pipe
unix  2      [ ]         STREAM     CONNECTED     14952    /tmp/.winbindd/pipe
unix  2      [ ]         STREAM     CONNECTED     14951    /tmp/.winbindd/pipe
unix  2      [ ]         DGRAM                    14537
unix  3      [ ]         STREAM     CONNECTED     14499
unix  3      [ ]         STREAM     CONNECTED     14498
unix  2      [ ]         DGRAM                    14484
unix  2      [ ]         DGRAM                    14395
unix  2      [ ]         DGRAM                    14393
unix  2      [ ]         DGRAM                    14335
unix  3      [ ]         STREAM     CONNECTED     14327
unix  3      [ ]         STREAM     CONNECTED     14326
unix  3      [ ]         STREAM     CONNECTED     14323
unix  3      [ ]         STREAM     CONNECTED     14322
unix  3      [ ]         STREAM     CONNECTED     14319
unix  3      [ ]         STREAM     CONNECTED     14318
unix  3      [ ]         STREAM     CONNECTED     14315
unix  3      [ ]         STREAM     CONNECTED     14314
unix  3      [ ]         STREAM     CONNECTED     14311
unix  3      [ ]         STREAM     CONNECTED     14310
unix  3      [ ]         STREAM     CONNECTED     14307
unix  3      [ ]         STREAM     CONNECTED     14306
unix  3      [ ]         STREAM     CONNECTED     14303
unix  3      [ ]         STREAM     CONNECTED     14302
unix  3      [ ]         STREAM     CONNECTED     14299
unix  3      [ ]         STREAM     CONNECTED     14298
unix  3      [ ]         STREAM     CONNECTED     14295
unix  3      [ ]         STREAM     CONNECTED     14294
unix  3      [ ]         STREAM     CONNECTED     14291
unix  3      [ ]         STREAM     CONNECTED     14290
unix  3      [ ]         STREAM     CONNECTED     14287
unix  3      [ ]         STREAM     CONNECTED     14286
unix  3      [ ]         STREAM     CONNECTED     14283
unix  3      [ ]         STREAM     CONNECTED     14282
unix  3      [ ]         STREAM     CONNECTED     14279
unix  3      [ ]         STREAM     CONNECTED     14278
unix  3      [ ]         STREAM     CONNECTED     14275
unix  3      [ ]         STREAM     CONNECTED     14274
unix  3      [ ]         STREAM     CONNECTED     14271
unix  3      [ ]         STREAM     CONNECTED     14270
unix  3      [ ]         STREAM     CONNECTED     14267
unix  3      [ ]         STREAM     CONNECTED     14266
unix  3      [ ]         STREAM     CONNECTED     14263
unix  3      [ ]         STREAM     CONNECTED     14262
unix  3      [ ]         STREAM     CONNECTED     14259
unix  3      [ ]         STREAM     CONNECTED     14258
unix  3      [ ]         STREAM     CONNECTED     14255
unix  3      [ ]         STREAM     CONNECTED     14254
unix  3      [ ]         STREAM     CONNECTED     14251
unix  3      [ ]         STREAM     CONNECTED     14250
unix  3      [ ]         STREAM     CONNECTED     14247
unix  3      [ ]         STREAM     CONNECTED     14246
unix  3      [ ]         STREAM     CONNECTED     14243
unix  3      [ ]         STREAM     CONNECTED     14242
unix  3      [ ]         STREAM     CONNECTED     14239
unix  3      [ ]         STREAM     CONNECTED     14238
unix  3      [ ]         STREAM     CONNECTED     14235
unix  3      [ ]         STREAM     CONNECTED     14234
unix  3      [ ]         STREAM     CONNECTED     14226
unix  3      [ ]         STREAM     CONNECTED     14225
unix  3      [ ]         STREAM     CONNECTED     14223
unix  3      [ ]         STREAM     CONNECTED     14222
unix  3      [ ]         STREAM     CONNECTED     14219
unix  3      [ ]         STREAM     CONNECTED     14218
unix  3      [ ]         STREAM     CONNECTED     14216
unix  3      [ ]         STREAM     CONNECTED     14215
unix  2      [ ]         DGRAM                    14205
unix  2      [ ]         DGRAM                    14087
unix  2      [ ]         DGRAM                    14086
unix  2      [ ]         DGRAM                    14084
unix  2      [ ]         DGRAM                    13884
unix  2      [ ]         DGRAM                    13758
```

"echo hello | telnet localhost 139" connects and is closed by the server
```
root@intranet:~# echo "hello" | telnet localhost 139 
Trying
Trying 127.0.0.1 ... 
Connected to localhost. Escape character is '^]'. 
Connection closed by foreign host. 
root@intranet:~#
```

testparm has no errors except for the winbind separator character.  However I run the same samba config (except I don't share /home/ftpsite) on another server with no problems.
```
root@intranet:~# testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[website]"
Processing section "[ftpsite]"
Processing section "[homes]"
Loaded services file OK.
ERROR: the 'winbind separator' parameter must be a single character.
Server role: ROLE_DOMAIN_MEMBER
Press enter to see a dump of your service definitions

root@intranet:~#
```

testing with smbclient fails.  I feel that if I could determine what is happening here I would have the answer to what is wrong
```
root@intranet:~# smbclient -L \\localhost -k
Receiving SMB: Server stopped responding
protocol negotiation failed
```
I get the same error if I try to connect from another Ubuntu box on the network

Restarting the Samba daemon causes the daemon to cease responding at all until the server is rebooted.
```
root@intranet:~# /etc/init.d/samba restart
 * Stopping Samba daemons...         [ OK ]
 * Starting Samba daemons            [ OK ]
root@intranet:~# smbclient -L \\localhost -k
Error connecting to 127.0.0.1 (Connection refused)
Connection to localhost failed (Error NT_STATUS_CONNECTION_REFUSED)
root@intranet:~#
```

wbinfo tests work for checking trust secrets, users and groups

I also attempted to rejoin the machine to the domain, but it never completes.
```
root@intranet:~# net ads join -U Administrator@MAGRATHEA.ORG
Administrator@MAGRATHEA.ORG's password:
Using short domain name -- MBDOM
```

Googling for "samba error Receiving SMB: Server stopped responding protocol negotiation failed" has turned up a few others having similar problems, but no answers that I was able to find.

I may very well be missing something basic, so please don't hesitate to suggest simple errors.  I'm not in any way an expert in Linux.  Please help!

---

