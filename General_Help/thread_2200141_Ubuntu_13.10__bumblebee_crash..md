---
title: "Ubuntu 13.10  bumblebee crash."
date: 2014-01-17
forum: General Help
---

### Post by kuckunniwi on 2014-01-17
Just installed bumblebee on Kubuntu 13.10.

Removed nouveau via 

```
sudo apt-get --purge remove xserver-xorg-video-nouveau
```

Then added bumblebee via ppa:bumblebee/stable

```
sudo apt-get install bumblebee bumblebee-nvidia virtualgl linux-headers-generic
```

Process froze in the middle of initramfs. Had to force shutdown, and now, can no longer log-in. Get message:

```
 Gave up waiting for root device. Common problems.

   - Boot args (cat /proc/cmdline)
        -Check rootdelay= (did the system wait long long enough?)
        -Check root= (did the system wait for the right device?)
   -Missing modules (cat /proc/modules; ls /dev)

ALERT /dev/disk&by-uuid/c5139233.d70f-4af3-b53C-f724b20e9b62 does not exist. Dropping to a shell!

Busybox v.120.2 (Ubuntu 1:1.20.0-8.1ubuntu1) built-in shell!
enter 'help' for list of built-in commands

(initramfs) 
```

Is there any way this can be fixed via Live-CD, without re-installing? I just did a fresh install a few days ago, and after installing all software, configuring apps and virtual desktops, icons, configs, etc., 

I can get as far as login screen using a previous kernel, but upon entering password, screen flickers and I'm sent back to log-in screen. Any ideas?

Thanks a ton!

---

