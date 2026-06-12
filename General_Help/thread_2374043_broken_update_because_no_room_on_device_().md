---
title: "broken update because no room on device (?)"
date: 2017-10-12
forum: General Help
---

### Post by matrooswolf on 2017-10-12
Hi everybody,

I updated my packages yesterday but I got an error with the unpacking of linux-headers saying "no more space on device" and "no apport-report is written because disk is full". But on my home I have 1,1 GB free space, and on / I have 1,8 GB free space. Isn't that enough? And if it is, is there another problem?

I tried ```
sudo apt-get install -f
```
But this is what i get:

```
Bezig met uitpakken van linux-headers-4.4.0-97 (4.4.0-97.120) ...
dpkg: fout bij verwerken van archief /var/cache/apt/archives/linux-headers-4.4.0-97_4.4.0-97.120_all.deb (--unpack):
 kan '/usr/src/linux-headers-4.4.0-97/arch/frv/include/asm/kmap_types.h.dpkg-new' niet aanmaken (bij het verwerken van './usr/src/linux-headers-4.4.0-97/arch/frv/include/asm/kmap_types.h'): Geen ruimte meer over op apparaat
Er is geen apport-verslag weggeschreven omdat de foutmelding als oorzaak een volle schijf opgeeft.
                  dpkg-deb: fout: subproces plakken werd gedood door signaal (Gebroken pijp)
Uitpakken van .../linux-headers-4.4.0-97-generic_4.4.0-97.120_amd64.deb wordt voorbereid...
Bezig met uitpakken van linux-headers-4.4.0-97-generic (4.4.0-97.120) ...
dpkg: fout bij verwerken van archief /var/cache/apt/archives/linux-headers-4.4.0-97-generic_4.4.0-97.120_amd64.deb (--unpack):
 kan '/usr/src/linux-headers-4.4.0-97-generic/include/config/media/tuner/mt2266.h.dpkg-new' niet aanmaken (bij het verwerken van './usr/src/linux-headers-4.4.0-97-generic/include/config/media/tuner/mt2266.h'): Geen ruimte meer over op apparaat
Er is geen apport-verslag weggeschreven omdat de foutmelding als oorzaak een volle schijf opgeeft.
                  Fouten gevonden tijdens verwerken van:
 /var/cache/apt/archives/linux-headers-4.4.0-97_4.4.0-97.120_all.deb
 /var/cache/apt/archives/linux-headers-4.4.0-97-generic_4.4.0-97.120_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Impavidus on 2017-10-12
1.8GB free space isn't much, but should give enough headroom to install the packages. You may also have run out of inodes. Post this:```
df
df -i
dpkg --list | grep linux-
```It will show disk space usage, inode usage and a list of installed kernel and header packages. You may have to uninstall old kernels or headers, but if you ran out of disk space or inodes, there may not be enough headroom for apt autoremove to work.

Also, which version of Ubuntu?

Edit: As noted below, you can be nice to other forum users and provide english output. Although personally I don't mind reading messages in my native language. They're standard messages anyway.

---

### Post by vasa1 on 2017-10-12
You can prefix LANG=C before each of the commands provided by Impavidus or any other commands to ensure output in English.```
LANG=C df
LANG=C df -i
LANG=C dpkg --list | grep linux-
```

---

### Post by matrooswolf on 2017-10-14
Hi Vasa1 and Impavidus,

I deleted some old kernels through Synaptics and now have 2,6 GB free space on / which seems enough because the problem fixed itself.

It ran the commands, before I did that, but I forgot to copy them at that time. Below they are as they are now. It could be that on /dev/sda2 IUSE was at 100% instead of 98% (but I'm not certain...)

Also there are a lot of old kernels listed in the last command, but I cannot find them in Synaptics. Are they still on my system? And if so, is there another way to remove them than through Synaptics?

Here's the response to ```
LANG=C df

