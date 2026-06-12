---
title: "install Radarr"
date: 2021-08-25
forum: General Help
---

### Post by jgw on 2021-08-25
I am thinking about installing Radarr  "https://radarr.video/"   I have made runs at it but it seems to get complicated .  I thought if anybody has come across an easy way to install or know how to do one that's easy.  If so I would appreciate the information.  I figured that somebody might have an easy solution and thought I would ask.

Thank you......................

---

### Post by jgw on 2021-08-28
I thought I would make a run at installing radarr.  I used the instructions at [https://low-orbit.net/how-to-install-radarr-ubuntu](https://low-orbit.net/how-to-install-radarr-ubuntu).  I did the following:
installed dependencies
Downloaded radar.master.3.2.2.5080,linux-core-x64.tar.gz
unpacked the tar.gz file and moved the results (in Radarr) to the opt/ folder 
(not sure Radarr shouldn't be radarr also noted that the files was full of a lot of microsoft stuff)


I then created a service file with cd /etc/systemd/system/ and then sudo gedit radarr.service
then inserted the code below and saved the file at /etc/sysemd/system/:
```

[Unit]
Description=Radarr Daemon
After=syslog.target network.target

[Service]
User=root
Group=root
Type=simple
ExecStart=/usr/bin/mono /opt/Radarr/Radarr.exe -nobrowser
TimeoutStopSec=20
KillMode=process
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

After saving the file, as "radar.service" I enabled it with "sudo systemctl enable radarr"  In theory this should fix it so 
that it starts running when I boot up.  (I am not sure about this one.  The name of the file was "radar.service", I enabled 'radarr' and wonder how it knows)

Then it told me to go to [http://192.168.0.108:7878](http://192.168.0.108:7878), in the browser, and it should appear - it didn't.

both owner and group of the radar.service file is 'root'

"server radarr status got me
```
greg@movies:~$ sudo service radarr status
&#9679; radarr.service - Radarr Daemon
     Loaded: loaded (/etc/systemd/system/radarr.service; enabled; vendor preset: enabled)
     Active: inactive (dead) since Sat 2021-08-28 14:21:35 PDT; 13min ago
    Process: 22662 ExecStart=/usr/bin/mono /opt/Radarr/Radarr.exe -nobrowser (code=exited, status=2)
   Main PID: 22662 (code=exited, status=2)

Aug 28 14:21:35 movies systemd[1]: radarr.service: Scheduled restart job, restart counter is at 5.
Aug 28 14:21:35 movies systemd[1]: Stopped Radarr Daemon.
Aug 28 14:21:35 movies systemd[1]: radarr.service: Start request repeated too quickly.
Aug 28 14:21:35 movies systemd[1]: radarr.service: Failed with result 'exit-code'.
Aug 28 14:21:35 movies systemd[1]: Failed to start Radarr Daemon.

```

I am now stopped as something isn't right.

Thoughts?

---

### Post by jgw on 2021-08-31
I tried another found at radarr.video  At the beginning there are prerequisites that confused me:
Installation Prerequisites
The below instructions are based on the following prerequisites. Change the instructions as needed to suit your specific needs if necessary.
* The user radarr is created
* The user radarr is part of the group media
* Your download clients and media server run as and are a part of the group media
* Your paths used by your download clients and media server are accessible (read/write) to the group media
* You created the directory /var/lib/radarr and ensured the user radarr has read/write permissions for it

These are assumptions that the reader has a clue about where stuff comes from so the following were my thoughts and the replies (ending with "linux 101"):

        The user radarr is created have no idea how this is created - no instructions

The radarr installation instructions are not linux 101. Previous Linux knowledge or basic google abilities are required.

        The user radarr is part of the group media OK - in what file, where?

A user being part of a group has nothing to do with a file at all. The radarr installation instructions are not linux 101. Previous Linux knowledge or basic google abilities are required.

        Your download clients and media server run as and are a part of the group media I use sabnzbd+ which is somehow attached to group media in what file?

A group has nothing to do with a file at all. You don't know what user and group you configured sabznbd to run as?

        Your paths used by your download clients and media server are accessible (read/write) to the group media More mystery with no documentation....

Basic linux paths/permissions/ownership. The radarr installation instructions are not linux 101. Previous Linux knowledge or basic google abilities are required. TL;DR Radarr needs to be able to read/write your download and library locations.

        You created the directory /var/lib/radarr and ensured the user radarr has read/write permissions for it Did I - don't think so - have no idea what the reference is or means

The radarr installation instructions are not linux 101. Previous Linux knowledge or basic google abilities are required. This means you created a directory and applied the correct ownership and permissions for it.
   
So, I just stopped as I got yelled at for not doing stuff for which there was no documentation.
First I thought to reply but thought better of it.  Does anybody have a clue as to what this guy is talking about?

Thank you...........

---

### Post by jgw on 2021-08-31
I have been doing yet more reading on this whole thing.  Seems that the latest radarr is 3.2.2.5080  This version no longer uses momo but something called core which I have no clue about.  I also found that there were bugs in version 3.  All told it would seem I would be better off to just forget radarr until its a bit more mature.  That being the case I am going to mark this as done in about a week to give anybody time to reply to my last.  Then I will mark this whole thing as solved and move on (and return in a couple of months to make another run at it)

---

### Post by HermanAB on 2021-08-31
Just a tip: When installing unsupported SW, it is best to make a virtual machine to experiment and instal the program.  This way, you don’t mess up your host system.

---

### Post by jgw on 2021-09-17
I have been studying on this and decided to just wait a bit as Radarr seems to still be in development and things are changing and this might not be the right time to install it.  That being said I am going to mark this as solved (that's the only choice)

Want to thank everybody who replied to my plight.............

---

