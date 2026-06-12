---
title: "ERROR while getting interface flags : no such device"
date: 2007-08-16
forum: General Help
---

### Post by lior751 on 2007-08-16
Dear surferers,

who can help me about this problem?

Thanks,
Lior

---

### Post by lopkiol on 2007-08-17
I have Debian Etch, but I have exactly the same issue.

During startup I get this message: "ERROR while getting interface flags: No such device
Failed to bring up wlan0."

Same message if I type ifup wlan0 in a shell.
And it only started this morning, my connection was ok yesterday. I had some update ready and I installed them. I am sure it is because of those. Lior, if you had the same problem after the installation of some updates let me know.

I had a look at etc/network/interfaces and it looks fine.
Can anyone help?

---

### Post by lkilcher on 2007-08-18
Hey,
I'm also running etch.  I was getting this error, but only because I had mis-spelled the link to my wpa_supplicant.conf file in the line:
wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf
in my /etc/network/interfaces file.

Have you tried bringing up your network using something like:
wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf

Once I got this working, I rebooted and things seemed to work fine.

My problem seemed to be related to typos, rather than software.  I must have checked 10 times before I found the stupid little error.

later,
abdul

---