Filesystem     1K-blocks      Used Available Use% Mounted on
udev             1941020         0   1941020   0% /dev
tmpfs             392280      6380    385900   2% /run
/dev/sda2       19295520  15713728   2578580  86% /
tmpfs            1961396       344   1961052   1% /dev/shm
tmpfs               5120         4      5116   1% /run/lock
tmpfs            1961396         0   1961396   0% /sys/fs/cgroup
/dev/sda5      240186888 226861112   1101932 100% /home
cgmfs                100         0       100   0% /run/cgmanager/fs
tmpfs             392280        76    392204   1% /run/user/1000

```
```
LANG=C df -i

Filesystem       Inodes   IUsed    IFree IUse% Mounted on
udev             485255     545   484710    1% /dev
tmpfs            490349     812   489537    1% /run
/dev/sda2       1234576 1208531    26045   98% /
tmpfs            490349      25   490324    1% /dev/shm
tmpfs            490349       4   490345    1% /run/lock
tmpfs            490349      18   490331    1% /sys/fs/cgroup
/dev/sda5      15261696   92253 15169443    1% /home
cgmfs            490349      14   490335    1% /run/cgmanager/fs
tmpfs            490349      37   490312    1% /run/user/1000

```
```
LANG=C dpkg --list | grep linux-

              4.0ubuntu1                                   all          Linux image base package
