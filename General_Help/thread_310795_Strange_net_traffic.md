---
title: "Strange net traffic"
date: 2006-12-01
forum: General Help
---

### Post by argusBR on 2006-12-01
I have an Ubuntu machine sharing the internet connection with a Windows box. Today I noticed a very high Internet traffic (both inbound and outbound), that persisted after turning off the Windows machine.

I have reinstalled Firestarter, and that reduced my outbound traffic from 10 kB/s to zero when I am not accessing the "outside world". As to the inbound traffic, although it has been greatly reduced (from 80 kB/s to 6 kB/s in idle condition), it won't get any lower than 5 kB/s. Is this normal? Or an "alien proccess" must be running, and I have been hacked or something? :confused: 

I don't know how to determine which proccess is using my bandwidth. Typing "netstat -a" gives me lots of output, but I have no idea of how to interpret it.

---

### Post by koenn on 2006-12-02
using netstat was a good idea to get a first impression of the connections your computerhas with other computers.
to limit the output, do
```
netstat -atu
``` or 
```
netstat -natu
```
this shows tcp connections and udp.

In the output , you'll get a list like this :
```

Proto Recv-Q Send-Q Local Address           Foreign Address    State
tcp        0      0 192.168.1.245:41295     66.102.9.99:www    ESTABLISHED


```
This line shows my computer's connection to a web server (www). 
Local address is your computer + the port it uses for that connection, Foreign address is the name or ip address of the computer your connected to + the port number or the service name on that computer. 

STATE is the state of the connection. 'Established' means there is a connection that can be actively used, LISTENING means your computer is waiting for a connection on that specific port, other values (FIN, ACK, CLOSED, WAIT ...) are usually steps in the creation or shutdown of a connection

This should help you determine if you have any (established) connections you did not expect - i.e. connections with computers/ip addresses you don't want to be talking to

-----
note to forum moderators : shouldn't this be in a networking forum ?
-----

---

### Post by argusBR on 2006-12-02
I get the following output for *netstat -natu*:

```
Proto Recv-Q Send-Q Local Address           Foreign Address    State      
tcp        0      0 0.0.0.0:2628            0.0.0.0:*               LISTEN   
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN 
tcp        0      0 0.0.0.0:8110            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:3310            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:8080            0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:8118          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:3128          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     
udp        0      0 0.0.0.0:32768           0.0.0.0:*                          
udp        0      0 192.168.0.1:137         0.0.0.0:*                          
udp        0      0 201.37.147.92:137       0.0.0.0:*                          
udp        0      0 0.0.0.0:137             0.0.0.0:*                          
udp        0    548 192.168.0.1:138         0.0.0.0:*                          
udp        0      0 201.37.147.92:138       0.0.0.0:*                          
udp        0      0 0.0.0.0:138             0.0.0.0:*                          
udp        0      0 0.0.0.0:3130            0.0.0.0:*                          
udp        0      0 0.0.0.0:68              0.0.0.0:*                          
udp        0      0 201.37.147.92:123       0.0.0.0:*                          
udp        0      0 192.168.0.1:123         0.0.0.0:*                          
udp        0      0 127.0.0.1:123           0.0.0.0:*                          
udp        0      0 0.0.0.0:123             0.0.0.0:*                          
udp6       0      0 :::123                  :::*  
```

The inbound traffic, however, is always 3-5 kB/s. Is there anything strange in the list above?
I have run chkrootkit and it didn't detect any problem.

---

### Post by koenn on 2006-12-07
It does not show established connections, so that's quite ok. 
You have some 9 services listening (i.e. waiting in case someone wants to connect) and you should ask yourself why the are there. 
You can look up most nimbers in /etc/services, e.g. 138 and 139 is "Windows" networking (do you have SAMBA ?), 8080 is usually a web proxy ... but it's up to uou to know if these are there because you want them to be, or not. 

Some port numbers I don't recognise or find in /ets/services - you might try to find them on the web (Google).

udp is a bit more difficult to judge because it's 'connectionless' but again the port numbers may give you a clue 

eg. 123 is communication with a time server, so if you've checked 'get time and date from internet servers' or if you are running your own time server, it's normal to have udp port 123 traffic. 

That way, you can try to figura out what network traffic is going on, and wheteher its 'strange' or not.

---

