---
title: "frequent writes by systemd-journald"
date: 2023-11-19
forum: General Help
---

### Post by bjlockie on 2023-11-19
I was getting frequent disk writes (every second) that I'm trying to figure out.

I think the biggest culprit was the hostapd.service.
There was tons in the journal shown by ```
$ journalctl -f
```

```
systemd[1]: Failed to start hostapd.service - Access point and authentication server for Wi-Fi and Ethernet. 

```

I disabled that service because I don't run an AP and it is misconfigured.

```
$ journalctl --disk-usage
Archived and active journals take up 3.2G in the file system.
```

I tried setting SystemMaxUse=100M
in
```
$ sudo vim  /etc/systemd/journald.conf

```


I'll see if that works.

---

