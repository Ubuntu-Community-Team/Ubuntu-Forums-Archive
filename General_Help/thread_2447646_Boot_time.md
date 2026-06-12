---
title: "Boot time"
date: 2020-07-23
forum: General Help
---

### Post by likhit on 2020-07-23
Hi,
I recently installed Ubuntu 20.04 and it is super fast on my PC. It is not the dual boot. My PC specs are:
CPU: Intel Pentium E5700@3GHz
Graphics: Intel G41(Onboard Graphics)
HDD: 250gb
Ram: 4GB + (4GB Swap)
But the boot times are very slow it takes about 1min to boot. At first it was about 30sec but now it is almost 1 minute. I checked boot time with systemd-analyze time it gave the results like this :
```
systemd-analyze time
Startup finished in 5.929s (kernel) + 51.893s (userspace) = 57.822s 
graphical.target reached after 51.826s in userspace
```

And I did check with systemd-analyze blame and it showed like this:
```
$ systemd-analyze blame
32.833s plymouth-quit-wait.service                                               
24.428s apport-autoreport.service                                                
11.315s dev-sda7.device                                                          
 7.112s accounts-daemon.service                                                  
 6.533s dev-loop8.device                                                         
 6.489s dev-loop3.device                                                         
 6.415s dev-loop4.device                                                         
 6.050s dev-loop0.device                                                         
 5.991s dev-loop2.device                                                         
 5.534s dev-loop1.device                                                         
 5.332s dev-loop5.device                                                         
 5.055s dev-loop6.device                                                         
 4.944s dev-loop7.device                                                         
 3.806s avahi-daemon.service                                                     
 3.625s switcheroo-control.service                                               
 3.613s thermald.service                                                         
 3.515s systemd-logind.service                                                   
 3.513s wpa_supplicant.service                                                   
 3.079s ufw.service                                                              
 2.880s gpu-manager.service                                                      
 2.688s snapd.service                                                            
 2.652s udisks2.service                                                          
 2.367s rsyslog.service                                                          
 2.327s grub-common.service                                                      
 2.252s e2scrub_reap.service                                                     
 2.237s preload.service                                                          
 1.855s systemd-udevd.service                                                    
 1.629s grub-initrd-fallback.service                                             
 1.615s apparmor.service                                                         
 1.350s systemd-modules-load.service                                             
 1.348s gdm.service                                                              
 1.260s fancontrol.service                                                       
 1.097s systemd-tmpfiles-setup.service                                           
 1.069s systemd-resolved.service                                                 
 1.019s lm-sensors.service                                                       
 1.004s systemd-sysctl.service                                                   
  987ms systemd-journal-flush.service                                            
  935ms systemd-tmpfiles-setup-dev.service                                       
  895ms systemd-journald.service                                                 
  801ms systemd-random-seed.service                                              
  781ms fwupd.service                                                            
  761ms systemd-timesyncd.service                                                
  686ms upower.service                                                           
  537ms plymouth-read-write.service                                              
  515ms snap-core18-1705.mount                                                   
  489ms keyboard-setup.service                                                   
  456ms systemd-sysusers.service                                                 
  412ms snap-core18-1880.mount                                                   
  398ms systemd-udev-trigger.service                                             
  379ms kerneloops.service                                                       
  372ms snap-gnome\x2d3\x2d28\x2d1804-128.mount                                  
  355ms snap-gnome\x2d3\x2d34\x2d1804-24.mount                                   
  341ms systemd-remount-fs.service                                               
  318ms snap-gnome\x2d3\x2d34\x2d1804-36.mount                                   
  315ms pppd-dns.service                                                         
  305ms [EMAIL="modprobe@drm.servic"]modprobe@drm.servic[/EMAIL]e                                                     
  230ms snap-snap\x2dstore-415.mount                                             
  222ms [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e                                                        
  220ms NetworkManager.service                                                   
  219ms polkit.service                                                           
  188ms console-setup.service                                                    
  173ms systemd-rfkill.service                                                   
  168ms snap-gtk\x2dcommon\x2dthemes-1506.mount                                  
  168ms snap-snapd-8542.mount                                                    
  131ms dev-mqueue.mount                                                         
  131ms systemd-update-utmp.service                                              
  130ms sys-kernel-debug.mount                                                   
  129ms dev-hugepages.mount                                                      
  129ms sys-kernel-tracing.mount                                                 
  128ms snap-snapd-7264.mount                                                    
  120ms kmod-static-nodes.service                                                
   93ms dev-disk-by\x2duuid-ee5aecd0\x2d8f8b\x2d461c\x2db8e0\x2d401f0dd6f584.swap
   86ms plymouth-start.service                                                   
   80ms colord.service                                                           
   78ms hddtemp.service                                                          
   62ms setvtrgb.service                                                         
   57ms systemd-user-sessions.service                                            
   31ms systemd-tmpfiles-clean.service                                           
   25ms [EMAIL="user-runtime-dir@1000.servic"]user-runtime-dir@1000.servic[/EMAIL]e                                            
   16ms systemd-update-utmp-runlevel.service                                     
   14ms alsa-restore.service                                                     
   10ms rtkit-daemon.service                                                     
    9ms sys-fs-fuse-connections.mount                                            
    4ms sys-kernel-config.mount                                                  
    4ms snapd.socket
```
 
