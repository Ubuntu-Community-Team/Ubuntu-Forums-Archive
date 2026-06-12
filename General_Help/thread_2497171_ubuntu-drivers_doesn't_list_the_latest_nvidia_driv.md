---
title: "ubuntu-drivers doesn't list the latest nvidia drivers after upgrading to 24.04"
date: 2024-04-25
forum: General Help
---

### Post by turan-mahmudov-l on 2024-04-25
Hey everyone,
I was using 23.10 and I had Nvidia 545 driver installed directly with `ubuntu-drivers install`, but after upgrading to Ubuntu 24.04 `ubuntu-drivers list` only lists drivers until 535. I see that `nvidia-driver-550` is in the repos and I can install it. But I wonder why `ubuntu-drivers` doesn't show it.

# ubuntu-drivers list
```

nvidia-driver-535-open, (kernel modules provided by linux-modules-nvidia-535-open-generic)
nvidia-driver-535-server-open, (kernel modules provided by linux-modules-nvidia-535-server-open-generic)
nvidia-driver-470, (kernel modules provided by linux-modules-nvidia-470-generic)
nvidia-driver-535, (kernel modules provided by linux-modules-nvidia-535-generic)
nvidia-driver-470-server, (kernel modules provided by linux-modules-nvidia-470-server-generic)
nvidia-driver-535-server, (kernel modules provided by linux-modules-nvidia-535-server-generic)

```

---

### Post by #&amp;thj^% on 2024-04-25
I had seen 545 back in development stage for Noble.
will it show here?
```
ubuntu-drivers devices
```

I'm one that uses the ppa:graphics-drivers/ppa, so that might be the difference

---

### Post by cm4w90c8 on 2024-04-29
I'm also not able to see or install the 550 version with ubuntu-drivers. Rather annoyingly, it says
```
$ sudo ubuntu-drivers install nvidia:550
udevadm hwdb is deprecated. Use systemd-hwdb instead.
udevadm hwdb is deprecated. Use systemd-hwdb instead.
udevadm hwdb is deprecated. Use systemd-hwdb instead.
udevadm hwdb is deprecated. Use systemd-hwdb instead.
udevadm hwdb is deprecated. Use systemd-hwdb instead.
All the available drivers are already installed.
```
but 550 doesn't show in the additional drivers list
```
$ ubuntu-drivers list
udevadm hwdb is deprecated. Use systemd-hwdb instead.
udevadm hwdb is deprecated. Use systemd-hwdb instead.
udevadm hwdb is deprecated. Use systemd-hwdb instead.
udevadm hwdb is deprecated. Use systemd-hwdb instead.
udevadm hwdb is deprecated. Use systemd-hwdb instead.
broadcom-sta-dkms, (kernel modules provided by broadcom-sta-dkms)
nvidia-driver-470, (kernel modules provided by linux-modules-nvidia-470-generic-hwe-24.04)
nvidia-driver-535-server, (kernel modules provided by linux-modules-nvidia-535-server-generic-hwe-24.04)
nvidia-driver-535, (kernel modules provided by linux-modules-nvidia-535-generic-hwe-24.04)
nvidia-driver-470-server, (kernel modules provided by linux-modules-nvidia-470-server-generic-hwe-24.04)
```

---

### Post by #&amp;thj^% on 2024-04-29
The only way to get or see the newer drivers is here: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
I'm one that knows how to fix my system and that said: I have found it very reliable since that PPA came to life.

WARNING: First remove/purge your current nvidia driver, before going with the new drivers listed on that site.

```
apt policy nvidia-driver-550
nvidia-driver-550:
  Installed: 550.78-0ubuntu0~gpu24.04.1
  Candidate: 550.78-0ubuntu0~gpu24.04.1
  Version table:
 *** 550.78-0ubuntu0~gpu24.04.1 500
        500 https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status
     550.67-0ubuntu3 500
        500 http://us.archive.ubuntu.com/ubuntu noble/restricted amd64 Packages

```

---

### Post by ubfan1 on 2024-05-01
Looks like launchpad bug [https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/2037004](https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/2037004)  Do add yourself to the "Does this affect me" list in the upper left corner (click on icon next to question).

---

### Post by #&amp;thj^% on 2024-05-01
I added to it as well after actually seeing it did not show for me as well.

Apologies for saying different in post # 4 and Post #2

---

