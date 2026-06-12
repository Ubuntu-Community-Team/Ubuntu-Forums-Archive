---
title: "Kubuntu Trusty Won't Update (&quot;No Public Key&quot; Error)"
date: 2015-07-09
forum: General Help
---

### Post by BlacklightHalo on 2015-07-09
Hi everyone,

I'm trying to update my Kubuntu Trusty, and when I type, 

```
sudo apt-get update
```

I get the following error:

```
W: GPG error: https://private-ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E131728675254D99
```

Connecting to the sources seems to take an especially long time as well, at least comparatively to how fast it used to run. Admittedly I haven't run an update in a long time. Does anyone know what the problem may be here, and if it may be something I need to fix with my computer?

---

### Post by Vladlenin5000 on 2015-07-09
The error message refers to a PPA, not to any official Ubuntu repositories. Check that first of all.

---

### Post by oldos2er on 2015-07-09
Add the key: ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E131728675254D99
```

---

### Post by BlacklightHalo on 2015-07-09
Got it. The faulty source was for something I tried to install that either never worked, or didn't install itself properly. I didn't need it either way so I just got rid of it. Thanks for the help. =)

---

