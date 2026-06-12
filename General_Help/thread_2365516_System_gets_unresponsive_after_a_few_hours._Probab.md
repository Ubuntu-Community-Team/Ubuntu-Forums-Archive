---
title: "System gets unresponsive after a few hours. Probably memory related, but why?"
date: 2017-07-07
forum: General Help
---

### Post by henrik-nyholm on 2017-07-07
Hi,

I have a HTPC running Ubuntu 17.04.

Since upgrading to 17.04 it has started to get unresponsive after a few hours uptime. It had issues before but then it could run for several weeks before it needed a reboot, so never bothered to figure out the problem then.

I have tried disabling services, like lightdm, etc. but that will only make the system hold out a few hours more before it runs out of memory.

 [ATTACH=CONFIG]275901[/ATTACH]

I have saved the output from top sorted by %MEM after boot and shortly before the system got unresponsive, but maybe this isn't the right tool to find out where the ram went?

```

top - 11:06:10 up 10min,  1 user,  load average: 1,42, 1,37, 0,87
Tasks: 148 total,  1 running, 147 sleeping,   0 stopped,   0 zombie
%Cpu(s):  3,9 us, 3,3 sy,  0,0 ni, 84,2 id,  8,6 wa,  0,0 hi,  0,0 si,  0,0 st
KiB Mem :  2045580total,   872020 free,   411960 used,   761600 buff/cache
KiB Swap:  2095100total,  2095100 free,        0 used.  1460952 avail Mem 


  PID USER      PR NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND              
 1620 mysql     20  0 2103660 181080  19468 S   7,9  8,9   0:10.70 mysqld               
 1734 root      20  0  335416  29996  22908 S   0,0  1,5   0:00.17 apache2              
 1748 www-data  20  0  341120  26740  13800 S   0,0  1,3   0:01.54 apache2              
 2350 www-data  20  0  341056  26668  13784 S   0,0  1,3   0:01.36 apache2              
 2621 www-data  20  0  341048  25692  12768 S   0,0  1,3   0:01.11 apache2              
 3497 www-data  20  0  341112  25616  12692 S   0,0  1,3   0:00.42 apache2              
 2351 www-data  20  0  341104  25584  12656 S   0,0  1,3   0:00.97 apache2              
 3199 www-data  20  0  339984  24584  12844 S   0,0  1,2   0:00.59 apache2              
 1749 www-data  20  0  339988  24460  12688 S   0,0  1,2   0:01.27 apache2              
 3532 www-data  20  0  339988  23612  11852 S   0,0  1,2   0:00.43 apache2              
 3657 www-data  20  0  338988  23548  12692 S   0,0  1,2   0:00.23 apache2              
 3531 www-data  20  0  339860  23452  11724 S   0,0  1,1   0:00.38 apache2              
  713 root      20  0  615628  18156  13472 S   0,0  0,9   0:11.07 NetworkManager       
  951 root      20  0  346368  16224  13612 S   0,0  0,8   0:00.02 smbd                 
  784 root      20  0  296112  10308   8944 S   0,0  0,5   0:00.09 cups-browsed         
  845 root      20  0  357168  10084   8756 S   0,0  0,5   0:00.39 upowerd              
  681 root      20  0 1020600   9512   6808 S   0,0  0,5   0:00.13 repowerd             
  686 root      20  0  422860   9456   7552 S   0,0  0,5   0:00.13 ModemManager         
 1741 snmp      20  0   62856   9016   4448 S   0,0  0,4   0:01.00 snmpd                
 4208 www-data  20  0  335448   9012   1916 S   0,0  0,4   0:00.00 apache2              
    1 root      20  0  205368   7724   5400 S   0,0  0,4   0:04.13 systemd              
  683 root      20  0  100764   7700   6528 S   0,0  0,4   0:00.04 cupsd                
  708 root      20  0  288824   7608   6080 S   0,0  0,4   0:00.48 accounts-daemon      
 1751 root      20  0  103564   6960   5972 S   0,0  0,3   0:00.06 sshd                 
 1794 henrik    20  0   65244   6816   5740 S   0,0  0,3   0:00.12 systemd              
  958 root      20  0  346376   6764   4152 S   0,0  0,3   0:00.00 lpqd      



top - 17:59:30 up 7:03,  1 user,  load average: 2,40, 2,39, 2,07
Tasks: 148 total,  1 running, 147 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0,8 us, 0,5 sy,  0,0 ni, 98,4 id,  0,2 wa,  0,0 hi,  0,0 si,  0,0 st
KiB Mem :  2045580total,    67452 free,  1925604 used,    52524 buff/cache
KiB Swap:  2095100total,  1855220 free,   239880 used.    16656 avail Mem 


  PID USER      PR NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND              
 1620 mysql     20  0 2300268  54344   2520 S   0,0  2,7   5:51.44 mysqld               
26886 www-data  20  0  341112  13588   6200 S   0,0  0,7   0:00.82 apache2              
27242 www-data  20  0  340016  13576   6056 S   0,0  0,7   0:00.63 apache2              
26655 www-data  20  0  341132  13320   5896 S   0,0  0,7   0:00.88 apache2              
25149 www-data  20  0  341124  13252   5596 S   0,0  0,6   0:01.37 apache2              
13202 www-data  20  0  341120  12444   5628 S   0,0  0,6   0:03.49 apache2              
29309 www-data  20  0  337812  11792   6236 S   0,0  0,6   0:00.19 apache2              
25895 www-data  20  0  341048   8752   5776 S   0,0  0,4   0:00.96 apache2              
  713 root      20  0  615820   5348   1808 D   2,6  0,3  11:15.38 NetworkManager       
  303 root      20  0   59652   2612   2444 S   0,3  0,1   1:05.64 systemd-journal      
    1 root      20  0  205368   2464   2208 S   0,0  0,1   0:05.50 systemd              
  691 message+  20  0   46292   1684   1124 S   0,7  0,1   1:53.74 dbus-daemon          
28655 www-data  20  0  337812   1656   1656 S   0,0  0,1   0:00.16 apache2              
 1741 snmp      20  0   62856   1560   1228 D   0,3  0,1   0:46.05 snmpd                
  711 root      20  0   46552   1460   1460 S   0,0  0,1   0:00.28 systemd-logind       
 2065 henrik    20  0   46944   1372    920 R   0,7  0,1   3:19.10 top                  
22380 www-data  20  0  341120   1364   1360 S   0,0  0,1   0:01.38 apache2              
29870 www-data  20  0  335448   1320   1296 S   0,0  0,1   0:00.00 apache2              
 1577 systemd+  20  0   49772   1264   1112 S   0,3  0,1   0:40.31 systemd-resolve      
  405 systemd+  20  0   48836   1240   1096 S   0,3  0,1   0:18.80 systemd-network      
 1734 root      20  0  335416   1232   1196 S   0,0  0,1   0:01.41 apache2              
 1683 root      20  0  261324   1216   1096 S   0,0  0,1   0:00.78 nmbd                 
  951 root      20  0  346364   1208   1208 S   0,0  0,1   0:00.21 smbd                 
  846 root      20  0  286312   1140   1140 S   0,0  0,1   0:00.07 polkitd              
 1794 henrik    20  0   65244   1136   1136 S   0,0  0,1   0:00.14 systemd              
681 root      20  0 1020600   1096   1096 S   0,0  0,1   0:00.14 repowerd    

```