### Post by MAFoElffen on 2024-05-01
> **ubfan1 said:**
> Looks like launchpad bug [https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/2037004](https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/2037004)  Do add yourself to the "Does this affect me" list in the upper left corner (click on icon next to question).

LOL. That's exactly what I was going to say. This bug needs to be resolved so that it works for "everyone". That's just the right thing to do.

---

### Post by #&amp;thj^% on 2024-05-02
+1 for the bug report, I just never use ubuntu-driver anything...instead I use:
```
 apt list nvidia-driver*
Listing... Done
nvidia-driver-390/noble 390.157-0ubuntu7 amd64
nvidia-driver-460-server/noble 470.239.06-0ubuntu2 amd64
nvidia-driver-460/noble 470.239.06-0ubuntu2 amd64
nvidia-driver-465/noble 470.239.06-0ubuntu2 amd64
nvidia-driver-470-server/noble 470.239.06-0ubuntu2 amd64
nvidia-driver-470/noble 470.239.06-0ubuntu2 amd64
nvidia-driver-510/noble 525.147.05-0ubuntu2 amd64
nvidia-driver-515-open/noble 525.147.05-0ubuntu2 amd64
nvidia-driver-515-server/noble 525.147.05-0ubuntu2 amd64
nvidia-driver-515/noble 525.147.05-0ubuntu2 amd64
nvidia-driver-520-open/noble 525.147.05-0ubuntu2 amd64
nvidia-driver-520/noble 525.147.05-0ubuntu2 amd64
nvidia-driver-525-open/noble 525.147.05-0ubuntu2 amd64
nvidia-driver-525-server/noble 525.147.05-0ubuntu2 amd64
nvidia-driver-525/noble 525.147.05-0ubuntu2 amd64
nvidia-driver-530-open/noble 535.171.04-0ubuntu2 amd64
nvidia-driver-530/noble 535.171.04-0ubuntu2 amd64
nvidia-driver-535-open/noble 535.171.04-0ubuntu2 amd64
nvidia-driver-535-server-open/noble 535.161.08-0ubuntu2 amd64
nvidia-driver-535-server/noble 535.161.08-0ubuntu2 amd64
nvidia-driver-535/noble 535.171.04-0ubuntu2 amd64
nvidia-driver-545-open/noble 545.29.06-0ubuntu0~gpu24.04.1 amd64
nvidia-driver-545/noble 545.29.06-0ubuntu0~gpu24.04.1 amd64
nvidia-driver-550-open/noble 550.78-0ubuntu0~gpu24.04.1 amd64
nvidia-driver-550-server-open/noble 550.54.15-0ubuntu2 amd64
nvidia-driver-550-server/noble 550.54.15-0ubuntu2 amd64
nvidia-driver-550/noble,now 550.78-0ubuntu0~gpu24.04.1 amd64 [installed]

```

---

### Post by den_ on 2024-05-25
But you can install 550 driver with apt?

---

### Post by den_ on 2024-05-25
> **1fallen said:**
> The only way to get or see the newer drivers is here: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
I'm one that knows how to fix my system and that said: I have found it very reliable since that PPA came to life.

WARNING: First remove/purge your current nvidia driver, before going with the new drivers listed on that site.

```
apt policy nvidia-driver-550
nvidia-driver-550:
  Installed: 550.78-0ubuntu0~gpu24.04.1
  Candidate: 550.78-0ubuntu0~gpu24.04.1
  Version table:
 *** 550.78-0ubuntu0~gpu24.04.1 500
        500 https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status
     550.67-0ubuntu3 500
        500 http://us.archive.ubuntu.com/ubuntu noble/restricted amd64 Packages

```

This is wrong. ubuntu-drivers list and Software & Updates -> Additional Drivers don't list newer drivers, but apt does. One can normally install say 550 driver with apt and everything appears to work well. So, why would one add the PPA?

---

### Post by #&amp;thj^% on 2024-05-25
You did see I corrected that Right?
And the PPA is a personal choice, I've used since it came to life.
To each their own....
Regards

---

### Post by den_ on 2024-05-25
> **1fallen said:**
> You did see I corrected that Right?
And the PPA is a personal choice, I've used since it came to life.
To each their own....
Regards

no I obviously didn't see that you have corrected, otherwise I wouldn't have replied. Re PPA, I mean I personally don't understand why use it in this case, but it's not that I am like against PPAs (Or that specific one). If you like the PPA sure, be my guest.

---

