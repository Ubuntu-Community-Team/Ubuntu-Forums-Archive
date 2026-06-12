---
title: "aa-genprof   AppArmorBug: Log contains unknown mode senw"
date: 2016-07-06
forum: General Help
---

### Post by cooloutac on 2016-07-06
[https://bugs.launchpad.net/apparmor/+bug/1399027](https://bugs.launchpad.net/apparmor/+bug/1399027)    How do I apply the hotfix for mentioned in this bug report?  can't use aa-genprof in newly installed ubuntu 16.04    

```
riting updated profile for /usr/bin/konversation.
Setting /usr/bin/konversation to complain mode.

Before you begin, you may wish to check if a
profile already exists for the application you
wish to confine. See the following wiki page for
more information:
[http://wiki.apparmor.net/index.php/Profiles](http://wiki.apparmor.net/index.php/Profiles)

Please start the application to be profiled in
another window and exercise its functionality now.

Once completed, select the "Scan" option below in 
order to scan the system logs for AppArmor events. 

For each AppArmor event, you will be given the 
opportunity to choose whether the access should be 
allowed or denied.

Profiling: /usr/bin/konversation

[(S)can system log for AppArmor events] / (F)inish
Reading log entries from /var/log/syslog.
Updating AppArmor profiles in /etc/apparmor.d.
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apparmor/logparser.py", line 402, in read_log
    self.add_event_to_tree(event)
  File "/usr/lib/python3/dist-packages/apparmor/logparser.py", line 206, in add_event_to_tree
    e = self.parse_event_for_tree(e)
  File "/usr/lib/python3/dist-packages/apparmor/logparser.py", line 303, in parse_event_for_tree
    raise AppArmorException(_('Log contains unknown mode %s') % rmask)
apparmor.common.AppArmorException: 'Log contains unknown mode senw'

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/sbin/aa-genprof", line 151, in <module>
    lp_ret = apparmor.do_logprof_pass(logmark, passno)
  File "/usr/lib/python3/dist-packages/apparmor/aa.py", line 2189, in do_logprof_pass
    log = log_reader.read_log(logmark)
  File "/usr/lib/python3/dist-packages/apparmor/logparser.py", line 407, in read_log
    raise AppArmorBug(ex_msg)  # py3-only: from None
apparmor.common.AppArmorBug: Log contains unknown mode senw

This error was caused by the log line:
Jul  6 12:31:45 kernel: [ 1585.343460] audit: type=1400 audit(1467822705.150:668): apparmor="ALLOWED" operation="file_perm" profile="/usr/bin/konversation" pid=6877 comm="konversation" laddr=192.168.1.22 lport=58236 faddr=164.132.77.237 fport=6697 family="inet" sock_type="stream" protocol=6 requested_mask="send" denied_mask="send"
```

---

### Post by cooloutac on 2016-07-06
oops I linked wrong bug report,  this is the correct one.  How do I apply the hotfix?   [https://bugs.launchpad.net/apparmor/+bug/1582374](https://bugs.launchpad.net/apparmor/+bug/1582374)

---

