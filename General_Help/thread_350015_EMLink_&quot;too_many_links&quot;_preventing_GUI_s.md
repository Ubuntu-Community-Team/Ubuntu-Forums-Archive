---
title: "EMLink &quot;too many links&quot; preventing GUI starting"
date: 2007-01-31
forum: General Help
---

### Post by MoLE on 2007-01-31
Ok, I've got a tricky one for the experts here.

Yesterday, my main system (which has been upgraded Hoary --> Dapper --> Edgy) was running fine - I left it before going to work with Azureus running (seeding), with Liferea polling, but no other applications going - logged into the GUI.  My wife reported no problems using her account later that day.  When I next checked the machine this morning, I found that I had been dumped back to the console with an error message - Xserver failed to load.

The output from the xserver errorlog was "failed to load /tmp/.Xauthority"

So I performed an sudo aptitude upgrade && sudo aptitude dist-upgrade.  The updates downloaded fine, however dpkg couldn't configure a couple of the packages, and so couldn't install them.

The error message was "Errno 31: Too many links, cannot write /tmp/gconfxxxx"
I have a root partition (which has /tmp on it) and a /home partition (and a swap of course).
Both root and /home are ext3 partitions.

A bit of googling seems to indicate that this error is a POSIX error [as I found described here]("http://www.wlug.org.nz/EMLINK").

The difficult question is: How do I identify where the excess links are likely to be and how do I fix the problem?
I have checked /tmp which is pretty much empty, except for one symbolic link.

Seems like a basic filesystem problem, but I'm not sure how to address it from the command line.

Update:
After a couple of reboots, ubuntu decided to do a fsck on the / filesystem - which seemed to fix the error. 
sudo aptitude dist-upgrade then completed successfully.

---

