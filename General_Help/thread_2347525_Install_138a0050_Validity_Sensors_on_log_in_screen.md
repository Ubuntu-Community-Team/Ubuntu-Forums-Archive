---
title: "Install 138a:0050 Validity Sensors on log in screen"
date: 2016-12-26
forum: General Help
---

### Post by thibaud-ecarot on 2016-12-26
Hello,

I try to use my fingerprint reader to log in on my xubuntu 16.04. I have 138a:0050 Validity Sensors, Inc. Swipe Fingerprint Sensor. But this sensor isn't supported device from fprint ([https://www.freedesktop.org/wiki/Software/fprint/libfprint/Unsupported_devices/](https://www.freedesktop.org/wiki/Software/fprint/libfprint/Unsupported_devices/)).
```
$ sudo lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 138a:0050 Validity Sensors, Inc. Swipe Fingerprint Sensor
Bus 001 Device 003: ID 0bda:b006 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 05c8:0389 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 005: ID 1c4f:0034 SiGma Micro 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
Then, on google I found a fprint's fork, here: git clone [https://github.com/payden/libfprint.git](https://github.com/payden/libfprint.git) 
I have compile, register my fingerprint and test and that's work :
```

$ sudo examples/verify
fp:debug [fp_img_save_to_file] written to 'verify.pgm'
Wrote scanned image to verify.pgm
MATCH!

```

So, my question is : How I can use my fingerprint or the library that I have compile to perform a log in with my fingerprint on Xubuntu. Because I don't find menu or command line to install fingerprint reader on Xubuntu log in screen. Can you help me?

Thank you in advance,
Have a nice day.

---

### Post by thibaud-ecarot on 2016-12-27
I found a simple solution. Validity Sensor exists in the latest version of fprintd. So we could do that :

**sudo** pam-auth-update
[LIST]
[*]fprintd-enroll
[/LIST]
**And Enjoy !**

---

### Post by oldos2er on 2016-12-27
It would be great if you could mark your thread 'Solved' using Thread Tools at the top of the page. Thanks!

---

### Post by neerajv on 2017-03-12
Hi thibaud-ecarot,

Its great to hear that you have enabled the 138a:0050 Validity Sensors, Inc. Swipe Fingerprint Sensor, and using it, could you please shed some light on how you eventually did?

I have cloned the git repo but couldn't find configure files which were mentioned in the INSTALL file so couldn't compile the repo as a whole. If possible can you please write the steps of what all you installed and made the Fingerprint Sensor work.

Thanks in advance
Neeraj
HP-envy-j048tx
Ubuntu 14.04

---

### Post by winnipeg8 on 2017-03-28
Follow the procedures here: [https://launchpad.net/~fingerprint/+archive/ubuntu/fingerprint-gui](https://launchpad.net/~fingerprint/+archive/ubuntu/fingerprint-gui) They finally support this sensor.
When you swipe your finger - do it fast :)

---

