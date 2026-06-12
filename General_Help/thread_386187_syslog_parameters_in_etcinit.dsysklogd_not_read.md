---
title: "syslog parameters in /etc/init.d/sysklogd not read"
date: 2007-03-16
forum: General Help
---

### Post by afternine on 2007-03-16
Hi!

I wanted to enable my syslogd to receive syslogs from other machines, so I did change  in /etc/init.d/ksyslogd the line

SYSLOGD="-u syslog"

to

SYSLOGD="-u syslog -r"

However, after the restart of syslogd (with /etc/init.d/ksyslogd restart), the syslog daemon does not not remote reception enabled. It does not start as user syslog either. If I stop it and start it manually with

/sbin/syslogd -u syslog -r 

it starts up with remote reception enabled and as user syslog.

Any idea why it does not read the parameters, anyone?

Bye

Sorry, forgot to mention: Kubuntu 6.10 on a  2.6.17-10-generic

---

### Post by rdsmf on 2007-05-14
Try this link, it worked for me. You seem to be having the same issue I was so give this a shot !

[http://ubuntuforums.org/showthread.p...light=sysklogd](http://ubuntuforums.org/showthread.p...light=sysklogd)

---

### Post by afternine on 2007-05-15
Sorry, but the link you posted does not return any discussion, just takes you to [http://ubuntuforums.org](http://ubuntuforums.org). Can you repost the link or find the direct link to article? 
Thanx

---

### Post by rdsmf on 2007-05-24
Sorry not sure why the link did not work but here it is again ..........

[http://ubuntuforums.org/showthread.php?t=366267](http://ubuntuforums.org/showthread.php?t=366267)

---

### Post by afternine on 2007-05-24
Thanx for posting the link, the problem and the solution described there are exactly as mine! Thanx again!

Bye

---

