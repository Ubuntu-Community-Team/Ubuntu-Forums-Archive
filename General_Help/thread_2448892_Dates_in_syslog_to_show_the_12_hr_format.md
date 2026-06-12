---
title: "Dates in syslog to show the 12 hr format"
date: 2020-08-15
forum: General Help
---

### Post by raleigh3 on 2020-08-15
Can I make some change so the dates in syslog to show the 12 hr format?

Thanks.

---

### Post by norobro on 2020-08-16
Perusing the man page  it looks like even if you create a custom template in /etc/rsyslog.conf you will only be able to get 24 hour time format as output from rsyslogd. 
From the man page: [http://manpages.ubuntu.com/manpages/bionic/man5/rsyslog.conf.5.html#property%20replacer](http://manpages.ubuntu.com/manpages/bionic/man5/rsyslog.conf.5.html#property%20replacer)
> $HOUR      The current hour in military (24 hour) time (2-digit)


It is rather trivial to write a script (bash, python, awk etc.) to output the file in 12 hr. format. 
An awk example:```
awk '{  split($3,a,/:/); # split the timestamp
        if (a[1]<12) {
            ampm="a";
        }
        else {
            ampm="p";
        }
        if (a[1] > 12){  
            a[1] = a[1]-12;
        } 
        a[1] = sprintf("% 2.0f", a[1]);
        $3=a[1]":"a[2]":"a[3]ampm;  # put new timestamp into original field
        print $0
     }' /var/log/syslog
```Sample output:```
Aug 16  7:32:52p Ubuntu anacron[6015]: Anacron 2.3 started on 2020-08-16
Aug 16  7:32:52p Ubuntu anacron[6015]: Normal exit (0 jobs run)
Aug 16  7:32:52p Ubuntu systemd[1]: anacron.service: Succeeded.
```
HTH

---

