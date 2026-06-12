---
title: "no login after kernel update?"
date: 2015-04-10
forum: General Help
---

### Post by fernando46 on 2015-04-10
Hi.
I'm new here; greetings to you all! I hope you can help me with a little (!) problem I'm having here...
The thing is as follows: I'm running (or was) Kubuntu 14.10 and recently updated the kernels; to do so, I previously manually deleted all the old ones (but the current one) from /boot. Then I updated and something must have gone awfully wrong, because now I can't log in. The system freezes at the login screen and I can't even write my password. No mouse, no keyboard, nothing.
If I try lo start with a live CD and I run Partition Manager, I can see:

Partition     Type             Mount Point                Label                Size            Used                          Flag
/dev/sda1         Fat32                                                                                          512.00 MiB         3.36 MiB
/dev/sda2          ext2                                                                                              244.00 MiB        79.59 MiB
/dev/sda3          unknown                                                                                  465.02 GiB                                 ---             lvm

I'm worried about /dev/sda3 type being unknown and also the fact that it's shown as unused, but I'm not sure that's what's stopping me from login.
I really need to fix the system. Any help would be much appreciated.
Thanks!

---

### Post by fernando46 on 2015-04-10
Damn! I don't know how to properly show the partition's info!

---

### Post by fernando46 on 2015-04-10
After a brief investigation, it seems that there can be video issues related to the kernel. Could one of those be the problem here?

---

