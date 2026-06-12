---
title: "Can't run cronjobs, service not even running"
date: 2013-01-24
forum: General Help
---

### Post by Ortix on 2013-01-24
I can't seem to run cronjobs as my own user (ortix)

I then checked if the cron service was running and it was only for root. 

So i tried starting the cron service and this happened:

```
ortix@icarus:~$ service cron start
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.41" (uid=1000 pid=3584 comm="start cron ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")

```Not sure what is going on..

My crontab (with crontab -e):
```

1 * * * * /usr/bin/touch /home/ortix/test.txt

```I used that just for testing purposes to see if I could get it working.

Also:

```
ortix@icarus:~$ ps aux | grep cron
root      1034  0.0  0.0  19112  1024 ?        Ss   18:53   0:00 cron
ortix     3620  0.0  0.0  13588   920 pts/2    S+   19:04   0:00 grep --color=auto cron
```Any ideas what I can do?

---

### Post by jonobr on 2013-01-24
Dopey question from me

Did you run ```
service cron start
```

with sudo?

Try stopping and starting?

---

### Post by Cheesehead on 2013-01-24
> **Ortix said:**
> I then checked if the cron service was running and it was only for root.

That is normal.



> **Ortix said:**
> 
My crontab (with crontab -e):
```

1 * * * * /usr/bin/touch /home/ortix/test.txt

```I used that just for testing purposes to see if I could get it working.

That's a good testing method. I use a similar.
Did you intend to run this test once each hour at 1 minute past the hour (1 * * * *)? What time did you try it?
Or did you intended to run it once each minute (* * * * *)?




> **Ortix said:**
> ```
ortix@icarus:~$ ps aux | grep cron
root      1034  0.0  0.0  19112  1024 ?        Ss   18:53   0:00 cron
ortix     3620  0.0  0.0  13588   920 pts/2    S+   19:04   0:00 grep --color=auto cron
```

That looks normal.

---

### Post by Ortix on 2013-01-24
**** you're right.. it was set to run past the hour. It's 1:09 here and the test file is created...

so how would I run it every 30 minutes? with */30 * * * * ?

Also, it seems that there is no mail being sent out. I defined an email with MAILTO=username@hotmail.com but i'm not receiving any emails (the cron is running every minute now)

---

### Post by elgordodude on 2013-01-24
yes

---

### Post by matt_symes on 2013-01-24
Hi

> **Ortix said:**
> **** you're right.. it was set to run past the hour. It's 1:09 here and the test file is created...

so how would I run it every 30 minutes? with [COLOR=Red]*/30 * * * * [/COLOR]


That will run it every 30 minutes.

You may want to read this.

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

Kind regards

---

### Post by Cheesehead on 2013-01-24
> **Ortix said:**
> it seems that there is no mail being sent out. I defined an email with MAILTO=username@hotmail.com but i'm not receiving any emails

Check /var/log/syslog
Cron requires a Mail Transfer Agent (MTA) to send the failure e-mail to you...but an MTA is not included in the stock install of Ubuntu.
If cron cannot find an MTA, cron will log the fact in /var/log/syslog.
Several MTAs, including sendmail and postfix, are in the Ubuntu repositories and quite easy to install using your favorite package manager.

---

