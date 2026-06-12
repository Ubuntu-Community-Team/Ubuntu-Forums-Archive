---
title: "klogd fails on boot after installing 686 kernel"
date: 2005-11-01
forum: General Help
---

### Post by towsonu2003 on 2005-11-01
I installed (using apt-get) the 686 kernel in the repositories a couple of days ago. from that day on, klogd fails on boot everytime I choose the 686 kernel from grub. I have absolutely no idea why.

kern.log was empty until today. kern.log.0 was last written 10 days ago (bf I installed new kernel) I had to figure out what program was failing during boot up (I had to learn to disable usplash) and which log it writes to. 

Today I figured all this and started klogd manually with sudo klogd -d from gnome's terminal. it did not give any errors and it is writing to kern.log now. 

However, it fails during boot. Can someone help me?

thanks.

PS. other users pointed previously that this is not critical, but I feel more comfortable with working log files...

[Edit] I just noticed that it says something like 'permission denied' on boot time as the error. I used Bastille to secure my box, but that was before I upgraded my kernel to 686 and at that time, everything was working...

---

### Post by towsonu2003 on 2005-11-21
no one?

may this be related to Bastille configuration?

---

### Post by towsonu2003 on 2005-12-16
](*,)

---

