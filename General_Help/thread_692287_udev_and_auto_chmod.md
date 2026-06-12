---
title: "udev and auto chmod"
date: 2008-02-09
forum: General Help
---

### Post by kafkaian on 2008-02-09
I have installed a Hauppauge hvr-1100 dvb-t card which works with Kaffeine through 'root' and the standard super-user. However, no matter what I do I cannot get this to run with a normal user after every reboot because:

1) Regardless of whether or not I change the permission of /dev/dvb/ to normal users through chmodding 755 or group, although it works after changing this, once rebooted the /dev/dvb/ reverts back to 'root'

2) Regardless of any udev intervention, I don;t seem to be able to override the default value for /dev/dvb/


Any help will be gratefully received because at the moment I'm doin' ma head in


Gutsy 2.6.22-14-generic:mad:

---

### Post by kafkaian on 2008-02-09
Ugh! Now it seems that every time I start Kaffeine under a normal/non admin user it requires the DVB source transmitter to be entered. Grr

---

