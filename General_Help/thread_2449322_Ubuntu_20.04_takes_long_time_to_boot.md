---
title: "Ubuntu 20.04 takes long time to boot"
date: 2020-08-24
forum: General Help
---

### Post by lisandrodm22 on 2020-08-24
Hi everyone, I'm new in the forum so I hope not begin annoying. As the title says, my computer became to take more time to boot, so I checked the outputs of systemd-analyze to see what is taking so much time (my computer used to boot on 10-20 seconds and now is at +50 secs). 
After the boot everything works fine, but I want to solve this to have the previous boot time. 
I will attach the outputs of these commands:

time:
```

Startup finished in 19.940s (firmware) + 4.325s (loader) + 21.873s (kernel) + 5.807s (userspace) = 51.947s 
graphical.target reached after 5.799s in userspace

```

blame (first lines)
```

3.751s NetworkManager-wait-online.service                   
2.568s plymouth-quit-wait.service                           
1.324s snap-kde\x2dframeworks\x2d5\x2dcore18-32.mount       
1.318s snap-snapd-8542.mount                                
1.301s snap-gimp-281.mount                                  
1.245s snap-snapd-8790.mount                                
1.195s snap-flutter-22.mount                                
1.139s snapd.service                                        
1.125s snap-spotify-41.mount                                
1.076s snap-core18-1885.mount                               
1.020s snap-canonical\x2dlivepatch-95.mount                 
 935ms snap-gnome\x2d3\x2d34\x2d1804-36.mount               
 879ms snap-core18-1880.mount                               
 871ms snap-gnome\x2d3\x2d34\x2d1804-24.mount               
 869ms snap-snap\x2dstore-433.mount                         
 868ms snap-snap\x2dstore-467.mount                         
 837ms dev-loop0.device                                     
 831ms dev-sda2.device                                      
 829ms snap-gtk\x2dcommon\x2dthemes-1506.mount              
 679ms dev-loop1.device                                     
 656ms snap-core-9665.mount                                 
 632ms snap-android\x2dstudio-90.mount                      
 622ms dev-loop6.device                                     
 612ms snap-gimp-292.mount                                  
 595ms snap-core-9804.mount                                 
 588ms snap-gnome\x2d3\x2d28\x2d1804-128.mount              
 569ms dev-loop5.device                                     
 560ms dev-loop2.device                                     
 555ms dev-loop7.device                                     
 507ms dev-loop3.device                                     
 481ms networkd-dispatcher.service                          
 452ms dev-loop4.device                                     
 440ms snap-flutter-21.mount                                
 412ms dev-loop9.device                                     
 409ms systemd-journal-flush.service                        
 408ms dev-loop8.device                                     
 401ms systemd-logind.service                               
 295ms accounts-daemon.service                              
 285ms udisks2.service                                      
 280ms dev-loop11.device                                    
 272ms grub-initrd-fallback.service                         
 264ms grub-common.service                                  
 263ms dev-loop10.device                                    
 252ms NetworkManager.service 

```

critical-chain
```

graphical.target @5.799s
&#9492;&#9472;multi-user.target @5.799s
  &#9492;&#9472;kerneloops.service @5.790s +8ms
    &#9492;&#9472;network-online.target @5.789s
      &#9492;&#9472;NetworkManager-wait-online.service @2.038s +3.751s
        &#9492;&#9472;NetworkManager.service @1.784s +252ms
          &#9492;&#9472;dbus.service @1.782s
            &#9492;&#9472;basic.target @1.774s
              &#9492;&#9472;sockets.target @1.774s
                &#9492;&#9472;snapd.socket @1.774s +360us
                  &#9492;&#9472;sysinit.target @1.770s
                    &#9492;&#9472;snapd.apparmor.service @1.733s +37ms
                      &#9492;&#9472;apparmor.service @1.668s +64ms
                        &#9492;&#9472;local-fs.target @1.667s
                          &#9492;&#9472;run-snapd-ns-canonical\x2dlivepatch.mnt.mount @2.835s
                            &#9492;&#9472;run-snapd-ns.mount @2.704s
                              &#9492;&#9472;swap.target @349ms
                                &#9492;&#9472;swapfile.swap @279ms +67ms
                                  &#9492;&#9472;systemd-remount-fs.service @267ms +11ms
                                    &#9492;&#9472;systemd-journald.socket @258ms
                                      &#9492;&#9472;-.mount @256ms
                                        &#9492;&#9472;system.slice @256ms
                                          &#9492;&#9472;-.slice @256ms

```

I would really appreciate any help, because I tried solutions around askubuntu and none of them worked for me. Thanks

---

### Post by TheFu on 2020-08-24
The graphical target is only 6 seconds.  How much faster do you need?

How willing are you to break things by going too far?

Is this a desktop or a laptop?
Is it using wifi or wired ethernet?
Looks like the DHCP server on the network might be slow. You don't have to use DHCP.
You don't have to use so many snaps.
You don't have to use a swap file.
Do you actually use livepatch?  That's for systems can absolutely, cannot, be down for months. Heck, I'm running multiple servers for clients and don't use livepatch.  I have scheduled maintenance periods approved weekly and short one approved nightly, though we seldom use the nightly ones.

My blame and critical-chain entries are nothing like yours.

