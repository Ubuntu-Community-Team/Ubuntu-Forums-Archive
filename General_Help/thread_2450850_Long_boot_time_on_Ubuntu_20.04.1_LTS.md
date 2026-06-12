---
title: "Long boot time on Ubuntu 20.04.1 LTS"
date: 2020-09-22
forum: General Help
---

### Post by herolies on 2020-09-22
Hello! I'm new to Ubuntu and been using it for over a month already.

though, I haven't really touched it for like 2 weeks. Coming back to it. It's taking long to boot compare to win10.

I went ahead and disabled ```
NetworkManager-wait-online.service
```. It seemed to have shaved off 10 seconds but boot time is still long. 

I used ```
systemd-analyze time
``` and got this
```
Startup finished in 8.438s (firmware) + 6.725s (loader) + 5.636s (kernel) + 1min 21.416s (userspace) = 1min 42.216s graphical.target reached after 1min 21.366s in userspace

```

then blame 
```
47.356s plymouth-quit-wait.service                           19.380s dev-sdc5.device                                      
18.482s snapd.service                                        
17.812s systemd-journal-flush.service                        
14.441s networkd-dispatcher.service                          
13.368s accounts-daemon.service                              
11.580s udisks2.service                                      
10.304s dev-loop16.device                                    
 8.662s dev-loop15.device                                    
 8.570s polkit.service                                       
 8.009s dev-loop13.device                                    
 7.996s dev-loop5.device                                     
 7.979s dev-loop10.device                                    
 7.935s dev-loop11.device                                    
 7.813s dev-loop14.device                                    
 7.660s dev-loop2.device                                     
 7.571s dev-loop8.device                                     
 7.521s avahi-daemon.service                                 
 7.496s NetworkManager.service                               
 7.285s dev-loop3.device                                     
 7.052s fwupd.service                                        
 7.019s dev-loop12.device                                    
 6.818s dev-loop9.device                                     
 6.701s dev-loop6.device                                     
 6.593s dev-loop7.device                                     
 6.405s ModemManager.service                                 
 6.056s switcheroo-control.service                           
 6.053s thermald.service                                     
 6.052s wpa_supplicant.service                               
 6.052s systemd-logind.service                               
 6.031s dev-loop0.device                                     
 5.923s dev-loop1.device                                     
 5.888s dev-loop4.device                                     
 5.068s bolt.service                                         
 4.087s gpu-manager.service                                  
 3.517s rsyslog.service                                      
 3.286s secureboot-db.service                                
 3.050s apport.service                                       
 3.035s systemd-udevd.service                                
 3.030s grub-common.service                                  
 3.013s gdm.service                                          
 2.725s grub-initrd-fallback.service                         
 2.446s apparmor.service                                     
 2.410s user@125.service                                     
 2.080s systemd-resolved.service                             
 1.519s nvidia-persistenced.service                          
 1.470s systemd-tmpfiles-setup.service                       
 1.441s e2scrub_reap.service                                 
 1.056s colord.service                                       
 1.005s snapd.apparmor.service                               
  887ms snap-bitwarden-29.mount                              
  862ms snapd.seeded.service                                 
  862ms snap-bitwarden-30.mount                              
  848ms systemd-modules-load.service                         
  805ms snap-canonical\x2dlivepatch-95.mount                 
  784ms plymouth-start.service                               
  738ms snap-code-43.mount                                   
  704ms snap-code-44.mount                                   
  697ms systemd-tmpfiles-setup-dev.service                   
  675ms pppd-dns.service                                     
  665ms systemd-update-utmp.service                          
  660ms keyboard-setup.service                               
  660ms systemd-random-seed.service                          
  653ms alsa-restore.service                                 
  641ms snap-core-9804.mount                                 
  604ms snap-core-9993.mount                                 
  578ms systemd-sysctl.service                               
  555ms snap-core18-1880.mount                               
  553ms swapfile.swap                                        
  533ms systemd-udev-trigger.service                         
  521ms snap-core18-1885.mount                               
  517ms systemd-sysusers.service                             
  488ms modprobe@drm.service                                 
  477ms snap-discord-115.mount                               
  442ms upower.service                                       
  441ms snap-gnome\x2d3\x2d28\x2d1804-128.mount              
  436ms systemd-journald.service                             
  415ms systemd-timesyncd.service                            
  409ms systemd-fsck@dev-disk-by\x2duuid-667C\x2d64C7.service
  390ms snap-gnome\x2d3\x2d34\x2d1804-36.mount               
  356ms kerneloops.service                                   
  324ms snap-gtk\x2dcommon\x2dthemes-1506.mount              
  282ms snap-snap\x2dstore-467.mount                         
  260ms ufw.service                                          
  231ms plymouth-read-write.service                          
  191ms openvpn.service                                      
  178ms dev-hugepages.mount                                  
  178ms dev-mqueue.mount                                     
  177ms sys-kernel-debug.mount                               
  177ms sys-kernel-tracing.mount                             
  175ms kmod-static-nodes.service                            
  167ms snap-snapd-9279.mount                                
  164ms snap-snapd-8790.mount                                
  146ms snap-spotify-41.mount                                
  137ms systemd-remount-fs.service                           
  133ms console-setup.service                                
  130ms user@1000.service                                    
   99ms user-runtime-dir@125.service                         
   96ms systemd-user-sessions.service                        
   95ms boot-efi.mount                                       
   56ms rtkit-daemon.service                                 
   47ms setvtrgb.service                                     
   43ms systemd-tmpfiles-clean.service                       
   10ms user-runtime-dir@1000.service                        
    6ms systemd-update-utmp-runlevel.service                 
    2ms sys-fs-fuse-connections.mount                        
    1ms sys-kernel-config.mount                              
  420us snapd.socket
```

Any way to improve it?
Thanks in advance!

---

### Post by oldfred on 2020-09-22
Are you using the snaps. A lot are installed by default.
I uninstall all snaps and for the apps I want only install the .deb version from synaptic or command line.

They have improved snaps since this post, but they still are slower loading.
boot time cut in half by removing snap
[https://ubuntuforums.org/showthread.php?t=2391341](https://ubuntuforums.org/showthread.php?t=2391341)
[https://ubuntuforums.org/showthread.php?t=2409173](https://ubuntuforums.org/showthread.php?t=2409173)
[https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements](https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements)
Removes all snaps:
sudo apt autoremove --purge snapd


The main things I do:
turned off NetworkManager-wait with systemctl
changed from quiet splash to noplymouth, will see boot process rather than Ubuntu logo
sudo apt install libblockdev-crypto2 libblockdev-mdraid2
turned off printer when rebooting
removed snaps

If UEFI firmware update not supported (yet), my motherboard is not in fwupd list, so I purge it.
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)
sudo apt-get purge fwupd

Slow Boot --------------------------------
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)

[https://askubuntu.com/questions/1187117/slow-boot-boot-19-10-tried-almost-everything](https://askubuntu.com/questions/1187117/slow-boot-boot-19-10-tried-almost-everything) & 
[https://askubuntu.com/questions/1018576/what-does-networkmanager-wait-online-service-do](https://askubuntu.com/questions/1018576/what-does-networkmanager-wait-online-service-do) & 
[https://askubuntu.com/questions/800479/ubuntu-16-04-slow-boot-apt-daily-service](https://askubuntu.com/questions/800479/ubuntu-16-04-slow-boot-apt-daily-service)

---

