---
title: "replace `syslog` with `syslog-ng`?"
date: 2006-10-10
forum: General Help
---

### Post by jmoses on 2006-10-10
I'd like to replace the ancient `syslog` that's installed by default with either `metalog` or `syslog-ng`.  Unfortunately, I see there's a metapackage, `ubuntu-minimal` that depends specifically on `syslog`.

My questions are:

 1 - If I remove `ubuntu-minimal` is that going to mess something else ubuntu-specific up?  I don't want to screw up my upgrades or anything.

 2 - Is there any faq or howto about this topic (replacing syslog)?  I haven't found any in the forums, or via google.

Thanks,
-jon

---

### Post by dcstar on 2006-10-11
> **jmoses said:**
> I'd like to replace the ancient `syslog` that's installed by default with either `metalog` or `syslog-ng`.  Unfortunately, I see there's a metapackage, `ubuntu-minimal` that depends specifically on `syslog`.

My questions are:

 1 - If I remove `ubuntu-minimal` is that going to mess something else ubuntu-specific up?  I don't want to screw up my upgrades or anything.

 2 - Is there any faq or howto about this topic (replacing syslog)?  I haven't found any in the forums, or via google.

Thanks,
-jon

Metapackages are there for your convenience, don't worry about it.

Just install syslog-ng, AFAIK everything will just work.

---

### Post by seeker1458 on 2008-02-29
Hey, I have just finished the install for syslog-ng-2.0.8.  I installed all dependent libs and everything went fine.  This could be that I am just checking something elese.  When I go to System>Administration>System Log, then go to help>about, it says that the version is Log Viewer 2.20.0.1 (not 2.0.8).  Am I even in the right program?  How do I get syslog-ng to start running instead of syslogd?  I just built this gutsy box, and haven't ever used syslog befor.  But the higher ups have requested a syslog server, and everything I read said syslog-ng is better.  Any help is appreciated.

---

### Post by SpaceTeddy on 2008-03-01
installing syslog-ng will automatically uninstall the old syslog facility (sysklogd and klogd). They are replaced by syslog-ng. during the install, the old syslog will be stopped and the new one started. 

syslog-ng is configured to behave like syslog, so you will not notive any difference between the two if you have the standard setup on your box.

---

### Post by seeker1458 on 2008-03-03
Ok thanks! One question though. How do I access the web interface for easier management once I start sending syslog reports from other devices?  Do I have to install something like Nagios?, or is there a .conf file I can edit to allow for use of a "prettier" interface?

---

### Post by SpaceTeddy on 2008-03-03
syslog-ng does not come with any configuration interface. you will need to install one manually... [here]("http://www.debianhelp.co.uk/syslogngweb.htm") is a list of a quick google search which gave a few possibilites on what you can use to configure your syslog-ng.

i have only done this directly on the conf file - never used a frontend.

---

### Post by seeker1458 on 2008-03-03
thanks!  I'll see which one seems to be the most user friendly!

---

