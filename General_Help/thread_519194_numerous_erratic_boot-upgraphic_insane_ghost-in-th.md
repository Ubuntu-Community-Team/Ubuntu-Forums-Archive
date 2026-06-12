---
title: "numerous erratic boot-up/graphic insane ghost-in-the-machine"
date: 2007-08-06
forum: General Help
---

### Post by GMachine_24 on 2007-08-06
My post got very long so I appended it to this post. Thanks for your understanding.

gm

---

### Post by nitro_n2o on 2007-08-06
loool such a long post.. 
do u have the Nvidia drivers installed and the restricted media thingy enabled?? 
and try removing seaMonkey maybe it's causing the problem.. 
and inspect /var/log/syslog for any weired entries or errors this should help if you find the error

---

### Post by GMachine_24 on 2007-08-07
Hi:

Thanks for being brave enough to take on the laptop from hell.

I like to tackle one problem/solution at a time, otherwise when I eventually fix the problem(s) I don't know which fix worked.

So, here are the contents of my /var/log/syslog

<code>

Aug  7 05:14:59 samba2 syslogd 1.4.1#18ubuntu6: restart.
Aug  7 05:14:59 samba2 anacron[4661]: Job `cron.daily' terminated
Aug  7 05:17:01 samba2 /USR/SBIN/CRON[5439]: (root) CMD (   run-parts --report /etc/cron.hourly)
Aug  7 05:18:31 samba2 anacron[4661]: Job `cron.weekly' started
Aug  7 05:18:31 samba2 anacron[5483]: Updated timestamp for job `cron.weekly' to 2007-08-07
Aug  7 05:18:56 samba2 exiting on signal 15
Aug  7 05:18:57 samba2 syslogd 1.4.1#18ubuntu6: restart.
Aug  7 05:18:57 samba2 anacron[4661]: Job `cron.weekly' terminated
Aug  7 05:18:57 samba2 anacron[4661]: Normal exit (2 jobs run)
Aug  7 05:38:58 samba2 -- MARK --
Aug  7 05:58:59 samba2 -- MARK --
Aug  7 06:17:01 samba2 /USR/SBIN/CRON[7108]: (root) CMD (   run-parts --report /etc/cron.hourly)
Aug  7 06:25:01 samba2 /USR/SBIN/CRON[7305]: (root) CMD (test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily)
Aug  7 06:39:02 samba2 -- MARK --
Aug  7 06:59:03 samba2 -- MARK --

</end code>

Honestly, most of this is jibberish to me. If it means something to you, please let me know.

I will work on the nvidia drivers - I know they are a consisten problem for Linux.

Thanks for your time.

--gm

---

### Post by GMachine_24 on 2007-08-09
Ok, sorry to beg but I have gotten nowhere fast attempting to resolve these issues. It appears from the syslog output the problem might be related to crontab or a cron file running ..... but I looked at the cron.daily and other files using vim and nothing jumps out at me. However, I am not familiar with what should be there.

It seems to me that, somewhere in my laptop, are files that, on reboot or start, tell my computer to run the various actions I mentioned in my initial post. Since the same actions are taken on every boot/reboot/startup I think we can rule out memory/power/hardware failure as those kinds of problems spew out randomly changing problems - not consistent problems such as I have.

So, thanks in advance. 

--gm24

---

### Post by GMachine_24 on 2007-08-10
Last night I jumped on the Ubuntu IRC chat channel and within two minutes someone had diagnosed my problem: I had inadvertently saved a "session" file - which ran every time I logged in.

Here is some information about sessions:

[http://www2.yo-linux.com/cgi-bin/man.cgi?section=all&topic=gnome-session](http://www2.yo-linux.com/cgi-bin/man.cgi?section=all&topic=gnome-session)

I deleted the file and my problems were gone.

This is an FYI post and I hope someone who has a similar problem will find this post early on instead of spending 10 hours banging their head against the wall.

gm

---

