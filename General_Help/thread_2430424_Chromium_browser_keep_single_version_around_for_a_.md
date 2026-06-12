---
title: "Chromium browser: keep single version around for a long time"
date: 2019-11-01
forum: General Help
---

### Post by whyscream on 2019-11-01
For a kiosk application we use a webpage as interface. This is displayed to users in a kiosk-configured chromium-browser. Every now and then, this breaks because the version of chromium in ubuntu is not stable: a newer version is released every few weeks. In newer versions, the command line switches that enforce the kiosk mode, keep changing (we need kiosk mode and other features like suppressing first-run dialog, startup errors etc).

The application is fully contained in the device, the browser doesn't access public internet. What is the best way to pin chromium to a specific version that we can keep using for a prolonged time. We tried to use pinning, but older versions of the browser are removed from the ubuntu repositories after some time. For my Xenial-based image, I can only use the current version (77.0.3865.90-0ubuntu0.16.04.1) and the release version (49.0.2623.108-0ubuntu1.1233, from 2016). Next month, the 'current' version will be changed, so the only stable version of the package I can use is 3 years old.

Are there any other good solutions for pinning a version of chromium-browser for a prolonged time?

---

### Post by TheFu on 2019-11-01
For a 100% self-contained system, Ubuntu is a huge amount of bloat.  For a Kiosk, check out the tinycore distro.

---

### Post by whyscream on 2019-11-01
We adopted the project and it was already based on ubuntu. We also need to support a rather long of exotic hardware that is connected to the machine. Rebuilding the image has been on our wishlist for some time, but the customer doesn't seem interested in (paying for) it. So for now I'm stuck with what I have. Question still stands

---

### Post by sdsurfer on 2019-11-01
Does this help?

> Google Chrome and Chromium are not auto-updated automatically on Linux; your package manager handles this.

[https://www.chromium.org/administrators/turning-off-auto-updates](https://www.chromium.org/administrators/turning-off-auto-updates)

---

### Post by dragonfly41 on 2019-11-01
> **whyscream said:**
> Are there any other good solutions for pinning a version of chromium-browser for a prolonged time?

Electron apps are based on a version of chromium-browser. Would Electron work for you? Explore Electron and Node.js.
I use Atom editor which can create Electron apps.

---

### Post by SeijiSensei on 2019-11-01
You can keep a package from being updated via apt with 
```

sudo apt-mark hold packagename

```

---

### Post by TheFu on 2019-11-01
> **whyscream said:**
> We adopted the project and it was already based on ubuntu. We also need to support a rather long of exotic hardware that is connected to the machine. Rebuilding the image has been on our wishlist for some time, but the customer doesn't seem interested in (paying for) it. So for now I'm stuck with what I have. Question still stands

If the system is self-contained, just don't run **apt** and no packages will be updated. If it must be on the internet, perhaps for remote data transmission, disable all automatic APT stuff and perhaps disable the network adaptors except during scheduled remote connection times.  Blocking all HTTP, HTTPS, FTP, rsync and other file transfer traffic in the firewall woudn't hurt.  
Or lock down the external subnets that the networking allows to only those which you control. That's inbound AND outbound.

BTW, if you update the rest of the system, but not Chromium, it is highly likely that dependency issues will arise.

SeijiSensei has provided the command to hold a package.

---

