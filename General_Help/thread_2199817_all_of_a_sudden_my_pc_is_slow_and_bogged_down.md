---
title: "all of a sudden my pc is slow and bogged down"
date: 2014-01-15
forum: General Help
---

### Post by alteahandle-launchpad on 2014-01-15
in the last 2 or 3 days my computer has become very slow. Webpages take a while (sometimes minutes) to load (yet I have about 40mbps down/2mbps up), youtube videos are unbearably slow and xbmc pins the cpu, menus studder and videos choke.
before, surfing was reasonably fast, I could play youtube videos in 720 or even 1080 and xbmc was buttery smooth
chromium will also pin the cpu if a page has videos on it (like youtube)

I suspect video acceleration has ceased but when I log in the nVidia splash page flashes.

Asus 1015pn, Voyager (xubuntu) 12.04, chromium

hopefully this is of help:

```
glxinfo | grep renderer
OpenGL renderer string: ION/PCIe/SSE2
```

[COLOR=#000000][FONT=arial]/var/log/apt/history.log
[/FONT][/COLOR]> 

Start-Date: 2014-01-02  08:14:01
Commandline: aptdaemon role='role-commit-packages' sender=':1.723'
Upgrade: wine-silverlight5.1-installer:i386 (0.8.6~ubuntu12.04.1, 0.8.7-2~ubuntu12.04.1), netflix-desktop:i386 (0.8.6~ubuntu12.04.1, 0.8.7-2~ubuntu12.04.1), wine-browser-installer:i386 (0.8.6~ubuntu12.04.1, 0.8.7-2~ubuntu12.04.1), wine-compholio:i386 (1.7.8-1~ubuntu12.04.1, 1.7.9~ubuntu12.04.1)
End-Date: 2014-01-02  08:15:11


Start-Date: 2014-01-03  08:04:37
Install: linux-headers-3.2.0-58:i386 (3.2.0-58.88, automatic), linux-headers-3.2.0-58-generic:i386 (3.2.0-58.88, automatic), linux-image-3.2.0-58-generic:i386 (3.2.0-58.88)
Upgrade: linux-headers-generic:i386 (3.2.0.57.68, 3.2.0.58.69), linux-image-generic:i386 (3.2.0.57.68, 3.2.0.58.69), linux-libc-dev:i386 (3.2.0-57.87, 3.2.0-58.88), linux-generic:i386 (3.2.0.57.68, 3.2.0.58.69)
End-Date: 2014-01-03  08:11:38


Start-Date: 2014-01-06  20:00:57
Commandline: aptdaemon role='role-commit-packages' sender=':1.177'
Upgrade: libaudclient2:i386 (3.4.2-1~webupd8~precise, 3.4.3-1~webupd8~precise)
End-Date: 2014-01-06  20:01:11


Start-Date: 2014-01-06  20:04:56
Commandline: aptdaemon role='role-commit-packages' sender=':1.177'
Upgrade: libglapi-mesa:i386 (8.0.4-0ubuntu0.6, 8.0.4-0ubuntu0.7), libxfixes3:i386 (5.0-4ubuntu4.1, 5.0-4ubuntu4.2), libqt4-opengl:i386 (4.8.1-0ubuntu4.5, 4.8.1-0ubuntu4.6), libegl1-mesa:i386 (8.0.4-0ubuntu0.6, 8.0.4-0ubuntu0.7), libqt4-declarative:i386 (4.8.1-0ubuntu4.5, 4.8.1-0ubuntu4.6), libegl1-mesa-drivers:i386 (8.0.4-0ubuntu0.6, 8.0.4-0ubuntu0.7), gir1.2-gtk-3.0:i386 (3.4.2-0ubuntu0.5, 3.4.2-0ubuntu0.6), python-software-properties:i386 (0.82.7.6, 0.82.7.7), qdbus:i386 (4.8.1-0ubuntu4.5, 4.8.1-0ubuntu4.6), libpixman-1-0:i386 (0.24.4-1ubuntu0.1, 0.30.2-1ubuntu0.0.0.0.1), libqt4-sql-mysql:i386 (4.8.1-0ubuntu4.5, 4.8.1-0ubuntu4.6), libqt4-dbus:i386 (4.8.1-0ubuntu4.5, 4.8.1-0ubuntu4.6), libglu1-mesa:i386 (8.0.4-0ubuntu0.6, 8.0.4-0ubuntu0.7), libqt4-qt3support:i386 (4.8.1-0ubuntu4.5, 4.8.1-0ubuntu4.6), bc:i386 (1.06.95-2, 1.06.95-2ubuntu1), libdrm-intel1:i386 (2.4.43-0ubuntu0.0.3, 2.4.46-1ubuntu0.0.0.1), dc:i386 (1.06.95-2, 1.06.95-2ubuntu1), libxatracker1:i386 (8.0.4-0ubuntu0.6, 8.0.4-0ubuntu0.7), libqt4-xmlpatterns:i386 (4.8.1-0ubuntu4.5, 4.8.1-0ubuntu4.6), libgtk-3-common:i386 (3.4.2-0ubuntu0.5, 3.4.2-0ubuntu0.6), libgles2-mesa:i386 (8.0.4-0ubuntu0.6, 8.0.4-0ubuntu0.7), libgbm1:i386 (8.0.4-0ubuntu0.6, 8.0.4-0ubuntu0.7), libdrm2:i386 (2.4.43-0ubuntu0.0.3, 2.4.46-1ubuntu0.0.0.1), libosmesa6:i386 (8.0.4-0ubuntu0.6, 8.0.4-0ubuntu0.7), libqtcore4:i386 (4.8.1-0ubuntu4.5, 4.8.1-0ubuntu4.6), libgtk-3-0:i386 (3.4.2-0ubuntu0.5, 3.4.2-0ubuntu0.6), libdrm-nouveau1a:i386 (2.4.43-0ubuntu0.0.3, 2.4.46-1ubuntu0.0.0.1), libqt4-sql-sqlite:i386 (4.8.1-0ubuntu4.5, 4.8.1-0ubuntu4.6), libgail-3-0:i386 (3.4.2-0ubuntu0.5, 3.4.2-0ubuntu0.6), libqt4-sql:i386 (4.8.1-0ubuntu4.5, 4.8.1-0ubuntu4.6), libqt4-svg:i386 (4.8.1-0ubuntu4.5, 4.8.1-0ubuntu4.6), software-properties-common:i386 (0.82.7.6, 0.82.7.7), libqt4-xml:i386 (4.8.1-0ubuntu4.5, 4.8.1-0ubuntu4.6), libdrm-radeon1:i386 (2.4.43-0ubuntu0.0.3, 2.4.46-1ubuntu0.0.0.1), software-properties-gtk:i386 (0.82.7.6, 0.82.7.7), libqt4-network:i386 (4.8.1-0ubuntu4.5, 4.8.1-0ubuntu4.6), libqt4-designer:i386 (4.8.1-0ubuntu4.5, 4.8.1-0ubuntu4.6), libgl1-mesa-dri:i386 (8.0.4-0ubuntu0.6, 8.0.4-0ubuntu0.7), libqtgui4:i386 (4.8.1-0ubuntu4.5, 4.8.1-0ubuntu4.6), libgl1-mesa-glx:i386 (8.0.4-0ubuntu0.6, 8.0.4-0ubuntu0.7), libgtk-3-bin:i386 (3.4.2-0ubuntu0.5, 3.4.2-0ubuntu0.6), libopenvg1-mesa:i386 (8.0.4-0ubuntu0.6, 8.0.4-0ubuntu0.7), libqt4-script:i386 (4.8.1-0ubuntu4.5, 4.8.1-0ubuntu4.6), libxi6:i386 (1.6.0-0ubuntu2.1, 1.7.1.901-1ubuntu1~precise1), libgles1-mesa:i386 (8.0.4-0ubuntu0.6, 8.0.4-0ubuntu0.7)
End-Date: 2014-01-06  20:07:17


Start-Date: 2014-01-07  07:46:06
Upgrade: gir1.2-appindicator3-0.1:i386 (0.4.92-0ubuntu1, 0.4.92-0ubuntu1.1), libappindicator0.1-cil:i386 (0.4.92-0ubuntu1, 0.4.92-0ubuntu1.1), python-appindicator:i386 (0.4.92-0ubuntu1, 0.4.92-0ubuntu1.1), libappindicator1:i386 (0.4.92-0ubuntu1, 0.4.92-0ubuntu1.1), libappindicator3-1:i386 (0.4.92-0ubuntu1, 0.4.92-0ubuntu1.1)
End-Date: 2014-01-07  07:46:28


Start-Date: 2014-01-07  19:29:19
Commandline: apt-get install xfce4-timer-plugin
Install: xfce4-timer-plugin:i386 (0.6.3-1ubuntu1)
End-Date: 2014-01-07  19:29:31


Start-Date: 2014-01-07  19:30:35
Commandline: apt-get autoremove
Remove: linux-headers-3.2.0-52-generic:i386 (3.2.0-52.78), linux-headers-3.2.0-52:i386 (3.2.0-52.78), linux-headers-3.2.0-53:i386 (3.2.0-53.81), linux-headers-3.2.0-54:i386 (3.2.0-54.82), linux-headers-3.2.0-56:i386 (3.2.0-56.86), libreoffice-l10n-zh-cn:i386 (3.5.7-0ubuntu5), libreoffice-help-zh-cn:i386 (3.5.7-0ubuntu5), libreoffice-l10n-en-gb:i386 (3.5.7-0ubuntu5), linux-headers-3.2.0-53-generic:i386 (3.2.0-53.81), libreoffice-l10n-en-za:i386 (3.5.7-0ubuntu5), libreoffice-help-en-gb:i386 (3.5.7-0ubuntu5), libreoffice-help-en-us:i386 (3.5.7-0ubuntu5), linux-headers-3.2.0-56-generic:i386 (3.2.0-56.86), mythes-en-au:i386 (2.1-5.3ubuntu1), mythes-en-us:i386 (3.3.0-2ubuntu3), openoffice.org-hyphenation:i386 (0.6), hyphen-en-us:i386 (2.8.3-1), linux-headers-3.2.0-54-generic:i386 (3.2.0-54.82)
End-Date: 2014-01-07  19:31:17


Start-Date: 2014-01-08  07:46:59
Upgrade: iproute:i386 (20111117-1ubuntu2, 20111117-1ubuntu2.1), libxfont1:i386 (1.4.4-1, 1.4.4-1ubuntu0.1)
End-Date: 2014-01-08  07:47:19


Start-Date: 2014-01-09  19:18:39
Commandline: aptdaemon role='role-commit-packages' sender=':1.152'
Upgrade: wine-compholio:i386 (1.7.9~ubuntu12.04.1, 1.7.10~ubuntu12.04.1)
End-Date: 2014-01-09  19:19:08


Start-Date: 2014-01-09  19:22:35
Commandline: aptdaemon role='role-commit-packages' sender=':1.152'
Upgrade: duplicity:i386 (0.6.18-0ubuntu3.3, 0.6.18-0ubuntu3.4), openssl:i386 (1.0.1-4ubuntu5.10, 1.0.1-4ubuntu5.11), libssl1.0.0:i386 (1.0.1-4ubuntu5.10, 1.0.1-4ubuntu5.11)
End-Date: 2014-01-09  19:23:07


Start-Date: 2014-01-10  07:47:43
Upgrade: libck-connector0:i386 (0.4.5-2, 0.4.5-2ubuntu0.1), libpam-ck-connector:i386 (0.4.5-2, 0.4.5-2ubuntu0.1), consolekit:i386 (0.4.5-2, 0.4.5-2ubuntu0.1)
End-Date: 2014-01-10  07:48:01


Start-Date: 2014-01-10  19:57:10
Commandline: aptdaemon role='role-commit-packages' sender=':1.152'
Upgrade: base-files:i386 (6.5ubuntu6.6, 6.5ubuntu6.7)
End-Date: 2014-01-10  19:58:36


Start-Date: 2014-01-14  08:01:49
Upgrade: language-pack-zh-hans:i386 (12.04+20130128, 12.04+20140106), bind9-host:i386 (9.8.1.dfsg.P1-4ubuntu0.7, 9.8.1.dfsg.P1-4ubuntu0.8), language-pack-en-base:i386 (12.04+20130128, 12.04+20140106), dnsutils:i386 (9.8.1.dfsg.P1-4ubuntu0.7, 9.8.1.dfsg.P1-4ubuntu0.8), language-pack-kde-en:i386 (12.04+20130128, 12.04+20140106), language-pack-gnome-en-base:i386 (12.04+20130128, 12.04+20140106), libdns81:i386 (9.8.1.dfsg.P1-4ubuntu0.7, 9.8.1.dfsg.P1-4ubuntu0.8), language-pack-kde-zh-hans:i386 (12.04+20130128, 12.04+20140106), language-pack-kde-en-base:i386 (12.04+20130128, 12.04+20140106), libisccc80:i386 (9.8.1.dfsg.P1-4ubuntu0.7, 9.8.1.dfsg.P1-4ubuntu0.8), liblwres80:i386 (9.8.1.dfsg.P1-4ubuntu0.7, 9.8.1.dfsg.P1-4ubuntu0.8), libbind9-80:i386 (9.8.1.dfsg.P1-4ubuntu0.7, 9.8.1.dfsg.P1-4ubuntu0.8), libisccfg82:i386 (9.8.1.dfsg.P1-4ubuntu0.7, 9.8.1.dfsg.P1-4ubuntu0.8), language-pack-zh-hans-base:i386 (12.04+20130128, 12.04+20140106), language-pack-en:i386 (12.04+20130128, 12.04+20140106), libisc83:i386 (9.8.1.dfsg.P1-4ubuntu0.7, 9.8.1.dfsg.P1-4ubuntu0.8), language-pack-kde-zh-hans-base:i386 (12.04+20130128, 12.04+20140106), language-pack-gnome-en:i386 (12.04+20130128, 12.04+20140106)
End-Date: 2014-01-14  08:05:34


Start-Date: 2014-01-14  19:31:35
Commandline: aptdaemon role='role-commit-packages' sender=':1.97'
Upgrade: grub-customizer:i386 (4.0.3-0ubuntu1~ppa1p, 4.0.4-0ubuntu1~ppa1p)
End-Date: 2014-01-14  19:32:19


Start-Date: 2014-01-14  19:42:16
Commandline: aptdaemon role='role-commit-packages' sender=':1.97'
Upgrade: flashplugin-installer:i386 (11.2.202.332ubuntu0.12.04.1, 11.2.202.335ubuntu0.12.04.1)
End-Date: 2014-01-14  19:42:44


[COLOR=#000000][FONT=arial]
[/FONT][/COLOR]

---

### Post by sireangelus on 2014-01-16
have you taken a look at top, or a task manager for anomalous cpu usage?

---

### Post by Bucky Ball on 2014-01-16
Also, just wondering why you're using the i386 install and not the AMD64. Old machine? Bit off topic, but just wondering ... :-k

---

### Post by finny388 on 2014-01-16
> **sireangelus said:**
> have you taken a look at top, or a task manager for anomalous cpu usage?

Yes
When it's chromium the cpu is occupied by chromium and chromium libflashplayer plugins
When it's xbmc it is xbmc

I can post the actual results if you'd like

[COLOR="#000080"]btw, I am the OP, I accidentally logged in with an account I created in error when SSO was introduced. That and lastpass created the mix up.[/COLOR]

---

### Post by finny388 on 2014-01-16
> **Bucky Ball said:**
> Also, just wondering why you're using the i386 install and not the AMD64. Old machine? Bit off topic, but just wondering ... :-k

Basically an 'if it's not broken' kind of thing

It not a powerful machine with an intel atom n550 and 2nd gen ION discrete graphics

But when vdpau is employed it plays 1080 video like a champ and that is my number one priority. (until I can save up enough to justify a new pc) [-o<

---

### Post by finny388 on 2014-01-16
top: idle, chromium, xbmc

Idle: terminal, leafpad
```
top - 20:13:09 up 1 day, 13:04,  1 user,  load average: 1.22, 3.44, 2.92
Tasks: 163 total,   1 running, 161 sleeping,   0 stopped,   1 zombie
Cpu(s):  0.2%us,  0.3%sy,  0.0%ni, 98.8%id,  0.5%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   2061216k total,  1308376k used,   752840k free,   167980k buffers
Swap:  5119996k total,    22372k used,  5097624k free,   827992k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4456 root      20   0 81316  51m  12m S    1  2.6 192:05.89 Xorg               
 4326 frank     20   0  2852 1180  896 R    1  0.1   0:00.10 top                
 4756 frank     20   0 60336 3720 2548 S    0  0.2  10:39.92 conky              
 5701 frank     20   0  145m  19m  11m S    0  1.0   7:11.83 xfce4-terminal     
20282 root      20   0     0    0    0 S    0  0.0   0:02.84 kworker/3:1        
    1 root      20   0  3676 1532  924 S    0  0.1   0:02.03 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.05 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:57.68 ksoftirqd/0        
    6 root      RT   0     0    0    0 S    0  0.0   0:26.14 migration/0        
    7 root      RT   0     0    0    0 S    0  0.0   0:05.78 watchdog/0         
    8 root      RT   0     0    0    0 S    0  0.0   0:15.31 migration/1        
   10 root      20   0     0    0    0 S    0  0.0   0:11.44 ksoftirqd/1        
   12 root      RT   0     0    0    0 S    0  0.0   0:01.39 watchdog/1         
   13 root      RT   0     0    0    0 S    0  0.0   0:07.04 migration/2        
   15 root      20   0     0    0    0 S    0  0.0   0:31.12 ksoftirqd/2        
   16 root      RT   0     0    0    0 S    0  0.0   0:01.38 watchdog/2         
   17 root      RT   0     0    0    0 S    0  0.0   0:13.33 migration/3    
```

XBMC (not playing just at the 'home' screen)
```
top - 20:07:10 up 1 day, 12:58,  1 user,  load average: 4.59, 4.29, 2.68
Tasks: 164 total,   3 running, 160 sleeping,   0 stopped,   1 zombie
Cpu(s): 47.2%us, 25.5%sy,  0.5%ni, 18.5%id,  0.0%wa,  0.0%hi,  8.3%si,  0.0%st
Mem:   2061216k total,  1396124k used,   665092k free,   166780k buffers
Swap:  5119996k total,    22372k used,  5097624k free,   826676k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
32063 frank     20   0  519m 116m  45m R  150  5.8  20:10.80 xbmc.bin           
 4456 root      20   0 80164  51m  12m S   64  2.5 189:21.46 Xorg               
 2390 frank      9 -11  153m 3900 2820 S   49  0.2  65:18.91 pulseaudio         
 2619 frank     20   0  2852 1192  896 R   21  0.1   0:25.21 top                
 5701 frank     20   0  106m  16m  10m S   14  0.8   6:07.42 xfce4-terminal     
 4756 frank     20   0 60336 3720 2548 S   12  0.2  10:14.77 conky              
 4593 frank     20   0 97924  14m 9332 R    9  0.7  33:41.86 xfwm4              
 4617 frank     20   0  103m  13m 7388 S    9  0.6   7:14.59 avant-window-na    
31915 root      20   0     0    0    0 S    5  0.0   0:07.87 kworker/0:1        
 1433 root      35  15  7572 4744  720 S    3  0.2   9:08.18 preload            
 4755 frank     20   0  111m  19m  11m S    1  1.0   1:37.65 python             
24725 root      20   0     0    0    0 S    1  0.0   0:02.22 kworker/1:1        
    7 root      RT   0     0    0    0 S    0  0.0   0:05.39 watchdog/0         
  233 root      20   0     0    0    0 S    0  0.0   0:31.15 usb-storage        
  247 root      20   0     0    0    0 S    0  0.0   0:20.68 jbd2/sda9-8        
  249 root      20   0     0    0    0 S    0  0.0   0:11.76 flush-8:0          
 2692 root      20   0     0    0    0 S    0  0.0   0:04.79 kworker/0:2 
``` 

chromium with youtube playing (chromium with no videos yield system wide total 1- 20% cpu i.e. as I'm typing this with only this webpage open cpu is 2%)
```
top - 20:17:29 up 1 day, 13:08,  1 user,  load average: 4.95, 4.07, 3.25
Tasks: 184 total,   5 running, 178 sleeping,   0 stopped,   1 zombie
Cpu(s): 82.1%us, 14.2%sy,  0.0%ni,  2.2%id,  0.0%wa,  0.0%hi,  1.5%si,  0.0%st
Mem:   2061216k total,  1769932k used,   291284k free,   120048k buffers
Swap:  5119996k total,    23984k used,  5096012k free,   776508k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                          
 5179 frank     20   0  524m 157m  30m R  189  7.8   1:13.51 chromium-browse                  
 4850 frank     20   0  601m 112m  48m R   68  5.6   2:32.02 chromium-browse                  
 5099 frank     20   0  232m  65m  24m S   37  3.3   1:42.58 chromium-browse                  
 4456 root      20   0 82280  52m  13m S   27  2.6 192:58.54 Xorg                             
 5107 frank     20   0  234m  64m  24m R   15  3.2   1:36.58 chromium-browse                  
   37 root      20   0     0    0    0 S   13  0.0   5:29.97 kswapd0                          
 5120 frank     20   0  256m 101m  37m S    8  5.1   1:07.53 chromium-browse                  
 2390 frank      9 -11  153m 3896 2816 S    7  0.2  66:57.69 pulseaudio                       
 5038 frank     20   0  202m  31m  19m S    6  1.6   0:05.23 chromium-browse                  
 5086 frank     20   0  233m  67m  25m S    4  3.4   0:20.20 chromium-browse                  
 5701 frank     20   0  145m  19m  11m S    4  1.0   7:13.74 xfce4-terminal                   
 4326 frank     20   0  2852 1180  896 R    4  0.1   0:05.44 top                              
 4593 frank     20   0 97924  14m 9288 S    3  0.7  34:14.43 xfwm4                            
  960 root      20   0  7584 1572  672 S    2  0.1  36:26.43 mount.ntfs-3g                    
 4756 frank     20   0 60336 3716 2544 S    2  0.2  10:42.12 conky                            
 3658 root      20   0     0    0    0 S    1  0.0   0:02.55 kworker/0:0                      
 4617 frank     20   0  103m  12m 7340 S    1  0.6   7:33.80 avant-window-na
```

---

### Post by Topsiho on 2014-01-17
Using XBMC or Chromium, the processor is used for more than 100% of the time (whatever that means).

You state that Xubuntu worked well before, but now it does not. So something has changed.
Either Xubuntu has changed, e.g. after an update. But than you'll see more people complain that Xubuntu has slowed down.
Or the hardware (situation) has changed. I am thinking now of a disk that is almost full.
So you could try how much hard disk space you still have. In a terminal you type: df -h, and see how much hard disk space is used, and how much is available for use.

To free up some space you could type (in a terminal): sudo apt-get clean (see man apt-get). This removes all downloaded update files from your computer, that after the update are not of any use. After many updates this frees quite an amount of space in a computer with a small hard disk.
If you want you could also try sudo apt-get autoremove, to remove any files that are not used anymore.

Topsiho

---

### Post by slooksterpsv on 2014-01-17
You may want to check and see if there's an updated driver for the nVidia card. If it did an update for a new kernel that the kernel couldn't load the nVidia driver, then it may need an updated driver or you can go back to an older kernel version.

EDIT: Oh I had this problem before, I think it was something where I had to enable compositing or disable compositing for XFCE, if that wasn't it it was a newer driver.

---

### Post by finny388 on 2014-01-17
Thanks Topsiho

You may be on to something
I checked space this morning and the OS is fine (16GB used of 44GB)
But the 2TB external usb drive I use for the majority of my storage is at 98% with 50GB free.

Not sure why that would affect youtube but it's worth trying.

I'll be able to look into that this weekend.

Thanks for the apt-get tips. I use clean and autoremove once in a while and they clean up nicely.

---

### Post by mansonfan78 on 2014-01-17
A couple of days ago I noticed extremely laggy video playback in flash.  I checked nvidia-settings and vdpau was gone.  No updates were installed for the past several days, so have no idea what caused it.  Reinstalled the video driver and now everything is working properly.  Perhaps you experienced something similar.

---

### Post by finny388 on 2014-01-19
> **mansonfan78 said:**
> A couple of days ago I noticed extremely laggy video playback in flash.  I checked nvidia-settings and vdpau was gone.  No updates were installed for the past several days, so have no idea what caused it.  Reinstalled the video driver and now everything is working properly.  Perhaps you experienced something similar.

Making ext hard drive space or disconnecting it all together didn't fix it

At one point the whole pc froze as it was trying to play a youtube video with the audio in an infinite loop of a 0.5 sec audio portion.

Checked additional drivers. I was using 304 and 309 was available so I activated it.
Now I couldn't get x to start in reboot so I reinstalled:
```
sudo apt-get --purge remove nvidia*
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings
```

(now the login screen accepted my pw but then just looped back to login - eventually I chowned ~/.Xauthority to my id and it fixed it)

So back to 304 and right back where I started.

 where do you see vdpau in nvidia-settings?
 what versions did you have and upgrade to?
 should I use the ubuntu-x-swat ppa?

---

### Post by mansonfan78 on 2014-01-19
I'm using the 331.20 driver from nvidia's website.  Never saw anything about vdpau in the older drivers, they just added it recently.

---

### Post by finny388 on 2014-01-19
> **mansonfan78 said:**
> I'm using the 331.20 driver from nvidia's website.  Never saw anything about vdpau in the older drivers, they just added it recently.

can you post a screen shot? I don't see it. Or where do you see it?

thanks

---

### Post by mansonfan78 on 2014-01-19
It's in nvidia-settings.

---

### Post by finny388 on 2014-01-19
okay
thanks
mine doesn't have that entry

added the ppa:ubuntu-x-swat/x-updates and it upgraded me from 304.88 to 304.116

they have 331 drivers too, not sure how to get it

](*,)

i'm not sure what changed either. very frustrating.

---

### Post by finny388 on 2014-01-21
The problem seems to be subsiding but not done

I've had a parallel problem that might be related:
My monitor is my tv and I just want it as a single (sep x) display. Every time I would log in, nvidia (i think it was nvidia-xconfig) would reset xorg.conf and I'd be in twinview with my laptop, I'd change it, save to xorg.conf successfully, reboot, and like Ground Hogs Day, be back in twinview.
I finally fixed that by removing the xorg.conf file, running nvidia-settings with sudo and to my great surprise, it so far has stuck.

Maybe some settings in the xorg.conf file were messing with my driver settings?

It's much better but
In youtube they actually play now, but eventually cpu ramps up and video starts lagging behind audio
In xbmc menus behave nicely, launch a 1080p movie and it plays... for a minute or two, then cpu ramps up and it starts stuttering and chopping well beyond any tolerability.

---

### Post by robin7 on 2014-01-21
[URL="https://sites.google.com/site/easylinuxtipsproject/first-xubuntu"]Do this first in Xubuntu - Easy Linux tips project
[/URL][https://sites.google.com/site/easylinuxtipsproject/first-xubuntu](https://sites.google.com/site/easylinuxtipsproject/first-xubuntu)
[COLOR=#000000]
This site helped me speed things up![/COLOR]

---

### Post by mansonfan78 on 2014-01-21
It sounds like your cpu is having to do all of the video processing (which probably means your video card doesn't have any video acceleration enabled).  Do the 331 drivers show up in "additional drivers"?  If so, they can be enabled by clicking the button next to it.  If not, they can be downloaded from Nvidia's website and installed manually.  If you need to know how to do that I can walk you through the steps.  This is not a guarantee that your problem will be solved, it could be some other issue altogether.  Either way, before messing with video drivers I recommend backing up your hard drive first - they can cause serious problems if the install doesn't go right.

---

### Post by finny388 on 2014-01-22
Thanks Robin7, looks like a great guide. I will have a look.

I'm not hopeful about trying new driver versions being that my machine is relatively mature and was working fine before. On the other hand I've got to keep trying things.

Additional Drivers are as such: (and pretty sure swat-x ppa modified it)
[[IMG]http://imagizer.imageshack.us/v2/xq90/713/t07c.png[/IMG]](https://imageshack.com/i/jtt07cp)

So the driver I have now has no description.

The 3 entries below the 304 selected item all start with:
>  The binary driver provide optimized hardware acceleration of OpenGL applications via a direct-rendering X Server. AGP, PCIe, SLI, TV-out and flat panel displays are also supported.

 This package also includes the source for building the kernel module required by the Xorg driver, and provides NVIDIA's implementation of the Video Decode and presentation API. The latter enables acceleration for GeForce 8 and later series cards for h264 video.

And end with:
1
>  GPUs such as GeForce series 6 or newer are supported.

 Release Notes and supported GPUs: htttp://www.nvidia.com/object/linux-display-ia32-304.108-driver.html

2
>  Release Notes and supported GPUs: htttp://www.nvidia.com/object/linux-display-ia32-319.32-driver.html

3
>  Release Notes and supported GPUs: htttp://www.nvidia.com/object/linux-display-ia32-331.20-driver.html
(They actually say http but the forum wouldn't stop formatting (and abbreviating) them into urls)

Hmm, I'll try 331 tomorrow night

MansonFan78, thank you so much for your help.

---

### Post by finny388 on 2014-01-23
I tried activating 331 from addit. drivers and it installed, I rebooted.

Going back into addit. drivers, it says 'activated but not currently in use'. Surfing around this appears to be buggy statement.

I used "lshw -C display" and it said driver=nvidia which from what I've read means it is in fact in use.

Things are better, (but not to a watchable degree), so it must be the driver/xorg fiddling I've been doing.

I will likely start another OS installation on another partition and start fresh. While I enjoy refreshing with a new distro/version once in a while it feels defeatist to leave this unresolved.

---

### Post by finny388 on 2014-02-02
Oddly, video has improved but not to the point of watch-ability

I've since started a fresh install on another partition of Xubuntu 12.04.3 64bit 
It too has the same troubles with the added issue of XBMC having menu clicking sound but when a video plays it states "Failed to initialize audio device" and no sound (over hdmi)
I even copied ~/.xbmc over to have the same settings (perhaps a conflict of 32 to 64bit?)

It is using nvidia 304.116 from "additional drivers"

---

### Post by finny388 on 2014-02-09
I installed Chrome and it too had no sound thru hdmi
So went into pulse sound settings (from the volume controller in the panel) and turned off Built-In Audio under Configuration tab and voila.

I've accepted low res youtube videos for now

Just need to get xmbc to play smoothly again. I'll try smplayer and see if it can play things well.

---

### Post by Bucky Ball on 2014-02-09
> **finny388 said:**
> 
I've accepted low res youtube videos for now



If you installed Chromium Browser, why? You can install the latest Flash 12, which you can't do in Firefox or Ubuntu any other way. There will be no new releases of Flash for Ubuntu so the newest available Flash for Ubuntu itself, and the last available Flash, is 11.2. Chromium Browser is the only way of getting past this.

You need to install Pepper Flash and then watch Youtube:

[https://duckduckgo.com/?q=install+pepper+flash+chromium](https://duckduckgo.com/?q=install+pepper+flash+chromium)

---

### Post by finny388 on 2014-02-10
> **Bucky Ball said:**
> If you installed Chromium Browser, why? You can install the latest Flash 12, which you can't do in Firefox or Ubuntu any other way. There will be no new releases of Flash for Ubuntu so the newest available Flash for Ubuntu itself, and the last available Flash, is 11.2. Chromium Browser is the only way of getting past this.

You need to install Pepper Flash and then watch Youtube:

[https://duckduckgo.com/?q=install+pepper+flash+chromium](https://duckduckgo.com/?q=install+pepper+flash+chromium)

Do you mean to say Chromium at every instance in your paragraph?

regardless,  I will try to install pepper flash in chromium

---

### Post by finny388 on 2014-02-10
installed smplayer and played a 720p movie. no go, cpu can't handle that
enabled vdpau. much better but the same as xbmc:
  it starts okay and cpu is 10 to 40%, then a few minutes in cpu pins and it starts to studder and gets out of a/v sync until it's just a studdering slide show with stilted sound.

I recently opened up the laptop to blow out the fans. Seems highly unlikely but I'm grasping at straws now. Could I've damaged something that could cause this?


Same problem in 2 different apps (xmbc and smplayer) on two different 12.04 installations.

---

### Post by mansonfan78 on 2014-02-10
After thinking about this, I'm wondering if there might be a problem with your ram.  When you first start playing a video it might still be using good ram, but as it loads more and uses more ram it hits a bad block.  Maybe.  Couldn't hurt to run memtest and see if it finds any problems.

---

### Post by Bucky Ball on 2014-02-10
> **finny388 said:**
> Do you mean to say Chromium at every instance in your paragraph?

regardless,  I will try to install pepper flash in chromium

What you on about? One paragraph, two Chromiums. Anyhow, you're here to get help, I gave you some (a solution to the flash part, actually). Pepperflash will take you to Flash 12+.  

Good luck with it.

---

### Post by finny388 on 2014-02-12
I started testing again on the new install with smplayer.
It played for over 10min a 720p mkv file staying under 10% aggregate cpu and using about 380MB/2GB ram.
I then played an avi with the same success. (some tearing but it played)

Then I tried xbmc. CPU immediately started into the 40's and 50's.
Started the mkv file and it ramped up cpu just as before and in a few min I was back to slide shows.

Oddly, after that smplayer had the same issues again. Then it crashed with a long log message (I will post when I get home) suggesting I had a weak cpu (guilty as charged), changing cache options and some other troubleshooting suggestions.

I tried purging xbmc and reinstalling (as I'd copied .xbmc over from the other OS) to start clean (had to remove .xmbc manually(? I thought purge did that))

So tried it again and no luck.

I ran memtest86+ and went to bed. This morning the laptop was shutdown. Is that normal?

I started it again before leaving the house today.

---

### Post by mansonfan78 on 2014-02-12
Your laptop's power management might have shut it down.  Depending on how much ram you have and how fast your processor is, memtest doesn't really take that long.  Consider running it while you're home (while watching a movie or something), so you can occasionally check on it.

---

### Post by finny388 on 2014-02-12
Ha, that's kind of funny. That's exactly what I did. (just finished watching The Other Guys for the 2nd time. still hilarious)
memtest86+ not so funny:
it shuts off in test 4 at inconsistent times into that test

power mgt. hmm. I'll poke around the bios and see if there's a setting
and I'm going to film the test to see if it flashes message

also, here's the smplayer crash log message from last night:
> /usr/bin/mplayer -noquiet -nofs -nomouseinput -vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau,ffodivxvdpau, -sub-fuzziness 1 -identify -slave -vo vdpau -ao pulse -nokeepaspect -framedrop -nodr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 67108901 -monitorpixelaspect 1 -ass -embeddedfonts -ass-line-spacing 0 -ass-font-scale 1 -ass-styles /home/frank/.config/smplayer/styles.ass -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -subpos 100 -volume 50 -cache 2048 -osdlevel 0 -noslices -channels 2 -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /media/HITACHI/Movies/The Wolverine (2013) [1080p]/The.Wolverine.2013.1080p.BluRay.x264.YIFY.mp4

MPlayer svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing /media/HITACHI/Movies/The Wolverine (2013) [1080p]/The.Wolverine.2013.1080p.BluRay.x264.YIFY.mp4.

Cache fill:  0.00% (0 bytes)   

libavformat version 53.21.1 (external)
Mismatching header version 53.19.0
libavformat file format detected.
ID_VIDEO_ID=0
[lavf] stream 0: video (h264), -vid 0
ID_AUDIO_ID=0
ID_AID_0_LANG=eng
[lavf] stream 1: audio (aac), -aid 0, -alang eng
VIDEO:  [H264]  1920x798  24bpp  23.976 fps  2016.0 kbps (246.1 kbyte/s)
Clip info:
 major_brand: isom
ID_CLIP_INFO_NAME0=major_brand
ID_CLIP_INFO_VALUE0=isom
 minor_version: 1
ID_CLIP_INFO_NAME1=minor_version
ID_CLIP_INFO_VALUE1=1
 compatible_brands: isomavc1
ID_CLIP_INFO_NAME2=compatible_brands
ID_CLIP_INFO_VALUE2=isomavc1
 creation_time: 2013-11-07 13:39:02
ID_CLIP_INFO_NAME3=creation_time
ID_CLIP_INFO_VALUE3=2013-11-07 13:39:02
ID_CLIP_INFO_N=4
Load subtitles in /media/HITACHI/Movies/The Wolverine (2013) [1080p]/
ID_FILENAME=/media/HITACHI/Movies/The Wolverine (2013) [1080p]/The.Wolverine.2013.1080p.BluRay.x264.YIFY.mp4
ID_DEMUXER=lavfpref
ID_VIDEO_FORMAT=H264
ID_VIDEO_BITRATE=2016032
ID_VIDEO_WIDTH=1920
ID_VIDEO_HEIGHT=798
ID_VIDEO_FPS=23.976
ID_VIDEO_ASPECT=2.4060
ID_AUDIO_FORMAT=MP4A
ID_AUDIO_BITRATE=93792
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
ID_START_TIME=0.00
ID_LENGTH=8294.53
ID_SEEKABLE=1
ID_CHAPTERS=0
Opening video filter: [ass auto=1]
Couldn't open video filter 'ass'.
ASS: cannot add video filter
==========================================================================
Forced video codec: ffh264vdpau
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 53.35.0 (external)
Mismatching header version 53.32.2
Selected video codec: [ffh264vdpau] vfm: ffmpeg (FFmpeg H.264 (VDPAU))
==========================================================================
ID_VIDEO_CODEC=ffh264vdpau
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 93.8 kbit/6.11% (ratio: 11724->192000)
ID_AUDIO_BITRATE=93792
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [pulse] 48000Hz 2ch floatle (4 bytes per sample)
ID_AUDIO_CODEC=ffaac
[Mixer] No hardware mixing, inserting volume filter.
Starting playback...
[VD_FFMPEG] Trying pixfmt=0.
Movie-Aspect is 2.41:1 - prescaling to correct movie aspect.
ID_VIDEO_ASPECT=2.4060
VO: [vdpau] 1920x798 => 1920x798 H.264 VDPAU acceleration 
[VD_FFMPEG] XVMC-accelerated MPEG-2.

ID_VIDEO_TRACK=0
ID_AUDIO_TRACK=0



           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.



---

### Post by finny388 on 2014-02-12
No error message when the laptop shuts off.
Not at the same time either so don't think it's power mgt. I don't see any power mgt options in the bios.
I'm running memtest86+ from grub by the way in case you were referring to desktop power mgt.

It's not running hot either, it's sitting on an active laptop cooler.

now to try pepper flash

---

### Post by finny388 on 2014-02-12
I got pepper flash installed

> Adobe Flash Player (2 files) - Version: 12.0.0.44
Shockwave Flash 12.0 r0

Now nothing plays. The page loads, the video seems to load, navigation bar is there but the video simply doesn't play
tried a variety of videos
tried pausing and playing, reloading page, no help

when I go to [HTML]https://www.adobe.com/software/flash/about/[/HTML]
i see the bouncing icon which I think is the flash test
it also says I have 12.0.0.44

any thoughts?

---

### Post by Topsiho on 2014-02-13
Memtest is very straightforward, and if something goes wrong here, a bad memory is indicated, or maybe a bad motherboard.
Memtest should easily continue a number of complete passes. If not, try removing memory sticks one at a time to find the bad one.
If you have only one, then remove it and put another one in, or put it into another slot.
Also a malfunctioning motherboard is possible, as I said before. A memory slot might not function the way it should.
If you have memory sticks which are not the same, then they might possibly not work well together (think timing problems).

Topsiho

---

### Post by Bucky Ball on 2014-02-13
Your issues with Pepper Flash are the stuff of another thread. You will greatly increase your chances of support by posting a new thread about this rather than being buried 30+ deep on a thread with an unrelated title.

Good luck and post a link to the new thread here if you like.

---

### Post by finny388 on 2014-02-13
Thank you Bucky Ball
I had the same sentiment
I'll create a new thread and post the link if after my own troubleshooting can't get it solved.

Here I'll concentrate on the possible ram problem affecting hardware accelerated video playback.

There are two sticks of 1GB each. I will try to test them individually tonight.
As far as compatibility, they've been working together for a year with no apparent issues.

Thanks everyone, your help is greatly appreciated

---

### Post by Bucky Ball on 2014-02-13
I had four sticks in my four slots for years then one day switched the computer on and one slot was gone. I had fun testing four sticks in four slots to find out which one it was! So, strange things can happen. The four sticks were fine. It was the slot itself. Just died. No warning.

---

### Post by finny388 on 2014-02-16
Okay
So I have a single ram slot in this laptop
I upgraded from 1 to 2GB (max) about a year and a half ago

I swapped in the 1GB stick and memtest shut down again in just over a minute. 
But I had pulled the laptop out to work with it and it was very hot where it was sitting so I suspected the heat.
cooled it off and put it back on the laptop cooler and it ran through. no errors. took just over an hour

so then for kicks I ran the 2GB thru. huh. 2hrs later it finished with no errors.

So then boot into the new install again and try a 1080p video with xbmc. Wow. It's working using 7% cpu and about 450/2000 ram.

I will further test to see if I can get thru a whole movie but this so fing weird to me. reseating ram rescued hardware acceleration?

---

### Post by mansonfan78 on 2014-02-16
It could have been a loose connection or some dust got into it and caused a bad connection.  These things happen.  A can of air-duster or a small, low power vacuum can do wonders for electronics.

---

### Post by finny388 on 2014-02-16
Hopefully that's just it

But wouldn't a loose connection with a single slot of ram be catastrophic instead of just hampering video?

---

### Post by finny388 on 2014-02-16
here's the link to my pepper flash issue:

[pepper flash in chromium freezes when I change resolution setting in youtube]("http://ubuntuforums.org/showthread.php?t=2205942")

---

### Post by finny388 on 2014-02-17
Woo hoo!:p
Marking as solved.
Bad ram connection needed to be reseated.

I watched a 2hr movie with no problems at all, mercilessly fast fwd'ing and navigating just fine. And I got a fresh os install in the process.;)

Thank you everyone for your help.):P
I'm very grateful

---

### Post by Topsiho on 2014-02-17
Great. Congratulations :)

Topsiho

---

### Post by mansonfan78 on 2014-02-17
Good to hear.

---

