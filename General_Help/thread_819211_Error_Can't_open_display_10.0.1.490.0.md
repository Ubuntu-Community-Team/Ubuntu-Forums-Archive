---
title: "Error: Can't open display: 10.0.1.49:0.0"
date: 2008-06-05
forum: General Help
---

### Post by ostorezio on 2008-06-05
Guys ... I'm not a newbie, been playing this X stuff since almost 20 years, but this is really driving me nuts and I know it must be trivial, but can't find a way out.

I'm running Ubuntu Gutsy and cannot (since a few days) use my display as an X server for remote clients.

When I first installed Ubuntu I had problems with remote X sessions and found out that the good old way:

local: xhost + 

remote: export DISPLAY=x.x.x.x:0.0
remote: xclock &

Did not work any more on Ubuntu, I believe for some security issues with port 6000, correct?

Then, after a good deal of googling, investigations, serendipity and word of mouth, I found that the trick was X through ssh:

local: xhost +
local: ssh -X remotehost

remote: export DISPLAY=10.0.1.49:0.0
remote: xclock &

BUUUUTTTTTT .... since last week this works no longer on my laptop !!!!!

No firewalls in between, I had "iptables -F" just to make sure there hare no impediments, but nothing, the remote systems says:

ezio@nagiossrv:~$ export DISPLAY=10.0.1.49:0.0
ezio@nagiossrv:~$ xclock 
Error: Can't open display: 10.0.1.49:0.0

No diagnostic in both systems syslog, no hint, no clue .... 

Any idea?

Thanks,

                 Ezio

---

### Post by ostorezio on 2008-06-09
BINGO !!!!

[http://www.ubuntu-forum.net/showthread.php?p=3348736](http://www.ubuntu-forum.net/showthread.php?p=3348736)

See the reply from "psychicist":

>Usually it's only necessary to connect using "ssh -X" and the display is 
>automatically redirected. 

Yeah ... ssh takes care of redirecting the display:

ezio@cevrin:~$ ssh -X  10.0.1.32 
ezio@10.0.1.32's password: 
Linux nagiossrv 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686

ezio@nagiossrv:~$ 
ezio@nagiossrv:~$ 
ezio@nagiossrv:~$ echo $DISPLAY
localhost:10.0


Cheers,

                   Ezio

---

### Post by k.sangeeth on 2009-02-04
Default installtion of Ubuntu denies TCP connections to Xserver.

So, to enable it do the following.
Go to System->Administration->Login Window
in the "security" tab .. uncheck against the field "Deny TCP connections to XServer".
restart X and do the same usual stuff.. (xhost,export DISPLAY .. etc.. etc)

hope this helped .. I myself struggled to find the solution ;)

[http://www.sangeek.com]("http://www.sangeek.com")

---

### Post by emacs on 2009-06-08
> **k.sangeeth said:**
> Default installtion of Ubuntu denies TCP connections to Xserver.

So, to enable it do the following.
Go to System->Administration->Login Window
in the "security" tab .. uncheck against the field "Deny TCP connections to XServer".
restart X and do the same usual stuff.. (xhost,export DISPLAY .. etc.. etc)

hope this helped .. I myself struggled to find the solution ;)

[http://www.sangeek.com]("http://www.sangeek.com")

Yes this worked for me.  Thanks.
Does anyone know the equivalent steps for KDE?

---

### Post by emacs on 2009-06-08
> **emacs said:**
> Yes this worked for me.  Thanks.
Does anyone know the equivalent steps for KDE?

Please ignore the request if you don't have the answer.
After I posted my original question, I learned that kubuntuforums.org existed.
So I'll go there and see if I can answer the question.

---

### Post by JackeyKing on 2009-07-29
> **k.sangeeth said:**
> Default installtion of Ubuntu denies TCP connections to Xserver.

So, to enable it do the following.
Go to System->Administration->Login Window
in the "security" tab .. uncheck against the field "Deny TCP connections to XServer".
restart X and do the same usual stuff.. (xhost,export DISPLAY .. etc.. etc)

hope this helped .. I myself struggled to find the solution ;)

[http://www.sangeek.com](http://www.sangeek.com)
It's worked for me, Thanks so much  :D
registed to say this.

---

