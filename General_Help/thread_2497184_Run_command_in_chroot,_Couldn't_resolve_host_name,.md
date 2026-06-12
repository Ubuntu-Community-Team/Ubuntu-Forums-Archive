---
title: "Run command in chroot, Couldn't resolve host name, systemd"
date: 2024-04-26
forum: General Help
---

### Post by helmut2024 on 2024-04-26
Hi,

I created a chroot env for freshclam. No big deal:

```
helmut@mail2:~$ sudo chroot --userspec=amavis:amavis /var/amavis/ /usr/bin/freshclam
Fri Apr 26 09:43:37 2024 -> ClamAV update process started at Fri Apr 26 09:43:37 2024
Fri Apr 26 09:43:37 2024 -> daily database available for download (remote version: 27256)
Time:    1.0s, ETA:    0.0s [========================>]   60.58MiB/60.58MiB
Fri Apr 26 09:43:40 2024 -> Testing database: '/var/lib/clamav/tmp.15e451200a/clamav-8f29cc5daf2695ebfa1a54fc8e98a788.tmp-daily.cvd' ...
Fri Apr 26 09:43:49 2024 -> Database test passed.
Fri Apr 26 09:43:49 2024 -> daily.cvd updated (version: 27256, sigs: 2060084, f-level: 90, builder: raynman)
Fri Apr 26 09:43:49 2024 -> main database available for download (remote version: 62)
Time:    1.1s, ETA:    0.0s [========================>]  162.58MiB/162.58MiB
Fri Apr 26 09:43:53 2024 -> Testing database: '/var/lib/clamav/tmp.15e451200a/clamav-f576baabf6755b6fcbe953d35b6bc31c.tmp-main.cvd' ...
Fri Apr 26 09:44:03 2024 -> Database test passed.
Fri Apr 26 09:44:03 2024 -> main.cvd updated (version: 62, sigs: 6647427, f-level: 90, builder: sigmgr)
Fri Apr 26 09:44:03 2024 -> bytecode database available for download (remote version: 335)
Time:    0.2s, ETA:    0.0s [========================>]  282.94KiB/282.94KiB
Fri Apr 26 09:44:03 2024 -> Testing database: '/var/lib/clamav/tmp.15e451200a/clamav-e88d0cbe99e3c61aae16863b372223ed.tmp-bytecode.cvd' ...
Fri Apr 26 09:44:03 2024 -> Database test passed.
Fri Apr 26 09:44:03 2024 -> bytecode.cvd updated (version: 335, sigs: 86, f-level: 90, builder: raynman)
helmut@mail2:~$

```

I then prepared a systemd service script:

```
[Unit]
Description=ClamAV virus database updater
Documentation=man:freshclam(1) man:freshclam.conf(5) https://docs.clamav.net/
ConditionPathExists=!/etc/cron.d/clamav-freshclam
Wants=network-online.target
After=network-online.target
[Service]
User=amavis
Group=amavis
RootDirectory=/var/amavis
ExecStart=/usr/bin/freshclam
[Install]
WantedBy=multi-user.target

```


```
helmut@mail2:~$ sudo service clamav-freshclam-chroot start
helmut@mail2:~$

```

Result:

```
Apr 26 09:46:45 mail2 freshclam[103342]: Fri Apr 26 09:46:45 2024 -> Trying to retrieve CVD header from https://database.clamav.net/daily.cvd
Apr 26 09:46:45 mail2 freshclam[103342]: Fri Apr 26 09:46:45 2024 -> ^remote_cvdhead: Download failed (6) Fri Apr 26 09:46:45 2024 -> ^ Message: **Couldn't resolve host name**
Apr 26 09:46:45 mail2 freshclam[103342]: Fri Apr 26 09:46:45 2024 -> ^Failed to get daily database version information from server: https://database.clamav.net
Apr 26 09:46:45 mail2 freshclam[103342]: Fri Apr 26 09:46:45 2024 -> !check_for_new_database_version: Failed to find daily database using server https://database.clamav.net.
Apr 26 09:46:45 mail2 freshclam[103342]: Fri Apr 26 09:46:45 2024 -> Trying again in 5 secs...
Apr 26 09:46:50 mail2 freshclam[103342]: Fri Apr 26 09:46:50 2024 -> Trying to retrieve CVD header from https://database.clamav.net/daily.cvd
Apr 26 09:46:50 mail2 freshclam[103342]: Fri Apr 26 09:46:50 2024 -> ^remote_cvdhead: Download failed (6) Fri Apr 26 09:46:50 2024 -> ^ Message: Couldn't resolve host name
Apr 26 09:46:50 mail2 freshclam[103342]: Fri Apr 26 09:46:50 2024 -> ^Failed to get daily database version information from server: https://database.clamav.net
Apr 26 09:46:50 mail2 freshclam[103342]: Fri Apr 26 09:46:50 2024 -> !check_for_new_database_version: Failed to find daily database using server https://database.clamav.net.
Apr 26 09:46:50 mail2 freshclam[103342]: Fri Apr 26 09:46:50 2024 -> Trying again in 5 secs...

```

Why? Ubuntu 22.04.4 LTS.

Thank you!

---

### Post by helmut2024 on 2024-04-27
/run must be mounted in the jail which I don't want to do. I ended up using an init script.

---

