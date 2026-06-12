---
title: "Ubuntu unable to boot"
date: 2008-04-22
forum: General Help
---

### Post by trowerpower35 on 2008-04-22
When attempting to boot ubuntu (gutsy) I get an error saying
"Mounting /root/dev on /dev/.static/dev failed: No such file or directory"
"/init: /init: 181: cannot open /root/dev/console: No such file".
This started after I had to force my computer to shutdown after it was unable to return from screensaver.  The screensaver came up while resuming from hibernate.  I think a bad hibernate image was left in swap possibly.  Any ideas ?

**it tries resuming from sda5 first but fails.
Also, I have access to files through vista dual boot, but no Install Cd's.  Please don't make me stay in Vista....
*sda1=vista,sda2=gutsy,sda3=swap,sda5=dvdrw

I was able to install hardy which resolved problems, hopefully this doesnt come up as issue in hardy also.

---

### Post by gogadan on 2008-10-10
i had a simaler problem with hardy and all i had to do was de-frag and run a disk-check in windows and then it worked fine for some reason its a long shot but worth a go!

---

