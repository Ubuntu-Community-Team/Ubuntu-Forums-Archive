---
title: "Sysctl Tuning"
date: 2008-07-08
forum: General Help
---

### Post by AndEat on 2008-07-08
Here is a some sysctl tuning parameters I've pulled in over time and links to where I got the hints. These seem to work well for me, my computer, and my connection but I haven't advanced enough yet to be able to test and provide hard data on utility.

I'd like to know what works for you in tweaking your systems and maybe pick up some pointers for more tweaks or what tweaks aren't worth the effort:

kernel.maps_protect = 1
kernel.printk = 4 4 1 7
kernel.shmall = 8388608
kernel.shmmax = 134217728
kernel.shmmni = 4096
net.core.netdev_max_backlog=2500
net.core.rmem_max = 16777216
net.core.somaxconn=1024
net.core.wmem_max = 16777216
net.ipv4.conf.all.accept_redirects=0
net.ipv4.conf.all.accept_redirects=0
net.ipv4.conf.all.accept_source_route=0
net.ipv4.conf.all.accept_source_route=0
net.ipv4.conf.all.log_martians=1
net.ipv4.conf.all.rp_filter=1
net.ipv4.conf.all.send_redirects=0
net.ipv4.conf.default.accept_redirects=0
net.ipv4.conf.default.accept_source_route=0
net.ipv4.conf.default.rp_filter=1
net.ipv4.conf.default.send_redirects=0
net.ipv4.icmp_echo_ignore_all=1
net.ipv4.icmp_echo_ignore_broadcasts=1
net.ipv4.icmp_ignore_bogus_error_responses=1
net.ipv4.icmp_ratelimit=10
#net.ipv4.ip_default_ttl=62  #[http://gentoo-wiki.com/HOWTO_TCP_Tuning](http://gentoo-wiki.com/HOWTO_TCP_Tuning)  how to get a random number between 60 and 100 here?
net.ipv4.ip_no_pmtu_disc=0
net.ipv4.route.flush=1
#net.ipv4.tcp_congestion_control= (only reno is compiled into default kernel it seems)
net.ipv4.tcp_fack=1
net.ipv4.tcp_fin_timeout=30
net.ipv4.tcp_keepalive_time=900
net.ipv4.tcp_max_orphans=16384
net.ipv4.tcp_max_syn_backlog=4096
net.ipv4.tcp_no_metrics_save=1
net.ipv4.tcp_rfc1337=1
net.ipv4.tcp_rmem = 4096 873800 8738000
net.ipv4.tcp_sack=1 
net.ipv4.tcp_synack_retries=3
net.ipv4.tcp_syncookies=1
net.ipv4.tcp_syncookies=1
net.ipv4.tcp_syn_retries=3
net.ipv4.tcp_timestamps=0 
net.ipv4.tcp_tw_recycle=1
net.ipv4.tcp_tw_reuse=1
net.ipv4.tcp_window_scaling=1
net.ipv4.tcp_wmem = 4096 655360 8738000
net.netfilter.nf_conntrack_tcp_loose=0
vm.dirty_background_ratio=5
vm.dirty_expire_centisecs=500
vm.dirty_ratio=10
vm.dirty_writeback_centisecs=250
vm.min_free_kbytes=102400
vm.swappiness=0


resources:
#[http://www.shell-tips.com/2006/11/25/fine-tuning-a-linux-apache-mysql-php-lamp-server/](http://www.shell-tips.com/2006/11/25/fine-tuning-a-linux-apache-mysql-php-lamp-server/)
#[http://dsd.lbl.gov/TCP-tuning/linux.html](http://dsd.lbl.gov/TCP-tuning/linux.html)
#[http://gentoo-wiki.com/HOWTO_TCP_Tuning](http://gentoo-wiki.com/HOWTO_TCP_Tuning)
#[http://www.speedguide.net/read_articles.php?id=121](http://www.speedguide.net/read_articles.php?id=121)
#[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables)
#[http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed)
#[http://ipsysctl-tutorial.frozentux.net/chunkyhtml/tcpvariables.html](http://ipsysctl-tutorial.frozentux.net/chunkyhtml/tcpvariables.html)
#[http://danieldegraaf.afraid.org/info/iptables/sysctl](http://danieldegraaf.afraid.org/info/iptables/sysctl)
#[http://www.gridpp.ac.uk/wiki/RAL_Tier1_Disk_Server_Tuning](http://www.gridpp.ac.uk/wiki/RAL_Tier1_Disk_Server_Tuning)
#[http://www.aerasec.de/security/systems/linux.html?lang=en](http://www.aerasec.de/security/systems/linux.html?lang=en)

---