I am not sure how to troubleshoot this problem.

Regards,
Henrik

---

### Post by farrinux on 2017-07-07
Try these- [https://www.linux.com/blog/5-commands-check-memory-usage-linux](https://www.linux.com/blog/5-commands-check-memory-usage-linux)
[http://www.upubuntu.com/2013/01/how-to-free-up-unused-memory-in.html](http://www.upubuntu.com/2013/01/how-to-free-up-unused-memory-in.html)
[https://askubuntu.com/questions/507699/why-does-ubuntu-not-seem-to-release-memory](https://askubuntu.com/questions/507699/why-does-ubuntu-not-seem-to-release-memory)
 and lastly 
[https://www.tecmint.com/clear-ram-memory-cache-buffer-and-swap-space-on-linux/](https://www.tecmint.com/clear-ram-memory-cache-buffer-and-swap-space-on-linux/)
After a quick look at these search results, most of them use the command line in terminal. 

You stated you upgraded.  Was that by the upgrade route or by a clean install? Also have you done an update since going to 17.04? If not that is where I would start.

---

### Post by henrik-nyholm on 2017-07-07
I will add 'sync && echo 3 | tee /proc/sys/vm/drop_caches' as a cron job every 2h and see if it gets any better.

> [COLOR=#000000]You stated you upgraded. Was that by the upgrade route or by a clean install? Also have you done an update since going to 17.04? If not that is where I would start.[/COLOR]

This HTPC started as a Hardy minimal installation and then I followed instructions from a webpage to install XBMC (now called Kodi). It has never been reinstalled, but I have upgraded to all LTS and most of the releases in-between, and I do apt-get update/upgrade regularly.

The memory issue started maybe a year ago, April 2016, and got worse after the latest release. 
[ATTACH=CONFIG]275902[/ATTACH]

---

### Post by henrik-nyholm on 2017-10-09
My memory problem disappeared after upgrading to 17.10.

---

### Post by oldspammer on 2017-10-21
My system also gets unresponsive.

When I did a top in a terminal window as root, 99.7% CPU was being used on systemd-journal and it was doing so for several minutes straight.

My computer's hard disk activity light was almost constantly on. I have an Intel Core i7 2600 Sandy Bridge with 32 Gbytes of DDR3 1866 w/Seagate 2 Tbyte HDD SATA2.

Just before this happened I had FireFox reporting an unresponsive script with the active tab open on the smplayer page that comes up right after it gets installed, banshee, smplayer, rhythmbox, kodi, vlcmedia player, streamtuner2 all loaded and idle.

When this was happening, my mouse cursor would not move for about 30 to 60 seconds at a time, then it would suddenly jump randomly across the screen where I obviously did not want it going.  It took keyboard shortcut "ctrl-Alt-T" to launch the terminal window, then "sudo su -" to do root commands like "top".

To get the thing back under control the only thing I quickly thought that I could do was a "shutdown -r now" to reboot gracefully.

When the system came back up, it looked like kodi rather than gnome was the xwindows window manager. During system setup I configured for auto login, but the system forced me to log in with my password then kodi would be running full screen. When I used the power button menu on kodi to exit out, it logged me out. Logging back in got kodi up in full screen mode again. What a pain in the butt?

I used Ctrl-Alt F1 or whatever to get into a regular character screen. I fired up aptitude the package manager and uninstalled kodi as fast as possible. When I switched back to xwindows gui and logged in again, gnome came up. I still think I have to manually log on each time. I'll have to look at the system settings applet to remedy that crap.

In other upgrades that I have done, the installation prompts me whether or not I want to keep "obsolete" packages. This time it did not do so or it asked me in a deceptive way as though these "packages" were now completely incompatible and the system "REQUIRED" their removal. It looks like it got rid of several hundred installations without my actual consent so that I now have a bare bones installation.  This should not ever happen unless these software packages no longer work and shall core dump / segmentation fault if even started... What a nightmare!!?

---

