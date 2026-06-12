---
title: "Problem with Kernel?"
date: 2007-02-08
forum: General Help
---

### Post by kitt on 2007-02-08
Hi folks,
           I have been using Dapper for about seven months now, and have experimented with other distributions as well. I have a Acer aspire 5000 laptop. 
          Over time, i have observed that my ubuntu install is considerably slower than the other distributions. I have tried Suse 10, Gentoo, and Knoppix. Below is the detailed description and diagnosis of my problem, and it would be great if you guys could tell me whether my observations are correct. 
          I have noticed a degradation in Ubuntu's performance. Initially, it was very fast. Now, it really is quite sluggish. Of course, i dont have many benchmarks to prove it - but i think a few examples can prove my point. One is the disk-access light of my laptop. Initially, it would light up only in case of heavy-load. But now, my disk is accessed even for such tasks as minimizing windows, etc. My boot-up time has also increased inspite of my efforts to remove useless services at boot-up.
         Suse 10.1 runs *much* faster. I have timed various application launch times, as well as compared their hdparm benchmarks, and it appears as if Suse is almost twice as responsive as ubuntu. 
          Off late, i have observed other interesting things. I feel that my ubuntu kernel is not doing its job well. Processes which are not needed are not killed, and dont give up the resources, stuff like that.
          Anybody out there can tell me whether Ubuntu's kernel is *not* the best out there. I am also thinking of compiling the latest linux kernel in the hope of getting a performance increase. Can i hope?
          Thanks in advance.

---

### Post by rogier.de.groot on 2007-02-08
Suse faster then Ubuntu? My experience with Suse is quite different...
You mentioned hdparm benchmarks - could you post the results? There shouldn't be any difference, after all it's mostly down to hardware. If there is a significant difference, could you also supply the output of "sudo hdparm /dev/hda" (or whatever drive) from both systems? Also the output of "free -m" from both OSes might be useful.
Any ideas as to which process(es) are using most memory/cpu on your machine?

---

### Post by kitt on 2007-02-08
I am sorry i cannot post the suse benchmarks, since i am not able to boot into it ;-)
But i do remember the hdparm results perfectly well
In ubuntu, with FF running, the max i get for buffered reads is 16 Mbps. If completely idle, it is 29 Mbps. In suse, even for heavy loads (mplayer+Openoffice+FF) was 25 Mbps, with idle at 35
The hdparm config in both are (was) the same ...dma on , readahead at 256, rest all off.
As for resource usgage, firefox and xorg always consume the most.

---

### Post by rogier.de.groot on 2007-02-08
Hmm... weird. The hdparm read test should just test harddisk performance, right? Maybe Suse & Ubuntu use different drivers (or module parameters). If it's filesystem performance, it might be a ext3 vs. reiserfs thing...
I'd still like to see your "free -m" output; and some "ps aux" output might come in handy to. Maybe some stray process is access disk all the time?

---

### Post by kitt on 2007-02-08
Sure, here is my free -m output:

             total       used       free     shared    buffers     cached
