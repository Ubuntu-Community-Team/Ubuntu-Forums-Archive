---
title: "Unusual behave - Virus Like"
date: 2015-04-09
forum: General Help
---

### Post by Flavio_SP on 2015-04-09
Hello everybody,

I am facing a very strange behave on my Ubuntu 14.04 LTS box. 
I have an IPTV system providing cable TV and Internet through a router. My Ubuntu box is connected to the router and provides file serving / print / internet services to my local network.

First symptom I noticed was a very poor performance on my TV system with image freezing and set top box complaining about lack of signal. After many calls to service provider without a solution, I noticed my Ubuntu box with fan turning at high speed.

A quick check and I noticed one single process taking up to 120% of CPU (it is a 4 core AMD) constantly. Strange enough, the process name was something like "hzydfardxg". By killing that process (which was running as root), cooler speed dropped to normal, not just that... My IPTV system resumed normal operation.

A few seconds later I noticed an increase in CPU load again and my IPTV stoped working, but now the process name have changed to "nujwyeloqx". After extensive checking that&#347; what I found:

- This strange named process starts as soon as I boot the machine
- An entry in /etc/init.d is created with same name of the suspect running process
- If I kill the process, a new one starts, with different random name and an entry in /etc/init.d is also created. Deleting the entry on /etc/init.d does not help
- When the process is running it takes lots of processor time and generates so much internet traffic that my IPTV stops working
- My machine does not boot on single user anymore, it freezes in the middle of the process or start asking for root password, which I provide but it seems to be incorrect because system asks again and again for root password.

This behave is very much like windows virus and despite knowing how linux security is I am inclined to say that my machine was infected. Not just that... It was probably infected while it was not even being used (as it is a network gateway nobody uses it as a desktop) which is even more unusual.

The computer is no longer connected to my IPTV router (internet) but I still  can see the processes being created and consuming CPU.

The very same think hapened to me last year on a 10.04 installation, since I was already planning to upgrade to 14.04 it did not bother me that much because I did a full install anyway. I was very surprised to see it happening again.

Do you guys have any clue on how to get rid of this behave?

Best regards,

Flavio

---

### Post by Holger_Gehrke on 2015-04-09
Three tools that can help you: 'ps -eF' to get a list of processes including as much information as the system has on them, including the id of the parent process (ppid), "lsof|grep 'name of the strange program' " to take a look at what files it uses and 'netstat -a --inet -p' to look at who it's talking to ...

---

### Post by Flavio_SP on 2015-04-09
I did some testing, check  the results of every command.