Here the critical-chain results also:
```
systemd-analyze critical-chain
The time when unit became active or started is printed after the "@" character.
The time the unit took to start is printed after the "+" character.

graphical.target @51.826s
&#9492;&#9472;multi-user.target @51.826s
  &#9492;&#9472;kerneloops.service @18.921s +379ms
    &#9492;&#9472;network-online.target @18.847s
      &#9492;&#9472;network.target @18.847s
        &#9492;&#9472;wpa_supplicant.service @15.333s +3.513s
          &#9492;&#9472;dbus.service @15.088s
            &#9492;&#9472;basic.target @14.995s
              &#9492;&#9472;sockets.target @14.994s
                &#9492;&#9472;snapd.socket @14.990s +4ms
                  &#9492;&#9472;sysinit.target @14.898s
                    &#9492;&#9472;swap.target @14.898s
                      &#9492;&#9472;dev-disk-by\x2duuid-ee5aecd0\x2d8f8b\x2d461c\x2db8e0\x2d401f0dd6f584.swap @14.804s +93ms
                        &#9492;&#9472;dev-disk-by\x2duuid-ee5aecd0\x2d8f8b\x2d461c\x2db8e0\x2d401f0dd6f584.device @14.801s
```

So how can I reduce my boot speed?

---

### Post by raleigh3 on 2020-07-23
If your boot time is 1 minute, I would be very happy.

---

### Post by Dennis N on 2020-07-23
Using an SSD would improve your boot time. Think about getting one to replace your HDD.

---

### Post by ActionParsnip on 2020-07-23
If you reboot and run:
```

dmesg -T > ~/Desktop/Bootup.txt

```

Open the file in your favourite text editor and look for large gaps in time. This will show what is slowing the boot

---

### Post by webaake on 2020-07-23
```
24.428s apport-autoreport.service
```

There's one service you can do without. And it has a big time gap.

Do you use snap? Do you use Avahi? Do you use Wifi? There are a few systemd services which you can disable. Ubuntu installs A "ONE SIZE FITS ALL" and usually you can disable those that you really don't need.

Here's a good example of plymouth-quit-wait.service:

[https://askubuntu.com/questions/1119167/slow-boot-issue-due-to-plymouth-quit-wait-service-ubuntu-18-04](https://askubuntu.com/questions/1119167/slow-boot-issue-due-to-plymouth-quit-wait-service-ubuntu-18-04)

It's long boot time is a bit misleading but still, it can be disabled and save some boot time.

---

### Post by webaake on 2020-07-23
How to disable a service:
```
To disable it, you call systemctl disable <service>. Without arguments, systemctl displays the current state, which is obviously not possible in a chroot.

Alternatively, you can also go to /etc/systemd/system/ and remove the symlink to your service (probably in the multi-user.target.wants folder).

If it is a service that is enabled by default, you need to create a symlink (named <service>.service) to /dev/null to disable it. Where the symlink needs to be depends on where in /lib/systemd/system the service is enabled.
```

To disable one level more you can "mask" it.

---

### Post by HermanAB on 2020-07-23
Why reboot, if you can use suspend or hibernate?

---

