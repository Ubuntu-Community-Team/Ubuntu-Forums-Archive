---
title: "Slow boot with SSD - Dual boot with windows"
date: 2020-11-13
forum: General Help
---

### Post by josuefs on 2020-11-13
I installed Ubuntu 20.04 and I'm using it in dual boot with windows 10 (installed first), I reserved a space of 100GB on my SSD to install it and I used the option "Install next to windows".


I'm having problems with the boot, I think it's taking too long to turn on and off, before when there was only windows running smoothly, the PC turned on in a maximum of 15s.


I ran some commands on linux as I was researching, but I couldn't solve the problem, I'll leave some of the logs below to show the boot time:


Solution I tried, but it didn't work:


I edited the file below:


```
    /etc/initramfs-tools/conf.d/resume

```

Editing the line:


```
    RESUME=none

```

And then:


```
    sudo update-initramfs -u

```

**Logs:**


**systemd-analyze time**


    ```

Startup finished in 3.183s (kernel) + 1min 7.952s (userspace) = 1min 11.136s
    graphical.target reached after 1min 7.866s in userspace
```


**systemd-analyze blame**    


    ```

34.868s plymouth-quit-wait.service                           
    19.044s networkd-dispatcher.service                          
    16.892s snapd.service                                        
    16.642s dev-sdb5.device                                      
    14.982s udisks2.service                                      
    12.542s accounts-daemon.service                              
    11.823s systemd-journal-flush.service                        
    11.762s NetworkManager-wait-online.service                   
    10.184s dev-loop8.device                                     
    10.072s dev-loop12.device                                    
    10.035s dev-loop10.device                                    
    10.028s dev-loop9.device                                     
     9.656s dev-loop11.device                                    
     9.545s NetworkManager.service                               
     9.400s dev-loop7.device                                     
     8.924s polkit.service                                       
     8.884s avahi-daemon.service                                 
     8.759s dev-loop6.device                                     
     8.057s switcheroo-control.service                           
     8.054s thermald.service                                     
     8.052s wpa_supplicant.service                               
     8.052s systemd-logind.service                               
     7.975s dev-loop3.device                                     
     7.887s dev-loop1.device                                     
     7.688s dev-loop2.device                                     
     7.197s dev-loop5.device                                     
     6.754s ModemManager.service                                 
     6.445s dev-loop0.device                                     
     5.840s dev-loop4.device                                     
     5.779s gpu-manager.service                                  
     5.349s grub-common.service                                  
     5.290s apport.service                                       
     4.082s rsyslog.service                                      
     3.340s e2scrub_reap.service                                 
     2.844s gdm.service                                          
     2.536s systemd-udevd.service                                
     2.436s systemd-resolved.service                             
     2.359s grub-initrd-fallback.service                         
     2.080s [EMAIL="user@125.servic"]user@125.servic[/EMAIL]e                                     
     1.512s apparmor.service                                     
     1.489s nvidia-persistenced.service                          
     1.206s pppd-dns.service                                     
      920ms systemd-modules-load.service                         
      813ms fwupd.service                                        
      761ms snapd.apparmor.service                               
      699ms systemd-tmpfiles-setup.service                       
      694ms snap-canonical\x2dlivepatch-95.mount                 
      693ms systemd-sysusers.service                             
      690ms snap-code-49.mount                                   
      686ms plymouth-start.service                               
      672ms systemd-random-seed.service                          
      639ms snap-code-50.mount                                   
      632ms snap-core-10185.mount                                
      631ms snap-core18-1705.mount                               
      610ms systemd-rfkill.service                               
      602ms snap-core18-1932.mount                               
      597ms systemd-udev-trigger.service                         
      584ms [EMAIL="modprobe@drm.servic"]modprobe@drm.servic[/EMAIL]e                                 
      561ms snap-gnome\x2d3\x2d34\x2d1804-24.mount               
      554ms systemd-tmpfiles-setup-dev.service                   
      547ms swapfile.swap                                        
      526ms keyboard-setup.service                               
      502ms snapd.seeded.service                                 
      454ms snap-gnome\x2d3\x2d34\x2d1804-60.mount               
      424ms colord.service                                       
      388ms systemd-sysctl.service                               
      387ms [EMAIL="systemd-fsck@dev-disk-by\x2duuid-C5FA\x2dAD5C.servic"]systemd-fsck@dev-disk-by\x2duuid-C5FA\x2dAD5C.servic[/EMAIL]e
      346ms ufw.service                                          
      331ms systemd-journald.service                             
      326ms systemd-timesyncd.service                            
      276ms snap-gtk\x2dcommon\x2dthemes-1506.mount              
      270ms upower.service                                       
      208ms console-setup.service                                
      205ms snap-snap\x2dstore-433.mount                         
      188ms snap-snapd-9721.mount                                
      184ms dev-hugepages.mount                                  
      184ms dev-mqueue.mount                                     
      183ms sys-kernel-debug.mount                               
      182ms sys-kernel-tracing.mount                             
      181ms kmod-static-nodes.service                            
      180ms snap-snapd-7264.mount                                
      160ms systemd-remount-fs.service                           
      156ms systemd-update-utmp.service                          
      145ms snap-snap\x2dstore-481.mount                         
      131ms systemd-user-sessions.service                        
      128ms [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e                                    
      125ms openvpn.service                                      
      105ms systemd-localed.service                              
       91ms systemd-hostnamed.service                            
       89ms kerneloops.service                                   
       83ms setvtrgb.service                                     
       82ms [EMAIL="user-runtime-dir@125.servic"]user-runtime-dir@125.servic[/EMAIL]e                         
       59ms boot-efi.mount                                       
       52ms plymouth-read-write.service                          
       45ms geoclue.service                                      
       28ms packagekit.service                                   
       22ms [EMAIL="user-runtime-dir@1000.servic"]user-runtime-dir@1000.servic[/EMAIL]e                        
       15ms rtkit-daemon.service                                 
        7ms systemd-update-utmp-runlevel.service                 
        5ms alsa-restore.service                                 
        2ms sys-fs-fuse-connections.mount                        
        1ms sys-kernel-config.mount                              
      554us snapd.socket                                         
      

```      
      
