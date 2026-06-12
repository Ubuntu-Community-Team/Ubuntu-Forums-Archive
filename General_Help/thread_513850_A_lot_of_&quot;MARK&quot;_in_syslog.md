---
title: "A lot of &quot;MARK&quot; in syslog"
date: 2007-07-31
forum: General Help
---

### Post by maorui on 2007-07-31
I installed Ubuntu 7.04 recently. I found there are lots of "-- MARK --" in /var/log/messages. Every 20 minutes, it will appear.

Jul 31 07:37:26 build syslogd 1.4.1#20ubuntu4: restart.
Jul 31 07:53:50 build -- MARK --
Jul 31 08:13:50 build -- MARK --
Jul 31 08:33:50 build -- MARK --
Jul 31 08:53:51 build -- MARK --
Jul 31 09:13:51 build -- MARK --
Jul 31 09:33:51 build -- MARK --
Jul 31 09:53:51 build -- MARK --
Jul 31 10:13:52 build -- MARK --
Jul 31 10:33:52 build -- MARK --
Jul 31 10:53:52 build -- MARK --
Jul 31 11:13:52 build -- MARK --
Jul 31 11:33:52 build -- MARK --
Jul 31 11:53:53 build -- MARK --

Where did these MARK come from? And how to get rid of them?

---

### Post by pofigster on 2007-07-31
Sorry, I shouldn't have messed with your distro....

---

### Post by maorui on 2007-08-01
No one has this issue except me?:(

---

### Post by Shib on 2007-08-01
It's just syslog letting you know that it's still working, even though no messages have been sent to your syslog in the last 20 minutes. pretty standard.

---

### Post by mgarces on 2007-08-15
I'm also having this problem! Is there a way to turn this off?
I never seen this, except on Ubuntu... :confused:

---

### Post by shad0w_walker on 2007-08-15
Its a perfectly normal part of the logging. Its very handy for spilting up the log into more manageable, understandable sections. If you look at the time it occurs they are steady intervals.

To repeat.

[SIZE="4"]This is NOT a error, problem or unwanted activity. It is perfectly normal.[/SIZE]

---

### Post by kirios on 2007-08-15
[COLOR="DarkRed"]Maybe the messages are from Mark Shuttleworth.[/COLOR]

---

### Post by mgarces on 2007-08-16
ah ahahahha :)
that was good! A friend of mine suggested that it was the kernel that was talking to me, since my name is Marco =)

I understand this is not a problem, but it's a feature I do not want, thereby it should be easy to remove. At least, it should be documented better. This is not the default for system logging, not that I know. =)
Have phun!

---

### Post by dragon76 on 2007-09-05
in /etc/default/syslogd

find the line that starts

SYSLOGD=

in the "" with the other options being passed add -m0 (that's a zero)

this will turn off the mark statements and is the default in some distros

---

