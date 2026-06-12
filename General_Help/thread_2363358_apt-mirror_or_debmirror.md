---
title: "apt-mirror or debmirror?"
date: 2017-06-09
forum: General Help
---

### Post by alldavid1959 on 2017-06-09
I have 8 computers that I maintain for a small business.  Surprisingly, 6 of them are currently running a Linux desktop on them, as well as the
company using it on the primary network/data server.  Unfortunately, because of the company's high network usage, downloading updates on
each computer is a very slow, time-consuming, and frustrating process.

I would like to create a mirror of the repository onto a local storage device, then update the other computers off of it; only having to download
the newest packages and updates once, onto the storage device.

After looking around online, the two best options I could find to create the mirror is to use either 'apt-mirror' or 'debmirror'.

[https://ubuntuforums.org/showthread.php?t=352460](https://ubuntuforums.org/showthread.php?t=352460)
[https://raymii.org/s/tutorials/Set_up_a_local_Ubuntu_debian_apt_mirror.html](https://raymii.org/s/tutorials/Set_up_a_local_Ubuntu_debian_apt_mirror.html)

Has anyone used either of these?  Does one seem better, or easier, than the other, or are they about the same?

---

### Post by Tadaen_Sylvermane on 2017-06-09
Mirroring the entire repo is not worth it for small deployment. Look at apt-cacher-ng. Or a squid proxy to cache stuff. Squid done right would speed up most of your network as well.

---

### Post by alldavid1959 on 2017-06-14
Sorry it's taken a while for me to reply.  I HAD thought about that, but in order for apt-cacher-ng to work, wouldn't the server need to be set up BETWEEN the router and the switch,
so that it could catch whatever application or service is being downloaded to the specific computer who "asked" for it from the internet?
I was just wanting to add the Repository Server to the network switch as if it were a regular file server.

---

