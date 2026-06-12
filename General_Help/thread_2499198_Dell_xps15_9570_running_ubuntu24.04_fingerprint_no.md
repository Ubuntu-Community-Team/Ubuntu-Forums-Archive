---
title: "Dell xps15 9570 running ubuntu24.04 fingerprint not working"
date: 2024-07-18
forum: General Help
---

### Post by l-u53r on 2024-07-18
This been been asked multiple times but none of the solutions given have actually worked for me so I am asking again, hoping that new information may have become available. I recently got myself an xps15 9570 and did a fresh install of ubuntu24.04 because, why not. My hardware version was adverstised as having the fingerprint sensor. Now I am trying to get the ubuntu to work with the finger print and so far nothing seems to work. 
I have read through a number of forums and they make mention of installing a package fprintd and libpam-fprint. As it happens ubuntu24.04 comes with all that already installed. I have also confirmed that the fingerprint sensor is present by running ```
lsusb
``` and here is the result;
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubBus 001 Device 002: ID 1ea7:0066 SHARKOON Technologies GmbH [Mediatrack Edge Mini Keyboard]
Bus 001 Device 003: ID 0cf3:e301 Qualcomm Atheros Communications 
Bus 001 Device 004: ID 27c6:5395 Shenzhen Goodix Technology Co.,Ltd. Fingerprint Reader
Bus 001 Device 005: ID 0c45:671d Microdia Integrated_Webcam_HD
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

```

From the instructions I have read from googling, I have to enable fingerprint authentication to which I have done  with ```
pam-auth-update
``` command. Before proceeding I restarted my system and the run ```
sudo systemctl status fprintd.service
``` to which the system responds that the fprint daemon is indeed running from the output log
```

fprintd.service - Fingerprint Authentication Daemon
     Loaded: loaded (/usr/lib/systemd/system/fprintd.service; static)
     Active: active (running) since Thu 2024-07-18 12:49:08 GMT; 3s ago
       Docs: man:fprintd(1)
   Main PID: 4489 (fprintd)
      Tasks: 6 (limit: 18721)
     Memory: 1.9M (peak: 3.0M)
        CPU: 62ms
     CGroup: /system.slice/fprintd.service
             &#9492;&#9472;4489 /usr/libexec/fprintd


Jul 18 12:49:08 alien systemd[1]: Starting fprintd.service - Fingerprint Authen>
Jul 18 12:49:08 alien fprintd[4489]: Creating TOD wrapper for goodix-tod (Goodi>
Jul 18 12:49:08 alien systemd[1]: Started fprintd.service - Fingerprint Authent>

```

Now when I run ```
fprintd-enroll
``` I get this error;
```

Impossible to enroll: GDBus.Error:net.reactivated.Fprint.Error.NoSuchDevice: No devices available

```
And when I run ```
sudo systemctl status fprintd.service
``` few seconds later it returns a log that basically says the fprintd daemon is inactive
```

fprintd.service - Fingerprint Authentication Daemon
     Loaded: loaded (/usr/lib/systemd/system/fprintd.service; static)
     Active: inactive (dead)
       Docs: man:fprintd(1)


Jul 18 12:10:58 alien systemd[1]: Started fprintd.service - Fingerprint Authent>
Jul 18 12:11:28 alien systemd[1]: fprintd.service: Deactivated successfully.
Jul 18 12:48:23 alien systemd[1]: Starting fprintd.service - Fingerprint Authen>
Jul 18 12:48:23 alien fprintd[4352]: Creating TOD wrapper for goodix-tod (Goodi>
Jul 18 12:48:23 alien systemd[1]: Started fprintd.service - Fingerprint Authent>
Jul 18 12:48:54 alien systemd[1]: fprintd.service: Deactivated successfully.
Jul 18 12:49:08 alien systemd[1]: Starting fprintd.service - Fingerprint Authen>
Jul 18 12:49:08 alien fprintd[4489]: Creating TOD wrapper for goodix-tod (Goodi>
Jul 18 12:49:08 alien systemd[1]: Started fprintd.service - Fingerprint Authent>
Jul 18 12:49:39 alien systemd[1]: fprintd.service: Deactivated successfully.

```

I have tried almost every hack I have read online including purging and reinstalling fprintd and libpam-fprint, Installing the goodix driver from dell and nothing seems to do the trick. Now I am wondering if this error could mean I may have been sold a laptop without the fingerprint sensor installed or is just an ubuntu issue.

---

### Post by gchutz on 2024-07-26
Were you able to get your fingerprint reader working? I'm having the same issue on an XPS 15.

---

### Post by l-u53r on 2024-08-18
No I haven't so far. I'm hoping that the point release will solve this issue. Unfortunately that has also been delayed by two weeks.

---

