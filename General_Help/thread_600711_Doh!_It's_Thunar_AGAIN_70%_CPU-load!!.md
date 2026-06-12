---
title: "Doh! It's Thunar AGAIN: 70% CPU-load!!"
date: 2007-11-02
forum: General Help
---

### Post by perixx on 2007-11-02
I really don't get it... Thunar strikes back... again! I'm constantly having trouble with this app, ever since installing Xubuntu 7.04.

It's really predictable: when I have some longer working sessions with Thunar open and do some major file operations or use Synaptic and/or other applications simultaneously - Thunar suddenly slows down the whole system at a CPU-load of about 55-80%. It won't recover unless Thunar is closed.

process manager, top and ps all show similar results:


> ps -ux
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
      4900  0.0  0.0   1712   496 ?        Ss   16:55   0:00 /bin/sh /etc/xdg/xfce4/xinitrc -- /
      4934  0.0  0.1   4260   536 ?        Ss   16:55   0:00 /usr/bin/ssh-agent /usr/bin/dbus-la
      4937  0.0  0.1   2660   632 ?        S    16:55   0:00 /usr/bin/dbus-launch --exit-with-se
      4938  0.0  0.1   2720   964 ?        Ss   16:55   0:00 /usr/bin/dbus-daemon --fork --print
      4944  0.0  0.4   5428  2276 ?        S    16:55   0:00 xscreensaver -no-splash
      4947  0.0  1.1  40632  6080 ?        Sl   16:55   0:02 /usr/bin/xfce4-session
      4953  0.0  2.3  46896 12008 ?        Ss   16:55   0:03 xfce-mcs-manager
      4955  0.0  0.1   2752   984 ?        S    16:55   0:00 gnome-keyring-daemon
      4957  0.0  0.5   5168  2720 ?        S    16:55   0:00 /usr/lib/libgconf2-4/gconfd-2 8
      4958  0.0  1.6  15332  8256 ?        S    16:55   0:03 xfwm4 --sm-client-id 117f0001010001
      4960  0.0  2.4  56704 12628 ?        S    16:55   0:02 xfdesktop --sm-client-id 117f000101
      4962  0.5  0.6   4756  3424 ?        S    16:55   0:46 /usr/lib/gamin/gam_server
      4964  0.1  2.4  47092 12704 ?        S    16:55   0:13 xfce4-panel --sm-client-id 117f0001
      4966  0.0  1.0   8784  5456 ?        Ss   16:55   0:00 python /usr/share/system-config-pri
      4973  0.1  2.2  36776 11772 ?        S    16:55   0:11 /usr/lib/xfdesktop4/xfce4/panel-plu
