---
title: "how to control history"
date: 2008-07-01
forum: General Help
---

### Post by dexter.deepak on 2008-07-01
i have heard in windows about a command like "histcontrol" , we can set it on or off to record our history as needed. is there something sysnonymous to that in ubuntu ?
also i have the browser history in mozilla, if i want i can delete it...isnt there a place where i can see my browser history (in some logs or blah) ?

---

### Post by VMC on 2008-07-01
> **dexter.deepak said:**
> i have heard in windows about a command like "histcontrol" , we can set it on or off to record our history as needed. is there something sysnonymous to that in ubuntu ?
also i have the browser history in mozilla, if i want i can delete it...isnt there a place where i can see my browser history (in some logs or blah) ?

In bash Terminal type "history". Also from Terminal type "man history". It explains all you can do. For example , if you type history in bash and you will get a lot of commands that you ran preceded by a number. If you type a "!" followed by one of the numbers then that command is executed:
vmc@vmc-desktop:~$history
...
  491  vim tryme.pl
  492  ps
  493  ps -x
  494  top
  495  vim tryme.pl
  496  vim tryme.py
...
vmc@vmc-desktop:~$ !492
ps
  PID TTY          TIME CMD
 7512 pts/0    00:00:00 bash
 7603 pts/0    00:00:00 bash
 7640 pts/0    00:00:00 ps

Hope that explains something, or maybe I'm missing your point.

---

### Post by sdennie on 2008-07-01
> **dexter.deepak said:**
> i have heard in windows about a command like "histcontrol" , we can set it on or off to record our history as needed. is there something sysnonymous to that in ubuntu ?


I'm not sure what you mean by this.  Do you mean the command line history or some other history?

> 
also i have the browser history in mozilla, if i want i can delete it...isnt there a place where i can see my browser history (in some logs or blah) ?

You can see the browser history using Ctrl-H or Ctrl-Shift-H in firefox.

---

### Post by dexter.deepak on 2008-07-01
thanks VMC, you got my first point.
regarding my second query, iam sorry for not explaining it well.i will try again:
i can very easily see and delete my browser history.
but what if i delete all my history from browser...can i STILL get some hints of my internet usage in some logs ...i think that all the http requests must be going through some firewall (i heard people call it iptables) ...which can record the list of sites visited.

---

