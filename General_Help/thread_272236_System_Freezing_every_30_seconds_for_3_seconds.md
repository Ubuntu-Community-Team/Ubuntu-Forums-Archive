---
title: "System Freezing every 30 seconds for 3 seconds"
date: 2006-10-05
forum: General Help
---

### Post by tetrahedron on 2006-10-05
After updated to the latest available updates my system freezes around every 30 seconds for like 2-3 seconds. The system monitor shows spikes for the CPU at the associated intervals.

My specs are: Core Duo (1.83) 2GB of DDR2-667, Geforce Go 7300, 80GB 7200rpm HDD.

Any ideas, suggestions... need more information from me?

---

### Post by tetrahedron on 2006-10-05
also wanted to say I am pretty much idle, just firefox and GAIM open, no process is using any extreme amount of CPU, though it still shows in the system manager on the resources tab spikes of 70% and 50% at times

---

### Post by aznlnx on 2006-10-05
Strange....the same thing is happening to me....

anyone know why its doing this?

---

### Post by jalm111 on 2006-10-06
What are you running on your system? copy and paste output of ps aux if possible on here. I used to have a similar problem a while ago and turns out it was gdesklets hanging and using 100% cpu. Upon restart of X (CTRL+SHIFT+BACKSPACE) everything would return to normal untill a little late same thing would happen. It is most likely an application that's going crazy.

---

### Post by towsonu2003 on 2006-10-06
you can monitor which program is running off with your cpu using top in a terminal. just watch the output and wait for the freeze. the one with 100% cpu usage is the guilty one, most probably. let us know.

ps. if looking at the system manager, make sure you can see applications belonging to all users, including root. the option should be somewhere in settings or similar. but top is better bc it doesn't eat cpu like the system manager. in system manager, as cpu pikes, system manager will also pike a little, so your results will be unreliable.

---

### Post by jalm111 on 2006-10-06
Heheh. Top.... ps is the ultimate when trying to use little system power. It gives you the current snap shot of the system with all the info you need (if you use the aux flags).   :cool:

---

### Post by amo-ej1 on 2006-10-06
simply run top and look at the cpu usage, if it isn't an application it can be some kernel/hw issue. Look at the %hi and %si for the percentage of the cpu spends in handling hardware and software interrupts.

---

### Post by towsonu2003 on 2006-10-06
> **amo-ej1 said:**
> Look at the %hi and %si

can't find those in top... I see %MEM and %CPU (and can add all sorts of fields, excepts those two)... I'm missing something, but what?

---

### Post by tetrahedron on 2006-10-06
> **jalm111 said:**
> What are you running on your system? copy and paste output of ps aux if possible on here. I used to have a similar problem a while ago and turns out it was gdesklets hanging and using 100% cpu. Upon restart of X (CTRL+SHIFT+BACKSPACE) everything would return to normal untill a little late same thing would happen. It is most likely an application that's going crazy.

