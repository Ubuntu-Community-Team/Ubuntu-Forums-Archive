---
title: "Show open/in use ports"
date: 2019-02-24
forum: General Help
---

### Post by raleigh3 on 2019-02-24
I have been trying to figure out whyt Thunderbird can't get  my yahoo mail.

I am able to read email thru Firefox.

It uses these ports.   465,587,993, and 995.

Is there a way to tell if those ports are open or being used?

I have no firewall.

---

### Post by bitsnpcs on 2019-02-24
Hello raleigh3,

this tutorial has the command for what programs are using or listening to ports - [https://serverfault.com/questions/261372/how-do-i-tell-what-is-running-on-which-ports-in-ubuntu](https://serverfault.com/questions/261372/how-do-i-tell-what-is-running-on-which-ports-in-ubuntu)

Tutorial How to Set Up Thunderbird with Yahoo - [https://support.mozilla.org/en-US/kb/thunderbird-and-yahoo](https://support.mozilla.org/en-US/kb/thunderbird-and-yahoo)
"You should enable an option to **allow apps that use less secure sign-in** in your Yahoo Account"

---

### Post by raleigh3 on 2019-02-24
```
unix  3      [ ]         SEQPACKET  CONNECTED     619660   12002/firefox    

```
Which one is the port?

---

### Post by bitsnpcs on 2019-02-24
12002 is a timeout code.

UFW (firewall) is preinstalled so you have one, you need to enable it to use it -

```
sudo ufw enable
```

then do 

```
sudo ufw status verbose
``` 

this will show you the likely default rules, such as (Allow Outgoing).

---

### Post by raleigh3 on 2019-02-24
I have enabled the firewall.

sudo ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip

I still see no port numbers.

```
sudo netstat -lp 
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
tcp        0      0 0.0.0.0:sunrpc          0.0.0.0:*               LISTEN      901/rpcbind         
tcp        0      0 localhost:domain        0.0.0.0:*               LISTEN      902/systemd-resolve 
tcp        0      0 localhost:ipp           0.0.0.0:*               LISTEN      931/cupsd           
tcp6       0      0 [::]:sunrpc             [::]:*                  LISTEN      901/rpcbind         
tcp6       0      0 localhost:ipp           [::]:*                  LISTEN      931/cupsd           
udp        0      0 0.0.0.0:60696           0.0.0.0:*                           939/avahi-daemon: r 
udp        0      0 localhost:domain        0.0.0.0:*                           902/systemd-resolve 
udp        0      0 0.0.0.0:bootpc          0.0.0.0:*                           1168/dhclient       
udp        0      0 0.0.0.0:sunrpc          0.0.0.0:*                           901/rpcbind         
udp        0      0 0.0.0.0:ipp             0.0.0.0:*                           1000/cups-browsed   
udp        0      0 0.0.0.0:653             0.0.0.0:*                           901/rpcbind         
udp        0      0 0.0.0.0:mdns            0.0.0.0:*                           939/avahi-daemon: r 
udp6       0      0 [::]:44139              [::]:*                              939/avahi-daemon: r 
udp6       0      0 [::]:sunrpc             [::]:*                              901/rpcbind         
udp6       0      0 [::]:653                [::]:*                              901/rpcbind         
udp6       0      0 [::]:mdns               [::]:*                              939/avahi-daemon: r 
raw6       0      0 [::]:ipv6-icmp          [::]:*                  7           942/NetworkManager
```

---

### Post by bitsnpcs on 2019-02-24
This looks quite detailed with examples - [https://hostpresto.com/community/tutorials/netstat-command-line-tips-and-tricks/](https://hostpresto.com/community/tutorials/netstat-command-line-tips-and-tricks/)

On the link the 

```
netstat -c
``` 

checks continuously, this looks like it may be good for send or check the email, and see if it reveals anything useful to check further.

Have you checked if your Yahoo settings need changing, how is discussed on the Mozilla link earlier in the thread ?
To rule this out as the cause.

---

### Post by raleigh3 on 2019-02-25
I tried TB on a pendrive and even there it would not work.

I have resigned myself to it being unsolvable.

I can read email thru Firefox.

---

### Post by slickymaster on 2019-02-25
You can check the open ports in your system running the following in a terminal window ```
ss -lntu
```

---

### Post by raleigh3 on 2019-02-25
I do not see a correlation between this and the ports that Thunderbird uses. such as 993, 587 etc.

```
Netid  State    Recv-Q   Send-Q      Local Address:Port      Peer Address:Port  
udp    UNCONN   0        0                 0.0.0.0:57334          0.0.0.0:*     
udp    UNCONN   0        0           127.0.0.53%lo:53             0.0.0.0:*     
udp    UNCONN   0        0                 0.0.0.0:68             0.0.0.0:*     
udp    UNCONN   0        0                 0.0.0.0:111            0.0.0.0:*     
udp    UNCONN   0        0                 0.0.0.0:631            0.0.0.0:*     
udp    UNCONN   0        0                 0.0.0.0:633            0.0.0.0:*     
udp    UNCONN   0        0                 0.0.0.0:5353           0.0.0.0:*     
udp    UNCONN   0        0                    [::]:111               [::]:*     
udp    UNCONN   0        0                    [::]:633               [::]:*     
udp    UNCONN   0        0                    [::]:5353              [::]:*     
udp    UNCONN   0        0                    [::]:46621             [::]:*     
tcp    LISTEN   0        128               0.0.0.0:111            0.0.0.0:*     
tcp    LISTEN   0        128         127.0.0.53%lo:53             0.0.0.0:*     
tcp    LISTEN   0        5               127.0.0.1:631            0.0.0.0:*     
tcp    LISTEN   0        128                  [::]:111               [::]:*     
tcp    LISTEN   0        5                   [::1]:631               [::]:*
```

---

### Post by deadflowr on 2019-02-25
look at all instead of just listening, 
with something like
```
ss -antu
```
Thunderbird is a client side program, so it doesn't "listen" for incoming connections. It makes outgoing connections.

---

