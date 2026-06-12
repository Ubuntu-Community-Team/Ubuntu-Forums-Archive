---
title: "how to delete old headers &amp; images"
date: 2017-04-30
forum: General Help
---

### Post by czgirb on 2017-04-30
currently i'm using 14.04 LTS and my
> dpkg -l | grep -E 'linux-(headers|image)'
is as follows:
```
ii  linux-headers-3.13.0-108-generic                      3.13.0-108.155                                      i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-109                              3.13.0-109.156                                      all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-109-generic                      3.13.0-109.156                                      i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-110                              3.13.0-110.157                                      all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-110-generic                      3.13.0-110.157                                      i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-112                              3.13.0-112.159                                      all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-112-generic                      3.13.0-112.159                                      i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-113                              3.13.0-113.160                                      all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-113-generic                      3.13.0-113.160                                      i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-115                              3.13.0-115.162                                      all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-115-generic                      3.13.0-115.162                                      i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-116                              3.13.0-116.163                                      all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-116-generic                      3.13.0-116.163                                      i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-117                              3.13.0-117.164                                      all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-117-generic                      3.13.0-117.164                                      i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-48                               3.13.0-48.80                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-48-generic                       3.13.0-48.80                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-49                               3.13.0-49.83                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-49-generic                       3.13.0-49.83                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-51                               3.13.0-51.84                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-51-generic                       3.13.0-51.84                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-52                               3.13.0-52.86                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-52-generic                       3.13.0-52.86                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-53                               3.13.0-53.89                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-53-generic                       3.13.0-53.89                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-54                               3.13.0-54.91                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-54-generic                       3.13.0-54.91                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-55                               3.13.0-55.94                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-55-generic                       3.13.0-55.94                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-57                               3.13.0-57.95                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-57-generic                       3.13.0-57.95                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-58                               3.13.0-58.97                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-58-generic                       3.13.0-58.97                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-59                               3.13.0-59.98                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-59-generic                       3.13.0-59.98                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-61                               3.13.0-61.100                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-61-generic                       3.13.0-61.100                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-62                               3.13.0-62.102                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-62-generic                       3.13.0-62.102                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-63                               3.13.0-63.103                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-63-generic                       3.13.0-63.103                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-65                               3.13.0-65.106                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-65-generic                       3.13.0-65.106                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-66                               3.13.0-66.108                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-66-generic                       3.13.0-66.108                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-77                               3.13.0-77.121                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-77-generic                       3.13.0-77.121                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-79                               3.13.0-79.123                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-79-generic                       3.13.0-79.123                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-83                               3.13.0-83.127                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-83-generic                       3.13.0-83.127                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-85                               3.13.0-85.129                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-85-generic                       3.13.0-85.129                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-86                               3.13.0-86.131                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-86-generic                       3.13.0-86.131                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-87                               3.13.0-87.133                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-87-generic                       3.13.0-87.133                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-88                               3.13.0-88.135                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-88-generic                       3.13.0-88.135                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-91                               3.13.0-91.138                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-91-generic                       3.13.0-91.138                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-92                               3.13.0-92.139                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-92-generic                       3.13.0-92.139                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-93                               3.13.0-93.140                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-93-generic                       3.13.0-93.140                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-95                               3.13.0-95.142                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-95-generic                       3.13.0-95.142                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-96                               3.13.0-96.143                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-96-generic                       3.13.0-96.143                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-98                               3.13.0-98.145                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-98-generic                       3.13.0-98.145                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.117.127                                      i386         Generic Linux kernel headers
ii  linux-image-3.13.0-100-generic                        3.13.0-100.147                                      i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-101-generic                        3.13.0-101.148                                      i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-103-generic                        3.13.0-103.150                                      i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-105-generic                        3.13.0-105.152                                      i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-106-generic                        3.13.0-106.153                                      i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-107-generic                        3.13.0-107.154                                      i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-108-generic                        3.13.0-108.155                                      i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-109-generic                        3.13.0-109.156                                      i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-110-generic                        3.13.0-110.157                                      i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-112-generic                        3.13.0-112.159                                      i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-113-generic                        3.13.0-113.160                                      i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-115-generic                        3.13.0-115.162                                      i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-116-generic                        3.13.0-116.163                                      i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-117-generic                        3.13.0-117.164                                      i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-37-generic                         3.13.0-37.64                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-39-generic                         3.13.0-39.66                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-40-generic                         3.13.0-40.69                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-43-generic                         3.13.0-43.72                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-44-generic                         3.13.0-44.73                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-45-generic                         3.13.0-45.74                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-46-generic                         3.13.0-46.79                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-48-generic                         3.13.0-48.80                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-49-generic                         3.13.0-49.83                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-51-generic                         3.13.0-51.84                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-52-generic                         3.13.0-52.86                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-53-generic                         3.13.0-53.89                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-54-generic                         3.13.0-54.91                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-55-generic                         3.13.0-55.94                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-57-generic                         3.13.0-57.95                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-58-generic                         3.13.0-58.97                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-59-generic                         3.13.0-59.98                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-61-generic                         3.13.0-61.100                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-62-generic                         3.13.0-62.102                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-63-generic                         3.13.0-63.103                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-65-generic                         3.13.0-65.106                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-66-generic                         3.13.0-66.108                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-77-generic                         3.13.0-77.121                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-79-generic                         3.13.0-79.123                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-83-generic                         3.13.0-83.127                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-85-generic                         3.13.0-85.129                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-86-generic                         3.13.0-86.131                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-87-generic                         3.13.0-87.133                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-88-generic                         3.13.0-88.135                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-91-generic                         3.13.0-91.138                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-92-generic                         3.13.0-92.139                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-93-generic                         3.13.0-93.140                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-95-generic                         3.13.0-95.142                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-96-generic                         3.13.0-96.143                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-98-generic                         3.13.0-98.145                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-100-generic                  3.13.0-100.147                                      i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-101-generic                  3.13.0-101.148                                      i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-103-generic                  3.13.0-103.150                                      i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-105-generic                  3.13.0-105.152                                      i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-106-generic                  3.13.0-106.153                                      i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-107-generic                  3.13.0-107.154                                      i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-108-generic                  3.13.0-108.155                                      i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-109-generic                  3.13.0-109.156                                      i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-110-generic                  3.13.0-110.157                                      i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-112-generic                  3.13.0-112.159                                      i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-113-generic                  3.13.0-113.160                                      i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-115-generic                  3.13.0-115.162                                      i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-116-generic                  3.13.0-116.163                                      i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-117-generic                  3.13.0-117.164                                      i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-37-generic                   3.13.0-37.64                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic                   3.13.0-39.66                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-40-generic                   3.13.0-40.69                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-43-generic                   3.13.0-43.72                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-44-generic                   3.13.0-44.73                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-45-generic                   3.13.0-45.74                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-46-generic                   3.13.0-46.79                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-48-generic                   3.13.0-48.80                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-49-generic                   3.13.0-49.83                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-51-generic                   3.13.0-51.84                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-52-generic                   3.13.0-52.86                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-53-generic                   3.13.0-53.89                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-54-generic                   3.13.0-54.91                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-55-generic                   3.13.0-55.94                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-57-generic                   3.13.0-57.95                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-58-generic                   3.13.0-58.97                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-59-generic                   3.13.0-59.98                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-61-generic                   3.13.0-61.100                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-62-generic                   3.13.0-62.102                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-63-generic                   3.13.0-63.103                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-65-generic                   3.13.0-65.106                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-66-generic                   3.13.0-66.108                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-77-generic                   3.13.0-77.121                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-79-generic                   3.13.0-79.123                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-83-generic                   3.13.0-83.127                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-85-generic                   3.13.0-85.129                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-86-generic                   3.13.0-86.131                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-87-generic                   3.13.0-87.133                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-88-generic                   3.13.0-88.135                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-91-generic                   3.13.0-91.138                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-92-generic                   3.13.0-92.139                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-93-generic                   3.13.0-93.140                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-95-generic                   3.13.0-95.142                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-96-generic                   3.13.0-96.143                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-98-generic                   3.13.0-98.145                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-generic                                   3.13.0.117.127                                      i386         Generic Linux kernel image

```

