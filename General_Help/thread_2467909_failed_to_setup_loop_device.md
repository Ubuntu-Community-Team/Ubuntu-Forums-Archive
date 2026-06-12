---
title: "failed to setup loop device"
date: 2021-10-12
forum: General Help
---

### Post by kjeld-flarup on 2021-10-12
After reinstalling my PC with Ubuntu 20.04 I can nolonger mount squashfs images (similar to iso images)

```
sudo mount -t squashfs -o loop artifacts/AMC300-PCM31_CODESYS3.5.15.20_v1.3.0.3-local-30-g2326606-dirty.raucb /tmp/tmp.d5vsSrGwq5/rauc
mount: /tmp/tmp.d5vsSrGwq5/rauc: failed to setup loop device for artifacts/AMC300-PCM31_CODESYS3.5.15.20_v1.3.0.3-local-30-g2326606-dirty.raucb.

``` 

It seems that all /dev/loop is taken by snap.

Did I forget to set up something. or has something changed?

---

### Post by TheFu on 2021-10-12
Delete some snaps and try again.  Is there a limit to the number of loop mounts ... more more likely is the default number too small for your needs?

[https://askubuntu.com/questions/617060/how-many-loopback-devices-can-linux-support](https://askubuntu.com/questions/617060/how-many-loopback-devices-can-linux-support) says that 64 is the default, but that's from 2015. They also say that modifying the limit in modules.conf or grub boot to be higher than 64 didn't seem to matter.

---

