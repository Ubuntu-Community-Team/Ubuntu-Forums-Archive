---
title: "disabling fsck auto from terminal"
date: 2007-09-17
forum: General Help
---

### Post by darkskye on 2007-09-17
Hello

If anyone has read my previous post, i was having some troubles with the fsck auto-boot. Basically it would freeze at a random percentage, and become unresponsive.

Trouble is, when i try to boot the live CD, it too would freeze at a certain part.

***I have now completely re-installed ubuntu feisty***

now i was wondering if there was anything i can do in the terminal to make it where fsck will never auto-boot again.

thank you.

-chris

---

### Post by notwen on 2007-09-17
Although I highly recommend leaving fsck on, or atleast changing it's # of reboots to a higher frequency more to your liking, here is the command which should disable fsck.

```
sudo tune2fs -c 0 /dev/hdx
```

---

### Post by bodhi.zazen on 2007-09-17
If you like, assuming you disable auto check at boot, you can manually check at at later date, usually from a live CD.

See man fsck

---

