---
title: "Help with installing WPA_supplicant &amp; Openssl"
date: 2005-10-24
forum: General Help
---

### Post by sylvius on 2005-10-24
Hi there.

I am new to Ubuntu, as well as the Linux world in general. I am running Breezy Badger on my Thinkpad T43. The default wireless settings are sufficient for my home wireless connection, but the wireless connection at my school requires the following:

- Encryption: WPA Radius with TKIP key exchange
- Authentication: 802.1x with PEAP and MSCHAPv2

After quite a bit of searching (online and in these forums), I thought that I had found my solution in WPA_supplicant. The readme said for PEAP-MSCHAPv2 support, I would have to get OpenSSL as well.

Well, I installed OpenSSL per its readme (well, I *think* that I installed it correctly). I then tried to install WPA_supplicant, only to get this error when I try to "make":

In file included from config.c:22:
sha1.h:6:25: error: openssl/sha.h: No such file or directory
make: *** [config.o] Error 1

I have tried to fix this problem on my own, but to no avail. Like I said, I am pretty new to the Linux world, so please forgive my ignorance. Thank you!:)

---

### Post by [Rui] on 2005-10-24
Well, you are going throught the hardest possible way.
A little less hard could be:
# apt-get install wpasupplicant

But if you're really into graphics go the the menu System -> Administration -> Synaptic Package Manager and search for wpasupplicant...

---

