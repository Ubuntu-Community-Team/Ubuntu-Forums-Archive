---
title: "[lubuntu] Unable to install Kile"
date: 2021-08-04
forum: General Help
---

### Post by RyanGates on 2021-08-04
How can I install [Kile]("https://kile.sourceforge.io/") on Lubuntu(Ubuntu 16.04.7 LTS) ? 

I have tried both
[LIST=1]
[*]Installing via Lubuntu Software Center Version 0.0.10 
[*]Installing via LXTerminal 0.2.0 with the command ```
sudo apt install kile
``` 
[/LIST]

However in both cases I get the below errors.

```

Failed to fetch [https://esm.ubuntu.com/infra/ubuntu/pool/main/e/exiv2/libexiv2-14_0.25-2.1ubuntu16.04.7+esm3_amd64.deb](https://esm.ubuntu.com/infra/ubuntu/pool/main/e/exiv2/libexiv2-14_0.25-2.1ubuntu16.04.7+esm3_amd64.deb) 401  Unauthorized
Failed to fetch [https://esm.ubuntu.com/infra/ubuntu/pool/main/libx/libxml2/libxml2-utils_2.9.3+dfsg1-1ubuntu0.7+esm1_amd64.deb](https://esm.ubuntu.com/infra/ubuntu/pool/main/libx/libxml2/libxml2-utils_2.9.3+dfsg1-1ubuntu0.7+esm1_amd64.deb) 401  Unauthorized
Failed to fetch [https://esm.ubuntu.com/infra/ubuntu/pool/main/r/ruby2.3/ruby2.3_2.3.1-2~ubuntu16.04.16+esm1_amd64.deb](https://esm.ubuntu.com/infra/ubuntu/pool/main/r/ruby2.3/ruby2.3_2.3.1-2~ubuntu16.04.16+esm1_amd64.deb) 401  Unauthorized
Failed to fetch [https://esm.ubuntu.com/infra/ubuntu/pool/main/r/ruby2.3/libruby2.3_2.3.1-2~ubuntu16.04.16+esm1_amd64.deb](https://esm.ubuntu.com/infra/ubuntu/pool/main/r/ruby2.3/libruby2.3_2.3.1-2~ubuntu16.04.16+esm1_amd64.deb) 401  Unauthorized

```

---

### Post by grahammechanical on 2021-08-04
Have you applied Canonical's Extended Security Maintenance (ESM) to this install of Lubuntu? I see that the installer is attempting to download Kile from the esm.ubuntu.com repository. It would be my guess that the only packages in the esm repository are those packages that are likely to be affected by security issues.

I would also guess that the way to download and install Kile is to edit the /etc/apt/sources.list file and add the standard Ubuntu repositories such as universe. They made be still in your sources.list file but commented with a #

Regards

---

### Post by deadflowr on 2021-08-04
Have you set up Ubuntu Advantage and grabbed the token yet?
[https://discourse.ubuntu.com/t/ubuntu-advantage-client/21788]("https://discourse.ubuntu.com/t/ubuntu-advantage-client/21788")

---

### Post by guiverc on 2021-08-05
Lubuntu packages reached for *xenial* or 16.04 reached EOL in 2019-April, and none of those are supported via ESM, so switch to using a server (no GUI) or Unity 7 (Ubuntu's desktop) as those are the only options supported for the five years, and ESM.

`kile` however is a package that ended support in 2019-April as it was community supported.

 ```
kile | 4:2.1.3-3ubuntu1   | xenial/universe          | source, amd64, arm64, armhf, i386, powerpc, ppc64el, s390x

```

---

### Post by RyanGates on 2021-10-27
Thank you for everyone's advice and assistance. I ended up installing [Lubuntu 20.04]("https://lubuntu.me/focal-released/") and after that I was able to install Kile through the Software Center and get it working.

---

### Post by ActionParsnip on 2021-10-27
> **RyanGates said:**
> Thank you for everyone's advice and assistance. I ended up installing [Lubuntu 20.04]("https://lubuntu.me/focal-released/") and after that I was able to install Kile through the Software Center and get it working.

This will also allow you to upgrade directly to 22.04 in April next year (LTS to LTS upgrade)

---

