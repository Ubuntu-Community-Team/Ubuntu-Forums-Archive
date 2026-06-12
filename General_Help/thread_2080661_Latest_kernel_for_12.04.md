---
title: "Latest kernel for 12.04?"
date: 2012-11-04
forum: General Help
---

### Post by Nutria on 2012-11-04
Hi,

According to [https://wiki.ubuntu.com/Kernel/Release/Rolling](https://wiki.ubuntu.com/Kernel/Release/Rolling) 12.04LTS should now also have the v3.5 kernel used in 12.10.

So, I'm wondering when (or if) it'll sow up in the official repository.

Ron

---

### Post by gordintoronto on 2012-11-04
> **Nutria said:**
> Hi,

According to [https://wiki.ubuntu.com/Kernel/Release/Rolling](https://wiki.ubuntu.com/Kernel/Release/Rolling) 12.04LTS should now also have the v3.5 kernel used in 12.10.

So, I'm wondering when (or if) it'll sow up in the official repository.

Ron

Have you tried installing linux-image-current?

---

### Post by Yellow Pasque on 2012-11-04
It's in the precise-proposed repo.

---

### Post by Nutria on 2012-11-04
> **gordintoronto said:**
> Have you tried installing linux-image-current?

There is no linux-image-current
```
$ apt-cache policy linux-image-current
N: Unable to locate package linux-image-current

```

```
$ apt-cache policy linux-image-current-generic
linux-image-current-generic:
  Installed: (none)
  Candidate: 3.2.0.32.35
  Version table:
     3.2.0.32.35 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/main amd64 Packages
```

Anyway, the closest packange name to linux-image-current is even older than what I have currently installed.

```
$ dpkg -l | grep linux-image | cut -c-70
rc  linux-image-3.2.0-29-generic                      3.2.0-29.46     
rc  linux-image-3.2.0-30-generic                      3.2.0-30.48     
rc  linux-image-3.2.0-31-generic                      3.2.0-31.50     
[COLOR="RoyalBlue"]ii  linux-image-3.2.0-32-generic                      3.2.0-32.51[/COLOR]     
[COLOR="Red"]ii  linux-image-generic                               3.2.0.32.35 [/COLOR]  
```

---

### Post by Nutria on 2012-11-04
> **Temüjin said:**
> It's in the precise-proposed repo.

Thanks.

How do I discern which [http://kernel.org/](http://kernel.org/) v3.5 kernel that 3.5.0.18.24 relates to?

---

### Post by pqwoerituytrueiwoq on 2012-11-04
i will point out that the 3.5 kernel is eol upstream
that said if you want the latest mainline kernel here is a installer/update checker

---

### Post by gordintoronto on 2012-11-05
> **Temüjin said:**
> It's in the precise-proposed repo.

Interesting. When I looked at the Properties using Synaptic, it said it is in precise-updates.

---

