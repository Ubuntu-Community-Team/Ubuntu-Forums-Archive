---
title: "Is this status showing someone can get into my system ?"
date: 2007-07-31
forum: General Help
---

### Post by scho on 2007-07-31
I don't know exactly about the addresses in  'Foreign address' field.
Does this mean my computer has open ports for somebody ?

I don't why there are hugh network traffic in several ports...

scho@pigmalion:~$ netstat -ta
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:2208          *:*                     LISTEN     
tcp        0      0 localhost:46032         *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 bruxxx.x.x:45218    mh-in-f104.google.c:www ESTABLISHED
tcp        0      0 bruxxx.x.x:34867    longman.com:www         ESTABLISHED
tcp        0      0 bruxxx.x.x:34866    longman.com:www         ESTABLISHED
tcp       16  88572 bruxxx.x.edu:36562    p54A62E51.dip0.t-i:3697 ESTABLISHED
tcp      144  62780 bruxxx.x.x:55212    c-76-102-14-81.hsd:1024 ESTABLISHED
tcp        0      0 bruxxx.x.x:39892    octopus.usc.edu:ssh     TIME_WAIT  
tcp        0  92145 bruxxx.x.x:36313    66-191-203-161.dh:62190 ESTABLISHED
tcp        0      0 bruxxx.x.x:52774    .:1200                  ESTABLISHED
tcp6       0      0 *:ssh                   *:*                     LISTEN     
[/PHP]

?????????:

---

### Post by jimbob on 2007-07-31
For your peace of mind (assuming you have a firewall set up) go to this URL and tell it to scan all ports.  If you see anything come back as not being "stealth" you can start to worry.
              [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

