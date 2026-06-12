---
title: "Syslog broken after 11.10LTS to 12.04LTS upgrade"
date: 2013-01-21
forum: General Help
---

### Post by CeruleanDragon on 2013-01-21
Hi Ubuntu Forums!
     I thought this might be a common issue but I can't seem to find other threads with people having the same issue. If there is one, please feel free to just link me over there, thanks ahead of time!

   I was running 11.10LTS (I think) as a syslog server for some of our networking gear. During one login I see a suggestion that v12.04LTS was available and to run do-release-upgrade to upgrade. I do so and it does its thing... and then suddenly no more incoming streams to syslog. Syslog only shows local system issues. It's not taking in the logging data from the networking equipment. I'm not even sure where to begin. Everything looks configured properly to my relative newbie eyes. A little while after this I start seeing that 12.10 is now available. I figure maybe upgrading again might fix it. Unfortunately I start getting this:

~~~~
New release '12.10' available.
Run 'do-release-upgrade' to upgrade to it.

me@mysystem:~$ sudo do-release-upgrade
[sudo] password for me:
Checking for a new Ubuntu release
No new release found
me@mysystem:~$
~~~~
I checked /etc/os-release just to be sure and sure enough, truly on 12.04.1 LTS
~~~~
Me@mysystem:/etc$ cat os-release
NAME="Ubuntu"
VERSION="12.04.1 LTS, Precise Pangolin"
~~~~

     Which is even more puzzling. Why is it suggesting there's a new version and yet... not? Strange. 
    
     Anyway, I tried installing syslog-ng, but that's not working and I can't figure out how to configure it (way too complicated for my tiny brain. Is there no way to just say, "Anything coming in from port 514 UDP/TCP, put in this file."?)

   My next step will be to just rebuild the system. However, I recognize that that's not really the best learning experience. "It broke? Reinstall the OS!" This isn't Windows after all. :)  On the flipside, I really *really* need to use it for troubleshooting firewall and router issues.

    Any help would be greatly appreciated. Thank you ahead time!

Isaac

---

