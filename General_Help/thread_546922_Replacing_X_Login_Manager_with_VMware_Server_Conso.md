---
title: "Replacing X Login Manager with VMware Server Console"
date: 2007-09-09
forum: General Help
---

### Post by bazz on 2007-09-09
I was wondering if someone could help me do this?
This tell you how to do it but ubuntu does not have /etc/inittab so I'm not sure how to attack this.
[http://www.vmware.com/community/thread.jspa?threadID=44623&tstart=0](http://www.vmware.com/community/thread.jspa?threadID=44623&tstart=0)
and
[http://www.vmware.com/community/thread.jspa?messageID=646593&#646593](http://www.vmware.com/community/thread.jspa?messageID=646593&#646593)

I am trying to run this with LTSP.

---

### Post by bazz on 2007-09-10
Okay does anyone know how I could edit what would have been the /etc/inittab. I know ubuntu no longer uses inittab. so how could I add this to what would have been in the inittab?

VM0:345:respawn:su - vmconsole -c "/usr/X11R6/bin/startx

---

### Post by bazz on 2007-09-10
Never mind... I got it to work.

---

