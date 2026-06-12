---
title: "Free Space A Lot Smaller Than Available Space?"
date: 2008-05-05
forum: General Help
---

### Post by Jordinho on 2008-05-05
I have 1.3 GB available but it says I have over 8 GB free. Is there a way to clear that space and reclaim the difference?

[IMG]http://img.photobucket.com/albums/v632/kamau84/Screenshot-1.png[/IMG]

---

### Post by Jordinho on 2008-05-22
Bumpskees

---

### Post by qpieus on 2008-05-22
yes there is a way to reclaim some of that space. The 7.4 GB of "missing" free space is the approx. 5% of disk size being reserved by the ext3 filesystem (145 Gb * 5% = ~7.4 GB). That's how the default ext3 filesystem is set up. I searched a little and it looks like you can adjust the reserve by using a program called tune2fs. See this post for info:


[http://boncey.org/2006_11_18_reclaiming_ext3_disk_space](http://boncey.org/2006_11_18_reclaiming_ext3_disk_space)

It doesn't sound like such a good idea to lower the reserve on your root partition though - that reserve space is there to prevent your disk from becoming completely full, which could cause problems. I recommend leaving it alone.

---