ii  linux-firmware                                              1.157.12                                     all          Firmware for Linux kernel drivers
ii  linux-headers-3.13.0-24                                     3.13.0-24.47                                 all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-27                                     3.13.0-27.50                                 all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-29                                     3.13.0-29.53                                 all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-30                                     3.13.0-30.55                                 all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-32                                     3.13.0-32.57                                 all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-32-generic                             3.13.0-32.57                                 amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-34                                     3.13.0-34.60                                 all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic                             3.13.0-34.60                                 amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-36                                     3.13.0-36.63                                 all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-36-generic                             3.13.0-36.63                                 amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-39                                     3.13.0-39.66                                 all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-39-generic                             3.13.0-39.66                                 amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-44                                     3.13.0-44.73                                 all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-45                                     3.13.0-45.74                                 all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-45-generic                             3.13.0-45.74                                 amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-49                                     3.13.0-49.83                                 all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-49-generic                             3.13.0-49.83                                 amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-52                                     3.13.0-52.86                                 all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-53                                     3.13.0-53.89                                 all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-53-generic                             3.13.0-53.89                                 amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-57                                     3.13.0-57.95                                 all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-57-generic                             3.13.0-57.95                                 amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-58                                     3.13.0-58.97                                 all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-61                                     3.13.0-61.100                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-65                                     3.13.0-65.106                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-65-generic                             3.13.0-65.106                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-68                                     3.13.0-68.111                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-4.4.0-62                                      4.4.0-62.83                                  all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-62-generic                              4.4.0-62.83                                  amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-63                                      4.4.0-63.84                                  all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-63-generic                              4.4.0-63.84                                  amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-64                                      4.4.0-64.85                                  all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-64-generic                              4.4.0-64.85                                  amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-66                                      4.4.0-66.87                                  all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-66-generic                              4.4.0-66.87                                  amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-67                                      4.4.0-67.88                                  all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-67-generic                              4.4.0-67.88                                  amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-70                                      4.4.0-70.91                                  all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-70-generic                              4.4.0-70.91                                  amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-71                                      4.4.0-71.92                                  all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-71-generic                              4.4.0-71.92                                  amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-72                                      4.4.0-72.93                                  all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-72-generic                              4.4.0-72.93                                  amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-75                                      4.4.0-75.96                                  all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-75-generic                              4.4.0-75.96                                  amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-77                                      4.4.0-77.98                                  all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-77-generic                              4.4.0-77.98                                  amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-78                                      4.4.0-78.99                                  all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-78-generic                              4.4.0-78.99                                  amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-79                                      4.4.0-79.100                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-79-generic                              4.4.0-79.100                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-83                                      4.4.0-83.106                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-83-generic                              4.4.0-83.106                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-87                                      4.4.0-87.110                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-87-generic                              4.4.0-87.110                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-89                                      4.4.0-89.112                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-89-generic                              4.4.0-89.112                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-91                                      4.4.0-91.114                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-91-generic                              4.4.0-91.114                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-92                                      4.4.0-92.115                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-92-generic                              4.4.0-92.115                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-93                                      4.4.0-93.116                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-93-generic                              4.4.0-93.116                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-96                                      4.4.0-96.119                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-96-generic                              4.4.0-96.119                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-12-generic                               3.11.0-12.19                                 amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-13-generic                               3.11.0-13.20                                 amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-14-generic                               3.11.0-14.21                                 amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-15-generic                               3.11.0-15.25                                 amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-17-generic                               3.11.0-17.31                                 amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-18-generic                               3.11.0-18.32                                 amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-19-generic                               3.11.0-19.33                                 amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-106-generic                              3.13.0-106.153                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-107-generic                              3.13.0-107.154                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-108-generic                              3.13.0-108.155                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-24-generic                               3.13.0-24.47                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-27-generic                               3.13.0-27.50                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-29-generic                               3.13.0-29.53                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-30-generic                               3.13.0-30.55                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-32-generic                               3.13.0-32.57                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-33-generic                               3.13.0-33.58                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-34-generic                               3.13.0-34.60                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-35-generic                               3.13.0-35.62                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-36-generic                               3.13.0-36.63                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-37-generic                               3.13.0-37.64                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-39-generic                               3.13.0-39.66                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-40-generic                               3.13.0-40.69                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-43-generic                               3.13.0-43.72                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-44-generic                               3.13.0-44.73                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-45-generic                               3.13.0-45.74                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-46-generic                               3.13.0-46.79                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-48-generic                               3.13.0-48.80                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-49-generic                               3.13.0-49.83                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-51-generic                               3.13.0-51.84                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-52-generic                               3.13.0-52.86                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-53-generic                               3.13.0-53.89                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-54-generic                               3.13.0-54.91                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-55-generic                               3.13.0-55.94                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-57-generic                               3.13.0-57.95                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-58-generic                               3.13.0-58.97                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-59-generic                               3.13.0-59.98                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-61-generic                               3.13.0-61.100                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-62-generic                               3.13.0-62.102                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-63-generic                               3.13.0-63.103                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-65-generic                               3.13.0-65.106                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-66-generic                               3.13.0-66.108                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-67-generic                               3.13.0-67.110                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-68-generic                               3.13.0-68.111                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-71-generic                               3.13.0-71.114                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-74-generic                               3.13.0-74.118                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-76-generic                               3.13.0-76.120                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-77-generic                               3.13.0-77.121                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-79-generic                               3.13.0-79.123                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-83-generic                               3.13.0-83.127                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-85-generic                               3.13.0-85.129                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-86-generic                               3.13.0-86.131                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-87-generic                               3.13.0-87.133                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-88-generic                               3.13.0-88.135                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-91-generic                               3.13.0-91.138                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-92-generic                               3.13.0-92.139                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-93-generic                               3.13.0-93.140                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-95-generic                               3.13.0-95.142                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-96-generic                               3.13.0-96.143                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-98-generic                               3.13.0-98.145                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-19-generic                                3.8.0-19.30                                  amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-21-generic                                3.8.0-21.32                                  amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-22-generic                                3.8.0-22.33                                  amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-23-generic                                3.8.0-23.34                                  amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-25-generic                                3.8.0-25.37                                  amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-26-generic                                3.8.0-26.38                                  amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-27-generic                                3.8.0-27.40                                  amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-29-generic                                3.8.0-29.42                                  amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-30-generic                                3.8.0-30.44                                  amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-31-generic                                3.8.0-31.46                                  amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-91-generic                                4.4.0-91.114                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-92-generic                                4.4.0-92.115                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-93-generic                                4.4.0-93.116                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-96-generic                                4.4.0-96.119                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-97-generic                                4.4.0-97.120                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-12-generic                         3.11.0-12.19                                 amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-13-generic                         3.11.0-13.20                                 amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-14-generic                         3.11.0-14.21                                 amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-15-generic                         3.11.0-15.25                                 amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-17-generic                         3.11.0-17.31                                 amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-18-generic                         3.11.0-18.32                                 amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-19-generic                         3.11.0-19.33                                 amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-100-generic                        3.13.0-100.147                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-101-generic                        3.13.0-101.148                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-103-generic                        3.13.0-103.150                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-105-generic                        3.13.0-105.152                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-106-generic                        3.13.0-106.153                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-107-generic                        3.13.0-107.154                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-108-generic                        3.13.0-108.155                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-24-generic                         3.13.0-24.47                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-27-generic                         3.13.0-27.50                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-29-generic                         3.13.0-29.53                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-30-generic                         3.13.0-30.55                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-32-generic                         3.13.0-32.57                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-33-generic                         3.13.0-33.58                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-34-generic                         3.13.0-34.60                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-35-generic                         3.13.0-35.62                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-36-generic                         3.13.0-36.63                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-37-generic                         3.13.0-37.64                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-39-generic                         3.13.0-39.66                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-40-generic                         3.13.0-40.69                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-43-generic                         3.13.0-43.72                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-44-generic                         3.13.0-44.73                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-45-generic                         3.13.0-45.74                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-46-generic                         3.13.0-46.79                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-48-generic                         3.13.0-48.80                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-49-generic                         3.13.0-49.83                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-51-generic                         3.13.0-51.84                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-52-generic                         3.13.0-52.86                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-53-generic                         3.13.0-53.89                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-54-generic                         3.13.0-54.91                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-55-generic                         3.13.0-55.94                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-57-generic                         3.13.0-57.95                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-58-generic                         3.13.0-58.97                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-59-generic                         3.13.0-59.98                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-61-generic                         3.13.0-61.100                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-62-generic                         3.13.0-62.102                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-63-generic                         3.13.0-63.103                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-65-generic                         3.13.0-65.106                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-66-generic                         3.13.0-66.108                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-67-generic                         3.13.0-67.110                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-68-generic                         3.13.0-68.111                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-71-generic                         3.13.0-71.114                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-74-generic                         3.13.0-74.118                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-76-generic                         3.13.0-76.120                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-77-generic                         3.13.0-77.121                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-79-generic                         3.13.0-79.123                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-83-generic                         3.13.0-83.127                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-85-generic                         3.13.0-85.129                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-86-generic                         3.13.0-86.131                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-87-generic                         3.13.0-87.133                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-88-generic                         3.13.0-88.135                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-91-generic                         3.13.0-91.138                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-92-generic                         3.13.0-92.139                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-93-generic                         3.13.0-93.140                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-95-generic                         3.13.0-95.142                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-96-generic                         3.13.0-96.143                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-98-generic                         3.13.0-98.145                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.8.0-19-generic                          3.8.0-19.30                                  amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-extra-3.8.0-21-generic                          3.8.0-21.32                                  amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-extra-3.8.0-22-generic                          3.8.0-22.33                                  amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-extra-3.8.0-23-generic                          3.8.0-23.34                                  amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-extra-3.8.0-25-generic                          3.8.0-25.37                                  amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-extra-3.8.0-26-generic                          3.8.0-26.38                                  amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-extra-3.8.0-27-generic                          3.8.0-27.40                                  amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-extra-3.8.0-29-generic                          3.8.0-29.42                                  amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-extra-3.8.0-30-generic                          3.8.0-30.44                                  amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-extra-3.8.0-31-generic                          3.8.0-31.46                                  amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-62-generic                          4.4.0-62.83                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-63-generic                          4.4.0-63.84                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-64-generic                          4.4.0-64.85                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-66-generic                          4.4.0-66.87                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-67-generic                          4.4.0-67.88                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-70-generic                          4.4.0-70.91                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-71-generic                          4.4.0-71.92                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-72-generic                          4.4.0-72.93                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-75-generic                          4.4.0-75.96                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-77-generic                          4.4.0-77.98                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-78-generic                          4.4.0-78.99                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-79-generic                          4.4.0-79.100                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-83-generic                          4.4.0-83.106                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-87-generic                          4.4.0-87.110                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-89-generic                          4.4.0-89.112                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-91-generic                          4.4.0-91.114                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-92-generic                          4.4.0-92.115                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-93-generic                          4.4.0-93.116                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-96-generic                          4.4.0-96.119                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-97-generic                          4.4.0-97.120                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                                         4.4.0.97.102                                 amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                        4.4.0-97.120                                 amd64        Linux Kernel Headers for development
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu5                         all          base package for ALSA and OSS sound systems
ii  syslinux-common                                             3:6.03+dfsg-11ubuntu1                        all          collection of bootloaders (common)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu8                         amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