Mem:           217        214          3          0          1         78
-/+ buffers/cache:        133         84
Swap:         1984         68       1915
----------------------------------------------------------------------------------------------------------------------
And this is the ps aux output:

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.2   1568   480 ?        S    13:50   0:01 init [2]
root         2  0.0  0.0      0     0 ?        SN   13:50   0:00 [ksoftirqd/0]
root         3  0.0  0.0      0     0 ?        S    13:50   0:00 [watchdog/0]
root         4  0.0  0.0      0     0 ?        S<   13:50   0:00 [events/0]
root         5  0.0  0.0      0     0 ?        S<   13:50   0:00 [khelper]
root         6  0.0  0.0      0     0 ?        S<   13:50   0:00 [kthread]
root         8  0.0  0.0      0     0 ?        S<   13:50   0:00 [kblockd/0]
root         9  0.0  0.0      0     0 ?        S<   13:50   0:00 [kacpid]
root        62  0.0  0.0      0     0 ?        S<   13:50   0:00 [kacpid-work-0]
root       113  0.0  0.0      0     0 ?        S    13:50   0:00 [pdflush]
root       114  0.0  0.0      0     0 ?        S    13:50   0:00 [pdflush]
root       116  0.0  0.0      0     0 ?        S<   13:50   0:00 [aio/0]
root       115  0.0  0.0      0     0 ?        S    13:50   0:00 [kswapd0]
root       703  0.0  0.0      0     0 ?        S<   13:50   0:00 [kseriod]
root      1804  0.0  0.0      0     0 ?        S<   13:51   0:00 [khubd]
root      1940  0.0  0.0      0     0 ?        S    13:51   0:00 [kjournald]
root      2187  0.0  0.1   2432   340 ?        S<s  13:51   0:00 /sbin/udevd --daemon
root      2969  0.0  0.0      0     0 ?        S    13:51   0:00 [shpchpd_event]
root      3045  0.0  0.0      0     0 ?        S    13:51   0:00 [pccardd]
root      3507  0.0  0.0      0     0 ?        S    13:54   0:00 [kjournald]
root      3511  0.0  0.0      0     0 ?        S    13:54   0:00 [kjournald]
root      3512  0.0  0.0      0     0 ?        S    13:54   0:00 [kjournald]
root      4053  0.0  0.3   2152   816 ?        Ss   13:54   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/
syslog    4070  0.0  0.2   1768   612 ?        Ss   13:54   0:00 /sbin/syslogd -u syslog
root      4096  0.0  0.1   1684   412 ?        Ss   13:54   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kms
klog      4098  0.0  0.1   2408   436 ?        Ss   13:54   0:00 /sbin/klogd -P /var/run/klogd/kmsg
104       4143  0.0  0.3   2324   832 ?        Ss   13:54   0:04 /usr/bin/dbus-daemon --system
108       4158  0.0  0.8   6756  1824 ?        Ss   13:54   0:04 /usr/sbin/hald
root      4159  0.0  0.3   2720   812 ?        S    13:54   0:00 hald-runner
108       4164  0.0  0.3   2008   816 ?        S    13:54   0:00 /usr/lib/hal/hald-addon-acpi
108       4214  0.0  0.3   2004   760 ?        S    13:54   0:00 /usr/lib/hal/hald-addon-keyboard
108       4224  0.0  0.3   2008   760 ?        S    13:54   0:00 /usr/lib/hal/hald-addon-storage
108       4225  0.0  0.3   2008   716 ?        S    13:54   0:00 /usr/lib/hal/hald-addon-storage
root      4246  0.0  0.2   1932   660 ?        Ss   13:54   0:00 /sbin/dhcdbd --system
root      4263  0.0  0.6  12124  1488 ?        Ssl  13:54   0:00 /usr/sbin/NetworkManager --pid-file=/var/run/Net
root      4277  0.0  0.4   2928  1032 ?        Ss   13:54   0:00 /usr/sbin/NetworkManagerDispatcher --pid-file=/v
dhcp      4602  0.0  0.2   2340   576 ?        S    13:54   0:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.et
root      4647  0.0  0.1   1628   260 ?        Ss   13:54   0:00 /sbin/mdadm -F -i /var/run/mdadm.pid -m root -f
root      4688  0.0  0.6   4296  1472 ?        S    13:54   0:01 /usr/sbin/powersaved -d -f /var/run/acpid.socket
daemon    4716  0.0  0.1   1800   300 ?        Ss   13:54   0:00 /usr/sbin/atd
root      4761  0.0  0.3   2120   736 ?        Ss   13:54   0:00 /usr/sbin/cron
root      4854  0.0  0.1   2744   416 ?        Ss   13:54   0:00 /usr/bin/kdm
root      4888  0.0  0.1   1564   416 tty1     Ss+  13:54   0:00 /sbin/getty 38400 tty1
root      4891  0.0  0.1   1560   416 tty2     Ss+  13:54   0:00 /sbin/getty 38400 tty2
root      4892  6.0  7.0  29156 15720 tty7     Ss+  13:54   5:49 /usr/bin/X -br -nolisten tcp :0 vt7 -auth /var/r
root      4895  0.0  0.3   3600   844 ?        S    13:54   0:00 -:0
prateek   4907  0.0  0.4   4160  1076 ?        Ss   13:54   0:00 /bin/sh /usr/bin/startkde
prateek   4946  0.0  0.1   4328   312 ?        Ss   13:54   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-w
prateek   4949  0.0  0.2   2712   516 ?        S    13:54   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bi
prateek   4950  0.0  0.3   2196   888 ?        Ss   13:54   0:00 dbus-daemon --fork --print-pid 8 --print-address
prateek   4981  0.0  1.0  24480  2432 ?        Ss   13:54   0:00 kdeinit Running...
prateek   4984  0.0  0.9  24456  2016 ?        S    13:54   0:00 dcopserver [kdeinit] --nosid
prateek   4986  0.0  2.3  25416  5260 ?        S    13:54   0:00 klauncher [kdeinit]
prateek   4988  0.0  4.0  30160  9000 ?        S    13:54   0:04 kded [kdeinit]
prateek   4990  0.0  0.5   2744  1160 ?        S    13:54   0:00 /usr/lib/gamin/gam_server
prateek   5001  0.0  1.6  12796  3772 ?        S    13:54   0:02 /usr/bin/artsd -F 10 -S 4096 -s 60 -m artsmessag
prateek   5003  0.0  2.3  25116  5224 ?        S    13:54   0:00 kaccess [kdeinit]
prateek   5006  0.0  0.1   1552   292 ?        S    13:54   0:00 kwrapper ksmserver
prateek   5008  0.0  2.4  25224  5444 ?        S    13:54   0:00 ksmserver [kdeinit]
prateek   5009  0.1  3.6  27972  8036 ?        S    13:54   0:05 kwin [kdeinit]
prateek   5011  0.0  6.3  31036 14128 ?        S    13:54   0:03 kdesktop [kdeinit]
prateek   5013  1.0  6.1  34820 13656 ?        S    13:54   1:02 kicker [kdeinit]
prateek   5021  0.0  3.3  28276  7472 ?        S    13:54   0:01 kpowersave [kdeinit]
prateek   5023  0.0  3.4  35996  7760 ?        S    13:54   0:00 konqueror [kdeinit] --preload
prateek   5026  0.0  1.7  24876  3968 ?        S    13:54   0:00 kio_file [kdeinit] file /tmp/ksocket-prateek/kla
prateek   5044  0.0  0.4   3652  1072 ?        S    13:54   0:00 /bin/sh /home/prateek/downloads/firefox/firefox
prateek   5047  0.0  0.4   4208  1064 ?        S    13:54   0:00 /bin/sh /home/prateek/downloads/firefox/run-mozi
prateek   5052  6.3 28.7 202668 64188 ?        Sl   13:54   6:01 /home/prateek/downloads/firefox/firefox-bin
prateek   5054  0.3  4.8  44604 10720 ?        S    13:54   0:17 gaim
prateek   5056  0.0  1.2   5928  2840 ?        S    13:54   0:00 /usr/lib/libgconf2-4/gconfd-2 12
prateek   5077  0.0  5.0  34816 11240 ?        S    13:55   0:01 knotify [kdeinit]
prateek   5122  0.0  1.0  16640  2368 ?        S    13:56   0:00 /usr/bin/kdesud
root      5149  0.0  0.0      0     0 ?        S<   13:59   0:00 [kacpid-work-1]
prateek   5531  0.0  3.6  29692  8068 ?        S    13:59   0:01 gksu /usr/bin/x-terminal-emulator
root      5532  0.0  0.0      0     0 ?        Zs   13:59   0:02 [gnome-terminal] <defunct>
root      5541  0.0  0.5   3088  1324 ?        Ss   14:00   0:00 /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd
prateek   5701  0.0  5.7  29184 12884 ?        S    14:21   0:00 kmix [kdeinit] -caption KMix -icon kmix -miniico
prateek   5715  0.0  3.7  30752  8408 ?        S    14:25   0:01 /usr/lib/notification-daemon/notification-daemon
prateek   6055  0.0  4.8  24940 10772 ?        S    14:49   0:00 kdesu -u root -c kdesu adept
root      6057  0.0  0.1   1424   300 pts/2    Ss+  14:49   0:00 /usr/bin/kdesu_stub -
root      6059  0.0  0.4   2472   980 pts/3    Ss+  14:49   0:00 /usr/bin/sudo -u root /usr/bin/kdesu_stub -
prateek   6100  0.1  5.5  26788 12448 ?        S    14:53   0:03 knetdockapp
prateek   6124  0.2  6.4  29980 14428 ?        S    15:04   0:03 konsole [kdeinit]
prateek   6125  0.0  1.4   5664  3340 pts/1    Ss   15:04   0:00 /bin/bash
prateek   6237  0.0  4.1  29696  9252 ?        S    15:05   0:01 gksu /usr/bin/x-terminal-emulator
root      6238  0.2  6.6  40452 14772 ?        Ssl  15:05   0:02 gnome-terminal
root      6240  0.0  1.5   5804  3380 ?        S    15:06   0:00 /usr/lib/libgconf2-4/gconfd-2 12
root      6242  0.0  1.1   6020  2652 ?        Ss   15:06   0:00 /usr/lib/bonobo-activation/bonobo-activation-ser
root      6245  0.0  0.3   2288   684 ?        S    15:06   0:00 gnome-pty-helper
root      6246  0.0  0.8   3956  1808 pts/4    Ss   15:06   0:00 bash
root      6310  0.0  4.9  13812 11016 pts/4    S+   15:08   0:00 apt-get install kdeartwork
root      6312  0.0  0.6   4332  1548 pts/4    S+   15:08   0:00 /usr/lib/apt/methods/http
prateek   6561  3.9  9.9 111076 22208 ?        SLl  15:15   0:34 rhythmbox
prateek   6563  0.0  1.2   6152  2768 ?        Ss   15:15   0:00 /usr/lib/bonobo-activation/bonobo-activation-ser
prateek   6568  0.0  1.6   8356  3628 ?        Sl   15:15   0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon --oaf-ac
prateek   7116  0.0  3.9 109924  8772 ?        Ss   15:21   0:00 rhythmbox
prateek   7671  0.0  0.4   2400  1016 pts/1    R+   15:29   0:00 ps aux

