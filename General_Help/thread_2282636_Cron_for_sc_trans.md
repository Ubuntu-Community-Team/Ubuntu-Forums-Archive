---
title: "Cron for sc_trans"
date: 2015-06-15
forum: General Help
---

### Post by michael136 on 2015-06-15
Greetings

I Am Running A Shoutcast Server With sc_trans40, For Some Reason sc_trans keeps losing connection to the Shoutcast Server.

Can Someone please tell me how to create a Cron to Check And restart sc_trans if It is Down

Thanks Guys 

Michael

---

### Post by JKyleOKC on 2015-06-15
I'm running an FTP server on a desktop system but last year it developed a similar problem. The server would sometimes shut down for no apparent reason, and stay down until I received an email or phone complaint from a would-be customer attempting to upload a database file for recovery. Starting it again always took care of things.

Here's the solution that has been working for me, for several months now. If the FTP server shuts down, it will automatically start within an hour, round the clock, and every hour the test result gets logged so that I have information available if another shutdown happens.

I created a text file named "ftpmonitor" with this content:
```
#! /bin/bash
#  Script to restart FTP server if not running
#  jk - 2 Dec 2014

s=$(service proftpd status)
r=$(echo "$s"|cut -c 50-56)

logger -p syslog.info "Checking FTP server..." 
if [ "$r" == "running" ]
  then logger -p syslog.info "$s"
  else logger -p syslog.info "$(service proftpd start)"
fi

exit 0

```Using sudo, I put the file into my /etc/cron.hourly directory, and made sure it was owned by root and had 700 permissions.

You'll need to modify the details, of course, and probably want to put the file elsewhere and call it from "crontab" to check more often than once an hour. Note that checking too often can put a heavy load on your system, though. It's a compromise between bogging things down, and responding rapidly to a failure.

The most difficult part of this was locating the exact offset in the status response for extracting the $r variable; I'm not familiar with the Shoutcast server, so different commands might be needed. The approach should work, though.

---

### Post by michael136 on 2015-06-16
Thanks Jim, I Will Try This


Mike

---

