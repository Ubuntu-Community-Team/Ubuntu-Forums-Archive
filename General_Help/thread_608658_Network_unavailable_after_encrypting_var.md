---
title: "Network unavailable after encrypting /var"
date: 2007-11-10
forum: General Help
---

### Post by humungous on 2007-11-10
Hi folks!

I did run into a network problem after having encrypted /var among /home and /tmp. Now, the encryption is working fine, but the network (including the loopback to 127.0.0.1) isn't working after booting.

I'm starting my cryptodisks via the startup-script */etc/init.d/cryptdisks-early*. The network system seems to be started earlier, and therefore unsuccessfully tries to write data to /var before it's mounted.

So, the question is: Is it possible to postpone the start of the network and loopback-device after the cryptodisks have been mounted?

I tried to reverse the order of the startup-scripts in the /etc/rcS.d/-folder with:

```
sudo mv /etc/rcS.d/S08loopback /etc/rcS.d/S29loopback
```

hence putting the loopback-script *after* "S26cryptdisks-early". Strangely, this did not solve my problem.

Greetings,
humungous

(Ubuntu 7.04)

---

### Post by humungous on 2007-11-11
Anyone?

---

