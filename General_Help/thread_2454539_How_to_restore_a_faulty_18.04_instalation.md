---
title: "How to restore a faulty 18.04 instalation?"
date: 2020-12-01
forum: General Help
---

### Post by lcvieira-br on 2020-12-01
Hello, gentlemen.

I've been dealing with Ubuntu as a definitive user for a while so far - 2012 straight ahead - but I never found the time nor the reason to go deeper into solving problems mostly because I've never faced "hard to deal with" problems as an Ubuntu user. In fact this is not exactly a kind reference to the system, instead a strong personal recognition to its value as a stable, trustable, robust, etc. etc. working environment. I'm actually using Linux versions since 1999 - Slackware, mostly - but after using Ubuntu in 2011 I definitely found in it my personal, preferred "flavor"

In November 2019 I upgraded a desktop from U16.04 to U18.04, along with two laptops, and I also installed a U18.04 in another desktop - this one was "from zero ground", not an update -. Both laptops and the "zero ground" installations work perfectly fine, but the one I upgraded was not able to establish connection to any network (the connection with the WWW was maintained during the installation and the automatic update occurred normally, but after the last procedure and reboot the network does not connect). This specific desktop is dual-boot with W7, and the W7 works totally fine, no problems after upgrading U16.04 to U18.04. Interestingly "ping 8.8.8.8" works fine, so the lower network layers are active, but neither intranet nor www are available.

I would very much like to try a restoration or an upgrade to U20.04, but since it does not connect to the www I am not sure about how to proceed. Would a regular, bootable pen drive do the job?

If there is no way to restore this installation, I'll sadly re-install a U18.04.5 from "zero ground"... Sadly because I'd like to keep the many applications already running on this installation.

I'd gladly follow any suggestions. And thank you all in advance.

Cheers.

---

### Post by ActionParsnip on 2020-12-01
If you run:
```

echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf > /dev/null

```
Does the web access work OK?

---