---

### Post by Impavidus on 2017-10-14
You have some disk space left. Not much, but enough for your system to run so you can do some clean-up. But you've almost run out of inodes. You have 1234576 inodes on your root partition, of which only 26045 are free, which means that you can only store 26045 additional files and directories before your disk is full, no matter how small those files are. Your old linux-headers packages consume most of these inodes.

Use synaptic or the command line to uninstall all linux-headers-* and linux-headers-*-generic packages with * some version number lower than 4.4.0-93. That should free some inodes. Further, you don't have linux-headers-4.4.0-97, although you do have linux-image-4.4.0-97-generic. For some reason **linux-headers-generic** is not installed on your system. I'm not sure you need it, but maybe best to install (*after* you uninstalled the old header packages). That will pull in the latest header packages whenever you get a kernel upgrade.

All packages labeled with rc in the first column of the dpkg output are uninstalled, but their configuration files have not been removed. As it happens, these packages have no configuration files, so that doesn't matter. If you want to remove the clutter from the output, you can completely uninstall them anyway. Using the terminal, use the purge option. In your dutch-language synaptic, the packages will be listed under "Niet geïnstalleerd (resterende configuratie)" (you may have to select "Status" first). You can remove them with "Markeren voor volledige verwijdering".

---

### Post by matrooswolf on 2017-10-14
Hi Impavidus,

