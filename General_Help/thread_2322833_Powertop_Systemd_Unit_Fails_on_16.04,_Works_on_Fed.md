---
title: "Powertop Systemd Unit Fails on 16.04, Works on Fedora"
date: 2016-04-30
forum: General Help
---

### Post by buzzingrobot on 2016-04-30
I've been frustrated getting powertop to execute via a Systemd unit in 16.04.

In Fedora 24, installing powertop also installs "powertop.service".  Then, a "sudo systemctl enable powertop.service", a reboot, and it's working.

Ubuntu's powertop package doesn't install a powertop.service unit.  If I copy Fedora's to Ubuntu, enable it, it does not start, either on system start or via "sudo systemctl start powertop.service".  "systemctl status powertop.service" reports it failed. Permissions, ownership, etc. are identical to Fedora's. (Also, powertop's readout would indicate it worked, but does not.)

Here's the unit:

```
[Unit]
Description=PowerTOP autotuner

[Service]
Type=oneshot
ExecStart=/usr/sbin/powertop --auto-tune

[Install]
WantedBy=multi-user.target
```

The "--auto-tune" parameter tells powertop to execute a set of power management tuning tweaks.

I'm stumped. Been down the usual paths in Google and elsewhere to no avail.

---

### Post by michael-woegerbauer on 2016-08-29
I found your post because I was struggling with the same problem (and, as a newbee, I didn't know what upstart was and what is systemd). I am on an older Asus Zenbook (2014) with Xubuntu 16.04.1 running. 

First of all, thank you for your code (I used, but added two paragraphs in the end, see below).

Maybe, I found half a solution: it seems to me that the powertop.service files has to be
1. non-executable and owned by root
2. end with two paragraphs (that's what I found the other .service-files to be like, but that maybe isn't compulsory)
3. be in /lib/systemd/system/powertop.service
4. in /etc/systemd/system/multi-user.target.wants/ there is only a symbolic link, so I copied it by doing sudo cp -s /lib/systemd/system/powertop.service /etc/systemd/system/multi-user.target.wants/
In the end, I did sudo systemctl enable powertop.service

The result:
- the service is still not loading automatically at startup
- BUT "sudo systemctl start powertop.service" WORKS

Question: why is the service not loading automatically at startup?

---

### Post by tak21 on 2017-03-27
Hi, I came accross this thread while installing Ubuntu 17.04 on my laptop. I wanted to permanently use the powertop tweaks, as I go down from 15 watt to 5 (!)

Based on your suggestions and other information I did the following:

```


$ sudo vi /lib/systemd/system/powertop.service

[Unit]
Description=Powertop tunings

[Service]
Type=idle
Environment="TERM=dumb"
ExecStart=/usr/sbin/powertop --auto-tune

[Install]
WantedBy=multi-user.target

$ sudo cp -s /lib/systemd/system/powertop.service /etc/systemd/system/multi-user.target.wants/
$ sudo systemctl enable powertop.service
$ sudo systemctl start powertop.service
```

That gave me a working service which is started on boot. Hope that helps you too (and thank you for your tips!).

---

