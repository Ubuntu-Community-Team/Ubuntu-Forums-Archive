---
title: "Slow Boot After Playing with Network Connection"
date: 2021-03-06
forum: General Help
---

### Post by Quarkrad on 2021-03-06
Running 20.04.  I've recently changed my network connection to have a bridge connection rather than a plan/standard ethernet connection. I have done this is so my kvm machines are in the same ip range as my host - this is all working fine.  However, since making this change my boot time has increased dramatically.  systemd-analyze blame results, show to me, that my playing with the network connection is causing this boot increase.  I've tried to look for network.service issues with boot times but so far not found anything useful.  Any help appreciated. 

```
dad@dadubuntu:~$ systemd-analyze blame
34.424s networking.service                                                        >
 1.369s ifupdown-pre.service                                                      >
  751ms apt-daily-upgrade.service                                                 >
  509ms udisks2.service                                                           >
  212ms blueman-mechanism.service                                                 >
  160ms dev-nvme0n1p2.device                                                      >
  158ms man-db.service                                                            >
  158ms snap-snapd-11036.mount                                                    >
  156ms snap-gtk\x2dcommon\x2dthemes-1514.mount                                   >
  139ms apport-autoreport.service                                                 >
  137ms logrotate.service                                                         >
  131ms snap-core18-1988.mount                                                    >
  129ms snap-gnome\x2d3\x2d28\x2d1804-145.mount                                   >
  121ms accounts-daemon.service                                                   >
  110ms systemd-modules-load.service                                              >
  105ms NetworkManager-wait-online.service                                        >
  104ms networkd-dispatcher.service                                               >
  103ms snap-chromium-1479.mount                                                  >
   92ms dev-loop0.device                                                          >
   92ms dev-loop1.device                                                          >
   74ms systemd-logind.service                                                    >
   74ms libvirtd.service                                                          >
   72ms lightdm.service                                                           >
   70ms lvm2-monitor.service                                                      >
   70ms plymouth-quit-wait.service                                                >
   68ms systemd-fsck@dev-disk-by\x2duuid-d9203686\x2d5296\x2d45b7\x2d9691\x2dce778>
   67ms user@1000.service                                                         >
   66ms systemd-fsck@dev-disk-by\x2duuid-09b4d0d4\x2d37cd\x2d4cfc\x2dbeb2\x2d09b26>
   66ms avahi-daemon.service                                                      >
   65ms polkit.service                                                            >
   62ms NetworkManager.service                                                    >
   62ms dev-loop2.device                                                          >
   52ms e2scrub_reap.service                                                      >
   52ms thermald.service      
```

---

