---
title: "Apparmor giving &quot;denied&quot; messages for firefox"
date: 2017-02-23
forum: General Help
---

### Post by PaulBx on 2017-02-23
uname -a gives Linux xxxxxx 4.4.0-64-generic #85-Ubuntu SMP Mon Feb 20 11:50:30 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
I'm getting these in the log. Don't know yet what is non-functioning in firefox.
```

[  441.087586] audit_printk_skb: 153 callbacks suppressed
[  441.087588] audit: type=1400 audit(1487896304.175:63): apparmor="DENIED" operation="open" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/proc/4392/net/arp" pid=4398 comm=4C696E6B204D6F6E69746F72 requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[  441.309977] audit: type=1400 audit(1487896304.395:64): apparmor="DENIED" operation="file_mprotect" profile="/usr/lib/firefox/firefox{,*[^s][^h]}//lsb_release" name="/usr/bin/python3.5" pid=4413 comm="lsb_release" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[  442.773216] audit: type=1400 audit(1487896305.859:65): apparmor="DENIED" operation="open" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/etc/xdg/lubuntu/applications/mimeinfo.cache" pid=4392 comm="firefox" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[  444.379434] audit: type=1400 audit(1487896307.467:66): apparmor="DENIED" operation="unlink" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/home/paul/.cache/mozilla/firefox/mjgcmg3t.default/safebrowsing-to_delete/test-track-simple.cache" pid=4443 comm=55524C20436C6173736966696572 requested_mask="d" denied_mask="d" fsuid=1000 ouid=0
[  448.053015] audit: type=1400 audit(1487896311.139:67): apparmor="DENIED" operation="unlink" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/home/paul/.cache/mozilla/firefox/mjgcmg3t.default/safebrowsing-to_delete/test-track-simple.cache" pid=4443 comm=55524C20436C6173736966696572 requested_mask="d" denied_mask="d" fsuid=1000 ouid=0
[  448.054470] audit: type=1400 audit(1487896311.139:68): apparmor="DENIED" operation="unlink" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/home/paul/.cache/mozilla/firefox/mjgcmg3t.default/safebrowsing-to_delete/test-track-simple.cache" pid=4443 comm=55524C20436C6173736966696572 requested_mask="d" denied_mask="d" fsuid=1000 ouid=0
[  535.833890] audit: type=1400 audit(1487896399.797:69): apparmor="DENIED" operation="open" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/sys/devices/system/node/node0/meminfo" pid=4392 comm="firefox" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0

```

Firefox is in enforce mode, I guess that's the default these days? I believe it is just the stock apparmor profile (has that been tightened up lately?). Any suggestions will be appreciated.

---

### Post by yoshii on 2017-02-23
I don't know what to do either.  
This type of thing is mentioned in the recent release notes and known issues for the recent Ubuntus.  
It's an AppArmor legacy/configuration issue of sorts.  
It will probably be fixed in future releases since it's more of a kernel issue, I think.

---

### Post by PaulBx on 2017-02-23
I found this helpful guide to the error messages, a little more clear than the man page:

[https://unix.stackexchange.com/questions/116591/why-am-i-getting-apparmor-error-messages-in-the-syslog-about-ntp-and-ldap](https://unix.stackexchange.com/questions/116591/why-am-i-getting-apparmor-error-messages-in-the-syslog-about-ntp-and-ldap)

BTW the man page still talks about upstart...

---

### Post by PaulBx on 2017-02-23
I see what you are saying in the 16.10 release notes about apparmor.

Well, I will leave it alone until I find something in firefox that no longer works.

---

### Post by &amp;KyT$0P# on 2017-02-23
I think this is a problem with the apparmor profile for Firefox.  These definitely should not be denied -
> ```
[  444.379434] audit: type=1400 audit(1487896307.467:66): apparmor="DENIED" operation="unlink" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/home/paul/.cache/mozilla/firefox/mjgcmg3t.default/safebrowsing-to_delete/test-track-simple.cache" pid=4443 comm=55524C20436C6173736966696572 requested_mask="d" denied_mask="d" fsuid=1000 ouid=0
[  448.053015] audit: type=1400 audit(1487896311.139:67): apparmor="DENIED" operation="unlink" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/home/paul/.cache/mozilla/firefox/mjgcmg3t.default/safebrowsing-to_delete/test-track-simple.cache" pid=4443 comm=55524C20436C6173736966696572 requested_mask="d" denied_mask="d" fsuid=1000 ouid=0
[  448.054470] audit: type=1400 audit(1487896311.139:68): apparmor="DENIED" operation="unlink" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/home/paul/.cache/mozilla/firefox/mjgcmg3t.default/safebrowsing-to_delete/test-track-simple.cache" pid=4443 comm=55524C20436C6173736966696572 requested_mask="d" denied_mask="d" fsuid=1000 ouid=0
```
[FONT=Courier New]~/.cache/mozilla/firefox[/FONT] is just the Firefox caches.  Everything in that directory should be write-accessible to Firefox.  Those denied operations are just Firefox trying to delete old cache files.

---