reko      4974  0.0  0.9  18956  4808 ?        Ss   16:55   0:00 gnome-volume-manager --sm-disable
      4984  0.0  1.6  16892  8464 ?        S    16:55   0:00 /usr/lib/xfce4-mount-plugin/xfce4/p
      4985  0.0  1.9  36772  9972 ?        S    16:55   0:00 /usr/lib/xfce4-mixer/xfce4/panel-pl
      4986  0.0  1.6  36836  8764 ?        S    16:55   0:00 /usr/lib/thunar/xfce4/panel-plugins
      5026  0.1  1.4  14640  7568 ?        S    16:55   0:11 /usr/lib/xfce4-netload-plugin/xfce4
      5028  7.5  6.1  94084 31924 ?        Sl   16:55  10:02 /usr/bin/Thunar --daemon
      5055  0.0  2.1  56736 10860 ?        Ss   17:08   0:01 exo-desktop-item-edit --display=:0.
      5058  1.8 11.9 177300 61824 ?        Ssl  17:09   2:16 /usr/lib/firefox/firefox-bin
      5735  0.0  0.0      0     0 ?        Z    18:09   0:00 [mousepad] <defunct>
      5739  0.0  0.0      0     0 ?        Z    18:12   0:00 [mousepad] <defunct>
      5750  0.0  0.0      0     0 ?        Z    18:14   0:00 [mousepad] <defunct>
      5769  0.0  0.0      0     0 ?        Z    18:17   0:00 [mousepad] <defunct>
      5770  0.0  0.0      0     0 ?        Z    18:18   0:00 [mousepad] <defunct>
      5836  0.0  1.1  31236  5732 ?        Sl   18:22   0:01 /usr/X11R6/bin/xfce4-session
      5840  0.0  0.1   2752  1012 ?        S    18:22   0:00 gnome-keyring-daemon
      5846  0.0  1.0   8784  5456 ?        Ss   18:22   0:00 python /usr/share/system-config-pri
      6168  0.0  0.0      0     0 ?        Z    18:35   0:00 [mousepad] <defunct>
      6220  2.6  6.5  67784 33800 ?        Ss   18:40   0:45 xfce4-taskmanager
      6360  0.2  0.0      0     0 ?        Z    18:51   0:02 [abiword] <defunct>
      7282  0.7  2.8  50172 14628 ?        S    19:08   0:00 /usr/bin/Terminal
      7283  0.0  0.1   2456   724 ?        S    19:08   0:00 gnome-pty-helper
      7284  0.4  0.6   5664  3148 pts/0    Ss   19:08   0:00 bash
      7314  0.0  0.1   2564  1000 pts/0    R+   19:09   0:00 ps -ux
 

top

top - 19:11:19 up  2:17,  2 users,  load average: 1.25, 2.04, 1.84
Tasks:  98 total,   3 running,  88 sleeping,   0 stopped,   7 zombie
Cpu(s): 75.7%us,  6.4%sy,  0.0%ni, 17.4%id,  0.0%wa,  0.4%hi,  0.0%si,  0.0%st
Mem:    515980k total,   439916k used,    76064k free,    24252k buffers
Swap:        0k total,        0k used,        0k free,   205188k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                
 5028 re      16   0 94084  31m  15m R 68.8  6.2  11:19.35 Thunar                                 
 4962 re      15   0  4756 3424 1000 S  6.0  0.7   0:51.85 gam_server                             
 4547 root      15   0  108m  23m 8056 S  3.8  4.6   8:19.27 Xorg                                   
 6220 re      16   0 69344  34m 6696 S  3.4  6.9   0:48.71 xfce4-taskmanag                        
 7324 re      15   0  2312 1148  880 R  0.4  0.2   0:00.14 top                                    
    1 root      15   0  2908 1844  524 S  0.0  0.4   0:01.55 init                                   
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0                            
    3 root      34  19     0    0    0 R  0.0  0.0   0:00.02 ksoftirqd/0                            
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                             
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.04 events/0                               
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 khelper                                
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread                                
   30 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0                              
   31 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                 
   32 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                           
   91 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                
  114 root      15   0     0    0    0 S  0.0  0.0   0:00.02 pdflush                                
  115 root      15   0     0    0    0 S  0.0  0.0   0:00.01 pdflush                                
  116 root      10  -5     0    0    0 S  0.0  0.0   0:00.20 kswapd0                                
  117 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                  
 1866 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                          
 1867 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                  
 2030 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0                                  
 2031 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                
 2192 root      10  -5     0    0    0 S  0.0  0.0   0:00.36 kjournald                              
 2389 root      16  -4  2860 1204  376 S  0.0  0.2   0:00.54 udevd    


What's wrong here??!!

Update: funny thing is, I have to shut down Thunar in the process manager TWICE - 1st: Thunar windows closes, 2nd: Thunar background process stopps (which consumes CPU load)
perixx

---

### Post by perixx on 2007-11-03
Actually, this seems to be a real bug, not my fault or mine system's....

I found a bugreport on bugzilla describing exactly the same problem like I have - that guy's also using feisty 7.04!


perixx

---

### Post by perixx on 2007-12-08
Well, not quite as often as with my older PC, but it still happens every now and then!! Since on completely different systems, it MUST be a **BUG** !

perixx

---

