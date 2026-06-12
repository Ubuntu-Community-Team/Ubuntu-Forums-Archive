---
title: "Any k3b .deb out there for Ubuntu 7.04?"
date: 2008-03-03
forum: General Help
---

### Post by s3a on 2008-03-03
Is there any k3b .deb out there for Feisty that won't go ask for an internet connection to download dependencies or, can someone help me use apt-zip to bring it over to my non-networked Ubuntu 7.04 computer by using a usb flash drive?

Thanks in advance!

---

### Post by jeffus_il on 2008-03-03
This may work.

Download the source package from here:
[http://archive.ubuntu.com/ubuntu/pool/main/k/k3b/k3b_1.0.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/main/k/k3b/k3b_1.0.orig.tar.gz)

Burn it to a CD

Run Synaptic.
In Settings->Repositories->Third Party Software
Choose "Add CDROM"

Place the CD in the drive.

Post us the result.

And if you're interested read this:
[https://wiki.ubuntu.com/AddLocalRepositorySpec](https://wiki.ubuntu.com/AddLocalRepositorySpec)

---