```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   1568   532 ?        S    08:38   0:01 init [2]
root         2  0.0  0.0      0     0 ?        S    08:38   0:00 [migration/0]
root         3  0.0  0.0      0     0 ?        SN   08:38   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    08:38   0:00 [watchdog/0]
root         5  0.0  0.0      0     0 ?        S    08:38   0:00 [migration/1]
root         6  0.0  0.0      0     0 ?        SN   08:38   0:00 [ksoftirqd/1]
root         7  0.0  0.0      0     0 ?        S    08:38   0:00 [watchdog/1]
root         8  0.0  0.0      0     0 ?        S<   08:38   0:00 [events/0]
root         9  0.0  0.0      0     0 ?        S<   08:38   0:00 [events/1]
root        10  0.0  0.0      0     0 ?        S<   08:38   0:00 [khelper]
root        11  0.0  0.0      0     0 ?        S<   08:38   0:00 [kthread]
root        14  0.0  0.0      0     0 ?        S<   08:38   0:00 [kblockd/0]
root        15  0.0  0.0      0     0 ?        S<   08:38   0:00 [kblockd/1]
root        16  0.0  0.0      0     0 ?        S<   08:38   0:00 [kacpid]
root       167  0.0  0.0      0     0 ?        S    08:38   0:00 [pdflush]
root       168  0.0  0.0      0     0 ?        S    08:38   0:00 [pdflush]
root       170  0.0  0.0      0     0 ?        S<   08:38   0:00 [aio/0]
root       171  0.0  0.0      0     0 ?        S<   08:38   0:00 [aio/1]
root       169  0.0  0.0      0     0 ?        S    08:38   0:00 [kswapd0]
root       767  0.0  0.0      0     0 ?        S<   08:38   0:00 [kseriod]
root       851  0.0  0.0      0     0 ?        S    08:38   0:00 [kirqd]
root      1812  0.1  0.0      0     0 ?        S<   08:38   0:02 [ata/0]
root      1813  0.0  0.0      0     0 ?        S<   08:38   0:00 [ata/1]
root      1814  0.0  0.0      0     0 ?        S<   08:38   0:00 [ata_hotplug/0]root      1815  0.0  0.0      0     0 ?        S<   08:38   0:00 [ata_hotplug/1]root      1820  0.0  0.0      0     0 ?        S<   08:38   0:00 [scsi_eh_0]
root      1821  0.0  0.0      0     0 ?        S<   08:38   0:00 [scsi_eh_1]
root      1892  0.0  0.0      0     0 ?        S<   08:38   0:00 [khubd]
root      1921  0.0  0.0      0     0 ?        S    08:38   0:00 [khpsbpkt]
root      1958  0.0  0.0      0     0 ?        S    08:38   0:00 [knodemgrd_0]
root      2029  0.0  0.0      0     0 ?        S    08:38   0:00 [kjournald]
root      2270  0.0  0.0   2428   920 ?        S<s  08:38   0:00 /sbin/udevd --droot      3032  0.0  0.0      0     0 ?        S    08:38   0:00 [shpchpd_event]root      3150  0.0  0.0      0     0 ?        S    08:38   0:00 [pccardd]
root      3192  0.0  0.0      0     0 ?        S<   08:38   0:00 [ipw3945/0]
root      3193  0.1  0.0      0     0 ?        S<   08:38   0:03 [ipw3945/1]
root      3194  0.0  0.0      0     0 ?        S<   08:38   0:00 [ipw3945/0]
root      3195  0.0  0.0      0     0 ?        S<   08:38   0:00 [ipw3945/1]
root      3361  0.0  0.0   1616   396 ?        S<   08:38   0:01 /sbin/ipw3945d-root      3895  0.0  0.0      0     0 ?        S<   08:38   0:00 [kacpid-work-0]root      3896  0.0  0.0      0     0 ?        S<   08:38   0:00 [kacpid-work-1]root      3897  0.0  0.0      0     0 ?        S<   08:38   0:00 [kacpid-work-2]root      4034  0.0  0.0   2548  1628 ?        Ss   08:38   0:00 /usr/sbin/acpidsyslog    4138  0.0  0.0   1768   672 ?        Ss   08:38   0:00 /sbin/syslogd -root      4164  0.0  0.0   1680   496 ?        Ss   08:38   0:00 /bin/dd bs 1 ifklog      4166  0.0  0.0   2396  1320 ?        Ss   08:38   0:00 /sbin/klogd -P
root      4488  0.0  0.0  10916  1808 ?        Ss   08:38   0:00 /usr/sbin/gdm
root      4504  0.0  0.1  11396  2624 ?        S    08:38   0:00 /usr/sbin/gdm
root      4519  6.2  3.6  78232 75608 ?        RL   08:38   1:46 /usr/bin/Xgl :0hplip     4527  0.0  0.0  12872   920 ?        Ssl  08:38   0:00 /usr/sbin/hpiodroot      4529  0.3  0.6  17720 14208 tty7     SLs+ 08:38   0:06 /usr/bin/Xorg vhplip     4534  0.0  0.2   9412  4668 ?        S    08:38   0:00 python /usr/sbicupsys    4585  0.0  0.0   4204  1784 ?        Ss   08:38   0:00 /usr/sbin/cupsd104       4614  0.0  0.0   2320   920 ?        Ss   08:38   0:00 /usr/bin/dbus-d108       4629  0.0  0.2   6900  5476 ?        Ss   08:38   0:01 /usr/sbin/hald
root      4630  0.0  0.0   2720   992 ?        S    08:38   0:00 hald-runner
108       4635  0.0  0.0   2008   872 ?        S    08:38   0:00 /usr/lib/hal/ha108       4685  0.0  0.0   2008   828 ?        S    08:38   0:00 /usr/lib/hal/ha108       4695  0.0  0.0   2012   864 ?        D    08:38   0:00 /usr/lib/hal/ha108       4696  0.0  0.0   2012   820 ?        D    08:38   0:00 /usr/lib/hal/haroot      4714  0.0  0.0   1936   820 ?        Ss   08:38   0:00 /sbin/dhcdbd --root      4737  0.0  0.1  21348  2092 ?        Ssl  08:38   0:00 /usr/sbin/Networoot      4750  0.0  0.0   2924  1288 ?        Ss   08:38   0:00 /usr/sbin/Networoot      4785  0.0  0.0   1556   260 ?        SNs  08:38   0:00 /usr/sbin/powerroot      4827  0.0  0.0   1968   712 ?        Ss   08:38   0:00 hcid: processinroot      4831  0.0  0.0   1620   460 ?        Ss   08:38   0:00 /usr/sbin/sdpd
root      4852  0.0  0.0      0     0 ?        S<   08:38   0:00 [krfcommd]
root      4865  0.0  0.0   1624   296 ?        Ss   08:38   0:00 /sbin/mdadm -F
daemon    4899  0.0  0.0   1800   396 ?        Ss   08:38   0:00 /usr/sbin/atd
root      4912  0.0  0.0   2120   832 ?        Ss   08:38   0:00 /usr/sbin/cron
root      4934  0.0  0.0   9676   692 ?        Ss   08:38   0:00 /usr/sbin/nvtvdroot      5013  0.0  0.0   1560   492 tty1     Ss+  08:38   0:00 /sbin/getty 384root      5014  0.0  0.0   1564   496 tty2     Ss+  08:38   0:00 /sbin/getty 384root      5015  0.0  0.0   1560   492 tty3     Ss+  08:38   0:00 /sbin/getty 384root      5016  0.0  0.0   1564   496 tty4     Ss+  08:38   0:00 /sbin/getty 384root      5017  0.0  0.0   1564   496 tty5     Ss+  08:38   0:00 /sbin/getty 384root      5018  0.0  0.0   1564   492 tty6     Ss+  08:38   0:00 /sbin/getty 384danknerd  5096  0.0  0.1   6268  2984 ?        Ss   08:39   0:00 /usr/lib/bonoboroot      5258  0.0  0.0   3340  1432 ?        S    08:39   0:00 /sbin/wpa_suppldhcp      5317  0.0  0.0   2336  1132 ?        S    08:39   0:00 /sbin/dhclient
danknerd  5436  0.0  0.1   6152  3732 ?        S    08:41   0:00 /usr/lib/libgcodanknerd  5455  0.0  0.4  19708 10356 ?        Ss   08:41   0:00 x-session-managdanknerd  5497  0.0  0.0   4332   684 ?        Ss   08:41   0:00 /usr/bin/ssh-agdanknerd  5500  0.0  0.0   2716   656 ?        S    08:41   0:00 /usr/bin/dbus-ldanknerd  5501  0.0  0.0   2196   928 ?        Ss   08:41   0:00 dbus-daemon --fdanknerd  5504  0.0  0.0   2344   732 ?        S    08:41   0:00 /usr/bin/gnome-danknerd  5506  0.0  0.5  29380 10956 ?        Sl   08:41   0:00 /usr/lib/controdanknerd  5508  0.0  0.2   5808  4340 ?        Ss   08:41   0:00 /usr/bin/esd -tdanknerd  5521  0.3  1.4  45364 29236 ?        Ssl  08:41   0:05 gnome-panel --sdanknerd  5523  0.4  1.2  76844 26952 ?        Ssl  08:41   0:06 nautilus --no-ddanknerd  5529  0.0  0.5  19468 10884 ?        Ss   08:41   0:00 update-notifierdanknerd  5532  0.0  0.1   8620  3860 ?        Sl   08:41   0:00 /usr/lib/gnome-danknerd  5536  0.0  0.4  40828  8768 ?        Ssl  08:41   0:00 beryl-manager
danknerd  5542  0.0  0.2  17220  5316 ?        Ss   08:41   0:00 gnome-volume-madanknerd  5546  0.0  0.5  21156 11896 ?        Ss   08:41   0:00 nm-applet --sm-danknerd  5565  0.0  0.3  37796  7904 ?        Ss   08:41   0:00 gnome-cups-icondanknerd  5567  0.1  1.4  61268 30184 ?        Sl   08:41   0:02 beagled --debugdanknerd  5572  0.0  0.3  17788  8188 ?        S    08:41   0:00 /usr/lib/gnome-danknerd  5574  0.0  0.4  19572  8680 ?        Ss   08:41   0:00 gnome-power-mandanknerd  5589  0.0  0.5  31212 10880 ?        Sl   08:41   0:00 /usr/lib/gnome-danknerd  5605  0.0  0.0   2288   804 ?        S    08:41   0:00 /usr/lib/nautildanknerd  5636  0.1  0.3  14384  8136 ?        S    08:41   0:02 emerald --repladanknerd  5646  0.0  0.5  37528 11348 ?        S    08:41   0:00 /usr/lib/gnome-danknerd  5657  0.0  1.4  45628 30020 ?        Sl   08:41   0:01 python /usr/libdanknerd  5659  0.0  0.4  19864 10328 ?        S    08:41   0:00 /usr/lib/gnome-danknerd  5661  0.0  0.5  23564 10948 ?        S    08:41   0:00 /usr/lib/gnome-danknerd  5664  0.0  0.5  21956 11664 ?        S    08:41   0:00 /usr/lib/gnome-danknerd  5869  0.5  1.0 102228 21124 ?        Sl   08:42   0:07 wxvlc /home/dandanknerd  6006  1.4  2.0 108640 42856 ?        Sl   08:46   0:18 /usr/lib/firefodanknerd  6027  0.4  0.9  37508 20324 ?        S    08:46   0:05 gaim
danknerd  6182  0.1  1.0  44956 22728 ?        Sl   08:51   0:01 beagled-helper
root      6362  0.0  0.0      0     0 ?        S<   08:56   0:00 [kacpid-work-3]danknerd  6675  0.4  0.4  15352  9428 ?        S    08:58   0:02 metacity --repldanknerd  6851 14.5  0.7  25036 14840 ?        Sl   09:03   0:35 gnome-system-modanknerd  6949  2.1  0.7  40140 15016 ?        Sl   09:06   0:00 gnome-terminal
danknerd  6953  0.0  0.0   2288   684 ?        S    09:06   0:00 gnome-pty-helpedanknerd  6954  0.5  0.1   5628  3320 pts/0    Ss   09:06   0:00 bash
root      6988  0.0  0.0   2396  1016 pts/0    R+   09:07   0:00 ps aux

```