```
ps -u root | grep "suspect_process_name":

2008 ?        00:00:00 kmcilrgveg  (the suspect name this time is kmcilrgveg, PID is 2008)

============================================================

ps -eF Results:

UID        PID  PPID  C    SZ   RSS PSR STIME TTY          TIME CMD
root         1     0  0  8502  3336   1 19:14 ?        00:00:02 /sbin/init
root         2     0  0     0     0   2 19:14 ?        00:00:00 [kthreadd]
root         3     2  0     0     0   0 19:14 ?        00:00:00 [ksoftirqd/0]
root         5     2  0     0     0   0 19:14 ?        00:00:00 [kworker/0:0H]
root         7     2  0     0     0   0 19:14 ?        00:00:01 [rcu_sched]
root         8     2  0     0     0   1 19:14 ?        00:00:00 [rcuos/0]
root         9     2  0     0     0   1 19:14 ?        00:00:00 [rcuos/1]
root        10     2  0     0     0   3 19:14 ?        00:00:00 [rcuos/2]
root        11     2  0     0     0   2 19:14 ?        00:00:00 [rcuos/3]
root        12     2  0     0     0   0 19:14 ?        00:00:00 [rcu_bh]
root        13     2  0     0     0   0 19:14 ?        00:00:00 [rcuob/0]
root        14     2  0     0     0   0 19:14 ?        00:00:00 [rcuob/1]
root        15     2  0     0     0   0 19:14 ?        00:00:00 [rcuob/2]
root        16     2  0     0     0   0 19:14 ?        00:00:00 [rcuob/3]
root        17     2  0     0     0   0 19:14 ?        00:00:00 [migration/0]
root        18     2  0     0     0   0 19:14 ?        00:00:00 [watchdog/0]
root        19     2  0     0     0   1 19:14 ?        00:00:00 [watchdog/1]
root        20     2  0     0     0   1 19:14 ?        00:00:00 [migration/1]
root        21     2  0     0     0   1 19:14 ?        00:00:00 [ksoftirqd/1]
root        22     2  0     0     0   1 19:14 ?        00:00:00 [kworker/1:0]
root        23     2  0     0     0   1 19:14 ?        00:00:00 [kworker/1:0H]
root        24     2  0     0     0   2 19:14 ?        00:00:00 [watchdog/2]
root        25     2  0     0     0   2 19:14 ?        00:00:00 [migration/2]
root        26     2  0     0     0   2 19:14 ?        00:00:00 [ksoftirqd/2]
root        27     2  0     0     0   2 19:14 ?        00:00:00 [kworker/2:0]
root        28     2  0     0     0   2 19:14 ?        00:00:00 [kworker/2:0H]
root        29     2  0     0     0   3 19:14 ?        00:00:00 [watchdog/3]
root        30     2  0     0     0   3 19:14 ?        00:00:00 [migration/3]
root        31     2  0     0     0   3 19:14 ?        00:00:00 [ksoftirqd/3]
root        33     2  0     0     0   3 19:14 ?        00:00:00 [kworker/3:0H]
root        34     2  0     0     0   3 19:14 ?        00:00:00 [khelper]
root        35     2  0     0     0   2 19:14 ?        00:00:00 [kdevtmpfs]
root        36     2  0     0     0   3 19:14 ?        00:00:00 [netns]
root        37     2  0     0     0   3 19:14 ?        00:00:00 [writeback]
root        38     2  0     0     0   2 19:14 ?        00:00:00 [kintegrityd]
root        39     2  0     0     0   2 19:14 ?        00:00:00 [bioset]
root        40     2  0     0     0   0 19:14 ?        00:00:00 [kworker/u9:0]
root        41     2  0     0     0   2 19:14 ?        00:00:00 [kblockd]
root        42     2  0     0     0   2 19:14 ?        00:00:00 [ata_sff]
root        43     2  0     0     0   2 19:14 ?        00:00:00 [khubd]
root        44     2  0     0     0   2 19:14 ?        00:00:00 [md]
root        45     2  0     0     0   3 19:14 ?        00:00:00 [devfreq_wq]
root        46     2  0     0     0   0 19:14 ?        00:00:00 [kworker/0:1]
root        47     2  0     0     0   1 19:14 ?        00:00:00 [kworker/1:1]
root        48     2  0     0     0   2 19:14 ?        00:00:00 [kworker/2:1]
root        49     2  0     0     0   3 19:14 ?        00:00:00 [kworker/3:1]
root        50     2  0     0     0   2 19:14 ?        00:00:00 [khungtaskd]
root        51     2  0     0     0   1 19:14 ?        00:00:00 [kswapd0]
root        52     2  0     0     0   1 19:14 ?        00:00:00 [ksmd]
root        53     2  0     0     0   3 19:14 ?        00:00:00 [khugepaged]
root        54     2  0     0     0   3 19:14 ?        00:00:00 [fsnotify_mark]
root        55     2  0     0     0   1 19:14 ?        00:00:00 [ecryptfs-kthrea]
root        56     2  0     0     0   1 19:14 ?        00:00:00 [crypto]
root        68     2  0     0     0   1 19:14 ?        00:00:00 [kthrotld]
root        88     2  0     0     0   1 19:14 ?        00:00:00 [deferwq]
root        89     2  0     0     0   2 19:14 ?        00:00:00 [charger_manager]
root       140     2  0     0     0   3 19:14 ?        00:00:00 [scsi_eh_0]
root       141     2  0     0     0   0 19:14 ?        00:00:00 [scsi_eh_1]
root       143     2  0     0     0   1 19:14 ?        00:00:00 [scsi_eh_2]
root       145     2  0     0     0   0 19:14 ?        00:00:00 [scsi_eh_3]
root       146     2  0     0     0   1 19:14 ?        00:00:00 [scsi_eh_4]
root       147     2  0     0     0   1 19:14 ?        00:00:00 [scsi_eh_5]
root       148     2  0     0     0   1 19:14 ?        00:00:00 [scsi_eh_6]
root       149     2  0     0     0   0 19:14 ?        00:00:00 [scsi_eh_7]
root       157     2  0     0     0   3 19:14 ?        00:00:00 [scsi_eh_8]
root       158     2  0     0     0   0 19:14 ?        00:00:00 [scsi_eh_9]
root       159     2  0     0     0   0 19:14 ?        00:00:00 [scsi_eh_10]
root       160     2  0     0     0   0 19:14 ?        00:00:00 [scsi_eh_11]
root       161     2  0     0     0   1 19:14 ?        00:00:00 [scsi_eh_12]
root       162     2  0     0     0   1 19:14 ?        00:00:00 [scsi_eh_13]
root       163     2  0     0     0   0 19:14 ?        00:00:00 [scsi_eh_14]
root       164     2  0     0     0   0 19:14 ?        00:00:00 [scsi_eh_15]
root       170     2  0     0     0   3 19:14 ?        00:00:00 [kworker/u8:15]
root       171     2  0     0     0   3 19:14 ?        00:00:00 [kworker/u8:16]
root       174     2  0     0     0   3 19:14 ?        00:00:00 [kworker/u9:1]
root       179     2  0     0     0   2 19:14 ?        00:00:00 [kpsmoused]
root       182     2  0     0     0   3 19:14 ?        00:00:00 [kworker/3:2]
root       184     2  0     0     0   2 19:14 ?        00:00:00 [raid5wq]
root       216     2  0     0     0   3 19:14 ?        00:00:00 [jbd2/sdb1-8]
root       217     2  0     0     0   2 19:14 ?        00:00:00 [ext4-rsv-conver]
root       441     1  0  4868   648   1 19:14 ?        00:00:00 upstart-udev-bridge --daemon
root       445     1  0 12936  1924   0 19:14 ?        00:00:00 /lib/systemd/systemd-udevd --daemon
root       501     2  0     0     0   0 19:14 ?        00:00:00 [edac-poller]
root       574     2  0     0     0   0 19:14 ?        00:00:00 [kvm-irqfd-clean]
root       599     2  0     0     0   1 19:14 ?        00:00:00 [hd-audio0]
root       826     1  0  3847   760   3 19:14 ?        00:00:00 upstart-socket-bridge --daemon
root       887     2  0     0     0   1 19:14 ?        00:00:00 [bioset]
root       888     2  0     0     0   1 19:14 ?        00:00:00 [md2_raid1]
root       931     2  0     0     0   0 19:14 ?        00:00:00 [bioset]
root       932     2  0     0     0   2 19:14 ?        00:00:00 [md1_raid1]
root       936     2  0     0     0   1 19:14 ?        00:00:00 [bioset]
root       937     2  0     0     0   2 19:14 ?        00:00:00 [md0_raid1]
root       941     2  0     0     0   3 19:14 ?        00:00:00 [jbd2/md2-8]
root       944     2  0     0     0   2 19:14 ?        00:00:00 [ext4-rsv-conver]
root       963     1  0 57836  5856   0 19:14 ?        00:00:00 /usr/sbin/winbindd -F
root       993     1  0 68384  7900   2 19:14 ?        00:00:00 smbd -F
root      1000     1  0  3818   632   3 19:14 ?        00:00:00 upstart-file-bridge --daemon
syslog    1004     1  0 63960  1328   0 19:14 ?        00:00:00 rsyslogd
message+  1006     1  0 10033  2396   2 19:14 ?        00:00:00 dbus-daemon --system --fork
root      1031     1  0  4823  1452   0 19:14 ?        00:00:00 /usr/sbin/bluetoothd
root      1036     1  0 10862  1824   2 19:14 ?        00:00:00 /lib/systemd/systemd-logind
avahi     1041     1  0  8088  1640   1 19:14 ?        00:00:00 avahi-daemon: running [linux.local]
avahi     1042  1041  0  8055   464   0 19:14 ?        00:00:00 avahi-daemon: chroot helper
root      1055     2  0     0     0   2 19:14 ?        00:00:00 [krfcommd]
root      1057     1  0 38074  5628   2 19:14 ?        00:00:00 /usr/sbin/cupsd -f
root      1061   963  0 59303  4644   1 19:14 ?        00:00:00 /usr/sbin/winbindd -F
root      1062     1  0 49141  3572   1 19:14 ?        00:00:00 nmbd -D
root      1064   963  0 57836  3752   3 19:14 ?        00:00:00 /usr/sbin/winbindd -F
root      1065   963  0 57836  3040   0 19:14 ?        00:00:00 /usr/sbin/winbindd -F
colord    1067     1  0 75373  5676   1 19:14 ?        00:00:00 /usr/lib/colord/colord
root      1068   993  0 68384  3956   1 19:14 ?        00:00:00 smbd -F
lp        1081  1057  0 15789  1960   3 19:14 ?        00:00:00 /usr/lib/cups/notifier/dbus dbus:// 
lp        1082  1057  0 15789  1964   1 19:14 ?        00:00:00 /usr/lib/cups/notifier/dbus dbus:// 
root      1098     1  0 18871  3368   3 19:14 ?        00:00:00 /usr/sbin/cups-browsed
root      1100     2  0     0     0   3 19:14 ?        00:00:00 [ttm_swap]
root      1348     1  0 82558  6380   2 19:15 ?        00:00:00 /usr/sbin/ModemManager
root      1443     1  0 86787  7032   1 19:15 ?        00:00:00 NetworkManager
root      1461     1  0 70259  6904   2 19:15 ?        00:00:00 /usr/lib/policykit-1/polkitd --no-debug
nobody    1475  1443  0  8123  1508   1 19:15 ?        00:00:00 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/run/sendsigs.omit.d/network-manager.dnsmasq.pid --listen-address=127.0.1.1 --conf-file=/var/run/NetworkManager/dnsmasq.conf --cache-size=0 --proxy-dnssec --enable-dbus=org.freedesktop.NetworkManager.dnsmasq --conf-dir=/etc/NetworkManager/dnsmasq.d
root      1702     1  0  4321   944   3 19:15 tty4     00:00:00 /sbin/getty -8 38400 tty4
root      1706     1  0  4321   932   3 19:15 tty5     00:00:00 /sbin/getty -8 38400 tty5
root      1716     1  0  4321   932   3 19:15 tty2     00:00:00 /sbin/getty -8 38400 tty2
root      1717     1  0  4321   940   3 19:15 tty3     00:00:00 /sbin/getty -8 38400 tty3
root      1722     1  0  4321   936   3 19:15 tty6     00:00:00 /sbin/getty -8 38400 tty6
root      1780     1  0 15341  3028   1 19:15 ?        00:00:00 /usr/sbin/sshd -D
root      1800     1  0  5913  1032   0 19:15 ?        00:00:00 cron
daemon    1801     1  0  4784   164   2 19:15 ?        00:00:00 atd
bind      1809     1  0 99461 27764   0 19:15 ?        00:00:01 /usr/sbin/named -u bind
whoopsie  1817     1  0 90325  5084   1 19:15 ?        00:00:00 whoopsie
dhcpd     1826     1  0  5012  7212   1 19:15 ?        00:00:00 dhcpd -user dhcpd -group dhcpd -f -q -4 -pf /run/dhcp-server/dhcpd.pid -cf /etc/dhcp/dhcpd.conf
root      1828     1  0  4796   748   0 19:15 ?        00:00:00 /usr/sbin/irqbalance
root      1830     1  0  1091   684   0 19:15 ?        00:00:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
kernoops  1861     1  0  9285  1008   1 19:15 ?        00:00:00 /usr/sbin/kerneloops
root      1875     1  0  2670   680   0 19:15 ?        00:00:00 /usr/sbin/pptpd
root      1961     1  0  3351   508   1 19:15 ?        00:00:00 /sbin/mdadm --monitor --pid-file /run/mdadm/monitor.pid --daemonise --scan --syslog
root      2008     1  0  8402   276   2 19:15 ?        00:00:00 ls -la             
root      2063     1  0 69464  3628   2 19:15 ?        00:00:00 lightdm
root      2072     1  0 71870  6300   1 19:15 ?        00:00:00 /usr/lib/accountsservice/accounts-daemon
root      2104  2063  2 57628 35256   1 19:15 tty7     00:00:21 /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
mysql     2106     1  0 137523 87648  1 19:15 ?        00:00:02 /usr/sbin/mysqld
root      2122  2063  0 46263  3804   2 19:15 ?        00:00:00 lightdm --session-child 12 15
root      2125     2  0     0     0   3 19:15 ?        00:00:00 [kauditd]
root      2165     1  0 69063 15088   1 19:15 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  2179  2165  0 69069  5836   1 19:15 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  2180  2165  0 69069  5836   1 19:15 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  2181  2165  0 69069  5836   1 19:15 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  2182  2165  0 69069  5836   1 19:15 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  2183  2165  0 69069  5836   1 19:15 ?        00:00:00 /usr/sbin/apache2 -k start
master    2184  2122  0  9364  2532   3 19:15 ?        00:00:00 init --user
master    2260  2184  0 10034  2208   3 19:15 ?        00:00:00 dbus-daemon --fork --session --address=unix:abstract=/tmp/dbus-j0tpnTNtGw
master    2271  2184  0  4892  1152   0 19:15 ?        00:00:00 upstart-event-bridge
master    2278  2184  0 18866  4348   2 19:15 ?        00:00:00 /usr/lib/x86_64-linux-gnu/hud/window-stack-bridge
master    2279  2184  0 91972  3448   1 19:15 ?        00:00:00 gnome-keyring-daemon --start --components pkcs11,secrets
master    2281  2184  0 89746  4252   2 19:15 ?        00:00:03 /usr/bin/ibus-daemon --daemonize --xim
master    2292  2184  0 137447 14388  1 19:15 ?        00:00:00 /usr/lib/x86_64-linux-gnu/bamf/bamfdaemon
master    2302  2184  0  4894   400   0 19:15 ?        00:00:00 upstart-dbus-bridge --daemon --system --user --bus-name system
master    2305  2184  0 48478  3092   3 19:15 ?        00:00:00 /usr/lib/gvfs/gvfsd
master    2307  2184  0 84392  3280   3 19:15 ?        00:00:00 /usr/lib/at-spi2-core/at-spi-bus-launcher
master    2316  2307  0  9811  1968   3 19:15 ?        00:00:00 /bin/dbus-daemon --config-file=/etc/at-spi2/accessibility.conf --nofork --print-address 3
master    2319  2184  0 86415  3116   2 19:15 ?        00:00:00 /usr/lib/gvfs/gvfsd-fuse /run/user/1000/gvfs -f -o big_writes
master    2323  2184  0 31253  3324   0 19:15 ?        00:00:00 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
master    2326  2184  0  4894   636   2 19:15 ?        00:00:00 upstart-dbus-bridge --daemon --session --user --bus-name session
master    2331  2184  0 202219 20256  2 19:15 ?        00:00:00 /usr/lib/unity-settings-daemon/unity-settings-daemon
master    2337  2184  0 159234 22960  0 19:15 ?        00:00:00 /usr/lib/x86_64-linux-gnu/hud/hud-service
master    2344  2184  0 143187 13192  3 19:15 ?        00:00:00 gnome-session --session=ubuntu
master    2358  2184  0  7013   728   3 19:15 ?        00:00:00 upstart-file-bridge --daemon --user
master    2359  2184  0 124066 18452  3 19:15 ?        00:00:00 /usr/lib/unity/unity-panel-service
root      2387     1  0 59839  4416   3 19:15 ?        00:00:00 /usr/lib/upower/upowerd
master    2523  2281  0 69537  3400   0 19:15 ?        00:00:00 /usr/lib/ibus/ibus-dconf
master    2530  2281  0 119949 17068  3 19:15 ?        00:00:00 /usr/lib/ibus/ibus-ui-gtk3
master    2532  2184  0 96025  7364   1 19:15 ?        00:00:00 /usr/lib/ibus/ibus-x11 --kill-daemon
master    2557  2184  0 163202 13048  3 19:15 ?        00:00:00 /usr/lib/x86_64-linux-gnu/indicator-keyboard-service --use-gtk
master    2560  2184  0 83088  6980   2 19:15 ?        00:00:00 /usr/lib/x86_64-linux-gnu/indicator-messages/indicator-messages-service
master    2561  2184  0 65227  2848   0 19:15 ?        00:00:00 /usr/lib/x86_64-linux-gnu/indicator-bluetooth/indicator-bluetooth-service
master    2571  2184  0 68931  3268   0 19:15 ?        00:00:00 /usr/lib/x86_64-linux-gnu/indicator-power/indicator-power-service
master    2572  2184  0 290097 11748  2 19:15 ?        00:00:00 /usr/lib/x86_64-linux-gnu/indicator-datetime/indicator-datetime-service
master    2574  2184  0 118620 7844   3 19:15 ?        00:00:00 /usr/lib/x86_64-linux-gnu/indicator-sound/indicator-sound-service
master    2577  2184  0 111074 13736  3 19:15 ?        00:00:00 /usr/lib/x86_64-linux-gnu/indicator-printers/indicator-printers-service
master    2587  2184  0 222748 5912   3 19:15 ?        00:00:00 /usr/lib/x86_64-linux-gnu/indicator-session/indicator-session-service
master    2614  2184  0 71686  4948   1 19:15 ?        00:00:00 /usr/lib/x86_64-linux-gnu/indicator-application/indicator-application-service
master    2627  2184  0 119548 12460  2 19:15 ?        00:00:00 /usr/lib/evolution/evolution-source-registry
master    2635  2184  0 44576  2684   2 19:15 ?        00:00:00 /usr/lib/dconf/dconf-service
root      2636     2  0     0     0   0 19:15 ?        00:00:00 [kworker/0:2]
master    2652  2184  0 110684 6176   3 19:15 ?        00:00:00 /usr/bin/pulseaudio --start --log-target=syslog
rtkit     2659     1  0 42228  1280   2 19:15 ?        00:00:00 /usr/lib/rtkit/rtkit-daemon
master    2677  2281  0 50605  7320   0 19:15 ?        00:00:00 /usr/lib/ibus/ibus-engine-simple
master    2786  2184  0 218603 45856  0 19:15 ?        00:00:00 /usr/lib/evolution/evolution-calendar-factory
master    2817  2184  0 84424  9920   3 19:15 ?        00:00:00 /usr/lib/x86_64-linux-gnu/notify-osd
master    2821  2344  2 371811 88752  0 19:15 ?        00:00:19 compiz --sm-client-id 10b1976e9964c5d9b142373564994322100000022890001
master    2877  2344  0 82259  9464   3 19:15 ?        00:00:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
master    2880  2344  0 148990 20084  3 19:15 ?        00:00:00 nm-applet
master    2888  2344  0 239336 34176  3 19:15 ?        00:00:00 nautilus -n
master    2898  2344  0 100152 9636   3 19:15 ?        00:00:00 /usr/lib/unity-settings-daemon/unity-fallback-mount-helper
master    2944  2184  0 74059  8084   1 19:15 ?        00:00:00 /usr/lib/gvfs/gvfs-udisks2-volume-monitor
root      2954     1  0 93027  8100   0 19:15 ?        00:00:00 /usr/lib/udisks2/udisksd --no-debug
master    2989  2184  0 13855  3616   2 19:15 ?        00:00:00 /usr/lib/x86_64-linux-gnu/gconf/gconfd-2
master    3024  2184  0 70808  5360   3 19:15 ?        00:00:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
master    3032  2184  0 52427  3044   3 19:15 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
master    3038  2184  0 49386  2736   3 19:15 ?        00:00:00 /usr/lib/gvfs/gvfs-mtp-volume-monitor
master    3048  2184  0 107603 5800   2 19:15 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.9 /org/gtk/gvfs/exec_spaw/0
master    3097  2184  0 30428  2696   1 19:15 ?        00:00:00 /usr/lib/gvfs/gvfsd-metadata
root      3100     1  0 22248 25076   0 19:15 ?        00:00:00 /usr/bin/perl /usr/share/webmin/miniserv.pl /etc/webmin/miniserv.conf
root      3106     1  0  4321   944   2 19:15 tty1     00:00:00 /sbin/getty -8 38400 tty1
master    3131  2184  0 66912  2772   0 19:15 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.9 /org/gtk/gvfs/exec_spaw/1
master    3446  2184  0 166325 27048  0 19:15 ?        00:00:07 gnome-terminal
master    3591  3446  0  3705   812   3 19:15 ?        00:00:00 gnome-pty-helper
master    3595  3446  0  6058  3792   1 19:15 pts/1    00:00:00 bash
master    4827  3595  0  6637  1792   3 19:15 pts/1    00:00:03 top
master    5108  2344  0 113107 11932  2 19:15 ?        00:00:00 telepathy-indicator
master    5117  2184  0 80618  7208   3 19:15 ?        00:00:00 /usr/lib/telepathy/mission-control-5
master    5145  2344  0 120927 9088   0 19:15 ?        00:00:00 zeitgeist-datahub
master    5150  2184  0 87244  4620   2 19:15 ?        00:00:00 /usr/bin/zeitgeist-daemon
master    5156  2184  0 58643  8840   0 19:15 ?        00:00:00 /usr/lib/x86_64-linux-gnu/zeitgeist-fts
master    5162  5156  0  2170   360   1 19:15 ?        00:00:00 /bin/cat
master    5197  3446  0  6057  3872   0 19:15 pts/3    00:00:00 bash
ntp       5237     1  0  8377  2028   1 19:15 ?        00:00:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 122:132
master    5397  3446  0  6058  3868   1 19:16 pts/4    00:00:00 bash
master    5468  2344  0 123535 11008  3 19:16 ?        00:00:00 update-notifier
master    5674  2344  0 93752  3800   1 19:17 ?        00:00:00 /usr/lib/x86_64-linux-gnu/deja-dup/deja-dup-monitor
master    5775  2184  0 152215 16900  1 19:17 ?        00:00:00 /usr/lib/x86_64-linux-gnu/unity-scope-home/unity-scope-home
master    5801  2184  0 147205 23920  2 19:17 ?        00:00:00 /usr/bin/unity-scope-loader applications/applications.scope applications/scopes.scope commands.scope
master    5803  2184  0 147860 10312  3 19:17 ?        00:00:00 /usr/lib/x86_64-linux-gnu/unity-lens-files/unity-files-daemon
master    5848  2184  1 145249 15752  0 19:17 ?        00:00:10 gkrellm
master    6773  3446  0  6057  3872   2 19:22 pts/2    00:00:00 bash
root      8093     2  0     0     0   0 19:28 ?        00:00:00 [kworker/u8:0]
root      8522     1  0   360   836   2 19:30 ?        00:00:00 ifconfig                         
root      8525     1  0   360   836   1 19:30 ?        00:00:00 ifconfig eth0                         
root      8526     1  0   360   836   0 19:30 ?        00:00:00 cd /etc                         
root      8528     1  0   360   840   3 19:30 ?        00:00:00 echo "find"                         
root      8530     1  0   360   832   2 19:30 ?        00:00:00 ls                         
master    8531  5397  0  4978  1284   3 19:30 pts/4    00:00:00 ps -eF

================================================================

ps aux Results:

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.2  0.0  34008  3336 ?        Ss   19:14   0:02 /sbin/init
root         2  0.0  0.0      0     0 ?        S    19:14   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    19:14   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   19:14   0:00 [kworker/0:0H]
root         7  0.1  0.0      0     0 ?        R    19:14   0:01 [rcu_sched]
root         8  0.0  0.0      0     0 ?        S    19:14   0:00 [rcuos/0]
root         9  0.0  0.0      0     0 ?        S    19:14   0:00 [rcuos/1]
root        10  0.0  0.0      0     0 ?        S    19:14   0:00 [rcuos/2]
root        11  0.0  0.0      0     0 ?        S    19:14   0:00 [rcuos/3]
root        12  0.0  0.0      0     0 ?        S    19:14   0:00 [rcu_bh]
root        13  0.0  0.0      0     0 ?        S    19:14   0:00 [rcuob/0]
root        14  0.0  0.0      0     0 ?        S    19:14   0:00 [rcuob/1]
root        15  0.0  0.0      0     0 ?        S    19:14   0:00 [rcuob/2]
root        16  0.0  0.0      0     0 ?        S    19:14   0:00 [rcuob/3]
root        17  0.0  0.0      0     0 ?        S    19:14   0:00 [migration/0]
root        18  0.0  0.0      0     0 ?        S    19:14   0:00 [watchdog/0]
root        19  0.0  0.0      0     0 ?        S    19:14   0:00 [watchdog/1]
root        20  0.0  0.0      0     0 ?        S    19:14   0:00 [migration/1]
root        21  0.0  0.0      0     0 ?        S    19:14   0:00 [ksoftirqd/1]
root        22  0.0  0.0      0     0 ?        S    19:14   0:00 [kworker/1:0]
root        23  0.0  0.0      0     0 ?        S<   19:14   0:00 [kworker/1:0H]
root        24  0.0  0.0      0     0 ?        S    19:14   0:00 [watchdog/2]
root        25  0.0  0.0      0     0 ?        S    19:14   0:00 [migration/2]
root        26  0.0  0.0      0     0 ?        S    19:14   0:00 [ksoftirqd/2]
root        27  0.0  0.0      0     0 ?        S    19:14   0:00 [kworker/2:0]
root        28  0.0  0.0      0     0 ?        S<   19:14   0:00 [kworker/2:0H]
root        29  0.0  0.0      0     0 ?        S    19:14   0:00 [watchdog/3]
root        30  0.0  0.0      0     0 ?        S    19:14   0:00 [migration/3]
root        31  0.0  0.0      0     0 ?        S    19:14   0:00 [ksoftirqd/3]
root        33  0.0  0.0      0     0 ?        S<   19:14   0:00 [kworker/3:0H]
root        34  0.0  0.0      0     0 ?        S<   19:14   0:00 [khelper]
root        35  0.0  0.0      0     0 ?        S    19:14   0:00 [kdevtmpfs]
root        36  0.0  0.0      0     0 ?        S<   19:14   0:00 [netns]
root        37  0.0  0.0      0     0 ?        S<   19:14   0:00 [writeback]
root        38  0.0  0.0      0     0 ?        S<   19:14   0:00 [kintegrityd]
root        39  0.0  0.0      0     0 ?        S<   19:14   0:00 [bioset]
root        40  0.0  0.0      0     0 ?        S<   19:14   0:00 [kworker/u9:0]
root        41  0.0  0.0      0     0 ?        S<   19:14   0:00 [kblockd]
root        42  0.0  0.0      0     0 ?        S<   19:14   0:00 [ata_sff]
root        43  0.0  0.0      0     0 ?        S    19:14   0:00 [khubd]
root        44  0.0  0.0      0     0 ?        S<   19:14   0:00 [md]
root        45  0.0  0.0      0     0 ?        S<   19:14   0:00 [devfreq_wq]
root        46  0.0  0.0      0     0 ?        S    19:14   0:00 [kworker/0:1]
root        47  0.0  0.0      0     0 ?        S    19:14   0:00 [kworker/1:1]
root        48  0.0  0.0      0     0 ?        S    19:14   0:00 [kworker/2:1]
root        49  0.0  0.0      0     0 ?        S    19:14   0:00 [kworker/3:1]
root        50  0.0  0.0      0     0 ?        S    19:14   0:00 [khungtaskd]
root        51  0.0  0.0      0     0 ?        S    19:14   0:00 [kswapd0]
root        52  0.0  0.0      0     0 ?        SN   19:14   0:00 [ksmd]
root        53  0.0  0.0      0     0 ?        SN   19:14   0:00 [khugepaged]
root        54  0.0  0.0      0     0 ?        S    19:14   0:00 [fsnotify_mark]
root        55  0.0  0.0      0     0 ?        S    19:14   0:00 [ecryptfs-kthrea]
root        56  0.0  0.0      0     0 ?        S<   19:14   0:00 [crypto]
root        68  0.0  0.0      0     0 ?        S<   19:14   0:00 [kthrotld]
root        88  0.0  0.0      0     0 ?        S<   19:14   0:00 [deferwq]
root        89  0.0  0.0      0     0 ?        S<   19:14   0:00 [charger_manager]
root       140  0.0  0.0      0     0 ?        S    19:14   0:00 [scsi_eh_0]
root       141  0.0  0.0      0     0 ?        S    19:14   0:00 [scsi_eh_1]
root       143  0.0  0.0      0     0 ?        S    19:14   0:00 [scsi_eh_2]
root       145  0.0  0.0      0     0 ?        S    19:14   0:00 [scsi_eh_3]
root       146  0.0  0.0      0     0 ?        S    19:14   0:00 [scsi_eh_4]
root       147  0.0  0.0      0     0 ?        S    19:14   0:00 [scsi_eh_5]
root       148  0.0  0.0      0     0 ?        S    19:14   0:00 [scsi_eh_6]
root       149  0.0  0.0      0     0 ?        S    19:14   0:00 [scsi_eh_7]
root       157  0.0  0.0      0     0 ?        S    19:14   0:00 [scsi_eh_8]
root       158  0.0  0.0      0     0 ?        S    19:14   0:00 [scsi_eh_9]
root       159  0.0  0.0      0     0 ?        S    19:14   0:00 [scsi_eh_10]
root       160  0.0  0.0      0     0 ?        S    19:14   0:00 [scsi_eh_11]
root       161  0.0  0.0      0     0 ?        S    19:14   0:00 [scsi_eh_12]
root       162  0.0  0.0      0     0 ?        S    19:14   0:00 [scsi_eh_13]
root       163  0.0  0.0      0     0 ?        S    19:14   0:00 [scsi_eh_14]
root       164  0.0  0.0      0     0 ?        S    19:14   0:00 [scsi_eh_15]
root       170  0.0  0.0      0     0 ?        S    19:14   0:00 [kworker/u8:15]
root       171  0.0  0.0      0     0 ?        S    19:14   0:00 [kworker/u8:16]
root       174  0.0  0.0      0     0 ?        S<   19:14   0:00 [kworker/u9:1]
root       179  0.0  0.0      0     0 ?        S<   19:14   0:00 [kpsmoused]
root       182  0.0  0.0      0     0 ?        S    19:14   0:00 [kworker/3:2]
root       184  0.0  0.0      0     0 ?        S<   19:14   0:00 [raid5wq]
root       216  0.0  0.0      0     0 ?        S    19:14   0:00 [jbd2/sdb1-8]
root       217  0.0  0.0      0     0 ?        S<   19:14   0:00 [ext4-rsv-conver]
root       441  0.0  0.0  19472   648 ?        S    19:14   0:00 upstart-udev-bridge --daemon
root       445  0.0  0.0  51744  1924 ?        Ss   19:14   0:00 /lib/systemd/systemd-udevd --daemon
root       501  0.0  0.0      0     0 ?        S<   19:14   0:00 [edac-poller]
root       574  0.0  0.0      0     0 ?        S<   19:14   0:00 [kvm-irqfd-clean]
root       599  0.0  0.0      0     0 ?        S<   19:14   0:00 [hd-audio0]
root       826  0.0  0.0  15388   760 ?        S    19:14   0:00 upstart-socket-bridge --daemon
root       887  0.0  0.0      0     0 ?        S<   19:14   0:00 [bioset]
root       888  0.0  0.0      0     0 ?        S    19:14   0:00 [md2_raid1]
root       931  0.0  0.0      0     0 ?        S<   19:14   0:00 [bioset]
root       932  0.0  0.0      0     0 ?        S    19:14   0:00 [md1_raid1]
root       936  0.0  0.0      0     0 ?        S<   19:14   0:00 [bioset]
root       937  0.0  0.0      0     0 ?        S    19:14   0:00 [md0_raid1]
root       941  0.0  0.0      0     0 ?        S    19:14   0:00 [jbd2/md2-8]
root       944  0.0  0.0      0     0 ?        S<   19:14   0:00 [ext4-rsv-conver]
root       963  0.0  0.1 231344  5856 ?        Ss   19:14   0:00 /usr/sbin/winbindd -F
root       993  0.0  0.2 273536  7900 ?        Ss   19:14   0:00 smbd -F
root      1000  0.0  0.0  15272   632 ?        S    19:14   0:00 upstart-file-bridge --daemon
syslog    1004  0.0  0.0 255840  1328 ?        Ssl  19:14   0:00 rsyslogd
message+  1006  0.0  0.0  40132  2396 ?        Ss   19:14   0:00 dbus-daemon --system --fork
root      1031  0.0  0.0  19292  1452 ?        Ss   19:14   0:00 /usr/sbin/bluetoothd
root      1036  0.0  0.0  43448  1824 ?        Ss   19:14   0:00 /lib/systemd/systemd-logind
avahi     1041  0.0  0.0  32352  1640 ?        S    19:14   0:00 avahi-daemon: running [linux.local]
avahi     1042  0.0  0.0  32220   464 ?        S    19:14   0:00 avahi-daemon: chroot helper
root      1055  0.0  0.0      0     0 ?        S<   19:14   0:00 [krfcommd]
root      1057  0.0  0.1 152296  5628 ?        Ssl  19:14   0:00 /usr/sbin/cupsd -f
root      1061  0.0  0.1 237212  4644 ?        S    19:14   0:00 /usr/sbin/winbindd -F
root      1062  0.0  0.0 196564  3572 ?        Ss   19:14   0:00 nmbd -D
root      1064  0.0  0.0 231344  3752 ?        S    19:14   0:00 /usr/sbin/winbindd -F
root      1065  0.0  0.0 231344  3040 ?        S    19:14   0:00 /usr/sbin/winbindd -F
colord    1067  0.0  0.1 301492  5676 ?        Sl   19:14   0:00 /usr/lib/colord/colord
root      1068  0.0  0.1 273536  3956 ?        S    19:14   0:00 smbd -F
lp        1081  0.0  0.0  63156  1960 ?        S    19:14   0:00 /usr/lib/cups/notifier/dbus dbus:// 
lp        1082  0.0  0.0  63156  1964 ?        S    19:14   0:00 /usr/lib/cups/notifier/dbus dbus:// 
root      1098  0.0  0.0  75484  3368 ?        Ss   19:14   0:00 /usr/sbin/cups-browsed
root      1100  0.0  0.0      0     0 ?        S<   19:14   0:00 [ttm_swap]
root      1348  0.0  0.1 330232  4356 ?        Ssl  19:15   0:00 /usr/sbin/ModemManager
root      1443  0.0  0.1 347148  7032 ?        Ssl  19:15   0:00 NetworkManager
root      1461  0.0  0.1 281036  6904 ?        Sl   19:15   0:00 /usr/lib/policykit-1/polkitd --no-debug
nobody    1475  0.0  0.0  32492  1508 ?        S    19:15   0:00 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/run/sendsigs.omit.d/network-manager.dnsmasq.pid --listen-address=127.0.1.1 --conf-file=/var/run/NetworkManager/dnsmasq.conf --cache-size=0 --proxy-dnssec --enable-dbus=org.freedesktop.NetworkManager.dnsmasq --conf-dir=/etc/NetworkManager/dnsmasq.d
root      1702  0.0  0.0  17284   944 tty4     Ss+  19:15   0:00 /sbin/getty -8 38400 tty4
root      1706  0.0  0.0  17284   932 tty5     Ss+  19:15   0:00 /sbin/getty -8 38400 tty5
root      1716  0.0  0.0  17284   932 tty2     Ss+  19:15   0:00 /sbin/getty -8 38400 tty2
root      1717  0.0  0.0  17284   940 tty3     Ss+  19:15   0:00 /sbin/getty -8 38400 tty3
root      1722  0.0  0.0  17284   936 tty6     Ss+  19:15   0:00 /sbin/getty -8 38400 tty6
root      1780  0.0  0.0  61364  3028 ?        Ss   19:15   0:00 /usr/sbin/sshd -D
root      1800  0.0  0.0  23652  1028 ?        Ss   19:15   0:00 cron
daemon    1801  0.0  0.0  19136   164 ?        Ss   19:15   0:00 atd
bind      1809  0.1  0.7 397844 27332 ?        Ssl  19:15   0:01 /usr/sbin/named -u bind
whoopsie  1817  0.0  0.1 361300  5084 ?        Ssl  19:15   0:00 whoopsie
dhcpd     1826  0.0  0.1  20048  7212 ?        Ss   19:15   0:00 dhcpd -user dhcpd -group dhcpd -f -q -4 -pf /run/dhcp-server/dhcpd.pid -cf /etc/dhcp/dhcpd.conf
root      1828  0.0  0.0  19184   748 ?        Ss   19:15   0:00 /usr/sbin/irqbalance
root      1830  0.0  0.0   4364   684 ?        Ss   19:15   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
kernoops  1861  0.0  0.0  37140  1008 ?        Ss   19:15   0:00 /usr/sbin/kerneloops
root      1875  0.0  0.0  10680   680 ?        Ss   19:15   0:00 /usr/sbin/pptpd
root      1961  0.0  0.0  13404   508 ?        Ss   19:15   0:00 /sbin/mdadm --monitor --pid-file /run/mdadm/monitor.pid --daemonise --scan --syslog
root      2008  0.0  0.0  33608   276 ?        Ssl  19:15   0:00 ls -la             
root      2063  0.0  0.0 277856  3628 ?        Ssl  19:15   0:00 lightdm
root      2072  0.0  0.1 287480  6300 ?        Sl   19:15   0:00 /usr/lib/accountsservice/accounts-daemon
root      2104  2.2  0.9 230512 35076 tty7     Ss+  19:15   0:17 /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
mysql     2106  0.2  2.3 550092 87648 ?        Ssl  19:15   0:02 /usr/sbin/mysqld
root      2122  0.0  0.1 185052  3804 ?        Sl   19:15   0:00 lightdm --session-child 12 15
root      2125  0.0  0.0      0     0 ?        S    19:15   0:00 [kauditd]
root      2165  0.0  0.3 276252 15088 ?        Ss   19:15   0:00 /usr/sbin/apache2 -k start
www-data  2179  0.0  0.1 276276  5836 ?        S    19:15   0:00 /usr/sbin/apache2 -k start
www-data  2180  0.0  0.1 276276  5836 ?        S    19:15   0:00 /usr/sbin/apache2 -k start
www-data  2181  0.0  0.1 276276  5836 ?        S    19:15   0:00 /usr/sbin/apache2 -k start
www-data  2182  0.0  0.1 276276  5836 ?        S    19:15   0:00 /usr/sbin/apache2 -k start
www-data  2183  0.0  0.1 276276  5836 ?        S    19:15   0:00 /usr/sbin/apache2 -k start
master    2184  0.0  0.0  37456  2532 ?        Ss   19:15   0:00 init --user
master    2260  0.0  0.0  40136  2208 ?        Ss   19:15   0:00 dbus-daemon --fork --session --address=unix:abstract=/tmp/dbus-j0tpnTNtGw
master    2271  0.0  0.0  19568  1152 ?        Ss   19:15   0:00 upstart-event-bridge
master    2278  0.0  0.1  75464  4348 ?        Ss   19:15   0:00 /usr/lib/x86_64-linux-gnu/hud/window-stack-bridge
master    2279  0.0  0.0 367888  3448 ?        Sl   19:15   0:00 gnome-keyring-daemon --start --components pkcs11,secrets
master    2281  0.3  0.1 358984  4252 ?        Ssl  19:15   0:02 /usr/bin/ibus-daemon --daemonize --xim
master    2292  0.0  0.3 549788 14388 ?        Sl   19:15   0:00 /usr/lib/x86_64-linux-gnu/bamf/bamfdaemon
master    2302  0.0  0.0  19576   400 ?        S    19:15   0:00 upstart-dbus-bridge --daemon --system --user --bus-name system
master    2305  0.0  0.0 193912  3092 ?        Sl   19:15   0:00 /usr/lib/gvfs/gvfsd
master    2307  0.0  0.0 337568  3280 ?        Sl   19:15   0:00 /usr/lib/at-spi2-core/at-spi-bus-launcher
master    2316  0.0  0.0  39244  1968 ?        S    19:15   0:00 /bin/dbus-daemon --config-file=/etc/at-spi2/accessibility.conf --nofork --print-address 3
master    2319  0.0  0.0 345660  3116 ?        Sl   19:15   0:00 /usr/lib/gvfs/gvfsd-fuse /run/user/1000/gvfs -f -o big_writes
master    2323  0.0  0.0 125012  3324 ?        Sl   19:15   0:00 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
master    2326  0.0  0.0  19576   636 ?        S    19:15   0:00 upstart-dbus-bridge --daemon --session --user --bus-name session
master    2331  0.0  0.5 808876 20256 ?        Ssl  19:15   0:00 /usr/lib/unity-settings-daemon/unity-settings-daemon
master    2337  0.0  0.6 636936 22956 ?        Ssl  19:15   0:00 /usr/lib/x86_64-linux-gnu/hud/hud-service
master    2344  0.0  0.3 572748 13192 ?        Ssl  19:15   0:00 gnome-session --session=ubuntu
master    2358  0.0  0.0  28052   728 ?        S    19:15   0:00 upstart-file-bridge --daemon --user
master    2359  0.0  0.4 496264 18188 ?        Ssl  19:15   0:00 /usr/lib/unity/unity-panel-service
root      2387  0.0  0.1 239356  4416 ?        Sl   19:15   0:00 /usr/lib/upower/upowerd
master    2523  0.0  0.0 278148  3400 ?        Sl   19:15   0:00 /usr/lib/ibus/ibus-dconf
master    2530  0.0  0.4 479796 17068 ?        Sl   19:15   0:00 /usr/lib/ibus/ibus-ui-gtk3
master    2532  0.0  0.1 384100  7364 ?        Sl   19:15   0:00 /usr/lib/ibus/ibus-x11 --kill-daemon
master    2557  0.0  0.3 652808 13048 ?        Sl   19:15   0:00 /usr/lib/x86_64-linux-gnu/indicator-keyboard-service --use-gtk
master    2560  0.0  0.1 332352  6980 ?        Ssl  19:15   0:00 /usr/lib/x86_64-linux-gnu/indicator-messages/indicator-messages-service
master    2561  0.0  0.0 260908  2848 ?        Ssl  19:15   0:00 /usr/lib/x86_64-linux-gnu/indicator-bluetooth/indicator-bluetooth-service
master    2571  0.0  0.0 275724  3268 ?        Ssl  19:15   0:00 /usr/lib/x86_64-linux-gnu/indicator-power/indicator-power-service
master    2572  0.0  0.3 1160388 11692 ?       Ssl  19:15   0:00 /usr/lib/x86_64-linux-gnu/indicator-datetime/indicator-datetime-service
master    2574  0.0  0.2 474480  7844 ?        Ssl  19:15   0:00 /usr/lib/x86_64-linux-gnu/indicator-sound/indicator-sound-service
master    2577  0.0  0.3 444296 13736 ?        Ssl  19:15   0:00 /usr/lib/x86_64-linux-gnu/indicator-printers/indicator-printers-service
master    2587  0.0  0.1 890992  5912 ?        Ssl  19:15   0:00 /usr/lib/x86_64-linux-gnu/indicator-session/indicator-session-service
master    2614  0.0  0.1 286744  4948 ?        Ssl  19:15   0:00 /usr/lib/x86_64-linux-gnu/indicator-application/indicator-application-service
master    2627  0.0  0.3 478192 12460 ?        Sl   19:15   0:00 /usr/lib/evolution/evolution-source-registry
master    2635  0.0  0.0 178304  2684 ?        Sl   19:15   0:00 /usr/lib/dconf/dconf-service
root      2636  0.0  0.0      0     0 ?        S    19:15   0:00 [kworker/0:2]
master    2652  0.0  0.1 442736  6176 ?        S<l  19:15   0:00 /usr/bin/pulseaudio --start --log-target=syslog
rtkit     2659  0.0  0.0 168912  1280 ?        SNl  19:15   0:00 /usr/lib/rtkit/rtkit-daemon
master    2677  0.1  0.1 202420  7320 ?        Sl   19:15   0:00 /usr/lib/ibus/ibus-engine-simple
master    2786  0.0  1.2 874412 45856 ?        Sl   19:15   0:00 /usr/lib/evolution/evolution-calendar-factory
master    2817  0.0  0.2 337696  9920 ?        Sl   19:15   0:00 /usr/lib/x86_64-linux-gnu/notify-osd
master    2821  2.0  2.3 1487244 88752 ?       Sl   19:15   0:15 compiz --sm-client-id 10b1976e9964c5d9b142373564994322100000022890001
master    2877  0.0  0.2 329036  9464 ?        Sl   19:15   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
master    2880  0.0  0.5 595960 20084 ?        Sl   19:15   0:00 nm-applet
master    2888  0.0  0.9 957344 34176 ?        Sl   19:15   0:00 nautilus -n
master    2898  0.0  0.2 400608  9636 ?        Sl   19:15   0:00 /usr/lib/unity-settings-daemon/unity-fallback-mount-helper
master    2944  0.0  0.2 296236  8084 ?        Sl   19:15   0:00 /usr/lib/gvfs/gvfs-udisks2-volume-monitor
root      2954  0.0  0.2 372108  8100 ?        Sl   19:15   0:00 /usr/lib/udisks2/udisksd --no-debug
master    2989  0.0  0.0  55420  3616 ?        S    19:15   0:00 /usr/lib/x86_64-linux-gnu/gconf/gconfd-2
master    3024  0.0  0.1 283232  5360 ?        Sl   19:15   0:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
master    3032  0.0  0.0 209708  3044 ?        Sl   19:15   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
master    3038  0.0  0.0 197544  2736 ?        Sl   19:15   0:00 /usr/lib/gvfs/gvfs-mtp-volume-monitor
master    3048  0.0  0.1 430412  5800 ?        Sl   19:15   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.9 /org/gtk/gvfs/exec_spaw/0
master    3097  0.0  0.0 121712  2696 ?        Sl   19:15   0:00 /usr/lib/gvfs/gvfsd-metadata
root      3100  0.0  0.6  88992 25076 ?        Ss   19:15   0:00 /usr/bin/perl /usr/share/webmin/miniserv.pl /etc/webmin/miniserv.conf
root      3106  0.0  0.0  17284   944 tty1     Ss+  19:15   0:00 /sbin/getty -8 38400 tty1
master    3131  0.0  0.0 267648  2772 ?        Sl   19:15   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.9 /org/gtk/gvfs/exec_spaw/1
master    3446  0.8  0.7 665484 27080 ?        Sl   19:15   0:06 gnome-terminal
master    3591  0.0  0.0  14820   812 ?        S    19:15   0:00 gnome-pty-helper
master    3595  0.0  0.1  24232  3792 pts/1    Ss   19:15   0:00 bash
master    4827  0.3  0.0  26548  1772 pts/1    S+   19:15   0:02 top
master    5108  0.0  0.3 452428 11932 ?        Sl   19:15   0:00 telepathy-indicator
master    5117  0.0  0.1 322472  7208 ?        Sl   19:15   0:00 /usr/lib/telepathy/mission-control-5
master    5145  0.0  0.2 483708  9088 ?        Sl   19:15   0:00 zeitgeist-datahub
master    5150  0.0  0.1 348976  4620 ?        Sl   19:15   0:00 /usr/bin/zeitgeist-daemon
master    5156  0.0  0.2 234572  8840 ?        Sl   19:15   0:00 /usr/lib/x86_64-linux-gnu/zeitgeist-fts
master    5162  0.0  0.0   8680   360 ?        S    19:15   0:00 /bin/cat
master    5197  0.0  0.1  24228  3872 pts/3    Ss+  19:15   0:00 bash
ntp       5237  0.0  0.0  33508  2028 ?        Ss   19:15   0:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 122:132
master    5397  0.0  0.1  24232  3868 pts/4    Ss   19:16   0:00 bash
master    5468  0.0  0.2 494140 11008 ?        Sl   19:16   0:00 update-notifier
master    5674  0.0  0.1 375008  3800 ?        Sl   19:17   0:00 /usr/lib/x86_64-linux-gnu/deja-dup/deja-dup-monitor
master    5775  0.0  0.4 608860 16900 ?        Sl   19:17   0:00 /usr/lib/x86_64-linux-gnu/unity-scope-home/unity-scope-home
master    5801  0.0  0.5 588820 21884 ?        Sl   19:17   0:00 /usr/bin/unity-scope-loader applications/applications.scope applications/scopes.scope commands.scope
master    5803  0.0  0.2 591440 10312 ?        Sl   19:17   0:00 /usr/lib/x86_64-linux-gnu/unity-lens-files/unity-files-daemon
master    5848  1.4  0.4 580996 15752 ?        Sl   19:17   0:08 gkrellm
master    6773  0.0  0.1  24228  3872 pts/2    Ss+  19:22   0:00 bash
root      7994  0.0  0.0   1440   836 ?        Ss   19:27   0:00 cat resolv.conf                         
root      7996  0.0  0.0   1440   832 ?        Ss   19:27   0:00 netstat -antop                         
root      8001  0.0  0.0   1440   836 ?        Ss   19:27   0:00 ls -la                         
root      8002  0.0  0.0   1440   836 ?        Ss   19:27   0:00 grep "A"                         
root      8003  0.0  0.0   1440   836 ?        Ss   19:27   0:00 netstat -antop                         
root      8013  0.0  0.0   1440   832 ?        Ss   19:27   0:00 cd /etc                         
root      8016  0.0  0.0   1440   836 ?        Ss   19:27   0:00 netstat -an                         
root      8018  0.0  0.0   1440   836 ?        Ss   19:27   0:00 netstat -an                         
root      8020  0.0  0.0   1440   832 ?        Ss   19:27   0:00 ls -la                         
root      8021  0.0  0.0   1440   840 ?        Ss   19:27   0:00 gnome-terminal                         
root      8022  0.0  0.0  85288  2244 pts/4    S+   19:27   0:00 sudo ps aux
root      8023  0.0  0.0  19912  1280 pts/4    R+   19:27   0:00 ps aux

============================================================

lsof | grep kmcilrgveg results:

kmcilrgve 2008            root  txt       REG               8,17   617704    3407892 /usr/bin/kmcilrgveg
kmcilrgve 2008 2018       root  txt       REG               8,17   617704    3407892 /usr/bin/kmcilrgveg
kmcilrgve 2008 2019       root  txt       REG               8,17   617704    3407892 /usr/bin/kmcilrgveg
kmcilrgve 2008 2020       root  txt       REG               8,17   617704    3407892 /usr/bin/kmcilrgveg
kmcilrgve 2008 2021       root  txt       REG               8,17   617704    3407892 /usr/bin/kmcilrgveg
```

