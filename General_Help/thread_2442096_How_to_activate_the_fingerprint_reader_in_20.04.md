---
title: "How to activate the fingerprint reader in 20.04"
date: 2020-04-29
forum: General Help
---

### Post by makem2 on 2020-04-29
DELL XPS 13 9300

```

makem@XPS-13-9300:~$ lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0bda:58fe Realtek Semiconductor Corp. Integrated_Webcam_HD
Bus 003 Device 002: ID 27c6:533c Shenzhen Goodix Technology Co.,Ltd. FingerPrint
Bus 003 Device 004: ID 8087:0026 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:000/CODE]2 Linux Foundation 2.0 root hub
makem@XPS-13-9300:~$

```

The fingerprint reader is inactive and the option to enable it in users is missing. It works in Windows 10.

[https://help.ubuntu.com/stable/ubuntu-help/session-fingerprint.html.en](https://help.ubuntu.com/stable/ubuntu-help/session-fingerprint.html.en)

I see packages fprintd, fprintd-doc and gir1.2-fprint-2.0 are available in the repo. However i read that Fingerprint GUI is no longer maintained and is not compatible with Ubuntu 20.04 and newer in this page:

[https://launchpad.net/~fingerprint/+archive/ubuntu/fingerprint-gui](https://launchpad.net/~fingerprint/+archive/ubuntu/fingerprint-gui)

Rather than mess up a new install on a new laptop, I ask for guidance before I dive in.

Has anyone got this working or can suggest which packages are needed?

---

### Post by CatKiller on 2020-04-29
[https://bartongeorge.io/2020/01/01/introducing-the-2020-xps-13-developer-edition-this-one-goes-to-32/](https://bartongeorge.io/2020/01/01/introducing-the-2020-xps-13-developer-edition-this-one-goes-to-32/)

> Fingerprint-reader support:  Another awaited feature is fingerprint-reader support.  While not available at launch, support will soon follow, first as an OTA (over-the-air) update and then as part of the preloaded image. 

---

### Post by makem2 on 2020-04-29
> **CatKiller said:**
> [https://bartongeorge.io/2020/01/01/introducing-the-2020-xps-13-developer-edition-this-one-goes-to-32/](https://bartongeorge.io/2020/01/01/introducing-the-2020-xps-13-developer-edition-this-one-goes-to-32/)


Thank you for that link.

DELL don't support 20.04 yet as far as I can see and they certainly don't support dual booted systems which I have. But your link explains perhaps why I cannot find any software.

So far that is the only thing I have come across which does not work, "out of the box" with 20.04 is the fingerprint log-in which is very convenient. I had a lot of problems with 18.04 until I gave up and tried the later version.

One little annoyance is screen flashing on, off, on when logging in and at other times.

Btw, my XPS is advertised as the NEW DELL XPS 13 and from there you can choose specs. The other 'XPS 13' is different,

---