---

### Post by mgmiller on 2006-10-06
> can't find those in top... I see %MEM and %CPU (and can add all sorts of fields, excepts those two)... I'm missing something, but what?

Those are not fields listed along with the rest.  They show up in the text above the rest of the info.  The 2 items are dynamic, they will change as you watch.   Just look in the 5 lines above the rest of the chart.    they are on the line that starts with Cpu(s):
Mine looks like this:  
Cpu(s):  9.0% us,  0.7% sy,  0.0% ni, 89.3% id,  0.0% wa,  0.7% hi,  0.3% si

---

### Post by towsonu2003 on 2006-10-06
> **mgmiller said:**
> Those are not fields listed along with the rest.  They show up in the text above the rest of the info.  The 2 items are dynamic, they will change as you watch.   Just look in the 5 lines above the rest of the chart.    they are on the line that starts with Cpu(s):
Mine looks like this:  
Cpu(s):  9.0% us,  0.7% sy,  0.0% ni, 89.3% id,  0.0% wa,  0.7% hi,  0.3% si

oopsie :mrgreen: there they are... any pointers on what they mean? couldn't understand what wikipedia was saying...

---

### Post by jalm111 on 2006-10-14
Tetrahedron,

From what you showed there doesn't seem to be anything using up any significant CPU. I see that you are running XGL perhaps that is going crazy every now and than?   Trying running without it for a while and see if that solves your problem.  To really see what's going on it would be helpful if you could somehow get the reult of ps aux while the system is spiking. See if maybe you can ssh into your system or jump to a different tty (ALT+CTRL+F1 or F2 or F3 ... F7 is your X) if your X is hanging and try to get the cpu usage there.

---