I even have the executable renamed and set apart, in case you guys want it for evalution.

Any sugestion to remove this think?

tahnks for helping.

---

### Post by Holger_Gehrke on 2015-04-10
A bit of searching on the net led me to [http://superuser.com/questions/877896/unknown-linux-process-with-random-command](http://superuser.com/questions/877896/unknown-linux-process-with-random-command) ,
although that one comes up as 'whoami' in ps while yours pretends to be a 'ls -la' started by process 1 (init) 
It seems you've got yourself a trojan/worm that turns your machine into part of a DDOS botnet with infection though a brute force attack against ssh. Is this machine connected to the internet directly or through a router ? In the latter case you should review the rules for your firewall on the router; in the first case, why is there no firewall on you machine ?

---

### Post by Flavio_SP on 2015-04-10
Thank you my friend, now at least I know what is happening. 
The  machine itself is my router and it has an extensive firewall script  protecting against many attacks, but apparently port 2828 was still  open. I also realize that my SSH server could have been be the entry  port for this issue. Will have to review my security policy.
Do you have any idea on how to clean this stuff or should I just re-install Linux?

---

### Post by wildmanne39 on 2015-04-10
I would wipe the hard drive completely then install ubuntu again.
The only way a virus can hurt your system is if you run ubuntu as root and you mentioned the virus has root privileges, so were you running ubuntu as root?
Please see how to use code tags in my signature.
Thanks

---

### Post by Holger_Gehrke on 2015-04-10
He probably wasn't running as root. If it's the XOR.DDoS trojan - which is described on a link in the page I linked to - than this P.O.S. brings a root kit along. It was first described in September of last year by MalwareMustDie.org and has been updated a few times since then.

---

### Post by dragonfly41 on 2015-04-10
Here is a useful link I use for checking vulnerability

[https://www.grc.com/shieldsup](https://www.grc.com/shieldsup)

also I installed Zenmap from Ubuntu Software Centre

---

