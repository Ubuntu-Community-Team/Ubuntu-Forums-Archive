---
title: "User processes left running after logout"
date: 2018-06-12
forum: General Help
---

### Post by maglin2 on 2018-06-12
After I log out a user some of that user's processes seem to still be running - see the attached image.

The condition is that user dave is logged in and users dg and fin are logged out.

I don't know if this is intended behaviour, a bug of xubuntu, or a fault specific to my system.

Any help appreciated.

Thanks

Edit: forgot to say, I'm running Xubuntu 18.04

---

### Post by PaulW2U on 2018-06-12
Sorry maglin2 but your screenshot is unreadable with my failing eyesight and advancing years.

Please use a terminal,  and copy and post the output using [NOPARSE]```
[/NOPARSE] tags of either:
[CODE]top -u <username>
htop -user=<username>

```where <username> is the user that you are querying.

---

### Post by maglin2 on 2018-06-12
Sorry about that.
Here is the top output for user fin when fin is logged out.


  ```
PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                                                   
10826 fin       20   0   77144   8532   6996 S   0.0  0.2   0:00.12 systemd                                                                                   
10827 fin       20   0  196104   2840     44 S   0.0  0.1   0:00.00 (sd-pam)                                                                                  
10857 fin       20   0   50524   5032   3928 S   0.0  0.1   0:00.22 dbus-daemon                                                                               
10944 fin       20   0   59352   5404   4744 S   0.0  0.1   0:00.04 xfconfd                                                                                   
10980 fin       20   0  367800   8840   7976 S   0.0  0.2   0:00.02 at-spi-bus-laun                                                                           
10984 fin       20   0  292448   7144   6216 S   0.0  0.2   0:00.04 gvfsd                                                                                     
10991 fin       20   0  432036   7928   7044 S   0.0  0.2   0:00.02 gvfsd-fuse                                                                                
11000 fin       20   0  261652  32392  15532 S   0.0  0.8   0:00.51 applet.py                                                                                 
11013 fin       20   0   49924   4292   3820 S   0.0  0.1   0:00.03 dbus-daemon                                                                               
11034 fin       20   0  187900   5052   4492 S   0.0  0.1   0:00.01 dconf-service                                                                             
11081 fin       20   0  320708  11032   9368 S   0.0  0.3   0:00.12 gvfs-udisks2-vo                                                                           
11085 fin       20   0  276340   6076   5424 S   0.0  0.2   0:00.01 gvfs-mtp-volume                                                                           
11089 fin       20   0  379312   7680   6808 S   0.0  0.2   0:00.01 gvfs-afc-volume                                                                           
11094 fin       20   0  289264   6640   5864 S   0.0  0.2   0:00.01 gvfs-gphoto2-vo                                                                           
11098 fin       20   0  274540   5972   5372 S   0.0  0.2   0:00.01 gvfs-goa-volume                                                                           
11107 fin       20   0  384528   9860   8540 S   0.0  0.2   0:00.04 gvfsd-trash                                                                               
11112 fin       20   0  204864   4872   4480 S   0.0  0.1   0:00.01 gvfsd-metadata                                                                            
11165 fin       20   0   82748   7048   6388 S   0.0  0.2   0:00.00 obexd
```

---

### Post by PaulW2U on 2018-06-12
[systemd: user processes remain after logout]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=885446#10") is a comment in a Debian bug report that suggests that that behaviour can be changed by editing a config file.

Obviously I'm not suggesting that you do that. :)

---

### Post by maglin2 on 2018-06-12
Thanks for that. My powers of googling plainly aren't strong - I'd already tried looking for bug reports.

What I would like to do is find out which is the culprit user process on my system. If it is something I have installed (and there isn't much) I can see if I can tweak it (or remove it if it isn't really used much). If it is something in the default installation then everyone else should be seeing the bug too, but since my googling yielded very little of relevance it doesn't seem likely that's the case. I suppose it may be related to my hardware.

