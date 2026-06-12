---
title: "Wubi Freezes on Blue Screen."
date: 2007-04-28
forum: General Help
---

### Post by Brummiesteven on 2007-04-28
Hi,
I'm having some trouble installing Wubi. The Windows side of everything is fine it's when I reboot and get to the blue screen. I get some progress bar and that completes. Then I get a second one, something about detecting hardware components. Once this is done nothing happens.

A black space under the blue screen appears where I can type in crap but nothing works. I've left it for over an hour and nothing has happened.

Any thoughts? :confused:

---

### Post by ago on 2007-04-28
press alt+f4 and check the logs.
That generally is due to the fact that we missed a driver required by your hard disk and that is using an unoptimized driver which works at very slow speed.

---

### Post by Brummiesteven on 2007-04-28
> **ago said:**
> press alt+f4 and check the logs.
That generally is due to the fact that we missed a driver required by your hard disk and that is using an unoptimized driver which works at very slow speed.

Thanks for the quick reply.

I took a photo:
[[IMG]http://img267.imageshack.us/img267/7605/28042007364sl1.th.jpg[/IMG]](http://img267.imageshack.us/my.php?image=28042007364sl1.jpg)

Any suggestions?

---

### Post by ago on 2007-04-28
press alt+f2 then at the command prompt run

nano /var/log/syslog

search for messages relating to loop7

---

### Post by Brummiesteven on 2007-04-28
It says syslog not found.

---

### Post by Soccrmastr on 2007-04-29
uninstall wubi from inside windws with uninstall.exe, and then delete the ISO that was downloaded, and start it over again.

---

### Post by Brummiesteven on 2007-04-30
I have actually downloaded Kubuntu and installed that on a partition.

If the creators of Wubi Want, I can leave Wubi on the windows partition for the moment to see if any fixes will work on it? Might be good incase others get problems.

---

### Post by ago on 2007-04-30
> **Brummiesteven said:**
> If the creators of Wubi Want, I can leave Wubi on the windows partition for the moment to see if any fixes will work on it? Might be good incase others get problems.

Yep that would be nice.

---

