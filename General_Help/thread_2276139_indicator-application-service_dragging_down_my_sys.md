---
title: "indicator-application-service dragging down my system"
date: 2015-04-30
forum: General Help
---

### Post by Jim_ on 2015-04-30
Has any one had to troubleshoot issues with 'indicator-application-service'? What I am seeing is over a period of time, maybe a few days, that application will slowly consume up to 40-60 percent of my CPU percentage. The system gets slower and slower, almost unusable, even fan output noticeably hotter, until I stop and look into the system monitor. When I kill this application, it does restart but using 0-2 percent of CPU, and the system is instantly back to where it should be. 

This randomly happens, but usually takes a couple of days of minimal usage. Any ideas how to remedy this? I'm glad I figured out where the problem lies but I don't want to just uninstall the system monitor indicator if I don't have to.

This is using Ubuntu 12.04 LTS 64 bit.
Thanks, Jim

---

### Post by dino99 on 2015-04-30
i suspect a plugin to be the real problem ; try to use them one at a time to identify the one to blame
maybe you can grab some help/idea if you glance at either xorg.0.log or syslog or journalctl in case you use 15.04

---

### Post by Jim_ on 2015-05-03
You hit the nail on the head - finally got it to act up again, and killed indicator-multiload instead and it dropped all the usage off of application. 

Now, I would like to keep some sort of system load indicator on my panel. I'm going to try just un and reinstalling it and see if that makes it any better. Any suggestions for deciding what the problem is with indicator-multiload?

thanks

---

### Post by Jim_ on 2015-05-03
I just found the old bug report about indicator-multiload having a big memory leak problem in 12.04. Guess I will just get rid of it while I have this version os.

---

