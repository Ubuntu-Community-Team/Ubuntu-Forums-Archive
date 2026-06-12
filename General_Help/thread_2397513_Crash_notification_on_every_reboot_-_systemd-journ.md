---
title: "Crash notification on every reboot - systemd-journald"
date: 2018-07-30
forum: General Help
---

### Post by Alan5127 on 2018-07-30
Hi All,

Every time I reboot my Ubuntu 16.04 LTS desktop, I get a notification that systemd-journald has crashed.

I took a screenshot and attached here (I can't seem to get it to display in-line, but this is the link):

[https://imagebin.ca/v/4AVcEzVCOZ5w](https://imagebin.ca/v/4AVcEzVCOZ5w)


However, if I run this command from the terminal:

```
systemctl status systemd-journald
```

I get this output, which seems to imply that the service is, in fact, running (albeit with the warning at the bottom):

```
user1@machine1:~$ systemctl status systemd-journald

&#9679; systemd-journald.service - Journal Service
   Loaded: loaded (/lib/systemd/system/systemd-journald.service; static; vendor preset: enabled)
   Active: active (running) since Tue 2018-07-31 01:13:19 NZST; 7h ago
     Docs: man:systemd-journald.service(8)
           man:journald.conf(5)
 Main PID: 246 (systemd-journal)
   Status: "Processing requests..."
   CGroup: /system.slice/systemd-journald.service
           &#9492;&#9472;246 /lib/systemd/systemd-journald

Jul 31 01:13:19 OptiPlex-GX280 systemd-journald[246]: Runtime journal (/run/log/journal/) is 4.8M, max 38.7M, 33.8M free.
Jul 31 01:13:19 OptiPlex-GX280 systemd-journald[246]: Journal started
Warning: Journal has been rotated since unit was started. Log output is incomplete or unavailable.

```


Not sure if this is relevant, but it seemed to start after I had a system crash a couple of days ago (an Ubuntu 18.04LTS VM hung in VirtualBox).  I had to kill the VM (and chose to restore to the last snapshot).

I then rebooted the machine using 'reboot' from a terminal, and it has been giving the crash error since.

Also, the machine is very slow now - I am guessing that is a symptom of systemd-journald crashing, but mentioning just in case.


I don't know where to go from here, so any suggestions welcome.


Thanks,

Alan.

---

### Post by mc4man on 2018-07-30
Try removing all the files in /var/crash folder, then reboot & see if it's still crashing.
You could use this if you copy & paste or type with care.
```
sudo rm /var/crash/*.*
```

---

### Post by Alan5127 on 2018-07-31
Hi Mc4Man,

> **mc4man said:**
> Try removing all the files in /var/crash folder, then reboot & see if it's still crashing.
You could use this if you copy & paste or type with care.
```
sudo rm /var/crash/*.*
```

Perfect - that seemed to fix it.

Thanks so much!

Alan.

---