Thank you, that helped. (I'm on 16.04 LTS by the way)

Things now look like this
```
LANG=C df -i

Filesystem        Inodes  IUsed     IFree IUse% Mounted on
udev              485255    565    484690    1% /dev
tmpfs             490349    844    489505    1% /run
/dev/sda2        1234576 420465    814111   35% /
tmpfs             490349     67    490282    1% /dev/shm
tmpfs             490349      4    490345    1% /run/lock
tmpfs             490349     18    490331    1% /sys/fs/cgroup
/dev/sda5       15261696  92760  15168936    1% /home
cgmfs             490349     14    490335    1% /run/cgmanager/fs
tmpfs             490349     37    490312    1% /run/user/1000


```
```
LANG=C dpkg --list | grep linux-

ii  linux-base                                                  4.0ubuntu1                                   all          Linux image base package
ii  linux-firmware                                              1.157.12                                     all          Firmware for Linux kernel drivers
ii  linux-headers-4.4.0-93                                      4.4.0-93.116                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-93-generic                              4.4.0-93.116                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-96                                      4.4.0-96.119                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-96-generic                              4.4.0-96.119                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-97                                      4.4.0-97.120                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-97-generic                              4.4.0-97.120                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                                       4.4.0.97.102                                 amd64        Generic Linux kernel headers
ii  linux-image-4.4.0-93-generic                                4.4.0-93.116                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-96-generic                                4.4.0-96.119                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-97-generic                                4.4.0-97.120                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-93-generic                          4.4.0-93.116                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-96-generic                          4.4.0-96.119                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-97-generic                          4.4.0-97.120                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                                         4.4.0.97.102                                 amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                        4.4.0-97.120                                 amd64        Linux Kernel Headers for development
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu5                         all          base package for ALSA and OSS sound systems
ii  syslinux-common                                             3:6.03+dfsg-11ubuntu1                        all          collection of bootloaders (common)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu8                         amd64        Bootloader for Linux/i386 using MS-DOS floppies


```

which freed up a lot of space on / and looks a lot healthier as inodes are back to 35%

---

### Post by mikewhatever on 2017-10-14
That was, in total, 74 kernels, 65 headers and 93 extras = 232 packages. Impressive! :~)

---

