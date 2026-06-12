---
title: "long boot times in 20.04"
date: 2021-06-17
forum: General Help
---

### Post by Timothy Taylor on 2021-06-17
I recently upgraded to 20.04 from 18.04.
The new installation has always been a slower starter than 18.04, but I'm now experiencing considerable delay from entering the disk encryption password to system log-in.  
Log-in and session start-up seem to proceed normally.

First 10 lines from *systemd-analyze blame*:

```
59.847s snapd.service                                                                            
57.730s udisks2.service                                                                          
30.368s NetworkManager-wait-online.service                                                       
24.138s systemd-journal-flush.service                                                            
12.942s blueman-mechanism.service                                                                
12.627s dev-mapper-vgubuntu\x2d\x2dmate\x2droot.device                                           
 6.163s accounts-daemon.service                                                                  
 6.142s networkd-dispatcher.service                                                              
 3.927s gpu-manager.service                                                                      
 3.874s lightdm.service                                            
```

Which seems consistent with the 1-2 minute waits I'm getting now.
Any ideas?

---

### Post by oldfred on 2021-06-17
Some things to review & see if they apply. 
But using SSD, is a hardware fix for some issues.

Slow Boot --------------------------------
[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)
[https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/](https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/)

[https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster](https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster)

---

### Post by GhX6GZMB on 2021-06-18
Check your UUIDs in grub, fstab and initramfs (and other places if applicable to your system). If they don't match you'll get very long boot times, but not necessarily an error.

This can happen if you do a partial reinstall/format of only / or if you restore a system backup.

---

