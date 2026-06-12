---
title: "need to block usb storage"
date: 2014-11-28
forum: General Help
---

### Post by mobin2 on 2014-11-28
Dear Sir,

I need to block normal user to access to usb storge.

I have tried two steps that are 

1. blacklist the usb_storage module by adding blacklist usb_storage to /etc/modprobe.d/blacklist.conf and

2. mv /lib/modules/3.2.0-35-generic-pae/kernel/drivers/usb/storage /lib/modules/3.2.0-35-generic-pae/kernel/drivers/usb/storage-old

but these won't work.

can any one please provide me solution for this

---

### Post by slickymaster on 2014-11-28
*Moved to the ***General Help*** sub-forum*

---

### Post by Yougo on 2014-11-28
Hi,

maybe this can help:

[http://askubuntu.com/questions/66718/how-to-manage-users-and-groups](http://askubuntu.com/questions/66718/how-to-manage-users-and-groups)

[http://www.ubuntubuzz.com/2012/05/install-old-graphical-users-and-groups.html](http://www.ubuntubuzz.com/2012/05/install-old-graphical-users-and-groups.html)

if you install gnome-system-tools, like described behind the link, you get access to more advanced user options. you can specify whether users are allowed do things like use a printer or go on the Internet. There is a setting about letting users use USB storage devices or not:
[IMG]http://1.bp.blogspot.com/-Gk1-6t7ismI/T6ckmqySrrI/AAAAAAAAD20/L4xvgTheiW4/s320/Selection_169.png[/IMG]

just make sure your own account is an administrator, so you keep all the permissions :-)

---

### Post by Yougo on 2014-12-02
@mobin2,

So... Did you solve your problem? 

If the solution is in this thread, please mark this thread as [SOLVED], and post a link to the solution in the first post.

---