The manpage for blame and critical-chain have warnings about misleading information.
```
       Note that the output might be
       misleading as the initialization of one service might be slow simply because it waits for the
       initialization of another service to complete. Also note: systemd-analyze blame doesn't display
       results for services with Type=simple, because systemd considers such services to be started
       immediately, hence no measurement of the initialization delays can be done. Also note that this
       command only shows the time units took for starting up, it does not show how long unit jobs
       spent in the execution queue.

```and
```
       Note that the output might be misleading as the initialization of services might depend on
       socket activation and because of the parallel execution of units. Also, similar to the blame
       command, this only takes into account the time units spent in "activating" state, and hence
       does not cover units that never went through an "activating" state (such as device units that
       transition directly from "inactive" to "active"). Moreover it does not show information on jobs
       (and in particular not jobs that timed out).
```

---

### Post by ActionParsnip on 2020-08-25
If you reboot and run:

dmesg -T > /tmp/boot.txt; gedit /tmp/boot.txt

Look for large gaps in time, this is where the slowness is and you can concentrate your efforts there

---

### Post by poorguy on 2020-08-25
I never have and never will understand the obsession with boot times. :-k

I get up in the morning and power on my desktop go start my coffee maker.

When I return to my desktop it is ready to use and takes less than one minute.

What's important is how it works when It's in use.

I don't think a computer is that boots up under one minute is anything to be concerned about.

[B]2013 Dell Optiplex XE.
[/B]Intel Core2 Duo E7400 (2.8 GHz)
Intel 4 Series Integrated Graphics.
8.0 GB DDR3 memory.
Western Digital  WD1600AAJS-22PSA0 (149.05 GiB) mechanical hard drive.


Here's my **sys****temd-analyze** output 
```


nelson@Dell-OptiPlex-XE:~$ systemd-analyze
Startup finished in 3.302s (kernel) + 43.703s (userspace) = 47.005s 
graphical.target reached after 43.416s in userspace
nelson@Dell-OptiPlex-XE:~$ 


```

Here's my **systemd-analyze blame **output.
```


nelson@Dell-OptiPlex-XE:~$ systemd-analyze blame
24.827s plymouth-quit-wait.service                           
13.661s snapd.service                                        
11.627s networkd-dispatcher.service                          
11.373s NetworkManager-wait-online.service                   
11.206s accounts-daemon.service                              
 8.281s systemd-journal-flush.service                        
 8.052s udisks2.service                                      
 7.998s dev-sda5.device                                      
 6.493s rsyslog.service                                      
 6.091s NetworkManager.service                               
 5.823s polkit.service                                       
 5.124s apt-daily-upgrade.service                            
 5.043s ModemManager.service                                 
 4.054s avahi-daemon.service                                 
 3.641s switcheroo-control.service                           
 3.503s dev-loop6.device                                     
 3.384s dev-loop1.device                                     
 3.362s thermald.service                                     
 3.358s systemd-logind.service                               
 3.356s wpa_supplicant.service                               
 3.271s apport.service                                       
 3.253s gpu-manager.service                                  
 3.244s dev-loop0.device                                     
 3.242s dev-loop4.device                                     
 3.222s dev-loop2.device                                     
 3.190s dev-loop3.device                                     
 2.965s dev-loop5.device                                     
 2.408s gdm.service                                          
 2.107s ufw.service                                          
 1.882s grub-common.service                                  
 1.532s grub-initrd-fallback.service                         
 1.202s systemd-modules-load.service                         
 1.200s apparmor.service                                     
  980ms systemd-sysusers.service                             
  886ms systemd-udevd.service                                
lines 1-35


```

---

### Post by TheFu on 2020-08-25
Boot times can matter greatly if they are running control systems to help or protect humans.
For a desktop, in a home environment, it really shouldn't matter. Who reboots their systems daily?
```
$ uptime
 10:20:59 up 30 days, 8 min,  6 users,  load average: 2.89, 1.40, 1.06
```
I'd get standby working instead.

OTOH, if it is a laptop and the owner cares about security, then she probably uses whole disk encryption.  Whole disk encryption has security wholes when running, in standby, and definitely when hibernated, so powering completely off is important whenever the laptop gets moved from 1 building to another.  Just walking between University buildings is more risk than I would accept for a system like that. Complete power off for security, which means a reboot in the next class.

But the last 6 months, my main laptop hasn't moved more than a foot, so security and boot speed don't matter.

---

### Post by poorguy on 2020-08-25
> **TheFu said:**
> Boot times can matter greatly if they are running control systems to help or protect humans.

I understand this and this makes damn good sense.

> **TheFu said:**
> 
For a desktop, in a home environment, it really shouldn't matter. Who reboots their systems daily?

I reboot once a week or after installing updates a habit I picked up somewhere and figure it doesn't hurt.


> **TheFu said:**
> 
OTOH, if it is a laptop and the owner cares about security, then she probably uses whole disk encryption.  Whole disk encryption has security wholes when running, in standby, and definitely when hibernated, so powering completely off is important whenever the laptop gets moved from 1 building to another.  Just walking between University buildings is more risk than I would accept for a system like that. Complete power off for security, which means a reboot in the next class.

But the last 6 months, my main laptop hasn't moved more than a foot, so security and boot speed don't matter.

I use desktops and never think about laptops unless the wife is nagging about her Windows 10 laptop although it never leaves the house.

I can understand about boot times when going from building to building to classes and that makes sense.

When I went to college we used slide rules although calculators were around they were expensive and I couldn't afford to buy one.

---

### Post by d4amenace on 2020-08-25
Depends on the CPU as well.  I have an amd8350 and it takes 4-5 minutes  to boot.  I also have an old intel zx8350 processor and it takes 30 seconds.  Que sera sera....

---

