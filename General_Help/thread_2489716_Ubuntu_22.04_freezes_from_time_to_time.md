---
title: "Ubuntu 22.04 freezes from time to time"
date: 2023-08-08
forum: General Help
---

### Post by satimis on 2023-08-08
Hi all,

Ubuntu 22.04 VM

On Terminal run;
$ sudo apt update ; sudo apt upgrade```

........
.......
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  libpostproc55 libavcodec58 libavutil56 libswscale5 libswresample3
  libavformat58 libavfilter7
Learn more about Ubuntu Pro at https://ubuntu.com/pro
....
....

```

Then I found following URL;
While updating packages: "Get more security upgrades through Ubuntu Pro with 'esm-apps' enabled"
[https://www.reddit.com/r/pop_os/comments/12ui24h/while_updating_packages_get_more_security/?rdt=59592&onetap_auto=true](https://www.reddit.com/r/pop_os/comments/12ui24h/while_updating_packages_get_more_security/?rdt=59592&onetap_auto=true)

According to the post of Chaos_Blades
(3 mo. ago)```

None of these commands worked for me except for sudo rm /etc/apt/apt.conf.d/20apt-esm-hook.conf

```

On Terminal I ran```

$ sudo rm /etc/apt/apt.conf.d/20apt-esm-hook.conf

```

Now the problem gone.
$ sudo apt update ; sudo apt upgrade```

Hit:1 http://hk.archive.ubuntu.com/ubuntu jammy InRelease
Hit:2 http://archive.ubuntu.com/ubuntu jammy-proposed InRelease
Hit:3 http://security.ubuntu.com/ubuntu jammy-security InRelease
Hit:4 http://hk.archive.ubuntu.com/ubuntu jammy-updates InRelease
Hit:5 http://hk.archive.ubuntu.com/ubuntu jammy-backports InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up to date.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I don't know WHY?  Please help me to understand it?

Besides Ubuntu 22.04 freezes occasionly on running the browser, both Chrome and Firefox.

Thanks

Regards

---

