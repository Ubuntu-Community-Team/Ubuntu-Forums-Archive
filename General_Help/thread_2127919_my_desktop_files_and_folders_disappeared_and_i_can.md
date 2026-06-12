---
title: "my desktop files and folders disappeared and i cant open home folder."
date: 2013-03-21
forum: General Help
---

### Post by dee00 on 2013-03-21
my desktop files and folders disappeared and i cant open home folder, and also my panels look like ******(i  think its the very old panel,just plain and silver),and on log-in the  bottom panel pics change to a file with an x(looks like a corrupted  file),it also became laggy. 
this happened after restarting for a finish upgrade(i upgraded the archive manager).
i tried restarting it again but its still like that.
what should i do? please help. i use 11.04

---

### Post by TheFu on 2013-03-21
Check the log files to see what might be happening.
[http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files)

BTW, 11.04 has not been supported since last October. I'd recommend getting to 12.04. If Unity is why you don't wish to use 12.04, you can run XFCE or LXDE GUI environments easily with just a few commands. You'll be at home then AND under an LTS supported release.

---

### Post by dee00 on 2013-03-21
when i turned on my laptop and logging in to try your suggestion,an error popped out "could not update ICEauthority file/home/keithdylan/.ICEauthority" then "there is a problem with the configuration server.(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256). then the screen turned blue and the panel is white.
then another error "You do not have the permissions necessary to view the contents of keithdylan".

uhhmm do you think there is a way to retrieve my files?

---

### Post by TheFu on 2013-03-22
We don't know that there is anything wrong with any specific files at this point.
Until you view the log files, we are blind. The issues you are seeing could just be a bad video driver or a failing GPU or corrupted files related to those.

Can you ssh in from another machine?
Can you pull the HDD from the machine and mount it from another?

---

