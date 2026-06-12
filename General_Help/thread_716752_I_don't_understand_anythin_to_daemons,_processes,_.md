---
title: "I don't understand anythin to daemons, processes, init, ..."
date: 2008-03-06
forum: General Help
---

### Post by Railsbuntu on 2008-03-06
Hi,

I am running a Ubuntu server edition (no gui), and the daemons and other stuff are getting me crazy.

I was playing with ddclient (dyndns autoupdater). I wanted Monit to monitor it. So I kill the ddclient with "sudo kill pid", and it died. But Monit was unable to revive it, and now I can't even start by hand, if I do: "sudo /etc/init.d/ddclient start" it tells me that it started, but it's not.

What's the deal with init.d and processes :confused:

Where can I find good info about that.


EDIT: I rebooted my server, and Monit didn't startup (I installed from source) and ddclient did start automatically. When I launched Monit by hand, I can now see that it is monitoring ddclient. I am getting confused...

Why didn't Monit start automatically? What to do to resolve that?

And still, when I kill the ddclient, Monit doesn't restart it, but it still says in the webserver that it is monitoring it and it is runnning which is not the case...


EDIT: acually it seems that Monit did restart ddclient, it's just that it doesn't restart dhclient which listens on port 62 (I don't know why), but in "ps aux" it shows up. 

But I don't understand anything. My website was still accessible (I was refreshing the pages) although the correct IP was not update, because now suddenly it just stopped working...

---

### Post by yota on 2008-03-06
Hi Railsbuntu,

since you killed the process, instead of doing an "/etc/init.d/ddclient stop", probably the pidfile (/var/run/ddclient.pid) has been left there and the system believes that ddclient is still running.
Please check if the file exists and eventually delete it.

Hope this helps!

p.s. if that doesn't work try to launch ddclient by hand with "ddclient --daemon 300" and see the output

---

### Post by Railsbuntu on 2008-03-06
Yep, you are right, the pid file is still there. But in Monit documentation they say that even if the pid file remains, monit is smart enough to check if it belongs to an orphin process or something  like that.

In the case one of my monitored application crashes, e.g: apache, does the pid file remain? Because in such case monit will never be able to revive the application.

---

### Post by yota on 2008-03-06
You are right too... monit claims to be able to detect if a pidfile effectively belongs to a running process [http://www.tildeslash.com/monit/doc/faq.php](http://www.tildeslash.com/monit/doc/faq.php)
Unfortunately I don't have much knowledge on monit, so I can't help on that side of the problem.
If tomorrow I'll find some spare time I'll do some test on my enviroment and let you know.

---

### Post by Railsbuntu on 2008-03-06
Hmmm,

What is that dhclient server?

Actually there are 2 processes involved: ddclient and dhclient ( I don't know what it is for yet).

If I kill ddclient, its pid file actually does get delete too, I got confused with dhclient. And I can restart it also and it works.

Now I have Monit which isn't starting at boot time, it's probably because I had to install from source, ubuntu's package being a bit old.

Thanks for your help yota. You gotta check Monit out, it is really good (when it works).

EDIT: when I kill dhclient, its pid file doesn't get deleted.

---

### Post by Railsbuntu on 2008-03-07
Okay I fixed monit.

I'd like to know how to activate/deactivate scripts at bootup. It seems that if a process has not been started by Monit, then it cannot monitor it. So I have to prevent my apps from being activated at boot time, and let Monit activate them.

I run only on commande line.

---

### Post by bodhi.zazen on 2008-03-07
It is a snap.

sudo /etc/init.d/service start|stop|restart

[http://www.debuntu.org/how-to-manage-services-with-update-rc.d](http://www.debuntu.org/how-to-manage-services-with-update-rc.d)

---

### Post by Railsbuntu on 2008-03-07
Smashing! Your link is a gem! I also added the site to my news aggregator :-D

However if I remove a script from startup, I see that sometimes the priorities are different than the default 20. Is it super important to reput them exactly the same as they were when I removed them? Should I write them down?

---

### Post by bodhi.zazen on 2008-03-07
NO ....

Keep in mind linux is case sensative, so ...

mv /etc/init.d/Sxxservice /etc/init.d/sxxservice

(change the S to a s )

---

### Post by Railsbuntu on 2008-03-07
That's smart.

Up to now what I did is ermove the executable marker from the script, but your method enables to still be able to start the script by hand if required. :KS


EDIT: by the way, at the time of inittab, if a process died, init would automatically respawn it. Nowadays how would you do that?

I use Monit, but I'd like to know if Monit can monitor itself or if I need to use something else to respawn it in case it dies.

---

### Post by Railsbuntu on 2008-03-09
> **bodhi.zazen said:**
> NO ....

Keep in mind linux is case sensative, so ...

mv /etc/init.d/Sxxservice /etc/init.d/sxxservice

(change the S to a s )
Actually, aren't we introducing an error by using such practice. Because in such case, if I start a process manually, during shutdown, the "stop" script won't be called by init, and it might result in some files or temporary data not being cleared correctly?

Shouldn't I remove all the links using update-rc.d -f remove, then recreate only the Kill ones? I think it is safer to do so.

---