**systemd-analyze critical-chain**


    ```

The time when unit became active or started is printed after the "@" character.
    The time the unit took to start is printed after the "+" character.
    
    graphical.target @1min 12.886s
    &#9492;&#9472;multi-user.target @1min 12.886s
      &#9492;&#9472;kerneloops.service @46.659s +162ms
        &#9492;&#9472;network-online.target @46.574s
          &#9492;&#9472;NetworkManager-wait-online.service @34.890s +11.682s
            &#9492;&#9472;NetworkManager.service @23.504s +11.381s
              &#9492;&#9472;dbus.service @23.502s
                &#9492;&#9472;basic.target @23.415s
                  &#9492;&#9472;sockets.target @23.415s
                    &#9492;&#9472;snapd.socket @23.415s +555us
                      &#9492;&#9472;sysinit.target @23.359s
                        &#9492;&#9472;snapd.apparmor.service @22.682s +677ms
                          &#9492;&#9472;apparmor.service @20.922s +1.758s
                            &#9492;&#9472;local-fs.target @20.922s
                              &#9492;&#9472;run-user-125-gvfs.mount @54.903s
                                &#9492;&#9472;run-user-125.mount @43.977s
                                  &#9492;&#9472;local-fs-pre.target @5.364s
                                    &#9492;&#9472;systemd-tmpfiles-setup-dev.service @4.769s +5>
                                      &#9492;&#9472;systemd-sysusers.service @4.134s +634ms
                                        &#9492;&#9472;systemd-remount-fs.service @3.788s +78ms
                                          &#9492;&#9472;systemd-journald.socket @3.658s
                                            &#9492;&#9472;-.mount @3.655s
                                              &#9492;&#9472;system.slice @3.655s
                                                &#9492;&#9472;-.slice @3.655s
```

---

