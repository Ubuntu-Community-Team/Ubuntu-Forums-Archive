---
title: "disk full after usage of script that used a default cache directory"
date: 2021-07-19
forum: General Help
---

### Post by moowii on 2021-07-19
i want to delete the cache so i can continue to use my server. as of now, there seems to be no space left for the OS and docker apps. somehow i am not able to find the cache directory which causes the problem.

```
df -h
df: /mnt/gdrive-media-crypt: Transport endpoint is not connected
Filesystem                         Size  Used Avail Use% Mounted on
udev                               7.8G     0  7.8G   0% /dev
tmpfs                              1.6G  166M  1.4G  11% /run
/dev/mapper/ubuntu--vg-ubuntu--lv  125G  125G     0 100% /
tmpfs                              7.8G     0  7.8G   0% /dev/shm
tmpfs                              5.0M     0  5.0M   0% /run/lock
tmpfs                              7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/sda2                          976M  107M  802M  12% /boot
/dev/sda1                          511M  7.9M  504M   2% /boot/efi
/dev/sdb2                          129G  126M  123G   1% /metadata
/dev/sdb1                          328G   69M  311G   1% /plex
/dev/sdc1                          916G  149G  721G  18% /gmedia/local
/dev/loop2                          68M   68M     0 100% /snap/lxd/20326
/dev/loop0                          56M   56M     0 100% /snap/core18/1944
/dev/loop3                          56M   56M     0 100% /snap/core18/2074
/dev/loop1                          70M   70M     0 100% /snap/lxd/19188
/dev/loop4                          33M   33M     0 100% /snap/snapd/12398
/dev/loop6                          32M   32M     0 100% /snap/snapd/10707
/dev/loop5                         1.2G  1.2G     0 100% /snap/root-framework/232
/dev/loop7                          62M   62M     0 100% /snap/core20/1026
gdrive:                            1.1P   55G  1.0P   1% /mnt/gmedia-cloud-old
overlay                            125G  125G     0 100% /var/lib/docker/overlay2/622f6c1d2f323cd2d397ff5058d2715e4867f6a5386b23922fa86d541c3d91aa/merged
overlay                            125G  125G     0 100% /var/lib/docker/overlay2/522ff8198c5e389d02b63066f5347de5b4bc2fad57b8ef93f24b73527c1641ed/merged
overlay                            125G  125G     0 100% /var/lib/docker/overlay2/b7f820c62852246904db68b3cfa2659e3f9d99e0512ec552d3d32e318f43d60a/merged
overlay                            125G  125G     0 100% /var/lib/docker/overlay2/81f4632389e7965d13b5b6c4f2b0529b16dc40d88d35456da99b3723a420b88a/merged
overlay                            125G  125G     0 100% /var/lib/docker/overlay2/e0948df8df8c4bf09c0e1e7c583e08b30f15828cc561cdcd37f0c47898474e59/merged
gdrive-media-crypt:                1.1P   55G  1.0P   1% /mnt/gmedia-cloud
overlay                            125G  125G     0 100% /var/lib/docker/overlay2/657e77efb6c2511c498df25bc5daaeb4b725828beb8df611d9f2f8db41f65d28/merged
overlay                            125G  125G     0 100% /var/lib/docker/overlay2/746f5e903ccde51507b41d2674a65d07e13b1d9dd03fbf9ea56a5e07f9fb2a23/merged
overlay                            125G  125G     0 100% /var/lib/docker/overlay2/cce396d93b00be5bc82531dd47ff4b45d3eac4726ba445d29f3f176bd38770b8/merged
overlay                            125G  125G     0 100% /var/lib/docker/overlay2/0ab27d7d5182488553449757500a0322fd8781bb48072e81508eded0be6201dc/merged
tmpfs                              1.6G     0  1.6G   0% /run/user/1000
gdrive-media-crypt:                1.1P   55G  1.0P   1% /mnt/gdrive-media-krypt
overlay                            125G  125G     0 100% /var/lib/docker/overlay2/faef83f62de9ba011f13db0e072b66c5ae42c1410399681b0b736b899de59961/merged
overlay                            125G  125G     0 100% /var/lib/docker/overlay2/b691f8d506d782cf9933c8c3c609a449b5fe40342f47e3be5c7683ea916f1726/merged

```

do you guys have any tips for this?

---

### Post by sudodus on 2021-07-19
You can check at the top level (mountpoint) of each file system (partition) with the following command

```

sudo du -h * .[a-Z]* | sort -h

```

The biggest directories will be shown at the tail end of the list.

---

### Post by TheFu on 2021-07-19
Check in your HOME directory.

---