thank you

---

### Post by TheFu on 2017-04-30
I would do it this way - to remove all the none 100 series kernels.
```

sudo apt-get remove linux-image-3.13.0-[3-9]*-generic
sudo apt-get autoremove
```

The 2nd command should remove the headers and extras for each.

Carefully review the feedback and <cntl>-c out if any of the 100 line of kernels is included.
I didn't test the command - here.  apt-get supports regex while apt and aptitude do not.

---

### Post by kc1di on 2017-04-30
you can also install ubuntu-cleaner [here]("http://www.omgubuntu.co.uk/2016/12/free-space-ubuntu-cleaner-janitor-app")

---

### Post by oldfred on 2017-04-30
I might use purge.
 purge
           purge is identical to remove except that packages are removed and
           purged (any configuration files are deleted too).


       Determine your current kernel:
uname -a
-s is similate so you can review first:
sudo apt-get -s autoremove
sudo apt-get install synaptic
In synaptic search for linux-image to choose to delete old ones
Using synaptic
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
cd /boot
ls -l /boot/vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic
Multiples, just be sure not to delete your current kernel:
sudo apt-get purge linux-image-3.13.0-{XX,XX,XX,XX,XX,XX}-generic
sudo apt-get purge linux-image-3.13.0-{54,55,57}-generic
[http://ubuntuforums.org/showthread.php?t=2308561&p=13417427#post13417427](http://ubuntuforums.org/showthread.php?t=2308561&p=13417427#post13417427)
sudo dpkg -P linux-image{,-extra}-3.19.0-{25,28,30,31,32}-generic

---

### Post by ajgreeny on 2017-04-30
It is worth while running sudo apt-get autoremove on a regular basis, perhaps every month or so as that will remove old kernel images except the two most recent, and should also take with the kernels the header packages of the same version.

You can also, if you like to see what is going on, do this using synaptic by searching for those version numbers using name only, and removing what you don't want any more.

I have no knowledge of the cleaner app suggested by kc1di but my feeling with cleaner applications generally is that they are not necessary, and if not configured properly can do more harm than good; that may not be true of that application.

EDIT:
Ah! Part ninja'd by oldfred with similar info.

---

### Post by czgirb on 2017-04-30
> **oldfred said:**
> I might use purge.
 purge
           purge is identical to remove except that packages are removed and
           purged (any configuration files are deleted too).


       Determine your current kernel:
uname -a
-s is similate so you can review first:
sudo apt-get -s autoremove
sudo apt-get install synaptic
In synaptic search for linux-image to choose to delete old ones
Using synaptic
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
cd /boot
ls -l /boot/vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic
Multiples, just be sure not to delete your current kernel:
sudo apt-get purge linux-image-3.13.0-{XX,XX,XX,XX,XX,XX}-generic
sudo apt-get purge linux-image-3.13.0-{54,55,57}-generic
[http://ubuntuforums.org/showthread.php?t=2308561&p=13417427#post13417427](http://ubuntuforums.org/showthread.php?t=2308561&p=13417427#post13417427)
sudo dpkg -P linux-image{,-extra}-3.19.0-{25,28,30,31,32}-generic

as requested
> ^[[C^[[C^[[Cczgirb@ubuntu:~$ uname -a
Linux ubuntu 3.13.0-117-generic #164-Ubuntu SMP Fri Apr 7 11:06:36 UTC 2017 i686 i686 i686 GNU/Linux
czgirb@ubuntu:~$ czgirb@ubuntu:~$ uname -s
Linux
czgirb@ubuntu:~$ 




---

### Post by TheFu on 2017-04-30
a) I'm extremely confident that the commands I provided will work.  I wrote a tool that cleaned up old kernels, hence my confidence.
b) After removing most of the old kernels, the autoremove will handle the headers and extras. No need to remove them manually.

My tool is here: [http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt](http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt) - but isn't necessary anymore with normal system maintenance practices.

---

### Post by czgirb on 2017-04-30
> **TheFu said:**
> a) I'm extremely confident that the commands I provided will work.  I wrote a tool that cleaned up old kernels, hence my confidence.
b) After removing most of the old kernels, the autoremove will handle the headers and extras. No need to remove them manually.

My tool is here: [http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt](http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt) - but isn't necessary anymore with normal system maintenance practices.

Dear TheFu, if you extremely confident that the commands you provided will work, would you mind to guide me step-by-step
although i had already used ubuntu for more than a year. but mostly to play music and video only. no more than that.
so ... please guide me step-by-step. cos although i had open the link you given. i still unable to understand th article. sorry.

please do not forget that there is ^[[C^[[C^[[C in the beginning of the terminal
and it made me unable to input the password and touch anything inside.

thank you

^[[Cczgirb@ubuntu:~$ sudo apt-get remove linux-image-3.13.0-[3-9]*-generic
[sudo] password for czgirb: 
^[[C^[[C^[[C^[[C^[[C^[[C^[[C^[[C^[[C^[[C^[[C^[[C^[[C^[[C^[[C^[[C^[[C^[[C^[[C^[[C^[[C^[[C^[[CSorry, try again.
[sudo] password for czgirb:

---

### Post by oldfred on 2017-04-30
Looks like you have stuck keys on keyboard, or short inside it.

---

### Post by czgirb on 2017-05-01
> **oldfred said:**
> Looks like you have stuck keys on keyboard, or short inside it.

maybe ... how can it be fixed? thank you
**update:**
fixed alreday ... thank you

---

### Post by TheFu on 2017-05-01
So - the 2 commands worked and this thread can be closed?
If not, please post the output from an fresh run of  **dpkg -l | egrep 'linux-(headers|image)' ** so we can see what is left.

---

### Post by Topsiho on 2017-05-01
After every update, especially on my netbook, and after an install of another kernel, in the terminal I execute:

sudo apt clear
sudo apt autoremove

using df -h I can monitor the results of this, as the available space in / increases.

clear deletes all downloaded files used for the update, and autoremove removes previous kernel images and headerfiles, except for the latest two.
And possibly other files that are not used anymore.

Topsiho

---

### Post by Dennis N on 2017-05-01
If you like GUI, you can also use Synaptic Package Manager:

1) Search for kernel number in search box - 4.10.0
2) Sort by Installed Version (click on column title) which groups files by kernel version.
3) Select older kernel files. 
4) Mark for Complete Removal, and Apply.

Image Attached!

(In this case, not going to remove these files, since only two kernels are installed).

---

