---
title: "Ubuntu 14.04.  Syslog and messages contain no entries"
date: 2017-11-02
forum: General Help
---

### Post by sefs on 2017-11-02
Hi all, I just realized syslog and messages contains no entires.  I see a previous syslog.1 and it stopped recording on April 14.
The last line was:
```

Apr 14 21:02:46 goseek102 rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1282" x-info="http://www.rsyslog.com"] rsyslogd was HUPed

```

Where do I even begin to resolve this. Not finding much information that helps.

---

### Post by aromo2 on 2017-11-02
Your rsyslogd service died. Try restarting it: systemctl restart rsyslogd
It may have died due to OOM killer (out of memory killer) if the machine was running low on memory at that time.
My 2 cents.

---

### Post by sefs on 2017-11-02
> **aromo2 said:**
> Your rsyslogd service died. Try restarting it: systemctl restart rsyslogd
It may have died due to OOM killer (out of memory killer) if the machine was running low on memory at that time.
My 2 cents.

Looks like I do not have this particular tool installed.
```

systemctl: command not found

```

---

### Post by steeldriver on 2017-11-02
14.04 would use the `upstart` init system (not `systemd`) , I think?

```

sudo service rsyslog restart

```

---

### Post by sefs on 2017-11-02
> **steeldriver said:**
> 14.04 would use the `upstart` init system (not `systemd`) , I think?

```

sudo service rsyslog restart

```

this was the result
```

rsyslog stop/waiting
rsyslog start/running, process 8598

```
Still nothing in syslog though.
Update to above I said it stop recording on april 14 that would be in *2015*. Wow. Amazed i am only now seeing this.

---

