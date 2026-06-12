---
title: "Unresponsive Unity on USB SSD"
date: 2016-05-28
forum: General Help
---

### Post by mika10 on 2016-05-28
Unity and application menus are randomly unresponsive, and it can take up to few second before the opened menu pops up.  During this Unity pauses, the video playback is not affected. Also the mouse move isn't affected. It's just like the interaction with the Unity is delayed.

Sometimes, if I press add tabs button on Firefox nothing happens. I press again, and few seconds later two new tabs will open. :confused:

I have Ubuntu 16.04 installed on Intenso External Solid State Drive USB 3.0. Previously I was using Ubuntu 15.10 on Transcend USB 3.0 memory stick without any problems.

I have created few tmpfs filesystems:

```

Filesystem              Size  Used Avail Use% Mounted on
udev                    7,9G     0  7,9G   0% /dev
tmpfs                   1,6G   18M  1,6G   2% /run
/dev/mapper/sdc5_crypt  113G   17G   91G  16% /
tmpfs                   7,9G  306M  7,6G   4% /dev/shm
tmpfs                   5,0M  4,0K  5,0M   1% /run/lock
tmpfs                   7,9G     0  7,9G   0% /sys/fs/cgroup
tmpfs                    10G  104K   10G   1% /var/tmp
tmpfs                    10G  152M  9,9G   2% /var/cache
tmpfs                    10G  655M  9,4G   7% /home/mika/.cache
tmpfs                    10G  367M  9,7G   4% /tmp
/dev/sdc1               453M  104M  322M  25% /boot
tmpfs                   1,6G   84K  1,6G   1% /run/user/1000

```

I have created a launcher which copies /opt/google/chrome into /home/mika/.cache/tmpfs/ and executes it from there.
The previous also with the Firefox.

My PC:
cpu i7-2600K
mem 16GB
gpu GTX 980 (Ubuntu additional driver: NVIDIA binary 361.42 with Ubuntu CUDA packages)


Any advice on how to improve the system responsiveness on USB? :popcorn:

---