---

### Post by rogier.de.groot on 2007-02-08
Hmm... still no thoughts on what the problem might be... But you've got a lot of running programs for a machine with 217 MB of RAM... And you're running Gnome programs on a KDE system (which probably loads a lot Gnome libraries).
I wonder, on Suse, were you using KDE as well, with those same Gnome programs (rhytmbox, gaim, gnome-terminal, etc), or KDE with KDE programs, or Gnome with Gnome programs?
I wouldn't run KDE or Gnome on a 217 MB machine... Or WinXP for that matter...

---

### Post by kitt on 2007-02-08
I was running KDE on Suse, running all sorts of gnome programs.. 
My main concern is the kernel...inefficiancy..why does it not kill processes it does not need? Why do i have to manually kill them??

---

### Post by rogier.de.groot on 2007-02-08
Killing unnecessary processes is not the kernel's job - Suse won't do this either. Besides, how should the kernel know if a process is unnecessary? If it isn't doing anything the kernel will swap out most or all of the memory it is using though. I didn't see many processes on your "ps aux" outpot that I'd deem unnecessary by the way.
If Suse works better for you, why not ditch Ubuntu and install Suse instead?

---

### Post by kitt on 2007-02-08
> Killing unnecessary processes is not the kernel's job - Suse won't do this either. Besides, how should the kernel know if a process is unnecessary? If it isn't doing anything the kernel will swap out most or all of the memory it is using though.
Please correct me if i am wrong, but isnt it the kernel's job to kill the processes of applications which are closed? 
Also, say one distribution of Linux is faster than the Other, all other things being equal..then what component of the OS is responsible for the better/worse performance?

---

