---
title: "postfix randomize IPS and limit domain/hour"
date: 2015-06-01
forum: General Help
---

### Post by daemoncesar on 2015-06-01
Good day,


I'm using the transport_maps to randomizer IPS my e- mail server marketing.


I am following this howto ( is working ) .


```

http://www.kutukupret.com/2010/12/06/postfix-randomizing-outgoing-ip-using-tcp_table-and-perl/

```


Now I need to send more slowly for hotmail , gmail and yahoo.


I am following this:
```

http://steam.io/2013/04/01/postfix-rate-limiting/

```


The problem is I can not use two transport_maps , and as I am already randomizing it does not allow .


How do I limit the yahoo e-mail , gmail etc ... using the same transport_maps ?






That's right?


```

127.0.0.1:2527 inet  n       n       n       -       0      spawn
          user=nobody argv=/etc/postfix/random.pl


rotate1  unix -       -       n       -       -       smtp
           gmail.com rotate1:
           yahoo.com rotate1:
           hotmail.com rotate1:
          -o syslog_name=postfix-rotate1
          -o smtp_helo_name=xx-113.xx.org.br
          -o smtp_bind_address=186.xx.91.1x


rotate2  unix -       -       n       -       -       smtp
           gmail.com rotate2:
           yahoo.com rotate2:
           hotmail.com rotate2:          
          -o syslog_name=postfix-rotate2
          -o smtp_helo_name=xx-114.xx.org.br
          -o smtp_bind_address=186.xx.91.x

```

---

### Post by tgalati4 on 2015-06-01
How are you monitoring your email campaign?  Many CRM's such as SugarCRM have built-in rate-limiting, which you can use in conjunction with a postfix randomizer.

Regards to your original question, if the above doesn't work, then try running a second server (through a vm) and use a second postfix and use a two-step email process--one that randomizes and one that rate-limits.

---

### Post by daemoncesar on 2015-06-01
I did not understand. :(
I would use the parameters in /etc/ transports , but it is in use
I heard postfix-policyd makes this limitation. But there is no package for debian7 .

---

### Post by tgalati4 on 2015-06-01
Create two transport maps and rotate between them with a cronjob:


On the hour:
postmap /etc/postfix/transport1; service postfix restart

On the 1/2 hour:
postmap /etc/postfix/transport2; service postfix restart

---

### Post by daemoncesar on 2015-06-01
But in main.cf I can not put two transport .

It is as follows:
```

transport_maps = tcp:[127.0.0.1]:2527
127.0.0.1:2527_time_limit = 3600s

```

master.cf

```

rotate4  unix -       -       n       -       -       smtp
          -o syslog_name=postfix-rotate4
          -o smtp_helo_name=sxs-118.x.org.br
          -o smtp_bind_address=x6.2x91.1x8


rotate5  unix -       -       n       -       -       smtp
          -o syslog_name=postfix-rotate5
          -o smtp_helo_name=x-x.x.org.br
          -o smtp_bind_address=186.x.91.1x

....

to 30

```



How do I put another transport ?

to limit the sending domains per hour ?


Thank you for help








hour.

---

### Post by daemoncesar on 2015-06-01
how it works ?
```

main.cf

transport_maps = tcp:[127.0.0.1]:2527
127.0.0.1:2527_time_limit = 3600s



```
```

master.cf

127.0.0.1:2527 inet  n       n       n       -       0      spawn
        user=nobody argv=/etc/postfix/random.pl


rotate1  unix -       -       n       -       -       smtp
          -o syslog_name=postfix-rotate1
          -o smtp_helo_name=x-113.x.x.x
          -o smtp_bind_address=x.z.z.z.
          -o transport_maps=hash:/etc/postfix/transport

```

---

### Post by tgalati4 on 2015-06-01
Perhaps make a random1.pl and random2.pl and use a main1.cf and main2.cf.  Make a cronjob to spawn random1.pl on the hour and random2.pl on the 1/2 hour.

---

### Post by daemoncesar on 2015-06-01
My way I posted above will not the right?

Two main.cf ? There is this ?

---

### Post by daemoncesar on 2015-06-02
up

---

