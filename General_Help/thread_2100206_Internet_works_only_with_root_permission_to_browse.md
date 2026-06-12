---
title: "Internet works only with root permission to browser!"
date: 2013-01-01
forum: General Help
---

### Post by dishonest.jack on 2013-01-01
I am in the same case. 

I am using USB mobile broadband from Airtel. The installation went smooth, but internet connects only to programs run as root. 

ping google.com
 does not connect ( unknown host ) but 
sudo ping google.com 
 works perfectly! 

The problem is definitely not with the browser. Even when I try to run the Huawei application as normal user it does not run.

```

~ $ /usr/local/airtel/MobilePartner
usage: sudo [-D level] -h | -K | -k | -V
usage: sudo -v [-AknS] [-D level] [-g groupname|#gid] [-p prompt] [-u user
            name|#uid]
usage: sudo -l[l] [-AknS] [-D level] [-g groupname|#gid] [-p prompt] [-U user
            name] [-u user name|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-D level] [-g groupname|#gid] [-p prompt] [-u
            user name|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-D level] [-g groupname|#gid] [-p prompt] [-u
            user name|#uid] file ...
../../src/mobilepartner/MobilePartner.cpp: MobilePartnerMain: another instance of mp running
../../src/mobilepartner/MobilePartner.cpp: main: MobilePartnerMain exit/return

```

Is there anyway to rectify this as it is annoying to have to copy all my .mozilla files.

---

### Post by uRock on 2013-01-01
Moved to new thread.

---

### Post by eazar001 on 2013-01-01
Try chown username:username nameofdirectory, or maybe that's too drastic, just do chmod, so it's not completely accessible.

I'm assuming it's an ownership problem?

---

### Post by dishonest.jack on 2013-01-02
Changing ownership does not make sense because, even when internet works normally like say when connected via ethernet, "ping" was still owned by root! 

```

~ $ ping google.com
ping: unknown host google.com
~ $ sudo ping google.com
PING google.com (74.125.236.100) 56(84) bytes of data.
64 bytes from bom03s01-in-f4.1e100.net (74.125.236.100): icmp_req=1 ttl=54 time=68.6 ms
64 bytes from bom03s01-in-f4.1e100.net (74.125.236.100): icmp_req=2 ttl=54 time=57.5 ms
64 bytes from bom03s01-in-f4.1e100.net (74.125.236.100): icmp_req=3 ttl=54 time=56.0 ms
^C
--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 56.075/60.758/68.658/5.618 ms
 ~ $ 

```

---

### Post by eazar001 on 2013-01-02
> **dishonest.jack said:**
> Changing ownership does not make sense because, even when internet works normally like say when connected via ethernet, "ping" was still owned by root! 

```

~ $ ping google.com
ping: unknown host google.com
~ $ sudo ping google.com
PING google.com (74.125.236.100) 56(84) bytes of data.
64 bytes from bom03s01-in-f4.1e100.net (74.125.236.100): icmp_req=1 ttl=54 time=68.6 ms
64 bytes from bom03s01-in-f4.1e100.net (74.125.236.100): icmp_req=2 ttl=54 time=57.5 ms
64 bytes from bom03s01-in-f4.1e100.net (74.125.236.100): icmp_req=3 ttl=54 time=56.0 ms
^C
--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 56.075/60.758/68.658/5.618 ms
 ~ $ 

```

Well that makes sense, because if I go to the /bin directory where ping is located, the ownership is by default, root.

---

### Post by eazar001 on 2013-01-02
wait a second actually on second thought, do this in your terminal:

ls -l | grep "ping", and display your output please.

---

### Post by eazar001 on 2013-01-02
okay, do chmod 4751 /bin/ping.
After you do that, try to run ping without sudo, and tell me if you still have the same problem.

---

### Post by dishonest.jack on 2013-01-03
I do not think the problem is with ping or with permissions. I think it is with DNS. Somehow the DNS has been set for root and not for user. Internet connects to user if I specify the IP address of the server ! See below! Thanks.

```

 ~ $ ping google.com
ping: unknown host google.com

 ~ $ sudo ping google.com
PING google.com (74.125.236.105) 56(84) bytes of data.
--- google.com ping statistics ---
2 packets transmitted, 1 received, 50% packet loss, time 1001ms
rtt min/avg/max/mdev = 349.618/349.618/349.618/0.000 ms

 ~ $ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
--- 8.8.8.8 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 47.088/62.749/78.410/15.661 ms


```

---

### Post by steeldriver on 2013-01-03
I suspect it's an issue with group membership - in particular, iirc your user may need to be added to the 'dip' group in order to use ppp dialout networking

You can see what groups the user belongs to with the 'groups' command

```
$ groups
```If the user does not belong to 'dip' you can add them with

```
$ sudo gpasswd --add *username *dip
```then log out / back in

---

### Post by dishonest.jack on 2013-01-04
Thanks for the reply. But unfortunately for me, user already belongs to dip! Here is my output for groups. 

jack@mais ~ $ groups
jack adm cdrom sudo dip plugdev lpadmin sambashare

---

### Post by steeldriver on 2013-01-04
Hmm... so where next? What version are you running? there have been some quite big changes in the way name resolution works

How did you set up the connection on the Airtel device?

---