The output of loginctl for fin is 
```
loginctl user-status fin
fin (1002)
           Since: Tue 2018-06-12 09:49:29 BST; 2h 5min ago
           State: closing
        Sessions: *c6
          Linger: no
            Unit: user-1002.slice
                  &#9500;&#9472;session-c6.scope
                  &#9474; &#9492;&#9472;11000 /usr/bin/python3 /usr/share/system-config-printer/applet.py
                  &#9492;&#9472;user@1002.service
                    &#9500;&#9472;at-spi-dbus-bus.service
                    &#9474; &#9500;&#9472;10980 /usr/lib/at-spi2-core/at-spi-bus-launcher
                    &#9474; &#9492;&#9472;11013 /usr/bin/dbus-daemon --config-file=/usr/share/defaults/at-spi2/accessibility.conf --nofork --print-address 3
                    &#9500;&#9472;dbus.service
                    &#9474; &#9500;&#9472;10857 /usr/bin/dbus-daemon --session --address=systemd: --nofork --nopidfile --systemd-activation --syslog-only
                    &#9474; &#9500;&#9472;10944 /usr/lib/x86_64-linux-gnu/xfce4/xfconf/xfconfd
                    &#9474; &#9492;&#9472;11034 /usr/lib/dconf/dconf-service
                    &#9500;&#9472;gvfs-afc-volume-monitor.service
                    &#9474; &#9492;&#9472;11089 /usr/lib/gvfs/gvfs-afc-volume-monitor
                    &#9500;&#9472;gvfs-daemon.service
                    &#9474; &#9500;&#9472;10984 /usr/lib/gvfs/gvfsd
                    &#9474; &#9500;&#9472;10991 /usr/lib/gvfs/gvfsd-fuse /run/user/1002/gvfs -f -o big_writes
                    &#9474; &#9492;&#9472;11107 /usr/lib/gvfs/gvfsd-trash --spawner :1.14 /org/gtk/gvfs/exec_spaw/0
                    &#9500;&#9472;gvfs-goa-volume-monitor.service
                    &#9474; &#9492;&#9472;11098 /usr/lib/gvfs/gvfs-goa-volume-monitor
                    &#9500;&#9472;gvfs-gphoto2-volume-monitor.service
                    &#9474; &#9492;&#9472;11094 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
                    &#9500;&#9472;gvfs-metadata.service
                    &#9474; &#9492;&#9472;11112 /usr/lib/gvfs/gvfsd-metadata
                    &#9500;&#9472;gvfs-mtp-volume-monitor.service
                    &#9474; &#9492;&#9472;11085 /usr/lib/gvfs/gvfs-mtp-volume-monitor
                    &#9500;&#9472;gvfs-udisks2-volume-monitor.service
                    &#9474; &#9492;&#9472;11081 /usr/lib/gvfs/gvfs-udisks2-volume-monitor
                    &#9500;&#9472;init.scope
                    &#9474; &#9500;&#9472;10826 /lib/systemd/systemd --user
                    &#9474; &#9492;&#9472;10827 (sd-pam)
                    &#9492;&#9472;obex.service
                      &#9492;&#9472;11165 /usr/lib/bluetooth/obexd
```


but I can't see from that what the culprit might be.
Do you have any suggestions or insights?
Thanks again
Dave

---

### Post by alecz20 on 2018-10-18
This occurs on all flavors of Ubuntu 18.04

I created two users: alex and alecz and I switched between them several times and now I have several session
[https://pastebin.com/WrHSTSR4](https://pastebin.com/WrHSTSR4)
```

alex@alex-mate:~$ loginctl
   SESSION        UID USER             SEAT             TTY             
       c18       1000 alex             seat0                            
       c12       1000 alex             seat0                            
        c2       1001 alecz            seat0                            
        c8       1000 alex             seat0                            
       c16       1001 alecz            seat0                            
        c4       1000 alex             seat0                            
        c6       1001 alecz            seat0   

```

loginctl user-status alecz shows several sessions as closing: [https://pastebin.com/mwwVUcXM](https://pastebin.com/mwwVUcXM)
[B]
This seems to happen on all Ubuntu 18.04 flavors.[/B] It does not happen on Ubuntu 16.04.

---

### Post by alecz20 on 2018-10-19
I also noticed that a process that is lingering in all sessions is: system-config-printer/applet.py and I found this bug report: [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=863227](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=863227)
But then on Lubuntu (where the same problem occurs), there is no system-config-printer/applet.py process, instead it's the ssh-agent.

This leads me to believe that this is more of an issue with a common process such as dbus than with individual applications like mentioned in the Debian bug report linked in @PaulW2U's post

---

### Post by alecz20 on 2018-10-19
I wonder if this announcement is somehow related to this issue:
Moving session startup from upstart to systemd: [https://lists.ubuntu.com/archives/ubuntu-devel/2016-July/039465.html](https://lists.ubuntu.com/archives/ubuntu-devel/2016-July/039465.html)
This started in Ubuntu 16.10. I haven't tested this issue against 16.10

---

