---
title: "Systemd shows incorrect &quot;Active:&quot; date and time"
date: 2020-08-05
forum: General Help
---

### Post by 0n0w1c on 2020-08-05
I have installed 20.04 on a Raspberry PI and some Intel boxes. On the Raspberry Pi when I view the "Active" date and time of systemd processes, the incorrect date and time is displayed... which never changes no matter if the process is stopped and restarted.

For example:

```
$ systemctl status cloud-config
* cloud-config.service - Apply the settings specified in cloud-config
     Loaded: loaded (/lib/systemd/system/cloud-config.service; enabled; vendor preset: enabled)
    Drop-In: /etc/systemd/system/cloud-config.service.d
             `-getty-wait.conf
     Active: active (exited) since Wed 2020-04-01 12:23:53 CDT; 4 months 4 days ago
    Process: 1236 ExecStart=/usr/bin/cloud-init modules --mode=config (code=exited, status=0/SUCCESS)
   Main PID: 1236 (code=exited, status=0/SUCCESS)

Warning: journal has been rotated since unit was started, output may be incomplete.

```

Also notice the Warning about the journal which is erroneous... I rebooted this PI just an hour or so ago.

```

$ timedatectl status
               Local time: Wed 2020-08-05 13:55:13 CDT 
           Universal time: Wed 2020-08-05 18:55:13 UTC 
                 RTC time: n/a                         
                Time zone: America/Chicago (CDT, -0500)
System clock synchronized: yes                         
              NTP service: active                      
          RTC in local TZ: no

```

My installations on the Intel machines do not have this issue.
Where does systemd store the date/time information? Something is amiss here, any suggestions?
Could it be because the Raspberry PI does not have a true RTC?

---

### Post by 0n0w1c on 2020-08-05
I answered my own question... yes, it is because the Raspberry Pi does not have a true RTC.
Install fake-hwclock to resolve this issue.

---

