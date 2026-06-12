---
title: "Lubuntu 18.04: Updating to Linux 4.15.0-108-generic (x86_64) caused boot issue"
date: 2020-06-24
forum: General Help
---

### Post by ardouronerous on 2020-06-24
Running Lubuntu 18.04.

I got the updates:

```
Install: linux-headers-4.15.0-108-generic:amd64 (4.15.0-108.109, automatic), linux-modules-4.15.0-108-generic:amd64 (4.15.0-108.109, automatic), linux-image-4.15.0-108-generic:amd64 (4.15.0-108.109, automatic), linux-modules-extra-4.15.0-108-generic:amd64 (4.15.0-108.109, automatic), linux-headers-4.15.0-108:amd64 (4.15.0-108.109, automatic)
Upgrade: linux-headers-generic:amd64 (4.15.0.106.94, 4.15.0.108.96), linux-libc-dev:amd64 (4.15.0-106.107, 4.15.0-108.109), libcurl4:amd64 (7.58.0-2ubuntu3.8, 7.58.0-2ubuntu3.9), linux-image-generic:amd64 (4.15.0.106.94, 4.15.0.108.96), linux-generic:amd64 (4.15.0.106.94, 4.15.0.108.96), libcurl3-gnutls:amd64 (7.58.0-2ubuntu3.8, 7.58.0-2ubuntu3.9)
```

After installing these updates, I got a prompt to restart, and so I did, but upon restarting, my system didn't boot. I heard my USB speakers pop, which usually happens whenever I boot my system, but after that, all I got was a black screen with nothing on it. After a couple of minutes, I long pressed the power button on my laptop and started it up again, and this time, it booted. Upon reaching the desktop, I was greeted with a "system program problem detected" message, in which I clicked to "report problem."

I'm using the laptop right now to report this issue and so far, I'm not getting any performance issues with my laptop.

I just want to know what caused the not booting issue after updating the kernel and restarting. Thanks.

---

### Post by poorguy on 2020-06-24
I've used Lubuntu since the days of Lubuntu 14.04 and have had the same thing happen more than once after kernel updates.

 I never figured out what happened or why it happens it just seems to happen sometimes and as long as it's working I never worried about it.

With some kernel updates I've had to revert back to an existing working kernel until a patch came about so it's always good to keep a last working kernel around.

I'm using Lubuntu 20.04 and have had a couple of kernel updates and so far haven't experienced any problems after kernel updates.

---

### Post by ardouronerous on 2020-06-24
Thanks for the reply.

Well, this is the first time this has ever happened to me, and I've been using Lubuntu since 12.04, so it kinda spooked me because my initial reaction was the kernel update bricked my system, something that I heard can happen.

Thanks for the advice on keeping old kernels handy.

---

### Post by Bashing-om on 2020-06-25
ardouronerous; Hello -

as to:
> 
I just want to know what caused the not booting issue after updating the kernel and restarting.


see what is in the directory:
```

ls -al /var/crash/

```

Nvidia graphics ? where the module did not build for the new kernel is but one likely source,

[INDENT][INDENT]maybe yes
[INDENT][INDENT]could be not so yes
[/INDENT][/INDENT][/INDENT][/INDENT]

---

