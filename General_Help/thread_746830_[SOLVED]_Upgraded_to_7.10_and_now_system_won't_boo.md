---
title: "[SOLVED] Upgraded to 7.10 and now system won't boot up"
date: 2008-04-05
forum: General Help
---

### Post by Reshuken on 2008-04-05
Hey guys. Today I upgraded from 7.04 to 7.10 (I know, a bit late, but I was preparing for 8.04) and everything went smooth until the system asked to reboot. I rebooted the system and it seemed to be fine Grub came up I selected the normal option and the system started to boot, but after a while I'm presented with a black screen and nothing comes up. 

I've tried booting up with the other options in Grub (the other kernels and the recovery modes), but it's the same. I'm guessing that something went bad with my video drivers, but honestly it's just an assumption and I don't know what I can do. I would gladly use some help here so I can boot up again into Ubuntu. Thanks in advance.

---

### Post by ajmorris on 2008-04-05
> **Reshuken said:**
> Hey guys. Today I upgraded from 7.04 to 7.10 (I know, a bit late, but I was preparing for 8.04) and everything went smooth until the system asked to reboot. I rebooted the system and it seemed to be fine Grub came up I selected the normal option and the system started to boot, but after a while I'm presented with a black screen and nothing comes up. 

I've tried booting up with the other options in Grub (the other kernels and the recovery modes), but it's the same. I'm guessing that something went bad with my video drivers, but honestly it's just an assumption and I don't know what I can do. I would gladly use some help here so I can boot up again into Ubuntu. Thanks in advance.

Can you please boot into a live-cd, and mount your ubuntu partition, then post your /var/log/syslog. Also, you could try re-installing grub to the MBR, this post will tell you how: [http://ubuntuforums.org/showpost.php?p=4542943&postcount=2](http://ubuntuforums.org/showpost.php?p=4542943&postcount=2)

Also, does it display the black screen straight after selecting the kernel, or does the system boot up a little bit?


AJ

---

### Post by Reshuken on 2008-04-06
Ok, so now I am on a live session. Actually, after I make the selection in Grub, the splash screen shows up and starts to boot, after which I get the black screen and nothing else, Last time I tried to start my system I waited for around 15 min and nothing. 

And here is my syslog:

```

Apr  5 07:36:46 MTOLEDOB syslogd 1.4.1#20ubuntu4: restart.
Apr  5 07:36:46 MTOLEDOB anacron[20513]: Job `cron.daily' terminated (exit status: 1) (mailing output)
Apr  5 07:36:47 MTOLEDOB anacron[20513]: Normal exit (1 job run)
Apr  5 07:36:52 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr  5 07:37:02 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 07:37:02 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 07:43:52 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Apr  5 07:43:57 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 07:44:05 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Apr  5 07:44:19 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Apr  5 07:44:23 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 07:44:23 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 07:47:26 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): nt: cmd=0x8b06 len=8 
Apr  5 07:47:26 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 07:47:26 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 07:47:26 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 07:47:26 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 07:47:26 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 07:47:26 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 07:47:26 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 07:47:26 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 07:47:26 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 07:47:26 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 07:47:26 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 07:47:26 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 07:47:26 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 07:47:26 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 07:47:26 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 07:47:26 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 07:47:26 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 07:47:26 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 07:47:26 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 07:48:52 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 07:49:00 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Apr  5 07:49:12 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr  5 07:49:22 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
Apr  5 07:49:23 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 07:49:23 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 07:55:09 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr  5 07:55:16 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Apr  5 07:55:31 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Apr  5 07:55:40 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 07:55:40 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 07:58:19 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr  5 07:58:22 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Apr  5 07:58:26 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Apr  5 07:58:35 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 07:58:43 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr  5 07:58:50 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 07:58:50 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 08:04:54 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr  5 08:05:01 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Apr  5 08:05:14 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr  5 08:05:25 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 08:05:25 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 08:07:28 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): cmd=0x8b06 len=8 
Apr  5 08:07:28 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 08:07:28 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 08:07:28 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 08:07:28 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 08:07:28 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 08:07:28 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 08:07:28 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 08:07:28 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 08:07:28 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 08:07:28 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 08:07:28 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 08:07:28 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 08:07:28 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 08:07:28 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 08:07:28 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 08:07:28 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 08:07:28 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 08:07:28 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 08:07:28 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 08:09:30 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Apr  5 08:09:35 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Apr  5 08:09:48 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Apr  5 08:10:01 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 08:10:01 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 08:14:20 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Apr  5 08:14:25 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr  5 08:14:36 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Apr  5 08:14:50 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
Apr  5 08:14:51 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 08:14:51 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 08:17:01 MTOLEDOB /USR/SBIN/CRON[3785]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  5 08:20:48 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr  5 08:20:54 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 08:21:02 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr  5 08:21:12 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr  5 08:21:19 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 08:21:19 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 08:24:22 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Apr  5 08:24:27 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr  5 08:24:33 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr  5 08:24:43 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr  5 08:24:53 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 08:24:53 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 08:27:31 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): 0x8b06 len=8 
Apr  5 08:27:31 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 08:27:31 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 08:27:31 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 08:27:31 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 08:27:31 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 08:27:31 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 08:27:31 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 08:27:31 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 08:27:31 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 08:27:31 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 08:27:31 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 08:27:31 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 08:27:31 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 08:27:31 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 08:27:31 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 08:27:31 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 08:27:31 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 08:27:31 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 08:27:31 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 08:28:02 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr  5 08:28:16 MTOLEDOB last message repeated 2 times
Apr  5 08:28:23 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr  5 08:28:33 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 08:28:33 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 08:35:37 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 08:35:45 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr  5 08:35:56 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Apr  5 08:36:08 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 08:36:08 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 08:43:30 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr  5 08:43:36 MTOLEDOB last message repeated 2 times
Apr  5 08:43:39 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Apr  5 08:43:43 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Apr  5 08:43:47 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr  5 08:43:53 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 08:44:01 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 08:44:01 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 08:47:34 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): 06 len=8 
Apr  5 08:47:34 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 08:47:34 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 08:47:34 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 08:47:34 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 08:47:34 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 08:47:34 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 08:47:34 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 08:47:34 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 08:47:34 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 08:47:34 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 08:47:34 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 08:47:34 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 08:47:34 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 08:47:34 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 08:47:34 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 08:47:34 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 08:47:34 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 08:47:34 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 08:47:34 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 08:49:17 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr  5 08:49:24 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Apr  5 08:49:38 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr  5 08:49:48 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 08:49:48 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 08:54:39 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 08:54:47 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
Apr  5 08:55:08 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
Apr  5 08:55:10 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 08:55:10 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 08:58:15 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr  5 08:58:21 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Apr  5 08:58:34 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Apr  5 08:58:46 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 08:58:46 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 09:02:03 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 09:02:11 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Apr  5 09:02:23 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr  5 09:02:33 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
Apr  5 09:02:34 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 09:02:34 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 09:07:37 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): en=8 
Apr  5 09:07:37 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 09:07:37 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 09:07:37 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 09:07:37 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 09:07:37 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 09:07:37 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 09:07:37 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 09:07:37 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 09:07:37 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 09:07:37 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 09:07:37 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 09:07:37 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 09:07:37 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 09:07:37 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 09:07:37 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 09:07:37 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 09:07:37 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 09:07:37 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 09:07:37 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 09:08:26 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr  5 09:08:33 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr  5 09:08:43 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr  5 09:08:53 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Apr  5 09:08:57 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 09:08:57 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 09:12:08 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 09:12:16 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Apr  5 09:12:30 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Apr  5 09:12:39 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 09:12:39 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 09:17:01 MTOLEDOB /USR/SBIN/CRON[5543]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  5 09:19:16 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Apr  5 09:19:21 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr  5 09:19:32 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Apr  5 09:19:44 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr  5 09:19:47 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 09:19:47 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 09:27:10 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr  5 09:27:17 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Apr  5 09:27:33 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 09:27:41 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 09:27:41 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 09:29:40 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429):  
Apr  5 09:29:40 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 09:29:40 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 09:29:40 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 09:29:40 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 09:29:40 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 09:29:40 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 09:29:40 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 09:29:40 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 09:29:40 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 09:29:40 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 09:29:40 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 09:29:40 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 09:29:40 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 09:29:40 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 09:29:40 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 09:29:40 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 09:29:40 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 09:29:40 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 09:29:40 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 09:29:40 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 09:34:29 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr  5 09:34:36 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr  5 09:34:47 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Apr  5 09:35:00 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 09:35:00 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 09:38:24 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr  5 09:38:30 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Apr  5 09:38:42 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Apr  5 09:38:54 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
Apr  5 09:38:55 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 09:38:55 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 09:42:16 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr  5 09:42:19 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Apr  5 09:42:23 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 09:42:31 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Apr  5 09:42:44 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr  5 09:42:47 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 09:42:47 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 09:49:00 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Apr  5 09:49:04 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Apr  5 09:49:09 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr  5 09:49:20 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr  5 09:49:31 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 09:49:31 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 09:49:43 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): _NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 09:49:43 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 09:49:43 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 09:49:43 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 09:49:43 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 09:49:43 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 09:49:43 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 09:49:43 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 09:49:43 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 09:49:43 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 09:49:43 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 09:49:43 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 09:49:43 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 09:49:43 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 09:49:43 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 09:49:43 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 09:49:43 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 09:49:43 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 09:49:43 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 09:49:43 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 09:56:28 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Apr  5 09:56:32 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr  5 09:56:38 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
Apr  5 09:56:56 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr  5 09:56:59 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 09:56:59 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 10:04:05 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Apr  5 10:04:09 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr  5 10:04:15 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Apr  5 10:04:24 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Apr  5 10:04:36 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 10:04:36 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 10:09:01 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Apr  5 10:09:05 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr  5 10:09:15 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 10:09:23 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Apr  5 10:09:32 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 10:09:32 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 10:09:46 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): LINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 10:09:46 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 10:09:46 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 10:09:46 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 10:09:46 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 10:09:46 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 10:09:46 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 10:09:46 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 10:09:46 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 10:09:46 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 10:09:46 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 10:09:46 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 10:09:46 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 10:09:46 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 10:09:46 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 10:09:46 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 10:09:46 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 10:09:46 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 10:09:46 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 10:09:46 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 10:12:50 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr  5 10:12:56 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Apr  5 10:13:09 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Apr  5 10:13:21 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 10:13:21 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 10:17:01 MTOLEDOB /USR/SBIN/CRON[7074]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  5 10:18:41 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Apr  5 10:18:45 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Apr  5 10:18:54 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Apr  5 10:19:06 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr  5 10:19:12 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 10:19:12 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 10:25:35 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr  5 10:25:38 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 10:25:46 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
Apr  5 10:26:06 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 10:26:06 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 10:29:49 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): K: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 10:29:49 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 10:29:49 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 10:29:49 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 10:29:49 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 10:29:49 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 10:29:49 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 10:29:49 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 10:29:49 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 10:29:49 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 10:29:49 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 10:29:49 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 10:29:49 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 10:29:49 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 10:29:49 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 10:29:49 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 10:29:49 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 10:29:49 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 10:29:49 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 10:29:49 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 10:30:39 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr  5 10:30:46 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr  5 10:30:56 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Apr  5 10:31:10 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 10:31:10 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 10:34:19 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr  5 10:34:26 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr  5 10:34:36 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Apr  5 10:34:49 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
Apr  5 10:34:50 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 10:34:50 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 10:41:34 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 10:41:42 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr  5 10:41:52 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Apr  5 10:42:05 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 10:42:05 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 10:45:20 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Apr  5 10:45:24 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Apr  5 10:45:33 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr  5 10:45:40 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr  5 10:45:51 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 10:45:51 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 10:49:52 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): erstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 10:49:52 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 10:49:52 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 10:49:52 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 10:49:52 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 10:49:52 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 10:49:52 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 10:49:52 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 10:49:52 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 10:49:52 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 10:49:52 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 10:49:52 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 10:49:52 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 10:49:52 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 10:49:52 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 10:49:52 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 10:49:52 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 10:49:52 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 10:49:52 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 10:49:52 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 10:49:54 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Apr  5 10:49:59 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr  5 10:50:10 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 10:50:18 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr  5 10:50:25 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 10:50:25 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 10:57:21 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 10:57:29 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr  5 10:57:40 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr  5 10:57:51 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
Apr  5 10:57:52 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 10:57:52 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 11:01:35 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 11:01:43 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Apr  5 11:01:52 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Apr  5 11:02:06 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 11:02:06 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 11:08:02 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr  5 11:08:05 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Apr  5 11:08:09 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr  5 11:08:20 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Apr  5 11:08:33 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 11:08:33 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 11:09:55 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): ate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 11:09:55 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 11:09:55 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 11:09:55 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 11:09:55 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 11:09:55 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 11:09:55 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 11:09:55 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 11:09:55 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 11:09:55 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 11:09:55 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 11:09:55 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 11:09:55 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 11:09:55 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 11:09:55 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 11:09:55 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 11:09:55 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 11:09:55 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 11:09:55 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 11:09:55 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 11:12:23 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Apr  5 11:12:27 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr  5 11:12:34 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
Apr  5 11:12:52 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
Apr  5 11:12:54 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 11:12:54 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 11:15:33 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Apr  5 11:15:38 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr  5 11:15:48 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Apr  5 11:16:04 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 11:16:04 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 11:17:01 MTOLEDOB /USR/SBIN/CRON[8593]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  5 11:18:37 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr  5 11:18:40 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 11:18:48 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr  5 11:18:59 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Apr  5 11:19:08 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 11:19:08 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 11:21:42 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr  5 11:21:48 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Apr  5 11:22:04 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Apr  5 11:22:13 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 11:22:13 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 11:28:45 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 11:28:53 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr  5 11:29:04 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Apr  5 11:29:16 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 11:29:16 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 11:29:58 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): 1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 11:29:58 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 11:29:58 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 11:29:58 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 11:29:58 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 11:29:58 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 11:29:58 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 11:29:58 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 11:29:58 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 11:29:58 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 11:29:58 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 11:29:58 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 11:29:58 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 11:29:58 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 11:29:58 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 11:29:58 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 11:29:58 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 11:29:58 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 11:29:58 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 11:29:58 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 11:34:26 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr  5 11:34:33 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Apr  5 11:34:45 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Apr  5 11:34:57 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 11:34:57 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 11:40:58 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr  5 11:41:01 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr  5 11:41:08 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
Apr  5 11:41:26 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr  5 11:41:29 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 11:41:29 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 11:44:03 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr  5 11:44:09 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Apr  5 11:44:22 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr  5 11:44:32 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
Apr  5 11:44:34 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 11:44:34 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 11:50:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): i_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 11:50:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 11:50:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 11:50:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 11:50:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 11:50:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 11:50:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 11:50:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 11:50:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 11:50:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 11:50:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 11:50:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 11:50:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 11:50:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 11:50:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 11:50:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 11:50:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 11:50:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 11:50:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 11:50:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 11:50:26 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Apr  5 11:50:31 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr  5 11:50:41 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Apr  5 11:50:54 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr  5 11:50:57 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 11:50:57 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 11:54:33 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Apr  5 11:54:38 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr  5 11:54:45 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr  5 11:54:52 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Apr  5 11:55:04 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 11:55:04 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 12:00:33 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 12:00:41 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Apr  5 12:00:56 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 12:01:04 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 12:01:04 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 12:04:15 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr  5 12:04:21 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr  5 12:04:28 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Apr  5 12:04:42 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Apr  5 12:04:46 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 12:04:46 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 12:07:58 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr  5 12:08:04 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr  5 12:08:14 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Apr  5 12:08:28 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
Apr  5 12:08:29 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 12:08:29 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 12:10:03 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): ags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 12:10:03 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 12:10:03 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 12:10:03 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 12:10:03 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 12:10:03 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 12:10:03 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 12:10:03 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 12:10:03 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 12:10:03 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 12:10:03 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 12:10:03 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 12:10:03 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 12:10:03 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 12:10:03 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 12:10:03 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 12:10:03 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 12:10:03 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 12:10:03 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 12:10:03 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 12:12:10 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Apr  5 12:12:15 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr  5 12:12:26 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr  5 12:12:33 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 12:12:41 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 12:12:41 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 12:17:01 MTOLEDOB /USR/SBIN/CRON[10107]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  5 12:18:54 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr  5 12:18:57 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr  5 12:19:04 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Apr  5 12:19:19 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr  5 12:19:25 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 12:19:25 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 12:25:24 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 12:25:32 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 12:25:40 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Apr  5 12:25:55 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 12:25:55 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 12:30:06 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): 0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 12:30:06 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 12:30:06 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 12:30:06 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 12:30:06 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 12:30:06 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 12:30:06 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 12:30:06 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 12:30:06 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 12:30:06 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 12:30:06 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 12:30:06 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 12:30:06 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 12:30:06 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 12:30:06 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 12:30:06 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 12:30:06 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 12:30:06 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 12:30:06 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 12:30:06 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 12:30:46 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 12:30:54 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr  5 12:31:05 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Apr  5 12:31:17 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 12:31:17 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 12:36:46 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr  5 12:36:53 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Apr  5 12:37:02 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Apr  5 12:37:17 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 12:37:17 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 12:40:16 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Apr  5 12:40:21 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Apr  5 12:40:34 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Apr  5 12:40:46 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
Apr  5 12:40:47 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 12:40:47 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 12:47:59 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 12:48:07 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Apr  5 12:48:16 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr  5 12:48:27 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr  5 12:48:30 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 12:48:30 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 12:50:09 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): 043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 12:50:09 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 12:50:09 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 12:50:09 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 12:50:09 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 12:50:09 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 12:50:09 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 12:50:09 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 12:50:09 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 12:50:09 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 12:50:09 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 12:50:09 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 12:50:09 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 12:50:09 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 12:50:09 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 12:50:09 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 12:50:09 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 12:50:09 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 12:50:09 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 12:50:09 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 12:52:27 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 12:52:35 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 12:52:43 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Apr  5 12:52:56 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
Apr  5 12:52:58 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 12:52:58 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 12:59:50 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Apr  5 12:59:54 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 13:00:02 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Apr  5 13:00:15 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr  5 13:00:21 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 13:00:21 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 13:06:40 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Apr  5 13:06:45 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Apr  5 13:06:50 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 13:06:58 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr  5 13:07:09 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
Apr  5 13:07:11 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 13:07:11 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 13:10:12 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): ([UP][RUNNING][LOWER_UP]) 
Apr  5 13:10:12 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 13:10:12 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 13:10:12 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 13:10:12 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 13:10:12 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 13:10:12 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 13:10:12 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 13:10:12 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 13:10:12 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 13:10:12 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 13:10:12 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 13:10:12 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 13:10:12 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 13:10:12 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 13:10:12 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 13:10:12 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 13:10:12 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 13:10:12 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 13:10:12 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 13:13:54 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 13:14:02 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Apr  5 13:14:15 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr  5 13:14:25 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 13:14:25 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 13:17:02 MTOLEDOB /USR/SBIN/CRON[11694]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  5 13:17:41 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Apr  5 13:17:46 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr  5 13:17:56 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Apr  5 13:18:12 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 13:18:12 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 13:24:42 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr  5 13:24:48 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 13:24:56 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
Apr  5 13:25:13 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 13:25:13 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 13:30:15 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): ][RUNNING][LOWER_UP]) 
Apr  5 13:30:15 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 13:30:15 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 13:30:15 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 13:30:15 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 13:30:15 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 13:30:15 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 13:30:15 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 13:30:15 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 13:30:15 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 13:30:15 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 13:30:15 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 13:30:15 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 13:30:15 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 13:30:15 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 13:30:15 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 13:30:15 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 13:30:15 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 13:30:15 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 13:30:15 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 13:32:18 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr  5 13:32:25 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Apr  5 13:32:39 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr  5 13:32:49 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 13:32:49 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 13:35:49 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr  5 13:35:55 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Apr  5 13:36:10 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr  5 13:36:20 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 13:36:20 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 13:43:04 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Apr  5 13:43:08 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 13:43:16 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Apr  5 13:43:29 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr  5 13:43:35 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 13:43:35 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 13:49:22 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr  5 13:49:29 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Apr  5 13:49:44 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Apr  5 13:49:53 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 13:49:53 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 13:50:18 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): NNING][LOWER_UP]) 
Apr  5 13:50:18 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 13:50:18 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 13:50:18 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 13:50:18 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 13:50:18 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 13:50:18 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 13:50:18 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 13:50:18 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 13:50:18 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 13:50:18 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 13:50:18 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 13:50:18 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 13:50:18 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 13:50:18 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 13:50:18 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 13:50:18 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 13:50:18 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 13:50:18 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 13:50:18 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 13:54:07 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr  5 13:54:14 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr  5 13:54:25 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr  5 13:54:35 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr  5 13:54:38 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 13:54:38 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 13:58:02 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr  5 13:58:05 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr  5 13:58:08 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr  5 13:58:15 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 13:58:23 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr  5 13:58:33 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 13:58:33 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 14:01:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): G][LOWER_UP]) 
Apr  5 14:01:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 14:01:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 14:01:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 14:01:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 14:01:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 14:01:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 14:01:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 14:01:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 14:01:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 14:01:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 14:01:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b06 len=8 
Apr  5 14:01:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x1003 ([UP]) 
Apr  5 14:01:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b15 len=20 
Apr  5 14:01:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: new AP: 00:00:00:00:00:00 
Apr  5 14:01:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Setting scan request: 0 sec 100000 usec 
Apr  5 14:01:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Added BSSID 00:16:b6:08:7f:fa into blacklist 
Apr  5 14:01:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys 
Apr  5 14:01:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 36 32 31 2d 32 00 
Apr  5 14:01:00 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): State: COMPLETED -> DISCONNECTED 
Apr  5 14:01:01 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): _driver_wext_set_operstate: operstate 1->0 (DORMANT) 
Apr  5 14:01:01 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): WEXT: Operstate: linkmode=-1, operstate=5 
Apr  5 14:01:01 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): EAPOL: External notification - portEnabled=0 
Apr  5 14:01:01 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): EAPOL: SUPP_PAE entering state DISCONNECTED 
Apr  5 14:01:01 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): EAPOL: SUPP_BE entering state INITIALIZE 
Apr  5 14:01:01 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): EAPOL: External notification - portValid=0 
Apr  5 14:01:01 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP]) 
Apr  5 14:01:01 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added 
Apr  5 14:01:01 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): State: DISCONNECTED -> SCANNING 
Apr  5 14:01:01 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Starting AP scan (broadcast SSID) 
Apr  5 14:01:01 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP]) 
Apr  5 14:01:01 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: cmd=0x8b15 len=20 
Apr  5 14:01:01 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Wireless event: new AP: 00:16:b6:08:7f:fa 
Apr  5 14:01:01 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): State: SCANNING -> ASSOCIATED 
Apr  5 14:01:01 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT) 
Apr  5 14:01:01 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): WEXT: Operstate: linkmode=-1, operstate=5 
Apr  5 14:01:01 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Associated to a new BSS: BSSID=00:16:b6:08:7f:fa 
Apr  5 14:01:01 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Associated with 00:16:b6:08:7f:fa 
Apr  5 14:01:01 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 36 32 31 2d 32 00 
Apr  5 14:01:01 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): WPA: Association event - clear replay counter 
Apr  5 14:01:04 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Enabled=0 
Apr  5 14:01:04 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): EAPOL: External notification - portValid=0 
Apr  5 14:01:04 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): EAPOL: External notification - portEnabled=1 
Apr  5 14:01:04 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): EAPOL: SUPP_PAE entering state S_FORCE_AUTH 
Apr  5 14:01:04 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): EAPOL: SUPP_BE entering state IDLE 
Apr  5 14:01:04 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Cancelling authentication timeout 
Apr  5 14:01:04 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Removed BSSID 00:16:b6:08:7f:fa from blacklist 
Apr  5 14:01:04 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): State: ASSOCIATED -> COMPLETED 
Apr  5 14:01:04 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): CTRL-EVENT-CONNECTED - Connection to 00:16:b6:08:7f:fa completed (reauth) [id=0 id_str=] 
Apr  5 14:01:04 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 36 32 31 2d 32 00 
Apr  5 14:01:04 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): wpa_driver_wext_set_operstate: operstate 0->1 (UP) 
Apr  5 14:01:04 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): WEXT: Operstate: linkmode=-1, operstate=6 
Apr  5 14:01:04 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Cancelling scan request 
Apr  5 14:01:04 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11003 ([UP][LOWER_UP]) 
Apr  5 14:01:04 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): WEXT: Operstate: linkmode=-1, operstate=6 
Apr  5 14:01:04 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added 
Apr  5 14:01:04 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr  5 14:01:04 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added 
Apr  5 14:01:04 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Scan timeout - try to get results 
Apr  5 14:01:04 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Received 224 bytes of scan results (1 BSSes) 
Apr  5 14:01:04 MTOLEDOB NetworkManager: <information>^Iwpa_supplicant(5429): Scan results: 1 
Apr  5 14:01:52 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr  5 14:01:59 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
Apr  5 14:02:20 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr  5 14:02:23 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 14:02:23 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 15:49:23 MTOLEDOB syslogd 1.4.1#20ubuntu4: restart.
Apr  5 15:49:23 MTOLEDOB kernel: Inspecting /boot/System.map-2.6.20-16-generic
Apr  5 15:49:23 MTOLEDOB kernel: Loaded 24980 symbols from /boot/System.map-2.6.20-16-generic.
Apr  5 15:49:23 MTOLEDOB kernel: Symbols match kernel version 2.6.20.
Apr  5 15:49:23 MTOLEDOB kernel: No module symbols loaded - kernel modules not enabled. 
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Tue Feb 12 05:41:34 UTC 2008 (Ubuntu 2.6.20-16.35-generic)
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000] BIOS-provided physical RAM map:
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000] sanitize start
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000] sanitize end
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f000 end: 000000000009f000 type: 1
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000] copy_e820_map() start: 000000000009f000 size: 0000000000001000 end: 00000000000a0000 type: 2
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001feae000 end: 000000001ffae000 type: 1
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000] copy_e820_map() start: 000000001ffae000 size: 0000000000052000 end: 0000000020000000 type: 2
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000] copy_e820_map() start: 00000000feda0000 size: 0000000000060000 end: 00000000fee00000 type: 2
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000] copy_e820_map() start: 00000000ffb00000 size: 0000000000500000 end: 0000000100000000 type: 2
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffae000 (usable)
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 000000001ffae000 - 0000000020000000 (reserved)
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fee00000 (reserved)
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000] 0MB HIGHMEM available.
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000] 511MB LOWMEM available.
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000] Entering add_active_range(0, 0, 130990) 0 entries of 256 used
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000] Zone PFN ranges:
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000]   DMA             0 ->     4096
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000]   Normal       4096 ->   130990
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000]   HighMem    130990 ->   130990
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000]     0:        0 ->   130990
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000] On node 0 totalpages: 130990
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000]   Normal zone: 991 pages used for memmap
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000]   Normal zone: 125903 pages, LIFO batch:31
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000] DMI 2.3 present.
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fdf00
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000] ACPI: RSDT (v001 DELL    CPi R   0x27d5011a ASL  0x00000061) @ 0x1fff0000
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000] ACPI: FADT (v001 DELL    CPi R   0x27d5011a ASL  0x00000061) @ 0x1fff0400
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000] ACPI: ASF! (v016 DELL    CPi R   0x27d5011a ASL  0x00000061) @ 0x1fff0800
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000] ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 MSFT 0x0100000e) @ 0x00000000
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:deda0000)
Apr  5 15:49:23 MTOLEDOB kernel: [    0.000000] Detected 1398.885 MHz processor.
Apr  5 15:49:23 MTOLEDOB kernel: [    8.046333] Built 1 zonelists.  Total pages: 129967
Apr  5 15:49:23 MTOLEDOB kernel: [    8.046338] Kernel command line: root=UUID=241da2db-0e86-4d13-ba31-7e747e81c264 ro quiet splash
Apr  5 15:49:23 MTOLEDOB kernel: [    8.046553] Local APIC disabled by BIOS -- you can enable it with "lapic"
Apr  5 15:49:23 MTOLEDOB kernel: [    8.046564] mapped APIC to ffffd000 (0140b000)
Apr  5 15:49:23 MTOLEDOB kernel: [    8.046567] Enabling fast FPU save and restore... done.
Apr  5 15:49:23 MTOLEDOB kernel: [    8.046571] Enabling unmasked SIMD FPU exception support... done.
Apr  5 15:49:23 MTOLEDOB kernel: [    8.046583] Initializing CPU#0
Apr  5 15:49:23 MTOLEDOB kernel: [    8.046654] PID hash table entries: 2048 (order: 11, 8192 bytes)
Apr  5 15:49:23 MTOLEDOB kernel: [    8.047732] Console: colour VGA+ 80x25
Apr  5 15:49:23 MTOLEDOB kernel: [    8.048034] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr  5 15:49:23 MTOLEDOB kernel: [    8.048349] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr  5 15:49:23 MTOLEDOB kernel: [    8.066051] Memory: 507192k/523960k available (1993k kernel code, 16240k reserved, 900k data, 328k init, 0k highmem)
Apr  5 15:49:23 MTOLEDOB kernel: [    8.066065] virtual kernel memory layout:
Apr  5 15:49:23 MTOLEDOB kernel: [    8.066067]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
Apr  5 15:49:23 MTOLEDOB kernel: [    8.066068]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr  5 15:49:23 MTOLEDOB kernel: [    8.066070]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
Apr  5 15:49:23 MTOLEDOB kernel: [    8.066071]     lowmem  : 0xc0000000 - 0xdffae000   ( 511 MB)
Apr  5 15:49:23 MTOLEDOB kernel: [    8.066073]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
Apr  5 15:49:23 MTOLEDOB kernel: [    8.066075]       .data : 0xc02f24c9 - 0xc03d36d4   ( 900 kB)
Apr  5 15:49:23 MTOLEDOB kernel: [    8.066076]       .text : 0xc0100000 - 0xc02f24c9   (1993 kB)
Apr  5 15:49:23 MTOLEDOB kernel: [    8.066081] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr  5 15:49:23 MTOLEDOB kernel: [    8.142658] Calibrating delay using timer specific routine.. 2799.67 BogoMIPS (lpj=5599354)
Apr  5 15:49:23 MTOLEDOB kernel: [    8.142713] Security Framework v1.0.0 initialized
Apr  5 15:49:23 MTOLEDOB kernel: [    8.142721] SELinux:  Disabled at boot.
Apr  5 15:49:23 MTOLEDOB kernel: [    8.142743] Mount-cache hash table entries: 512
Apr  5 15:49:23 MTOLEDOB kernel: [    8.142911] CPU: After generic identify, caps: a7e9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
Apr  5 15:49:23 MTOLEDOB kernel: [    8.142926] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr  5 15:49:23 MTOLEDOB kernel: [    8.142930] CPU: L2 cache: 1024K
Apr  5 15:49:23 MTOLEDOB kernel: [    8.142933] CPU: After all inits, caps: a7e9f9bf 00000000 00000000 00002040 00000180 00000000 00000000
Apr  5 15:49:23 MTOLEDOB kernel: [    8.142945] Compat vDSO mapped to ffffe000.
Apr  5 15:49:23 MTOLEDOB kernel: [    8.142950] Remapping vsyscall page to ffffe000
Apr  5 15:49:23 MTOLEDOB kernel: [    8.142963] Checking 'hlt' instruction... OK.
Apr  5 15:49:23 MTOLEDOB kernel: [    8.158758] SMP alternatives: switching to UP code
Apr  5 15:49:23 MTOLEDOB kernel: [    8.158939] Freeing SMP alternatives: 11k freed
Apr  5 15:49:23 MTOLEDOB kernel: [    8.159146] Early unpacking initramfs... done
Apr  5 15:49:23 MTOLEDOB kernel: [    8.582550] ACPI: Core revision 20060707
Apr  5 15:49:23 MTOLEDOB kernel: [    8.589373] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Apr  5 15:49:23 MTOLEDOB kernel: [    8.591049] ACPI: setting ELCR to 0200 (from 0800)
Apr  5 15:49:23 MTOLEDOB kernel: [    8.593399] CPU0: Intel(R) Pentium(R) M processor 1400MHz stepping 05
Apr  5 15:49:23 MTOLEDOB kernel: [    8.593406] SMP motherboard not detected.
Apr  5 15:49:23 MTOLEDOB kernel: [    8.593409] Local APIC not detected. Using dummy APIC emulation.
Apr  5 15:49:23 MTOLEDOB kernel: [    8.593447] Brought up 1 CPUs
Apr  5 15:49:23 MTOLEDOB kernel: [    8.593722] Booting paravirtualized kernel on bare hardware
Apr  5 15:49:23 MTOLEDOB kernel: [    8.593793] Time: 15:48:52  Date: 03/05/108
Apr  5 15:49:23 MTOLEDOB kernel: [    8.593827] NET: Registered protocol family 16
Apr  5 15:49:23 MTOLEDOB kernel: [    8.593925] EISA bus registered
Apr  5 15:49:23 MTOLEDOB kernel: [    8.593930] ACPI: bus type pci registered
Apr  5 15:49:23 MTOLEDOB kernel: [    8.627504] PCI: PCI BIOS revision 2.10 entry at 0xfc96e, last bus=2
Apr  5 15:49:23 MTOLEDOB kernel: [    8.627507] PCI: Using configuration type 1
Apr  5 15:49:23 MTOLEDOB kernel: [    8.627509] Setting up standard PCI resources
Apr  5 15:49:23 MTOLEDOB kernel: [    8.639620] ACPI: Interpreter enabled
Apr  5 15:49:23 MTOLEDOB kernel: [    8.639624] ACPI: Using PIC for interrupt routing
Apr  5 15:49:23 MTOLEDOB kernel: [    8.641229] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr  5 15:49:23 MTOLEDOB kernel: [    8.641241] PCI: Probing PCI hardware (bus 00)
Apr  5 15:49:23 MTOLEDOB kernel: [    8.641384] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
Apr  5 15:49:23 MTOLEDOB kernel: [    8.647578] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
Apr  5 15:49:23 MTOLEDOB kernel: [    8.647583] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
Apr  5 15:49:23 MTOLEDOB kernel: [    8.647792] Boot video device is 0000:01:00.0
Apr  5 15:49:23 MTOLEDOB kernel: [    8.648051] PCI: Transparent bridge - 0000:00:1e.0
Apr  5 15:49:23 MTOLEDOB kernel: [    8.648115] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
Apr  5 15:49:23 MTOLEDOB kernel: [    8.648118] Please report the result to linux-kernel to fix this permanently
Apr  5 15:49:23 MTOLEDOB kernel: [    8.648158] PCI: Bus #07 (-#0a) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
Apr  5 15:49:23 MTOLEDOB kernel: [    8.648162] Please report the result to linux-kernel to fix this permanently
Apr  5 15:49:23 MTOLEDOB kernel: [    8.648181] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr  5 15:49:23 MTOLEDOB kernel: [    8.682452] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
Apr  5 15:49:23 MTOLEDOB kernel: [    8.682754] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
Apr  5 15:49:23 MTOLEDOB kernel: [    8.683041] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
Apr  5 15:49:23 MTOLEDOB kernel: [    8.683328] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
Apr  5 15:49:23 MTOLEDOB kernel: [    8.683600] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Apr  5 15:49:23 MTOLEDOB kernel: [    8.683890] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Apr  5 15:49:23 MTOLEDOB kernel: [    8.685290] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Apr  5 15:49:23 MTOLEDOB kernel: [    8.686150] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Apr  5 15:49:23 MTOLEDOB kernel: [    8.687264] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr  5 15:49:23 MTOLEDOB kernel: [    8.687280] pnp: PnP ACPI init
Apr  5 15:49:23 MTOLEDOB kernel: [    8.720522] pnp: PnP ACPI: found 13 devices
Apr  5 15:49:23 MTOLEDOB kernel: [    8.720529] PnPBIOS: Disabled by ACPI PNP
Apr  5 15:49:23 MTOLEDOB kernel: [    8.720582] PCI: Using ACPI for IRQ routing
Apr  5 15:49:23 MTOLEDOB kernel: [    8.720586] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr  5 15:49:23 MTOLEDOB kernel: [    8.727011] NET: Registered protocol family 8
Apr  5 15:49:23 MTOLEDOB kernel: [    8.727014] NET: Registered protocol family 20
Apr  5 15:49:23 MTOLEDOB kernel: [    8.732911] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
Apr  5 15:49:23 MTOLEDOB kernel: [    8.732916] pnp: 00:02: ioport range 0x800-0x805 could not be reserved
Apr  5 15:49:23 MTOLEDOB kernel: [    8.732920] pnp: 00:02: ioport range 0x808-0x80f could not be reserved
Apr  5 15:49:23 MTOLEDOB kernel: [    8.732926] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
Apr  5 15:49:23 MTOLEDOB kernel: [    8.732930] pnp: 00:03: ioport range 0x806-0x807 has been reserved
Apr  5 15:49:23 MTOLEDOB kernel: [    8.732934] pnp: 00:03: ioport range 0x810-0x85f could not be reserved
Apr  5 15:49:23 MTOLEDOB kernel: [    8.732937] pnp: 00:03: ioport range 0x860-0x87f has been reserved
Apr  5 15:49:23 MTOLEDOB kernel: [    8.732941] pnp: 00:03: ioport range 0x880-0x8bf has been reserved
Apr  5 15:49:23 MTOLEDOB kernel: [    8.732945] pnp: 00:03: ioport range 0x8c0-0x8df has been reserved
Apr  5 15:49:23 MTOLEDOB kernel: [    8.732953] pnp: 00:08: ioport range 0x900-0x97f has been reserved
Apr  5 15:49:23 MTOLEDOB kernel: [    8.733265] PCI: Bridge: 0000:00:01.0
Apr  5 15:49:23 MTOLEDOB kernel: [    8.733268]   IO window: c000-cfff
Apr  5 15:49:23 MTOLEDOB kernel: [    8.733273]   MEM window: fc000000-fdffffff
Apr  5 15:49:23 MTOLEDOB kernel: [    8.733277]   PREFETCH window: e8000000-efffffff
Apr  5 15:49:23 MTOLEDOB kernel: [    8.733291] PCI: Bus 3, cardbus bridge: 0000:02:01.0
Apr  5 15:49:23 MTOLEDOB kernel: [    8.733294]   IO window: 0000d000-0000d0ff
Apr  5 15:49:23 MTOLEDOB kernel: [    8.733299]   IO window: 0000d400-0000d4ff
Apr  5 15:49:23 MTOLEDOB kernel: [    8.733304]   PREFETCH window: 30000000-33ffffff
Apr  5 15:49:23 MTOLEDOB kernel: [    8.733308]   MEM window: 3c000000-3fffffff
Apr  5 15:49:23 MTOLEDOB kernel: [    8.733313] PCI: Bus 7, cardbus bridge: 0000:02:01.1
Apr  5 15:49:23 MTOLEDOB kernel: [    8.733315]   IO window: 0000d800-0000d8ff
Apr  5 15:49:23 MTOLEDOB kernel: [    8.733320]   IO window: 0000dc00-0000dcff
Apr  5 15:49:23 MTOLEDOB kernel: [    8.733325]   PREFETCH window: 34000000-37ffffff
Apr  5 15:49:23 MTOLEDOB kernel: [    8.733329]   MEM window: 40000000-43ffffff
Apr  5 15:49:23 MTOLEDOB kernel: [    8.733334] PCI: Bridge: 0000:00:1e.0
Apr  5 15:49:23 MTOLEDOB kernel: [    8.733337]   IO window: d000-efff
Apr  5 15:49:23 MTOLEDOB kernel: [    8.733343]   MEM window: f6000000-fbffffff
Apr  5 15:49:23 MTOLEDOB kernel: [    8.733348]   PREFETCH window: 30000000-37ffffff
Apr  5 15:49:23 MTOLEDOB kernel: [    8.733365] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Apr  5 15:49:23 MTOLEDOB kernel: [    8.733379] PCI: Enabling device 0000:02:01.0 (0000 -> 0003)
Apr  5 15:49:23 MTOLEDOB kernel: [    8.733589] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Apr  5 15:49:23 MTOLEDOB kernel: [    8.733592] PCI: setting IRQ 11 as level-triggered
Apr  5 15:49:23 MTOLEDOB kernel: [    8.733597] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Apr  5 15:49:23 MTOLEDOB kernel: [    8.733614] PCI: Enabling device 0000:02:01.1 (0000 -> 0003)
Apr  5 15:49:23 MTOLEDOB kernel: [    8.733619] ACPI: PCI Interrupt 0000:02:01.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Apr  5 15:49:23 MTOLEDOB kernel: [    8.733657] NET: Registered protocol family 2
Apr  5 15:49:23 MTOLEDOB kernel: [    8.770729] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Apr  5 15:49:23 MTOLEDOB kernel: [    8.770829] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Apr  5 15:49:23 MTOLEDOB kernel: [    8.770969] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
Apr  5 15:49:23 MTOLEDOB kernel: [    8.771041] TCP: Hash tables configured (established 16384 bind 8192)
Apr  5 15:49:23 MTOLEDOB kernel: [    8.771045] TCP reno registered
Apr  5 15:49:23 MTOLEDOB kernel: [    8.782796] checking if image is initramfs... it is
Apr  5 15:49:23 MTOLEDOB kernel: [    9.621382] Freeing initrd memory: 8036k freed
Apr  5 15:49:23 MTOLEDOB kernel: [    9.621870] audit: initializing netlink socket (disabled)
Apr  5 15:49:23 MTOLEDOB kernel: [    9.621890] audit(1207410532.756:1): initialized
Apr  5 15:49:23 MTOLEDOB kernel: [    9.622059] VFS: Disk quotas dquot_6.5.1
Apr  5 15:49:23 MTOLEDOB kernel: [    9.622088] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr  5 15:49:23 MTOLEDOB kernel: [    9.622154] io scheduler noop registered
Apr  5 15:49:23 MTOLEDOB kernel: [    9.622157] io scheduler anticipatory registered
Apr  5 15:49:23 MTOLEDOB kernel: [    9.622160] io scheduler deadline registered
Apr  5 15:49:23 MTOLEDOB kernel: [    9.622176] io scheduler cfq registered (default)
Apr  5 15:49:23 MTOLEDOB kernel: [    9.622538] isapnp: Scanning for PnP cards...
Apr  5 15:49:23 MTOLEDOB kernel: [    9.975467] isapnp: No Plug & Play device found
Apr  5 15:49:23 MTOLEDOB kernel: [   10.012919] Real Time Clock Driver v1.12ac
Apr  5 15:49:23 MTOLEDOB kernel: [   10.012995] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr  5 15:49:23 MTOLEDOB kernel: [   10.013124] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr  5 15:49:23 MTOLEDOB kernel: [   10.014045] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr  5 15:49:23 MTOLEDOB kernel: [   10.014569] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
Apr  5 15:49:23 MTOLEDOB kernel: [   10.014573] PCI: setting IRQ 5 as level-triggered
Apr  5 15:49:23 MTOLEDOB kernel: [   10.014578] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Apr  5 15:49:23 MTOLEDOB kernel: [   10.014588] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
Apr  5 15:49:23 MTOLEDOB kernel: [   10.015783] mice: PS/2 mouse device common for all mice
Apr  5 15:49:23 MTOLEDOB kernel: [   10.016381] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr  5 15:49:23 MTOLEDOB kernel: [   10.016565] input: Macintosh mouse button emulation as /class/input/input0
Apr  5 15:49:23 MTOLEDOB kernel: [   10.016605] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Apr  5 15:49:23 MTOLEDOB kernel: [   10.016609] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Apr  5 15:49:23 MTOLEDOB kernel: [   10.016811] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Apr  5 15:49:23 MTOLEDOB kernel: [   10.021685] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr  5 15:49:23 MTOLEDOB kernel: [   10.021690] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr  5 15:49:23 MTOLEDOB kernel: [   10.021868] EISA: Probing bus 0 at eisa.0
Apr  5 15:49:23 MTOLEDOB kernel: [   10.021896] EISA: Detected 0 cards.
Apr  5 15:49:23 MTOLEDOB kernel: [   10.052010] TCP cubic registered
Apr  5 15:49:23 MTOLEDOB kernel: [   10.052023] NET: Registered protocol family 1
Apr  5 15:49:23 MTOLEDOB kernel: [   10.052048] Using IPI No-Shortcut mode
Apr  5 15:49:23 MTOLEDOB kernel: [   10.052119] ACPI: (supports S0 S1 S3 S4 S5)
Apr  5 15:49:23 MTOLEDOB kernel: [   10.052172]   Magic number: 4:739:840
Apr  5 15:49:23 MTOLEDOB kernel: [   10.052320]   hash matches device ptyu6
Apr  5 15:49:23 MTOLEDOB kernel: [   10.052634] Freeing unused kernel memory: 328k freed
Apr  5 15:49:23 MTOLEDOB kernel: [   10.054347] input: AT Translated Set 2 keyboard as /class/input/input1
Apr  5 15:49:23 MTOLEDOB kernel: [   10.054639] Time: tsc clocksource has been installed.
Apr  5 15:49:23 MTOLEDOB kernel: [   11.289939] Capability LSM initialized
Apr  5 15:49:23 MTOLEDOB kernel: [   11.332016] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
Apr  5 15:49:23 MTOLEDOB kernel: [   11.332024] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr  5 15:49:23 MTOLEDOB kernel: [   11.336327] ACPI: Thermal Zone [THM] (42 C)
Apr  5 15:49:23 MTOLEDOB kernel: [   11.741189] usbcore: registered new interface driver usbfs
Apr  5 15:49:23 MTOLEDOB kernel: [   11.741219] usbcore: registered new interface driver hub
Apr  5 15:49:23 MTOLEDOB kernel: [   11.741243] usbcore: registered new device driver usb
Apr  5 15:49:23 MTOLEDOB kernel: [   11.743034] USB Universal Host Controller Interface driver v3.0
Apr  5 15:49:23 MTOLEDOB kernel: [   11.743386] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
Apr  5 15:49:23 MTOLEDOB kernel: [   11.743390] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Apr  5 15:49:23 MTOLEDOB kernel: [   11.743405] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Apr  5 15:49:23 MTOLEDOB kernel: [   11.743409] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr  5 15:49:23 MTOLEDOB kernel: [   11.743617] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Apr  5 15:49:23 MTOLEDOB kernel: [   11.743643] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
Apr  5 15:49:23 MTOLEDOB kernel: [   11.743764] usb usb1: configuration #1 chosen from 1 choice
Apr  5 15:49:23 MTOLEDOB kernel: [   11.743798] hub 1-0:1.0: USB hub found
Apr  5 15:49:23 MTOLEDOB kernel: [   11.743804] hub 1-0:1.0: 2 ports detected
Apr  5 15:49:23 MTOLEDOB kernel: [   11.817157] SCSI subsystem initialized
Apr  5 15:49:23 MTOLEDOB kernel: [   11.829583] libata version 2.20 loaded.
Apr  5 15:49:23 MTOLEDOB kernel: [   11.846807] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Apr  5 15:49:23 MTOLEDOB kernel: [   11.846823] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Apr  5 15:49:23 MTOLEDOB kernel: [   11.846829] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr  5 15:49:23 MTOLEDOB kernel: [   11.846854] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Apr  5 15:49:23 MTOLEDOB kernel: [   11.846881] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
Apr  5 15:49:23 MTOLEDOB kernel: [   11.846990] usb usb2: configuration #1 chosen from 1 choice
Apr  5 15:49:23 MTOLEDOB kernel: [   11.847023] hub 2-0:1.0: USB hub found
Apr  5 15:49:23 MTOLEDOB kernel: [   11.847030] hub 2-0:1.0: 2 ports detected
Apr  5 15:49:23 MTOLEDOB kernel: [   11.951078] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
Apr  5 15:49:23 MTOLEDOB kernel: [   11.951085] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Apr  5 15:49:23 MTOLEDOB kernel: [   11.951099] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Apr  5 15:49:23 MTOLEDOB kernel: [   11.951103] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr  5 15:49:23 MTOLEDOB kernel: [   11.951139] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Apr  5 15:49:23 MTOLEDOB kernel: [   11.951167] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
Apr  5 15:49:23 MTOLEDOB kernel: [   11.951284] usb usb3: configuration #1 chosen from 1 choice
Apr  5 15:49:23 MTOLEDOB kernel: [   11.951315] hub 3-0:1.0: USB hub found
Apr  5 15:49:23 MTOLEDOB kernel: [   11.951322] hub 3-0:1.0: 2 ports detected
Apr  5 15:49:23 MTOLEDOB kernel: [   12.056503] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
Apr  5 15:49:23 MTOLEDOB kernel: [   12.056510] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
Apr  5 15:49:23 MTOLEDOB kernel: [   12.056528] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Apr  5 15:49:23 MTOLEDOB kernel: [   12.056533] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr  5 15:49:23 MTOLEDOB kernel: [   12.056585] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
Apr  5 15:49:23 MTOLEDOB kernel: [   12.056626] ehci_hcd 0000:00:1d.7: debug port 1
Apr  5 15:49:23 MTOLEDOB kernel: [   12.056633] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Apr  5 15:49:23 MTOLEDOB kernel: [   12.056646] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf4fffc00
Apr  5 15:49:23 MTOLEDOB kernel: [   12.060533] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Apr  5 15:49:23 MTOLEDOB kernel: [   12.060680] usb usb4: configuration #1 chosen from 1 choice
Apr  5 15:49:23 MTOLEDOB kernel: [   12.060715] hub 4-0:1.0: USB hub found
Apr  5 15:49:23 MTOLEDOB kernel: [   12.060725] hub 4-0:1.0: 6 ports detected
Apr  5 15:49:23 MTOLEDOB kernel: [    4.092000] Time: acpi_pm clocksource has been installed.
Apr  5 15:49:23 MTOLEDOB kernel: [    4.116000] ata_piix 0000:00:1f.1: version 2.10ac1
Apr  5 15:49:23 MTOLEDOB kernel: [    4.116000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
Apr  5 15:49:23 MTOLEDOB kernel: [    4.116000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Apr  5 15:49:23 MTOLEDOB kernel: [    4.116000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Apr  5 15:49:23 MTOLEDOB kernel: [    4.116000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
Apr  5 15:49:23 MTOLEDOB kernel: [    4.116000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
Apr  5 15:49:23 MTOLEDOB kernel: [    4.116000] scsi0 : ata_piix
Apr  5 15:49:23 MTOLEDOB kernel: [    4.280000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
Apr  5 15:49:23 MTOLEDOB kernel: [    4.280000] ata1.00: ATA-6: ST980815A, 3.ALD, max UDMA/100
Apr  5 15:49:23 MTOLEDOB kernel: [    4.280000] ata1.00: 156301488 sectors, multi 8: LBA48 
Apr  5 15:49:23 MTOLEDOB kernel: [    4.288000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
Apr  5 15:49:23 MTOLEDOB kernel: [    4.288000] ata1.00: configured for UDMA/100
Apr  5 15:49:23 MTOLEDOB kernel: [    4.288000] scsi1 : ata_piix
Apr  5 15:49:23 MTOLEDOB kernel: [    4.608000] ata2.00: ATAPI, max UDMA/33
Apr  5 15:49:23 MTOLEDOB kernel: [    4.772000] ata2.00: configured for UDMA/33
Apr  5 15:49:23 MTOLEDOB kernel: [    4.772000] scsi 0:0:0:0: Direct-Access     ATA      ST980815A        3.AL PQ: 0 ANSI: 5
Apr  5 15:49:23 MTOLEDOB kernel: [    4.776000] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4241N A101 PQ: 0 ANSI: 5
Apr  5 15:49:23 MTOLEDOB kernel: [    4.784000] tg3.c:v3.72.1 (January 8, 2007)
Apr  5 15:49:23 MTOLEDOB kernel: [    4.784000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Apr  5 15:49:23 MTOLEDOB kernel: [    4.832000] eth0: Tigon3 [partno(BCM95705A50) rev 3001 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000Base-T Ethernet 00:11:43:53:d5:22
Apr  5 15:49:23 MTOLEDOB kernel: [    4.832000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
Apr  5 15:49:23 MTOLEDOB kernel: [    4.832000] eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
Apr  5 15:49:23 MTOLEDOB kernel: [    4.836000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
Apr  5 15:49:23 MTOLEDOB kernel: [    4.836000] sda: Write Protect is off
Apr  5 15:49:23 MTOLEDOB kernel: [    4.836000] sda: Mode Sense: 00 3a 00 00
Apr  5 15:49:23 MTOLEDOB kernel: [    4.836000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  5 15:49:23 MTOLEDOB kernel: [    4.836000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
Apr  5 15:49:23 MTOLEDOB kernel: [    4.836000] sda: Write Protect is off
Apr  5 15:49:23 MTOLEDOB kernel: [    4.836000] sda: Mode Sense: 00 3a 00 00
Apr  5 15:49:23 MTOLEDOB kernel: [    4.836000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  5 15:49:23 MTOLEDOB kernel: [    4.836000]  sda: sda1 sda2 sda3 < sda5 >
Apr  5 15:49:23 MTOLEDOB kernel: [    4.888000] sd 0:0:0:0: Attached scsi disk sda
Apr  5 15:49:23 MTOLEDOB kernel: [    4.892000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr  5 15:49:23 MTOLEDOB kernel: [    4.892000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
Apr  5 15:49:23 MTOLEDOB kernel: [    4.916000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Apr  5 15:49:23 MTOLEDOB kernel: [    4.916000] Uniform CD-ROM driver Revision: 3.20
Apr  5 15:49:23 MTOLEDOB kernel: [    4.916000] sr 1:0:0:0: Attached scsi CD-ROM sr0
Apr  5 15:49:23 MTOLEDOB kernel: [    5.184000] Attempting manual resume
Apr  5 15:49:23 MTOLEDOB kernel: [    5.184000] swsusp: Resume From Partition 8:5
Apr  5 15:49:23 MTOLEDOB kernel: [    5.184000] PM: Checking swsusp image.
Apr  5 15:49:23 MTOLEDOB kernel: [    5.184000] PM: Resume from disk failed.
Apr  5 15:49:23 MTOLEDOB kernel: [    5.204000] EXT3-fs: INFO: recovery required on readonly filesystem.
Apr  5 15:49:23 MTOLEDOB kernel: [    5.204000] EXT3-fs: write access will be enabled during recovery.
Apr  5 15:49:23 MTOLEDOB kernel: [    7.872000] kjournald starting.  Commit interval 5 seconds
Apr  5 15:49:23 MTOLEDOB kernel: [    7.872000] EXT3-fs: recovery complete.
Apr  5 15:49:23 MTOLEDOB kernel: [    7.880000] EXT3-fs: mounted filesystem with ordered data mode.
Apr  5 15:49:23 MTOLEDOB kernel: [   21.172000] PM: Writing back config space on device 0000:02:00.0 at offset c (was ffbf0000, writing 0)
Apr  5 15:49:23 MTOLEDOB kernel: [   21.172000] PM: Writing back config space on device 0000:02:00.0 at offset b (was 165d14e4, writing 865d1028)
Apr  5 15:49:23 MTOLEDOB kernel: [   21.172000] PM: Writing back config space on device 0000:02:00.0 at offset 3 (was 0, writing 2008)
Apr  5 15:49:23 MTOLEDOB kernel: [   21.172000] PM: Writing back config space on device 0000:02:00.0 at offset 2 (was 2000000, writing 2000001)
Apr  5 15:49:23 MTOLEDOB kernel: [   21.172000] PM: Writing back config space on device 0000:02:00.0 at offset 1 (was 2b00000, writing 2b00106)
Apr  5 15:49:23 MTOLEDOB kernel: [   22.860000] NET: Registered protocol family 17
Apr  5 15:49:23 MTOLEDOB kernel: [   23.124000] iTCO_vendor_support: vendor-support=0
Apr  5 15:49:23 MTOLEDOB kernel: [   23.128000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
Apr  5 15:49:23 MTOLEDOB kernel: [   23.128000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x0860)
Apr  5 15:49:23 MTOLEDOB kernel: [   23.128000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Apr  5 15:49:23 MTOLEDOB kernel: [   23.232000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr  5 15:49:23 MTOLEDOB kernel: [   23.236000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr  5 15:49:23 MTOLEDOB kernel: [   23.292000] intel_rng: FWH not detected
Apr  5 15:49:23 MTOLEDOB kernel: [   23.496000] Linux agpgart interface v0.102 (c) Dave Jones
Apr  5 15:49:23 MTOLEDOB kernel: [   23.620000] agpgart: Detected an Intel 855PM Chipset.
Apr  5 15:49:23 MTOLEDOB kernel: [   23.624000] agpgart: AGP aperture is 128M @ 0xe0000000
Apr  5 15:49:23 MTOLEDOB kernel: [   24.180000] input: DualPoint Stick as /class/input/input2
Apr  5 15:49:23 MTOLEDOB kernel: [   24.200000] input: AlpsPS/2 ALPS DualPoint TouchPad as /class/input/input3
Apr  5 15:49:23 MTOLEDOB kernel: [   24.284000] Yenta: CardBus bridge found at 0000:02:01.0 [1028:011d]
Apr  5 15:49:23 MTOLEDOB kernel: [   24.284000] Yenta O2: res at 0x94/0xD4: 00/ea
Apr  5 15:49:23 MTOLEDOB kernel: [   24.284000] Yenta O2: enabling read prefetch/write burst
Apr  5 15:49:23 MTOLEDOB kernel: [   24.300000] ieee80211_crypt: registered algorithm 'NULL'
Apr  5 15:49:23 MTOLEDOB kernel: [   24.304000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Apr  5 15:49:23 MTOLEDOB kernel: [   24.304000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Apr  5 15:49:23 MTOLEDOB kernel: [   24.352000] input: PC Speaker as /class/input/input4
Apr  5 15:49:23 MTOLEDOB kernel: [   24.412000] Yenta: ISA IRQ mask 0x0498, PCI irq 11
Apr  5 15:49:23 MTOLEDOB kernel: [   24.412000] Socket status: 30000006
Apr  5 15:49:23 MTOLEDOB kernel: [   24.412000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
Apr  5 15:49:23 MTOLEDOB kernel: [   24.412000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
Apr  5 15:49:23 MTOLEDOB kernel: [   24.412000] cs: IO port probe 0xd000-0xefff: clean.
Apr  5 15:49:23 MTOLEDOB kernel: [   24.412000] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
Apr  5 15:49:23 MTOLEDOB kernel: [   24.412000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x37ffffff
Apr  5 15:49:23 MTOLEDOB kernel: [   24.412000] Yenta: CardBus bridge found at 0000:02:01.1 [1028:011d]
Apr  5 15:49:23 MTOLEDOB kernel: [   24.568000] Yenta: ISA IRQ mask 0x0498, PCI irq 11
Apr  5 15:49:23 MTOLEDOB kernel: [   24.568000] Socket status: 30000410
Apr  5 15:49:23 MTOLEDOB kernel: [   24.568000] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
Apr  5 15:49:23 MTOLEDOB kernel: [   24.568000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
Apr  5 15:49:23 MTOLEDOB kernel: [   24.568000] cs: IO port probe 0xd000-0xefff: clean.
Apr  5 15:49:23 MTOLEDOB kernel: [   24.568000] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
Apr  5 15:49:23 MTOLEDOB kernel: [   24.568000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x37ffffff
Apr  5 15:49:23 MTOLEDOB kernel: [   24.632000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
Apr  5 15:49:23 MTOLEDOB kernel: [   24.632000] ipw2100: Copyright(c) 2003-2006 Intel Corporation
Apr  5 15:49:23 MTOLEDOB kernel: [   24.632000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Apr  5 15:49:23 MTOLEDOB kernel: [   24.632000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
Apr  5 15:49:23 MTOLEDOB kernel: [   24.796000] parport: PnPBIOS parport detected.
Apr  5 15:49:23 MTOLEDOB kernel: [   24.796000] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Apr  5 15:49:23 MTOLEDOB kernel: [   25.016000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Apr  5 15:49:23 MTOLEDOB kernel: [   25.016000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
Apr  5 15:49:23 MTOLEDOB kernel: [   25.204000] pccard: PCMCIA card inserted into slot 1
Apr  5 15:49:23 MTOLEDOB kernel: [   25.396000] cs: memory probe 0xf6000000-0xfbffffff: excluding 0xf6000000-0xf65fffff 0xf6c00000-0xf71fffff 0xf7e00000-0xf83fffff 0xf9c00000-0xfa1fffff 0xfae00000-0xfb3fffff
Apr  5 15:49:23 MTOLEDOB kernel: [   25.408000] pcmcia: registering new device pcmcia1.0
Apr  5 15:49:23 MTOLEDOB kernel: [   25.468000] cs: IO port probe 0x100-0x3af: clean.
Apr  5 15:49:23 MTOLEDOB kernel: [   25.468000] cs: IO port probe 0x3e0-0x4ff: clean.
Apr  5 15:49:23 MTOLEDOB kernel: [   25.468000] cs: IO port probe 0x820-0x8ff: clean.
Apr  5 15:49:23 MTOLEDOB kernel: [   25.468000] cs: IO port probe 0xc00-0xcf7: clean.
Apr  5 15:49:23 MTOLEDOB kernel: [   25.468000] cs: IO port probe 0xa00-0xaff: clean.
Apr  5 15:49:23 MTOLEDOB kernel: [   25.472000] cs: IO port probe 0x100-0x3af: clean.
Apr  5 15:49:23 MTOLEDOB kernel: [   25.472000] cs: IO port probe 0x3e0-0x4ff: clean.
Apr  5 15:49:23 MTOLEDOB kernel: [   25.472000] cs: IO port probe 0x820-0x8ff: clean.
Apr  5 15:49:23 MTOLEDOB kernel: [   25.472000] cs: IO port probe 0xc00-0xcf7: clean.
Apr  5 15:49:23 MTOLEDOB kernel: [   25.472000] cs: IO port probe 0xa00-0xaff: clean.
Apr  5 15:49:23 MTOLEDOB kernel: [   25.836000] intel8x0_measure_ac97_clock: measured 55451 usecs
Apr  5 15:49:23 MTOLEDOB kernel: [   25.836000] intel8x0: clocking to 48000
Apr  5 15:49:23 MTOLEDOB kernel: [   25.980000] fuse init (API version 7.8)
Apr  5 15:49:23 MTOLEDOB kernel: [   26.016000] lp0: using parport0 (interrupt-driven).
Apr  5 15:49:23 MTOLEDOB kernel: [   26.040000] Adding 1510068k swap on /dev/disk/by-uuid/aaabdd49-42ff-4b7f-ac15-b1a4f0ed1a87.  Priority:-1 extents:1 across:1510068k
Apr  5 15:49:23 MTOLEDOB kernel: [   26.156000] EXT3 FS on sda2, internal journal
Apr  5 15:49:23 MTOLEDOB kernel: [   30.496000] ACPI: AC Adapter [AC] (on-line)
Apr  5 15:49:23 MTOLEDOB kernel: [   30.552000] input: Lid Switch as /class/input/input5
Apr  5 15:49:23 MTOLEDOB kernel: [   30.556000] ACPI: Lid Switch [LID]
Apr  5 15:49:23 MTOLEDOB kernel: [   30.600000] input: Power Button (CM) as /class/input/input6
Apr  5 15:49:23 MTOLEDOB kernel: [   30.604000] ACPI: Power Button (CM) [PBTN]
Apr  5 15:49:23 MTOLEDOB kernel: [   30.648000] input: Sleep Button (CM) as /class/input/input7
Apr  5 15:49:23 MTOLEDOB kernel: [   30.652000] ACPI: Sleep Button (CM) [SBTN]
Apr  5 15:49:23 MTOLEDOB kernel: [   30.672000] ACPI: ACPI Dock Station Driver 
Apr  5 15:49:23 MTOLEDOB kernel: [   31.116000] ACPI: Battery Slot [BAT0] (battery present)
Apr  5 15:49:23 MTOLEDOB kernel: [   31.116000] ACPI: Battery Slot [BAT1] (battery absent)
Apr  5 15:49:23 MTOLEDOB kernel: [   31.128000] Using specific hotkey driver
Apr  5 15:49:23 MTOLEDOB kernel: [   31.160000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Apr  5 15:49:23 MTOLEDOB kernel: [   31.232000] ibm_acpi: ec object not found
Apr  5 15:49:23 MTOLEDOB kernel: [   31.304000] pcc_acpi: loading...
Apr  5 15:49:25 MTOLEDOB dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Apr  5 15:49:26 MTOLEDOB dhcdbd: Started up.
Apr  5 15:49:26 MTOLEDOB NetworkManager: <information>^Istarting... 
Apr  5 15:49:27 MTOLEDOB NetworkManager: <information>^Ieth1: Device is fully-supported using driver 'ipw2100'. 
Apr  5 15:49:27 MTOLEDOB NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Apr  5 15:49:27 MTOLEDOB avahi-daemon[4607]: Found user 'avahi' (UID 105) and group 'avahi' (GID 109).
Apr  5 15:49:27 MTOLEDOB avahi-daemon[4607]: Successfully dropped root privileges.
Apr  5 15:49:27 MTOLEDOB avahi-daemon[4607]: avahi-daemon 0.6.17 starting up.
Apr  5 15:49:27 MTOLEDOB avahi-daemon[4607]: Successfully called chroot().
Apr  5 15:49:27 MTOLEDOB avahi-daemon[4607]: Successfully dropped remaining capabilities.
Apr  5 15:49:27 MTOLEDOB avahi-daemon[4607]: No service found in /etc/avahi/services.
Apr  5 15:49:27 MTOLEDOB avahi-daemon[4607]: Network interface enumeration completed.
Apr  5 15:49:27 MTOLEDOB avahi-daemon[4607]: Registering HINFO record with values 'I686'/'LINUX'.
Apr  5 15:49:27 MTOLEDOB avahi-daemon[4607]: Server startup complete. Host name is MTOLEDOB.local. Local service cookie is 1819308686.
Apr  5 15:49:27 MTOLEDOB NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Apr  5 15:49:27 MTOLEDOB NetworkManager: <information>^INow managing wireless (802.11) device 'eth1'. 
Apr  5 15:49:27 MTOLEDOB NetworkManager: <information>^IDeactivating device eth1. 
Apr  5 15:49:27 MTOLEDOB NetworkManager: <information>^Ieth0: Device is fully-supported using driver 'tg3'. 
Apr  5 15:49:27 MTOLEDOB NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Apr  5 15:49:27 MTOLEDOB NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Apr  5 15:49:27 MTOLEDOB NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth0'. 
Apr  5 15:49:27 MTOLEDOB NetworkManager: <information>^IDeactivating device eth0. 
Apr  5 15:49:27 MTOLEDOB kernel: [   36.068000] [drm] Initialized drm 1.1.0 20060810
Apr  5 15:49:27 MTOLEDOB kernel: [   36.104000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Apr  5 15:49:28 MTOLEDOB kernel: [   36.108000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
Apr  5 15:49:28 MTOLEDOB kernel: [   36.712000] ppdev: user-space parallel port driver
Apr  5 15:49:29 MTOLEDOB hpiod: 1.7.3 accepting connections at 2208... 
Apr  5 15:49:30 MTOLEDOB kernel: [   38.128000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Apr  5 15:49:30 MTOLEDOB kernel: [   38.128000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Apr  5 15:49:30 MTOLEDOB kernel: [   38.128000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Apr  5 15:49:30 MTOLEDOB kernel: [   38.204000] apm: BIOS not found.
Apr  5 15:49:30 MTOLEDOB kernel: [   38.388000] [drm] Setting GART location based on new memory map
Apr  5 15:49:30 MTOLEDOB kernel: [   38.388000] [drm] Loading R200 Microcode
Apr  5 15:49:30 MTOLEDOB kernel: [   38.388000] [drm] writeback test succeeded in 2 usecs
Apr  5 15:49:31 MTOLEDOB kernel: [   39.148000] vboxdrv: Trying to deactivate the NMI watchdog permanently...
Apr  5 15:49:31 MTOLEDOB kernel: [   39.148000] vboxdrv: Successfully done.
Apr  5 15:49:31 MTOLEDOB hcid[4992]: Bluetooth HCI daemon
Apr  5 15:49:31 MTOLEDOB kernel: [   39.524000] Bluetooth: Core ver 2.11
Apr  5 15:49:31 MTOLEDOB NetworkManager: <debug info>^I[1207432171.455513] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Apr  5 15:49:31 MTOLEDOB kernel: [   39.548000] NET: Registered protocol family 31
Apr  5 15:49:31 MTOLEDOB kernel: [   39.548000] Bluetooth: HCI device and connection manager initialized
Apr  5 15:49:31 MTOLEDOB kernel: [   39.548000] Bluetooth: HCI socket layer initialized
Apr  5 15:49:31 MTOLEDOB hcid[4992]: Starting SDP server
Apr  5 15:49:31 MTOLEDOB kernel: [   39.584000] Bluetooth: L2CAP ver 2.8
Apr  5 15:49:31 MTOLEDOB kernel: [   39.584000] Bluetooth: L2CAP socket layer initialized
Apr  5 15:49:31 MTOLEDOB kernel: [   39.712000] Bluetooth: RFCOMM socket layer initialized
Apr  5 15:49:31 MTOLEDOB kernel: [   39.712000] Bluetooth: RFCOMM TTY layer initialized
Apr  5 15:49:31 MTOLEDOB kernel: [   39.712000] Bluetooth: RFCOMM ver 1.8
Apr  5 15:49:31 MTOLEDOB anacron[5031]: Anacron 2.3 started on 2008-04-05
Apr  5 15:49:31 MTOLEDOB anacron[5031]: Normal exit (0 jobs run)
Apr  5 15:49:31 MTOLEDOB /usr/sbin/cron[5058]: (CRON) INFO (pidfile fd = 3)
Apr  5 15:49:31 MTOLEDOB /usr/sbin/cron[5059]: (CRON) STARTUP (fork ok)
Apr  5 15:49:31 MTOLEDOB /usr/sbin/cron[5059]: (CRON) INFO (Running @reboot jobs)
Apr  5 15:49:32 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Apr  5 15:49:32 MTOLEDOB anacron[5147]: Anacron 2.3 started on 2008-04-05
Apr  5 15:49:32 MTOLEDOB anacron[5147]: Normal exit (0 jobs run)
Apr  5 15:49:34 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr  5 15:49:37 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr  5 15:49:42 MTOLEDOB gconfd (mario-5253): starting (version 2.18.0.1), pid 5253 user 'mario'
Apr  5 15:49:42 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr  5 15:49:42 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readwrite:/home/mario/.gconf" to a writable configuration source at position 1
Apr  5 15:49:42 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr  5 15:49:42 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Apr  5 15:49:42 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Apr  5 15:49:44 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
Apr  5 15:49:45 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
Apr  5 15:49:45 MTOLEDOB kernel: [   54.012000] NET: Registered protocol family 10
Apr  5 15:49:45 MTOLEDOB kernel: [   54.012000] lo: Disabled Privacy Extensions
Apr  5 15:49:45 MTOLEDOB kernel: [   54.012000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr  5 15:49:45 MTOLEDOB kernel: [   54.012000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr  5 15:49:46 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 15:49:46 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 15:49:46 MTOLEDOB avahi-autoipd(eth0)[5278]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 108).
Apr  5 15:49:46 MTOLEDOB avahi-autoipd(eth0)[5278]: Successfully called chroot().
Apr  5 15:49:46 MTOLEDOB avahi-autoipd(eth0)[5278]: Successfully dropped root privileges.
Apr  5 15:49:46 MTOLEDOB avahi-autoipd(eth0)[5278]: fopen() failed: Permission denied
Apr  5 15:49:46 MTOLEDOB avahi-autoipd(eth0)[5278]: Starting with address 169.254.5.143
Apr  5 15:49:51 MTOLEDOB avahi-autoipd(eth0)[5278]: Callout BIND, address 169.254.5.143 on interface eth0
Apr  5 15:49:51 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.5.143.
Apr  5 15:49:51 MTOLEDOB avahi-daemon[4607]: New relevant interface eth0.IPv4 for mDNS.
Apr  5 15:49:51 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.5.143 on eth0.IPv4.
Apr  5 15:49:55 MTOLEDOB avahi-autoipd(eth0)[5278]: Successfully claimed IP address 169.254.5.143
Apr  5 15:49:55 MTOLEDOB avahi-autoipd(eth0)[5278]: fopen() failed: Permission denied
Apr  5 15:50:00 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Apr  5 15:50:03 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 15:50:03 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 15:50:03 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 15:50:03 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 15:50:03 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 15:50:04 MTOLEDOB NetworkManager: <information>^IUpdating allowed wireless network lists. 
Apr  5 15:50:05 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readwrite:/home/mario/.gconf" to a writable configuration source at position 0
Apr  5 15:50:06 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 15:50:06 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 15:50:06 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 15:50:06 MTOLEDOB avahi-autoipd(eth1)[5444]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 108).
Apr  5 15:50:06 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully called chroot().
Apr  5 15:50:06 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully dropped root privileges.
Apr  5 15:50:06 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 15:50:06 MTOLEDOB avahi-autoipd(eth1)[5444]: Starting with address 169.254.4.218
Apr  5 15:50:11 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 15:50:11 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 15:50:11 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 15:50:11 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 15:50:11 MTOLEDOB avahi-autoipd(eth1)[5445]: client: RTNETLINK answers: File exists
Apr  5 15:50:15 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 15:50:15 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 15:50:15 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 15:53:24 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr  5 15:53:31 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Apr  5 15:53:44 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Apr  5 15:53:53 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 15:53:55 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 15:53:55 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 15:53:55 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 15:53:55 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 15:53:55 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 15:53:55 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 15:53:55 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 15:53:55 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 15:53:55 MTOLEDOB avahi-autoipd(eth1)[5445]: client: RTNETLINK answers: No such process
Apr  5 15:53:58 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 15:53:58 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 15:53:58 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 15:53:58 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 15:53:58 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 15:54:01 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
Apr  5 15:54:03 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 15:54:03 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 15:54:03 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 15:54:03 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 15:54:03 MTOLEDOB avahi-autoipd(eth1)[5445]: client: RTNETLINK answers: File exists
Apr  5 15:54:07 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 15:54:07 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 15:54:16 MTOLEDOB dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Apr  5 15:54:16 MTOLEDOB NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
Apr  5 15:54:16 MTOLEDOB NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Apr  5 15:54:16 MTOLEDOB dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Apr  5 15:54:16 MTOLEDOB NetworkManager: <information>^IWill activate connection 'eth0'. 
Apr  5 15:54:16 MTOLEDOB NetworkManager: <information>^IDevice eth0 activation scheduled... 
Apr  5 15:54:16 MTOLEDOB NetworkManager: <information>^IActivation (eth0) started... 
Apr  5 15:54:16 MTOLEDOB NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr  5 15:54:16 MTOLEDOB NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Apr  5 15:54:16 MTOLEDOB NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Apr  5 15:54:16 MTOLEDOB NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Apr  5 15:54:16 MTOLEDOB NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Apr  5 15:54:16 MTOLEDOB NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Apr  5 15:54:16 MTOLEDOB NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr  5 15:54:16 MTOLEDOB NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Apr  5 15:54:16 MTOLEDOB NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Apr  5 15:54:16 MTOLEDOB kernel: [  324.664000] tg3: eth0: Link is up at 100 Mbps, full duplex.
Apr  5 15:54:16 MTOLEDOB kernel: [  324.664000] tg3: eth0: Flow control is off for TX and off for RX.
Apr  5 15:54:16 MTOLEDOB kernel: [  324.668000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Apr  5 15:54:17 MTOLEDOB NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Apr  5 15:54:17 MTOLEDOB avahi-daemon[4607]: Registering new address record for fe80::211:43ff:fe53:d522 on eth0.*.
Apr  5 15:54:17 MTOLEDOB NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Apr  5 15:54:17 MTOLEDOB NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0 
Apr  5 15:54:17 MTOLEDOB avahi-autoipd(eth0)[5278]: Got SIGTERM, quitting.
Apr  5 15:54:17 MTOLEDOB avahi-autoipd(eth0)[5278]: Callout STOP, address 169.254.5.143 on interface eth0
Apr  5 15:54:17 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.5.143 on eth0.
Apr  5 15:54:17 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.5.143.
Apr  5 15:54:17 MTOLEDOB avahi-daemon[4607]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr  5 15:54:17 MTOLEDOB avahi-autoipd(eth0)[5279]: client: RTNETLINK answers: No such process
Apr  5 15:54:18 MTOLEDOB NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0 
Apr  5 15:54:20 MTOLEDOB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Apr  5 15:54:21 MTOLEDOB dhclient: DHCPOFFER from 192.168.0.1
Apr  5 15:54:21 MTOLEDOB dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Apr  5 15:54:21 MTOLEDOB dhclient: DHCPACK from 192.168.0.1
Apr  5 15:54:21 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.4.
Apr  5 15:54:21 MTOLEDOB avahi-daemon[4607]: New relevant interface eth0.IPv4 for mDNS.
Apr  5 15:54:21 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.0.4 on eth0.IPv4.
Apr  5 15:54:21 MTOLEDOB NetworkManager: <information>^IDHCP daemon state is now 2 (bound) for interface eth0 
Apr  5 15:54:21 MTOLEDOB NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Apr  5 15:54:21 MTOLEDOB NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Apr  5 15:54:21 MTOLEDOB dhclient: bound to 192.168.0.4 -- renewal in 1533 seconds.
Apr  5 15:54:21 MTOLEDOB dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Apr  5 15:54:21 MTOLEDOB dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Apr  5 15:54:21 MTOLEDOB dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Apr  5 15:54:21 MTOLEDOB dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Apr  5 15:54:21 MTOLEDOB NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon: 
Apr  5 15:54:21 MTOLEDOB NetworkManager: <information>^I  address 192.168.0.4 
Apr  5 15:54:21 MTOLEDOB NetworkManager: <information>^I  netmask 255.255.255.0 
Apr  5 15:54:21 MTOLEDOB NetworkManager: <information>^I  broadcast 192.168.0.255 
Apr  5 15:54:21 MTOLEDOB NetworkManager: <information>^I  gateway 192.168.0.1 
Apr  5 15:54:21 MTOLEDOB NetworkManager: <information>^I  nameserver 192.168.0.1 
Apr  5 15:54:21 MTOLEDOB NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Apr  5 15:54:21 MTOLEDOB NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Apr  5 15:54:21 MTOLEDOB NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Apr  5 15:54:21 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.0.4 on eth0.
Apr  5 15:54:21 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.4.
Apr  5 15:54:21 MTOLEDOB avahi-daemon[4607]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr  5 15:54:21 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for fe80::211:43ff:fe53:d522 on eth0.
Apr  5 15:54:21 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.4.
Apr  5 15:54:21 MTOLEDOB avahi-daemon[4607]: New relevant interface eth0.IPv4 for mDNS.
Apr  5 15:54:21 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.0.4 on eth0.IPv4.
Apr  5 15:54:22 MTOLEDOB NetworkManager: <information>^IClearing nscd hosts cache. 
Apr  5 15:54:22 MTOLEDOB NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Apr  5 15:54:22 MTOLEDOB NetworkManager: <information>^IActivation (eth0) successful, device activated. 
Apr  5 15:54:22 MTOLEDOB NetworkManager: <information>^IActivation (eth0) Finish handler scheduled. 
Apr  5 15:54:22 MTOLEDOB NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Apr  5 15:54:23 MTOLEDOB avahi-daemon[4607]: Registering new address record for fe80::211:43ff:fe53:d522 on eth0.*.
Apr  5 15:54:32 MTOLEDOB kernel: [  340.440000] eth0: no IPv6 routers present
Apr  5 15:57:55 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Apr  5 15:58:00 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Apr  5 15:58:14 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Apr  5 15:58:26 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 15:58:26 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 15:58:26 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 15:58:26 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 15:58:26 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 15:58:26 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 15:58:26 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 15:58:26 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 15:58:26 MTOLEDOB avahi-autoipd(eth1)[5445]: client: RTNETLINK answers: No such process
Apr  5 15:58:29 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 15:58:29 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 15:58:29 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 15:58:29 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 15:58:29 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 15:58:35 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 15:58:35 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 15:58:35 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 15:58:35 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 15:58:39 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 15:58:39 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 16:01:40 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr  5 16:01:47 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Apr  5 16:02:01 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr  5 16:02:08 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Apr  5 16:02:11 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 16:02:11 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 16:02:11 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 16:02:11 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 16:02:11 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 16:02:11 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 16:02:11 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 16:02:11 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 16:02:14 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 16:02:14 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 16:02:14 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 16:02:14 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 16:02:14 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 16:02:19 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 16:02:19 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 16:02:19 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 16:02:19 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 16:02:23 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 16:02:23 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 16:06:48 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Apr  5 16:06:51 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr  5 16:06:58 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Apr  5 16:07:10 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Apr  5 16:07:19 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 16:07:19 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 16:07:19 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 16:07:19 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 16:07:19 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 16:07:19 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 16:07:19 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 16:07:19 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 16:07:22 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 16:07:22 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 16:07:22 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 16:07:22 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 16:07:22 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 16:07:27 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 16:07:27 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 16:07:27 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 16:07:27 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 16:07:31 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 16:07:31 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 16:11:30 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr  5 16:11:37 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Apr  5 16:11:51 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Apr  5 16:12:01 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 16:12:01 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 16:12:01 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 16:12:01 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 16:12:01 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 16:12:01 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 16:12:01 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 16:12:01 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 16:12:04 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 16:12:04 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 16:12:04 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 16:12:04 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 16:12:04 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 16:12:09 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 16:12:09 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 16:12:09 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 16:12:09 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 16:12:13 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 16:12:13 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 16:15:44 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Apr  5 16:15:47 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Apr  5 16:15:51 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Apr  5 16:16:01 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Apr  5 16:16:15 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 16:16:15 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 16:16:15 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 16:16:15 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 16:16:15 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 16:16:15 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 16:16:15 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 16:16:15 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 16:16:18 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 16:16:18 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 16:16:18 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 16:16:18 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 16:16:18 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 16:16:23 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 16:16:23 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 16:16:23 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 16:16:23 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 16:16:27 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 16:16:27 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 16:17:01 MTOLEDOB /USR/SBIN/CRON[6605]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  5 16:19:54 MTOLEDOB dhclient: DHCPREQUEST on eth0 to 192.168.0.1 port 67
Apr  5 16:19:54 MTOLEDOB dhclient: DHCPACK from 192.168.0.1
Apr  5 16:19:54 MTOLEDOB NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
Apr  5 16:19:54 MTOLEDOB dhclient: bound to 192.168.0.4 -- renewal in 1443 seconds.
Apr  5 16:20:28 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Apr  5 16:20:36 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Apr  5 16:20:47 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Apr  5 16:20:59 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 16:20:59 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 16:20:59 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 16:20:59 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 16:20:59 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 16:20:59 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 16:20:59 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 16:20:59 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 16:21:02 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 16:21:02 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 16:21:02 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 16:21:02 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 16:21:02 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 16:21:07 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 16:21:07 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 16:21:07 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 16:21:07 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 16:21:11 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 16:21:11 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 16:27:14 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Apr  5 16:27:20 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Apr  5 16:27:31 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Apr  5 16:27:45 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 16:27:45 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 16:27:45 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 16:27:45 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 16:27:45 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 16:27:45 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 16:27:45 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 16:27:45 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 16:27:48 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 16:27:48 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 16:27:48 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 16:27:48 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 16:27:48 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 16:27:54 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 16:27:54 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 16:27:54 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 16:27:54 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 16:27:58 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 16:27:58 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 16:30:27 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr  5 16:30:34 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
Apr  5 16:30:54 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Apr  5 16:30:58 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 16:30:58 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 16:30:58 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 16:30:58 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 16:30:58 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 16:30:58 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 16:30:58 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 16:30:58 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 16:31:01 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 16:31:01 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 16:31:01 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 16:31:01 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 16:31:01 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 16:31:06 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 16:31:06 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 16:31:06 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 16:31:06 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 16:31:10 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 16:31:10 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 16:37:05 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Apr  5 16:37:09 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Apr  5 16:37:19 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
Apr  5 16:37:34 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
Apr  5 16:37:36 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 16:37:36 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 16:37:36 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 16:37:36 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 16:37:36 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 16:37:36 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 16:37:36 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 16:37:36 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 16:37:39 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 16:37:39 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 16:37:39 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 16:37:39 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 16:37:39 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 16:37:44 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 16:37:44 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 16:37:44 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 16:37:44 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 16:37:48 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 16:37:48 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 16:41:22 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Apr  5 16:41:26 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr  5 16:41:33 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr  5 16:41:40 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Apr  5 16:41:49 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Apr  5 16:41:53 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 16:41:53 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 16:41:53 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 16:41:53 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 16:41:53 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 16:41:53 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 16:41:53 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 16:41:53 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 16:41:56 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 16:41:56 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 16:41:56 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 16:41:56 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 16:41:56 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 16:42:01 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 16:42:01 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 16:42:01 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 16:42:01 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 16:42:05 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 16:42:05 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 16:43:57 MTOLEDOB dhclient: DHCPREQUEST on eth0 to 192.168.0.1 port 67
Apr  5 16:43:57 MTOLEDOB dhclient: DHCPACK from 192.168.0.1
Apr  5 16:43:57 MTOLEDOB NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
Apr  5 16:43:57 MTOLEDOB dhclient: bound to 192.168.0.4 -- renewal in 1385 seconds.
Apr  5 16:45:37 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Apr  5 16:45:43 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
Apr  5 16:45:58 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Apr  5 16:46:08 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 16:46:08 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 16:46:08 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 16:46:08 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 16:46:08 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 16:46:08 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 16:46:08 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 16:46:08 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 16:46:11 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 16:46:11 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 16:46:11 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 16:46:11 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 16:46:11 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 16:46:16 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 16:46:16 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 16:46:16 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 16:46:16 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 16:46:20 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 16:46:20 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 16:49:59 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Apr  5 16:50:03 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Apr  5 16:50:11 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Apr  5 16:50:20 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Apr  5 16:50:30 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 16:50:30 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 16:50:30 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 16:50:30 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 16:50:30 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 16:50:30 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 16:50:30 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 16:50:30 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 16:50:33 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 16:50:33 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 16:50:33 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 16:50:33 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 16:50:33 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 16:50:39 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 16:50:39 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 16:50:39 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 16:50:39 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 16:50:43 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 16:50:43 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 16:55:53 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Apr  5 16:55:59 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Apr  5 16:56:11 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Apr  5 16:56:24 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 16:56:24 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 16:56:24 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 16:56:24 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 16:56:24 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 16:56:24 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 16:56:24 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 16:56:24 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 16:56:27 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 16:56:27 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 16:56:27 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 16:56:27 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 16:56:27 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 16:56:33 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 16:56:33 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 16:56:33 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 16:56:33 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 16:56:37 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 16:56:37 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 17:01:36 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Apr  5 17:01:40 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Apr  5 17:01:48 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
Apr  5 17:02:03 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Apr  5 17:02:07 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 17:02:07 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 17:02:07 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 17:02:07 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 17:02:07 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 17:02:07 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 17:02:07 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 17:02:07 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 17:02:10 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 17:02:10 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 17:02:10 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 17:02:10 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 17:02:10 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 17:02:15 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 17:02:15 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 17:02:15 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 17:02:15 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 17:02:19 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 17:02:19 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 17:05:48 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Apr  5 17:05:54 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Apr  5 17:06:00 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
Apr  5 17:06:16 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Apr  5 17:06:19 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 17:06:19 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 17:06:19 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 17:06:19 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 17:06:19 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 17:06:19 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 17:06:19 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 17:06:19 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 17:06:22 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 17:06:22 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 17:06:22 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 17:06:22 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 17:06:22 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 17:06:27 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 17:06:27 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 17:06:27 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 17:06:27 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 17:06:31 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 17:06:31 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 17:07:02 MTOLEDOB dhclient: DHCPREQUEST on eth0 to 192.168.0.1 port 67
Apr  5 17:07:02 MTOLEDOB dhclient: DHCPACK from 192.168.0.1
Apr  5 17:07:02 MTOLEDOB NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
Apr  5 17:07:02 MTOLEDOB dhclient: bound to 192.168.0.4 -- renewal in 1537 seconds.
Apr  5 17:13:45 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Apr  5 17:13:53 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Apr  5 17:14:06 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Apr  5 17:14:16 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 17:14:16 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 17:14:16 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 17:14:16 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 17:14:16 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 17:14:16 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 17:14:16 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 17:14:16 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 17:14:19 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 17:14:19 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 17:14:19 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 17:14:19 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 17:14:19 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 17:14:23 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 17:14:23 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 17:14:23 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 17:14:23 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 17:14:27 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 17:14:27 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 17:17:01 MTOLEDOB /USR/SBIN/CRON[8390]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  5 17:19:23 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Apr  5 17:19:26 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Apr  5 17:19:30 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr  5 17:19:37 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
Apr  5 17:19:52 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
Apr  5 17:19:54 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 17:19:54 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 17:19:54 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 17:19:54 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 17:19:54 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 17:19:54 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 17:19:54 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 17:19:54 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 17:19:57 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 17:19:57 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 17:19:57 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 17:19:57 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 17:19:57 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 17:20:02 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 17:20:02 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 17:20:02 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 17:20:02 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 17:20:06 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 17:20:06 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 17:25:44 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Apr  5 17:25:52 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Apr  5 17:26:03 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Apr  5 17:26:15 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 17:26:15 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 17:26:15 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 17:26:15 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 17:26:15 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 17:26:15 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 17:26:15 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 17:26:15 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 17:26:18 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 17:26:18 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 17:26:18 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 17:26:18 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 17:26:18 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 17:26:23 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 17:26:23 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 17:26:23 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 17:26:23 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 17:26:27 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 17:26:27 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 17:32:37 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Apr  5 17:32:39 MTOLEDOB dhclient: DHCPREQUEST on eth0 to 192.168.0.1 port 67
Apr  5 17:32:39 MTOLEDOB dhclient: DHCPACK from 192.168.0.1
Apr  5 17:32:39 MTOLEDOB NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
Apr  5 17:32:39 MTOLEDOB dhclient: bound to 192.168.0.4 -- renewal in 1419 seconds.
Apr  5 17:32:42 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Apr  5 17:32:55 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Apr  5 17:33:05 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Apr  5 17:33:08 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 17:33:08 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 17:33:08 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 17:33:08 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 17:33:08 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 17:33:08 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 17:33:08 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 17:33:08 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 17:33:11 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 17:33:11 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 17:33:11 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 17:33:11 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 17:33:11 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 17:33:16 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 17:33:16 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 17:33:16 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 17:33:16 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 17:33:20 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 17:33:20 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 17:36:25 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Apr  5 17:36:30 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Apr  5 17:36:44 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Apr  5 17:36:56 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 17:36:56 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 17:36:56 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 17:36:56 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 17:36:56 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 17:36:56 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 17:36:56 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 17:36:56 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 17:36:59 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 17:36:59 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 17:36:59 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 17:36:59 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 17:36:59 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 17:37:05 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 17:37:05 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 17:37:05 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 17:37:05 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 17:37:09 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 17:37:09 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 17:40:10 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Apr  5 17:40:14 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Apr  5 17:40:20 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Apr  5 17:40:30 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr  5 17:40:37 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Apr  5 17:40:41 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 17:40:41 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 17:40:41 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 17:40:41 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 17:40:41 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 17:40:41 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 17:40:41 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 17:40:41 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 17:40:44 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 17:40:44 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 17:40:44 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 17:40:44 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 17:40:44 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 17:40:49 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 17:40:49 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 17:40:49 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 17:40:49 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 17:40:53 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 17:40:53 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 17:48:06 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Apr  5 17:48:12 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Apr  5 17:48:24 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Apr  5 17:48:37 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 17:48:37 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 17:48:37 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 17:48:37 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 17:48:37 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 17:48:37 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 17:48:37 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 17:48:37 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 17:48:40 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 17:48:40 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 17:48:40 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 17:48:40 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 17:48:40 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 17:48:45 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 17:48:45 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 17:48:45 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 17:48:45 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 17:48:49 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 17:48:49 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 17:51:45 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Apr  5 17:51:51 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr  5 17:51:58 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Apr  5 17:52:12 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Apr  5 17:52:16 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 17:52:16 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 17:52:16 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 17:52:16 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 17:52:16 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 17:52:16 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 17:52:16 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 17:52:16 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 17:52:19 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 17:52:19 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 17:52:19 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 17:52:19 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 17:52:19 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 17:52:24 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 17:52:24 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 17:52:24 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 17:52:24 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 17:52:28 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 17:52:28 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 17:56:18 MTOLEDOB dhclient: DHCPREQUEST on eth0 to 192.168.0.1 port 67
Apr  5 17:56:18 MTOLEDOB dhclient: DHCPACK from 192.168.0.1
Apr  5 17:56:18 MTOLEDOB dhclient: bound to 192.168.0.4 -- renewal in 1445 seconds.
Apr  5 17:56:18 MTOLEDOB NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
Apr  5 17:56:47 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Apr  5 17:56:53 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Apr  5 17:57:04 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Apr  5 17:57:18 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 17:57:18 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 17:57:18 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 17:57:18 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 17:57:18 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 17:57:18 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 17:57:18 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 17:57:18 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 17:57:21 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 17:57:21 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 17:57:21 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 17:57:21 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 17:57:21 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 17:57:27 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 17:57:27 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 17:57:27 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 17:57:27 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 17:57:31 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 17:57:31 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 18:01:02 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Apr  5 18:01:06 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Apr  5 18:01:15 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Apr  5 18:01:25 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Apr  5 18:01:33 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 18:01:33 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 18:01:33 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 18:01:33 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 18:01:33 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 18:01:33 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 18:01:33 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 18:01:33 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 18:01:36 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 18:01:36 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 18:01:36 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 18:01:36 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 18:01:36 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 18:01:41 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 18:01:41 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 18:01:41 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 18:01:41 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 18:01:45 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 18:01:45 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 18:05:42 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Apr  5 18:05:45 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr  5 18:05:52 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Apr  5 18:06:06 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr  5 18:06:13 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 18:06:13 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 18:06:13 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 18:06:13 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 18:06:13 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 18:06:13 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 18:06:13 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 18:06:13 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 18:06:16 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 18:06:16 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 18:06:16 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 18:06:16 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 18:06:16 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 18:06:22 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 18:06:22 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 18:06:22 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 18:06:22 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 18:06:26 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 18:06:26 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 18:10:28 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Apr  5 18:10:36 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
Apr  5 18:10:56 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Apr  5 18:10:59 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 18:10:59 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 18:10:59 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 18:10:59 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 18:10:59 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 18:10:59 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 18:10:59 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 18:10:59 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 18:11:02 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 18:11:02 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 18:11:02 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 18:11:02 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 18:11:02 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 18:11:08 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 18:11:08 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 18:11:08 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 18:11:08 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 18:11:12 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 18:11:12 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 18:17:01 MTOLEDOB /USR/SBIN/CRON[10106]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  5 18:18:02 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr  5 18:18:09 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Apr  5 18:18:23 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Apr  5 18:18:33 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 18:18:33 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 18:18:33 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 18:18:33 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 18:18:33 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 18:18:33 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 18:18:33 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 18:18:33 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 18:18:36 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 18:18:36 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 18:18:36 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 18:18:36 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 18:18:36 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 18:18:40 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 18:18:40 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 18:18:40 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 18:18:40 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 18:18:44 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 18:18:44 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 18:20:23 MTOLEDOB dhclient: DHCPREQUEST on eth0 to 192.168.0.1 port 67
Apr  5 18:20:23 MTOLEDOB dhclient: DHCPACK from 192.168.0.1
Apr  5 18:20:23 MTOLEDOB NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
Apr  5 18:20:23 MTOLEDOB dhclient: bound to 192.168.0.4 -- renewal in 1770 seconds.
Apr  5 18:26:03 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr  5 18:26:10 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Apr  5 18:26:24 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Apr  5 18:26:34 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 18:26:34 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 18:26:34 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 18:26:34 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 18:26:34 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 18:26:34 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 18:26:34 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 18:26:34 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 18:26:37 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 18:26:37 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 18:26:37 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 18:26:37 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 18:26:37 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 18:26:42 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 18:26:42 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 18:26:42 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 18:26:42 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 18:26:46 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 18:26:46 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 18:32:28 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Apr  5 18:32:36 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
Apr  5 18:32:51 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Apr  5 18:32:59 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 18:32:59 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 18:32:59 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 18:32:59 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 18:32:59 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 18:32:59 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 18:32:59 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 18:32:59 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 18:33:02 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 18:33:02 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 18:33:02 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 18:33:02 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 18:33:02 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 18:33:06 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 18:33:06 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 18:33:06 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 18:33:06 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 18:33:10 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 18:33:10 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 18:39:27 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Apr  5 18:39:31 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr  5 18:39:38 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
Apr  5 18:39:53 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Apr  5 18:39:58 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 18:39:58 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 18:39:58 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 18:39:58 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 18:39:58 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 18:39:58 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 18:39:58 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 18:39:58 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 18:40:01 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 18:40:01 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 18:40:01 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 18:40:01 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 18:40:01 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 18:40:07 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 18:40:07 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 18:40:07 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 18:40:07 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 18:40:11 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 18:40:11 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 18:44:40 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Apr  5 18:44:48 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Apr  5 18:44:56 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
Apr  5 18:45:11 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 18:45:11 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 18:45:11 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 18:45:11 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 18:45:11 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 18:45:11 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 18:45:11 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 18:45:11 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 18:45:14 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 18:45:14 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 18:45:14 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 18:45:14 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 18:45:14 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 18:45:19 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 18:45:19 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 18:45:19 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 18:45:19 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 18:45:23 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 18:45:23 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 18:49:53 MTOLEDOB dhclient: DHCPREQUEST on eth0 to 192.168.0.1 port 67
Apr  5 18:49:53 MTOLEDOB dhclient: DHCPACK from 192.168.0.1
Apr  5 18:49:53 MTOLEDOB NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
Apr  5 18:49:53 MTOLEDOB dhclient: bound to 192.168.0.4 -- renewal in 1786 seconds.
Apr  5 18:50:37 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Apr  5 18:50:45 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
Apr  5 18:51:01 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr  5 18:51:08 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 18:51:08 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 18:51:08 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 18:51:08 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 18:51:08 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 18:51:08 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 18:51:08 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 18:51:08 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 18:51:11 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 18:51:11 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 18:51:11 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 18:51:11 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 18:51:11 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 18:51:15 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 18:51:15 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 18:51:15 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 18:51:15 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 18:51:19 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 18:51:19 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 18:54:23 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Apr  5 18:54:29 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Apr  5 18:54:39 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Apr  5 18:54:51 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Apr  5 18:54:54 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 18:54:54 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 18:54:54 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 18:54:54 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 18:54:54 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 18:54:54 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 18:54:54 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 18:54:54 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 18:54:57 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 18:54:57 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 18:54:57 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 18:54:57 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 18:54:57 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 18:55:02 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 18:55:02 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 18:55:02 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 18:55:02 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 18:55:06 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 18:55:06 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 19:00:24 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Apr  5 19:00:30 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Apr  5 19:00:40 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
Apr  5 19:00:55 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 19:00:55 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 19:00:55 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 19:00:55 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 19:00:55 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 19:00:55 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 19:00:55 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 19:00:55 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 19:00:58 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 19:00:58 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 19:00:58 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 19:00:58 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 19:00:58 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 19:01:02 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 19:01:02 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 19:01:02 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 19:01:02 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 19:01:06 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 19:01:06 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 19:04:11 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Apr  5 19:04:14 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Apr  5 19:04:18 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Apr  5 19:04:29 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Apr  5 19:04:41 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
Apr  5 19:04:42 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 19:04:42 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 19:04:42 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 19:04:42 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 19:04:42 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 19:04:42 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 19:04:42 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 19:04:42 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 19:04:45 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 19:04:45 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 19:04:45 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 19:04:45 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 19:04:45 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 19:04:50 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 19:04:50 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 19:04:50 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 19:04:50 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 19:04:54 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 19:04:54 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 19:09:46 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Apr  5 19:09:51 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Apr  5 19:10:05 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Apr  5 19:10:14 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Apr  5 19:10:17 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 19:10:17 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 19:10:17 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 19:10:17 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 19:10:17 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 19:10:17 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 19:10:17 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 19:10:17 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 19:10:20 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 19:10:20 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 19:10:20 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 19:10:20 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 19:10:20 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 19:10:26 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 19:10:26 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 19:10:26 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 19:10:26 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 19:10:30 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 19:10:30 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 19:15:59 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Apr  5 19:16:02 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr  5 19:16:09 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Apr  5 19:16:22 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Apr  5 19:16:30 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 19:16:30 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 19:16:30 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 19:16:30 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 19:16:30 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 19:16:30 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 19:16:30 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 19:16:30 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 19:16:33 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 19:16:33 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 19:16:33 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 19:16:33 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 19:16:33 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 19:16:38 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 19:16:38 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 19:16:38 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 19:16:38 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 19:16:42 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 19:16:42 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 19:17:01 MTOLEDOB /USR/SBIN/CRON[11818]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  5 19:19:28 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr  5 19:19:35 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Apr  5 19:19:39 MTOLEDOB dhclient: DHCPREQUEST on eth0 to 192.168.0.1 port 67
Apr  5 19:19:39 MTOLEDOB dhclient: DHCPACK from 192.168.0.1
Apr  5 19:19:39 MTOLEDOB NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
Apr  5 19:19:39 MTOLEDOB dhclient: bound to 192.168.0.4 -- renewal in 1800 seconds.
Apr  5 19:19:44 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
Apr  5 19:19:59 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 19:19:59 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 19:19:59 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 19:19:59 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 19:19:59 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 19:19:59 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 19:19:59 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 19:19:59 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 19:20:02 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 19:20:02 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 19:20:02 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 19:20:02 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 19:20:02 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 19:20:07 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 19:20:07 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 19:20:07 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 19:20:07 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 19:20:11 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 19:20:11 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 19:25:52 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Apr  5 19:25:55 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Apr  5 19:26:03 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Apr  5 19:26:13 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Apr  5 19:26:23 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 19:26:23 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 19:26:23 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 19:26:23 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 19:26:23 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 19:26:23 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 19:26:23 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 19:26:23 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 19:26:26 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 19:26:26 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 19:26:26 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 19:26:26 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 19:26:26 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 19:26:31 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 19:26:31 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 19:26:31 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 19:26:31 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 19:26:35 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 19:26:35 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 19:32:31 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr  5 19:32:38 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
Apr  5 19:32:57 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Apr  5 19:33:02 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 19:33:02 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 19:33:02 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 19:33:02 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 19:33:02 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 19:33:02 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 19:33:02 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 19:33:02 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 19:33:05 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 19:33:05 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 19:33:05 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 19:33:05 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 19:33:05 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 19:33:10 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 19:33:10 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 19:33:10 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 19:33:10 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 19:33:14 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 19:33:14 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 19:36:56 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Apr  5 19:37:02 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Apr  5 19:37:10 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
Apr  5 19:37:25 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
Apr  5 19:37:27 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 19:37:27 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 19:37:27 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 19:37:27 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 19:37:27 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 19:37:27 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 19:37:27 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 19:37:27 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 19:37:30 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 19:37:30 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 19:37:30 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 19:37:30 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 19:37:30 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 19:37:35 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 19:37:35 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 19:37:35 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 19:37:35 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 19:37:39 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 19:37:39 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 19:38:53 MTOLEDOB gconfd (root-12456): starting (version 2.18.0.1), pid 12456 user 'root'
Apr  5 19:38:53 MTOLEDOB gconfd (root-12456): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr  5 19:38:53 MTOLEDOB gconfd (root-12456): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Apr  5 19:38:53 MTOLEDOB gconfd (root-12456): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr  5 19:38:53 MTOLEDOB gconfd (root-12456): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Apr  5 19:38:53 MTOLEDOB gconfd (root-12456): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Apr  5 19:39:23 MTOLEDOB gconfd (root-12456): GConf server is not in use, shutting down.
Apr  5 19:39:24 MTOLEDOB gconfd (root-12456): Exiting
Apr  5 19:40:35 MTOLEDOB gconfd (root-15477): starting (version 2.18.0.1), pid 15477 user 'root'
Apr  5 19:40:35 MTOLEDOB gconfd (root-15477): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr  5 19:40:35 MTOLEDOB gconfd (root-15477): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Apr  5 19:40:35 MTOLEDOB gconfd (root-15477): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr  5 19:40:35 MTOLEDOB gconfd (root-15477): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Apr  5 19:40:35 MTOLEDOB gconfd (root-15477): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Apr  5 19:41:05 MTOLEDOB gconfd (root-15477): GConf server is not in use, shutting down.
Apr  5 19:41:05 MTOLEDOB gconfd (root-15477): Exiting
Apr  5 19:43:56 MTOLEDOB /usr/sbin/cron[17327]: (CRON) INFO (pidfile fd = 5)
Apr  5 19:43:56 MTOLEDOB /usr/sbin/cron[17328]: (CRON) STARTUP (fork ok)
Apr  5 19:43:56 MTOLEDOB /usr/sbin/cron[17328]: (CRON) INFO (Skipping @reboot jobs -- not system startup)
Apr  5 19:44:38 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Apr  5 19:44:42 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Apr  5 19:44:53 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
Apr  5 19:45:08 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
Apr  5 19:45:09 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 19:45:09 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 19:45:09 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 19:45:09 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 19:45:09 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 19:45:09 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 19:45:09 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 19:45:09 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 19:45:12 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 19:45:12 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 19:45:12 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 19:45:12 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 19:45:12 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 19:45:14 MTOLEDOB gconfd (mario-5253): SIGHUP received, reloading all databases
Apr  5 19:45:15 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr  5 19:45:15 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readwrite:/home/mario/.gconf" to a writable configuration source at position 1
Apr  5 19:45:15 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr  5 19:45:15 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Apr  5 19:45:15 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Apr  5 19:45:16 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 19:45:16 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 19:45:16 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 19:45:16 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 19:45:20 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 19:45:20 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 19:46:44 MTOLEDOB gconfd (mario-5253): SIGHUP received, reloading all databases
Apr  5 19:46:44 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr  5 19:46:44 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readwrite:/home/mario/.gconf" to a writable configuration source at position 1
Apr  5 19:46:44 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr  5 19:46:44 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Apr  5 19:46:44 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Apr  5 19:48:14 MTOLEDOB gconfd (mario-5253): SIGHUP received, reloading all databases
Apr  5 19:48:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr  5 19:48:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readwrite:/home/mario/.gconf" to a writable configuration source at position 1
Apr  5 19:48:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr  5 19:48:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Apr  5 19:48:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Apr  5 19:49:39 MTOLEDOB dhclient: DHCPREQUEST on eth0 to 192.168.0.1 port 67
Apr  5 19:49:39 MTOLEDOB dhclient: DHCPACK from 192.168.0.1
Apr  5 19:49:40 MTOLEDOB NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
Apr  5 19:49:40 MTOLEDOB dhclient: bound to 192.168.0.4 -- renewal in 1759 seconds.
Apr  5 19:50:14 MTOLEDOB gconfd (mario-5253): SIGHUP received, reloading all databases
Apr  5 19:50:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr  5 19:50:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readwrite:/home/mario/.gconf" to a writable configuration source at position 1
Apr  5 19:50:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr  5 19:50:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Apr  5 19:50:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Apr  5 19:50:57 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr  5 19:51:04 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
Apr  5 19:51:21 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr  5 19:51:28 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 19:51:28 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 19:51:29 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 19:51:29 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 19:51:29 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 19:51:29 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 19:51:29 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 19:51:29 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 19:51:32 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 19:51:32 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 19:51:32 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 19:51:32 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 19:51:32 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 19:51:37 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 19:51:37 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 19:51:37 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 19:51:37 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 19:51:41 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 19:51:41 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 19:52:14 MTOLEDOB gconfd (mario-5253): SIGHUP received, reloading all databases
Apr  5 19:52:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr  5 19:52:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readwrite:/home/mario/.gconf" to a writable configuration source at position 1
Apr  5 19:52:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr  5 19:52:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Apr  5 19:52:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Apr  5 19:52:22 MTOLEDOB kernel: [14609.980000] apm: BIOS not found.
Apr  5 19:56:14 MTOLEDOB gconfd (mario-5253): SIGHUP received, reloading all databases
Apr  5 19:56:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr  5 19:56:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readwrite:/home/mario/.gconf" to a writable configuration source at position 1
Apr  5 19:56:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr  5 19:56:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Apr  5 19:56:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Apr  5 19:57:16 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Apr  5 19:57:21 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Apr  5 19:57:34 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Apr  5 19:57:47 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 19:57:47 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 19:57:47 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 19:57:47 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 19:57:47 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 19:57:47 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 19:57:47 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 19:57:47 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 19:57:49 MTOLEDOB udevd[2479]: udev_rules_init: could not read '/etc/udev/rules.d/libmtp.rules': No such file or directory
Apr  5 19:57:51 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 19:57:51 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 19:57:51 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 19:57:51 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 19:57:51 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 19:57:57 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 19:57:57 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 19:57:57 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 19:57:57 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 19:58:01 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 19:58:01 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 19:58:21 MTOLEDOB udevd[2479]: udev_rules_init: could not read '/etc/udev/rules.d/libmtp.rules': No such file or directory
Apr  5 19:58:35 MTOLEDOB last message repeated 6 times
Apr  5 19:59:22 MTOLEDOB last message repeated 4 times
Apr  5 20:00:25 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Apr  5 20:00:30 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Apr  5 20:00:40 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
Apr  5 20:00:56 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 20:00:56 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 20:00:57 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 20:00:57 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 20:00:57 MTOLEDOB avahi-daemon[4607]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr  5 20:00:57 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 169.254.4.218 on eth1.
Apr  5 20:00:57 MTOLEDOB avahi-autoipd(eth1)[5444]: A routable address has been configured.
Apr  5 20:00:57 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout UNBIND, address 169.254.4.218 on interface eth1
Apr  5 20:01:00 MTOLEDOB avahi-autoipd(eth1)[5444]: No longer a routable address configured, restarting probe process.
Apr  5 20:01:00 MTOLEDOB avahi-daemon[4607]: Withdrawing address record for 192.168.1.100 on eth1.
Apr  5 20:01:00 MTOLEDOB avahi-daemon[4607]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr  5 20:01:00 MTOLEDOB avahi-daemon[4607]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr  5 20:01:00 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 20:01:06 MTOLEDOB avahi-autoipd(eth1)[5444]: Callout BIND, address 169.254.4.218 on interface eth1
Apr  5 20:01:06 MTOLEDOB avahi-daemon[4607]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.218.
Apr  5 20:01:06 MTOLEDOB avahi-daemon[4607]: New relevant interface eth1.IPv4 for mDNS.
Apr  5 20:01:06 MTOLEDOB avahi-daemon[4607]: Registering new address record for 169.254.4.218 on eth1.IPv4.
Apr  5 20:01:10 MTOLEDOB avahi-autoipd(eth1)[5444]: Successfully claimed IP address 169.254.4.218
Apr  5 20:01:10 MTOLEDOB avahi-autoipd(eth1)[5444]: fopen() failed: Permission denied
Apr  5 20:02:22 MTOLEDOB hcid[4992]: Stopping SDP server
Apr  5 20:02:22 MTOLEDOB hcid[4992]: Unregister path: /org/bluez
Apr  5 20:02:22 MTOLEDOB hcid[4992]: Exit
Apr  5 20:02:25 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readwrite:/home/mario/.gconf" to a writable configuration source at position 0
Apr  5 20:03:33 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Apr  5 20:03:37 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Apr  5 20:03:46 MTOLEDOB udevd[2479]: udev_rules_init: could not read '/etc/udev/rules.d/libmtp.rules': No such file or directory
Apr  5 20:03:46 MTOLEDOB udevd[2479]: udev_rules_init: could not read '/etc/udev/rules.d/libmtp.rules': No such file or directory
Apr  5 20:03:48 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Apr  5 20:04:00 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Apr  5 20:04:04 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 20:04:04 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 20:04:14 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 20:04:14 MTOLEDOB gconfd (mario-5253): SIGHUP received, reloading all databases
Apr  5 20:04:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr  5 20:04:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readwrite:/home/mario/.gconf" to a writable configuration source at position 1
Apr  5 20:04:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr  5 20:04:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Apr  5 20:04:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Apr  5 20:07:40 MTOLEDOB udevd[2479]: udev_rules_init: could not read '/etc/udev/rules.d/libmtp.rules': No such file or directory
Apr  5 20:07:40 MTOLEDOB udevd[2479]: udev_rules_init: could not read '/etc/udev/rules.d/libmtp.rules': No such file or directory
Apr  5 20:07:43 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Apr  5 20:07:47 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Apr  5 20:07:55 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Apr  5 20:08:07 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr  5 20:08:14 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 20:08:14 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 20:08:24 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 20:12:49 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Apr  5 20:12:52 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Apr  5 20:12:58 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Apr  5 20:13:07 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Apr  5 20:13:20 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 20:13:20 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 20:13:30 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 20:16:44 MTOLEDOB gconfd (mario-5253): SIGHUP received, reloading all databases
Apr  5 20:16:44 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr  5 20:16:44 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readwrite:/home/mario/.gconf" to a writable configuration source at position 1
Apr  5 20:16:44 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr  5 20:16:44 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Apr  5 20:16:44 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Apr  5 20:17:02 MTOLEDOB /USR/SBIN/CRON[11902]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  5 20:17:14 MTOLEDOB gconfd (mario-5253): SIGHUP received, reloading all databases
Apr  5 20:17:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr  5 20:17:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readwrite:/home/mario/.gconf" to a writable configuration source at position 1
Apr  5 20:17:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr  5 20:17:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Apr  5 20:17:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Apr  5 20:17:17 MTOLEDOB udevd[2479]: udev_rules_init: could not read '/etc/udev/rules.d/libmtp.rules': No such file or directory
Apr  5 20:17:32 MTOLEDOB last message repeated 2 times
Apr  5 20:17:44 MTOLEDOB gconfd (mario-5253): SIGHUP received, reloading all databases
Apr  5 20:17:44 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr  5 20:17:44 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readwrite:/home/mario/.gconf" to a writable configuration source at position 1
Apr  5 20:17:44 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr  5 20:17:44 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Apr  5 20:17:44 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Apr  5 20:17:51 MTOLEDOB kernel: [16138.436000] Using specific hotkey driver
Apr  5 20:17:51 MTOLEDOB kernel: [16138.600000] ibm_acpi: ec object not found
Apr  5 20:17:51 MTOLEDOB udevd[2479]: udev_rules_init: could not read '/etc/udev/rules.d/libmtp.rules': No such file or directory
Apr  5 20:17:54 MTOLEDOB kernel: [16141.956000] Using specific hotkey driver
Apr  5 20:17:54 MTOLEDOB kernel: [16142.032000] ibm_acpi: ec object not found
Apr  5 20:17:57 MTOLEDOB kernel: [16145.124000] apm: BIOS not found.
Apr  5 20:18:14 MTOLEDOB gconfd (mario-5253): SIGHUP received, reloading all databases
Apr  5 20:18:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr  5 20:18:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readwrite:/home/mario/.gconf" to a writable configuration source at position 1
Apr  5 20:18:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr  5 20:18:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Apr  5 20:18:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Apr  5 20:18:44 MTOLEDOB gconfd (mario-5253): SIGHUP received, reloading all databases
Apr  5 20:18:45 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr  5 20:18:45 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readwrite:/home/mario/.gconf" to a writable configuration source at position 1
Apr  5 20:18:45 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr  5 20:18:45 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Apr  5 20:18:45 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Apr  5 20:18:57 MTOLEDOB udevd[2479]: udev_rules_init: could not read '/etc/udev/rules.d/libmtp.rules': No such file or directory
Apr  5 20:18:59 MTOLEDOB dhclient: DHCPREQUEST on eth0 to 192.168.0.1 port 67
Apr  5 20:18:59 MTOLEDOB dhclient: DHCPACK from 192.168.0.1
Apr  5 20:19:27 MTOLEDOB udevd[2479]: udev_rules_init: could not read '/etc/udev/rules.d/libmtp.rules': No such file or directory
Apr  5 20:19:44 MTOLEDOB gconfd (mario-5253): SIGHUP received, reloading all databases
Apr  5 20:19:45 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr  5 20:19:45 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readwrite:/home/mario/.gconf" to a writable configuration source at position 1
Apr  5 20:19:45 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr  5 20:19:45 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Apr  5 20:19:45 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Apr  5 20:19:50 MTOLEDOB init: Re-executing /sbin/init
Apr  5 20:19:59 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Apr  5 20:20:05 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Apr  5 20:20:15 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
Apr  5 20:20:30 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 20:20:30 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 20:20:40 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 20:21:14 MTOLEDOB gconfd (mario-5253): SIGHUP received, reloading all databases
Apr  5 20:21:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr  5 20:21:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readwrite:/home/mario/.gconf" to a writable configuration source at position 1
Apr  5 20:21:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr  5 20:21:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Apr  5 20:21:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Apr  5 20:21:15 MTOLEDOB hcid[18686]: Bluetooth HCI daemon
Apr  5 20:21:15 MTOLEDOB hcid[18686]: Starting SDP server
Apr  5 20:21:15 MTOLEDOB hcid[18686]: Created local server at unix:abstract=/var/run/dbus-1Ymt304zCc,guid=c5a9cf21ed487ab77cc58c0047f8339b
Apr  5 20:21:15 MTOLEDOB audio[18689]: Bluetooth Audio daemon
Apr  5 20:21:15 MTOLEDOB audio[18689]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Apr  5 20:21:15 MTOLEDOB audio[18689]: Unix socket created: 5
Apr  5 20:21:15 MTOLEDOB input[18690]: Bluetooth Input daemon
Apr  5 20:21:15 MTOLEDOB input[18690]: Registered input manager path:/org/bluez/input
Apr  5 20:21:15 MTOLEDOB audio[18689]: add_service_record: got record id 0x10000
Apr  5 20:21:15 MTOLEDOB audio[18689]: add_service_record: got record id 0x10001
Apr  5 20:21:15 MTOLEDOB audio[18689]: Registered manager path:/org/bluez/audio
Apr  5 20:21:32 MTOLEDOB dhcdbd: Started up.
Apr  5 20:21:46 MTOLEDOB udevd[2479]: udev_rules_init: could not read '/etc/udev/rules.d/libmtp.rules': No such file or directory
Apr  5 20:21:46 MTOLEDOB udevd[2479]: udev_rules_init: could not read '/etc/udev/rules.d/libmtp.rules': No such file or directory
Apr  5 20:25:48 MTOLEDOB kernel: Kernel logging (proc) stopped.
Apr  5 20:25:48 MTOLEDOB kernel: Kernel log daemon terminating.
Apr  5 20:25:51 MTOLEDOB kernel: Inspecting /boot/System.map-2.6.20-16-generic
Apr  5 20:25:51 MTOLEDOB kernel: Loaded 24980 symbols from /boot/System.map-2.6.20-16-generic.
Apr  5 20:25:51 MTOLEDOB kernel: Symbols match kernel version 2.6.20.
Apr  5 20:25:51 MTOLEDOB kernel: No module symbols loaded - kernel modules not enabled. 
Apr  5 20:25:52 MTOLEDOB exiting on signal 15
Apr  5 20:25:52 MTOLEDOB syslogd 1.4.1#21ubuntu3: restart.
Apr  5 20:26:09 MTOLEDOB udevd[2479]: udev_rules_init: could not read '/etc/udev/rules.d/libmtp.rules': No such file or directory
Apr  5 20:26:11 MTOLEDOB last message repeated 32 times
Apr  5 20:26:13 MTOLEDOB NetworkManager: <debug info>^I[1207448773.759976] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_3340'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.243649] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_3341'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.336656] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_4c66'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.344813] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c2'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.348963] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.351255] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.353326] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c4'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.355626] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.357702] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.360179] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c7'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.362375] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.364515] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.366632] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24cd'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.368765] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.370886] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.372972] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.375045] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_165d'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.377191] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1217_7113'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.379594] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1217_7113_0'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.381772] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pcmcia__1__1'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.383851] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_1043'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.386070] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24cc'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.388193] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.390375] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.392475] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_scsi_device_lun0'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.394642] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_0'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.396665] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_0_scsi_device_lun0'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.398963] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.401007] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c6'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.403251] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.405327] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_dock_0'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.407466] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.409562] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.411813] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.413918] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.416039] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.418339] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.420603] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.422696] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_vesafb_0'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.424783] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.427022] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.429167] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.431254] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.433382] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.435615] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.437773] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.440135] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.442412] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.444445] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.447966] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.450306] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.452547] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0401'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.454583] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.456670] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.459220] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.461494] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.463564] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_11_43_53_d5_22'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.479072] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_0c_f1_1c_20_6b'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.490275] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_scsi_device_lun0_scsi_generic'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.492563] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.494656] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_pcm_1'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.496931] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_pcm_0'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.499263] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_control__1'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.501487] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_pcm_0_0'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.503661] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_mixer__1'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.505939] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_0'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.508057] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_playback_0'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.510349] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_1'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.512495] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_2'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.514897] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_3'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.517000] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_playback_4'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.519462] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.521533] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.523906] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.526008] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.528160] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.530293] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.532546] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.534530] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.536731] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.714036] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.731591] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.733636] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Apr  5 20:26:14 MTOLEDOB NetworkManager: <debug info>^I[1207448774.735863] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Apr  5 20:26:15 MTOLEDOB NetworkManager: <debug info>^I[1207448775.005587] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_ST980815A'). 
Apr  5 20:26:15 MTOLEDOB NetworkManager: <debug info>^I[1207448775.263357] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_606C05936C0564DE'). 
Apr  5 20:26:15 MTOLEDOB NetworkManager: <debug info>^I[1207448775.349184] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_241da2db_0e86_4d13_ba31_7e747e81c264'). 
Apr  5 20:26:15 MTOLEDOB NetworkManager: <debug info>^I[1207448775.499601] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part3_size_1024'). 
Apr  5 20:26:15 MTOLEDOB NetworkManager: <debug info>^I[1207448775.619313] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_aaabdd49_42ff_4b7f_ac15_b1a4f0ed1a87'). 
Apr  5 20:26:15 MTOLEDOB NetworkManager: <debug info>^I[1207448775.862796] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT1'). 
Apr  5 20:26:15 MTOLEDOB NetworkManager: <debug info>^I[1207448775.954076] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Apr  5 20:26:15 MTOLEDOB NetworkManager: <debug info>^I[1207448775.956103] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Apr  5 20:26:15 MTOLEDOB NetworkManager: <debug info>^I[1207448775.958571] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Apr  5 20:26:15 MTOLEDOB NetworkManager: <debug info>^I[1207448775.973637] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_RW/DVD_GCC_4241N'). 
Apr  5 20:26:29 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr  5 20:26:36 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Apr  5 20:26:44 MTOLEDOB gconfd (mario-5253): SIGHUP received, reloading all databases
Apr  5 20:26:45 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Apr  5 20:26:45 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr  5 20:26:45 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readwrite:/home/mario/.gconf" to a writable configuration source at position 1
Apr  5 20:26:45 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr  5 20:26:45 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Apr  5 20:26:45 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Apr  5 20:26:57 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Apr  5 20:27:00 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 20:27:00 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 20:27:03 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 20:27:09 MTOLEDOB udevd[2479]: udev_rules_init: could not read '/etc/udev/rules.d/libmtp.rules': No such file or directory
Apr  5 20:27:10 MTOLEDOB last message repeated 2 times
Apr  5 20:27:14 MTOLEDOB gconfd (mario-5253): SIGHUP received, reloading all databases
Apr  5 20:27:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr  5 20:27:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readwrite:/home/mario/.gconf" to a writable configuration source at position 1
Apr  5 20:27:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr  5 20:27:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Apr  5 20:27:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Apr  5 20:27:45 MTOLEDOB gconfd (mario-5253): SIGHUP received, reloading all databases
Apr  5 20:27:45 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr  5 20:27:45 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readwrite:/home/mario/.gconf" to a writable configuration source at position 1
Apr  5 20:27:45 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr  5 20:27:45 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Apr  5 20:27:45 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Apr  5 20:28:14 MTOLEDOB gconfd (mario-5253): SIGHUP received, reloading all databases
Apr  5 20:28:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr  5 20:28:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readwrite:/home/mario/.gconf" to a writable configuration source at position 1
Apr  5 20:28:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr  5 20:28:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Apr  5 20:28:14 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Apr  5 20:28:44 MTOLEDOB gconfd (mario-5253): SIGHUP received, reloading all databases
Apr  5 20:28:44 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr  5 20:28:45 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readwrite:/home/mario/.gconf" to a writable configuration source at position 1
Apr  5 20:28:45 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr  5 20:28:45 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Apr  5 20:28:45 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Apr  5 20:29:15 MTOLEDOB gconfd (mario-5253): SIGHUP received, reloading all databases
Apr  5 20:29:15 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr  5 20:29:15 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readwrite:/home/mario/.gconf" to a writable configuration source at position 1
Apr  5 20:29:15 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr  5 20:29:15 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Apr  5 20:29:15 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Apr  5 20:29:28 MTOLEDOB kernel: [16836.068000] pcmcia: Detected deprecated PCMCIA ioctl usage from process: discover.
Apr  5 20:29:28 MTOLEDOB kernel: [16836.068000] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
Apr  5 20:29:28 MTOLEDOB kernel: [16836.068000] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.
Apr  5 20:29:44 MTOLEDOB gconfd (mario-5253): SIGHUP received, reloading all databases
Apr  5 20:29:44 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr  5 20:29:44 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readwrite:/home/mario/.gconf" to a writable configuration source at position 1
Apr  5 20:29:44 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr  5 20:29:44 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Apr  5 20:29:44 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Apr  5 20:31:14 MTOLEDOB gconfd (mario-5253): SIGHUP received, reloading all databases
Apr  5 20:31:15 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr  5 20:31:15 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readwrite:/home/mario/.gconf" to a writable configuration source at position 1
Apr  5 20:31:15 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr  5 20:31:15 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Apr  5 20:31:15 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Apr  5 20:31:44 MTOLEDOB gconfd (mario-5253): SIGHUP received, reloading all databases
Apr  5 20:31:45 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr  5 20:31:45 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readwrite:/home/mario/.gconf" to a writable configuration source at position 1
Apr  5 20:31:45 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr  5 20:31:45 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Apr  5 20:31:45 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Apr  5 20:31:57 MTOLEDOB NetworkManager: <WARNING>^I nm_signal_handler (): Caught signal 15, shutting down normally. 
Apr  5 20:31:57 MTOLEDOB NetworkManager: <information>^ICaught terminiation signal 
Apr  5 20:31:57 MTOLEDOB NetworkManager: <debug info>^I[1207449117.831080] nm_print_open_socks (): Open Sockets List: 
Apr  5 20:31:57 MTOLEDOB NetworkManager: <debug info>^I[1207449117.831116] nm_print_open_socks (): Open Sockets List Done. 
Apr  5 20:31:57 MTOLEDOB NetworkManager: <information>^IDeactivating device eth1. 
Apr  5 20:31:58 MTOLEDOB NetworkManager: <information>^IDeactivating device eth0. 
Apr  5 20:31:59 MTOLEDOB NetworkManager: <info>  starting... 
Apr  5 20:31:59 MTOLEDOB NetworkManager: <info>  eth1: Device is fully-supported using driver 'ipw2100'. 
Apr  5 20:31:59 MTOLEDOB NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Apr  5 20:31:59 MTOLEDOB NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Apr  5 20:31:59 MTOLEDOB NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Apr  5 20:31:59 MTOLEDOB NetworkManager: <info>  Deactivating device eth1. 
Apr  5 20:31:59 MTOLEDOB NetworkManager: <info>  eth0: Device is fully-supported using driver 'tg3'. 
Apr  5 20:31:59 MTOLEDOB NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Apr  5 20:31:59 MTOLEDOB NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Apr  5 20:31:59 MTOLEDOB NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Apr  5 20:31:59 MTOLEDOB NetworkManager: <info>  Deactivating device eth0. 
Apr  5 20:31:59 MTOLEDOB NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Apr  5 20:31:59 MTOLEDOB NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Apr  5 20:31:59 MTOLEDOB dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Apr  5 20:31:59 MTOLEDOB NetworkManager: <info>  Will activate connection 'eth0'. 
Apr  5 20:31:59 MTOLEDOB NetworkManager: <info>  Device eth0 activation scheduled... 
Apr  5 20:31:59 MTOLEDOB NetworkManager: <info>  Activation (eth0) started... 
Apr  5 20:31:59 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr  5 20:31:59 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Apr  5 20:31:59 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Apr  5 20:31:59 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Apr  5 20:31:59 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Apr  5 20:31:59 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Apr  5 20:31:59 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr  5 20:31:59 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Apr  5 20:31:59 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Apr  5 20:32:00 MTOLEDOB NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Apr  5 20:32:01 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Apr  5 20:32:01 MTOLEDOB NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Apr  5 20:32:03 MTOLEDOB NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Apr  5 20:32:07 MTOLEDOB dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Apr  5 20:32:07 MTOLEDOB dhclient: DHCPACK from 192.168.0.1
Apr  5 20:32:08 MTOLEDOB NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface eth0 
Apr  5 20:32:08 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Apr  5 20:32:08 MTOLEDOB dhclient: bound to 192.168.0.4 -- renewal in 1639 seconds.
Apr  5 20:32:08 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Apr  5 20:32:08 MTOLEDOB dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Apr  5 20:32:08 MTOLEDOB dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Apr  5 20:32:08 MTOLEDOB dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Apr  5 20:32:08 MTOLEDOB dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Apr  5 20:32:08 MTOLEDOB NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Apr  5 20:32:08 MTOLEDOB NetworkManager: <info>    address 192.168.0.4 
Apr  5 20:32:08 MTOLEDOB NetworkManager: <info>    netmask 255.255.255.0 
Apr  5 20:32:08 MTOLEDOB NetworkManager: <info>    broadcast 192.168.0.255 
Apr  5 20:32:08 MTOLEDOB NetworkManager: <info>    gateway 192.168.0.1 
Apr  5 20:32:08 MTOLEDOB NetworkManager: <info>    nameserver 192.168.0.1 
Apr  5 20:32:08 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Apr  5 20:32:08 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Apr  5 20:32:08 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Apr  5 20:32:09 MTOLEDOB NetworkManager: <info>  Old device 'eth0' activating, won't change. 
Apr  5 20:32:09 MTOLEDOB NetworkManager: <info>  Clearing nscd hosts cache. 
Apr  5 20:32:09 MTOLEDOB NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Apr  5 20:32:10 MTOLEDOB NetworkManager: <info>  Activation (eth0) successful, device activated. 
Apr  5 20:32:10 MTOLEDOB NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Apr  5 20:32:10 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Apr  5 20:32:11 MTOLEDOB ntpdate[10095]: no servers can be used, exiting
Apr  5 20:32:20 MTOLEDOB kernel: [17007.964000] eth0: no IPv6 routers present
Apr  5 20:32:32 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Apr  5 20:32:40 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Apr  5 20:32:45 MTOLEDOB gconfd (mario-5253): SIGHUP received, reloading all databases
Apr  5 20:32:45 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr  5 20:32:45 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readwrite:/home/mario/.gconf" to a writable configuration source at position 1
Apr  5 20:32:45 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr  5 20:32:45 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Apr  5 20:32:45 MTOLEDOB gconfd (mario-5253): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Apr  5 20:32:49 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Apr  5 20:33:00 MTOLEDOB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Apr  5 20:33:03 MTOLEDOB dhclient: No DHCPOFFERS received.
Apr  5 20:33:03 MTOLEDOB dhclient: Trying recorded lease 192.168.1.100
Apr  5 20:33:03 MTOLEDOB avahi-autoipd(eth1)[5445]: client: RTNETLINK answers: Cannot assign requested address
Apr  5 20:33:03 MTOLEDOB avahi-autoipd(eth1)[5445]: Script execution failed with return value 2
Apr  5 20:33:06 MTOLEDOB dhclient: No working leases in persistent database - sleeping.
Apr  5 20:36:30 MTOLEDOB gconfd (mario-5253): Received signal 15, shutting down cleanly
Apr  5 20:36:30 MTOLEDOB gconfd (mario-5253): Exiting
Apr  5 20:36:33 MTOLEDOB kernel: [17260.624000] mtrr: no MTRR for e8000000,2000000 found
Apr  5 20:36:38 MTOLEDOB exiting on signal 15
Apr  5 20:39:33 MTOLEDOB syslogd 1.4.1#21ubuntu3: restart.
Apr  5 20:39:34 MTOLEDOB kernel: Inspecting /boot/System.map-2.6.22-14-generic
Apr  5 20:39:34 MTOLEDOB kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Apr  5 20:39:34 MTOLEDOB kernel: Symbols match kernel version 2.6.22.
Apr  5 20:39:34 MTOLEDOB kernel: No module symbols loaded - kernel modules not enabled. 
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000] BIOS-provided physical RAM map:
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffae000 (usable)
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 000000001ffae000 - 0000000020000000 (reserved)
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fee00000 (reserved)
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000] 0MB HIGHMEM available.
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000] 511MB LOWMEM available.
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000] Entering add_active_range(0, 0, 130990) 0 entries of 256 used
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000] Zone PFN ranges:
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000]   DMA             0 ->     4096
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000]   Normal       4096 ->   130990
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000]   HighMem    130990 ->   130990
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000]     0:        0 ->   130990
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000] On node 0 totalpages: 130990
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000]   Normal zone: 991 pages used for memmap
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000]   Normal zone: 125903 pages, LIFO batch:31
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000] DMI 2.3 present.
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FDF00 checksum 0
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000] ACPI: RSDP 000FDF00, 0014 (r0 DELL  )
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000] ACPI: RSDT 1FFF0000, 002C (r1 DELL    CPi R   27D5011A ASL        61)
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000] ACPI: FACP 1FFF0400, 0074 (r1 DELL    CPi R   27D5011A ASL        61)
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000] ACPI: DSDT 1FFF0C00, 2E1A (r1 INT430 SYSFexxx     1001 MSFT  100000E)
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000] ACPI: FACS 1FFFF800, 0040
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000] ACPI: ASF! 1FFF0800, 005B (r16 DELL    CPi R   27D5011A ASL        61)
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:deda0000)
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000] Built 1 zonelists.  Total pages: 129967
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000] Kernel command line: root=UUID=241da2db-0e86-4d13-ba31-7e747e81c264 ro quiet splash
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000] mapped APIC to ffffd000 (0140d000)
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000] Initializing CPU#0
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
Apr  5 20:39:34 MTOLEDOB kernel: [    0.000000] Detected 1398.847 MHz processor.
Apr  5 20:39:34 MTOLEDOB kernel: [   22.268356] Console: colour VGA+ 80x25
Apr  5 20:39:34 MTOLEDOB kernel: [   22.268665] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr  5 20:39:34 MTOLEDOB kernel: [   22.268987] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr  5 20:39:34 MTOLEDOB kernel: [   22.286750] Memory: 506636k/523960k available (2015k kernel code, 16752k reserved, 915k data, 364k init, 0k highmem)
Apr  5 20:39:34 MTOLEDOB kernel: [   22.286763] virtual kernel memory layout:
Apr  5 20:39:34 MTOLEDOB kernel: [   22.286765]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Apr  5 20:39:34 MTOLEDOB kernel: [   22.286767]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr  5 20:39:34 MTOLEDOB kernel: [   22.286768]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
Apr  5 20:39:34 MTOLEDOB kernel: [   22.286770]     lowmem  : 0xc0000000 - 0xdffae000   ( 511 MB)
Apr  5 20:39:34 MTOLEDOB kernel: [   22.286772]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Apr  5 20:39:34 MTOLEDOB kernel: [   22.286774]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
Apr  5 20:39:34 MTOLEDOB kernel: [   22.286775]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
Apr  5 20:39:34 MTOLEDOB kernel: [   22.286780] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr  5 20:39:34 MTOLEDOB kernel: [   22.286828] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Apr  5 20:39:34 MTOLEDOB kernel: [   22.366848] Calibrating delay using timer specific routine.. 2799.71 BogoMIPS (lpj=5599421)
Apr  5 20:39:34 MTOLEDOB kernel: [   22.366879] Security Framework v1.0.0 initialized
Apr  5 20:39:34 MTOLEDOB kernel: [   22.366888] SELinux:  Disabled at boot.
Apr  5 20:39:34 MTOLEDOB kernel: [   22.366907] Mount-cache hash table entries: 512
Apr  5 20:39:34 MTOLEDOB kernel: [   22.367062] CPU: After generic identify, caps: a7e9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
Apr  5 20:39:34 MTOLEDOB kernel: [   22.367077] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr  5 20:39:34 MTOLEDOB kernel: [   22.367081] CPU: L2 cache: 1024K
Apr  5 20:39:34 MTOLEDOB kernel: [   22.367084] CPU: After all inits, caps: a7e9f9bf 00000000 00000000 00002040 00000180 00000000 00000000
Apr  5 20:39:34 MTOLEDOB kernel: [   22.367096] Compat vDSO mapped to ffffe000.
Apr  5 20:39:34 MTOLEDOB kernel: [   22.367109] Checking 'hlt' instruction... OK.
Apr  5 20:39:34 MTOLEDOB kernel: [   22.382956] SMP alternatives: switching to UP code
Apr  5 20:39:34 MTOLEDOB kernel: [   22.383137] Freeing SMP alternatives: 11k freed
Apr  5 20:39:34 MTOLEDOB kernel: [   22.383443] Early unpacking initramfs... done
Apr  5 20:39:34 MTOLEDOB kernel: [   22.827825] ACPI: Core revision 20070126
Apr  5 20:39:34 MTOLEDOB kernel: [   22.827901] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Apr  5 20:39:34 MTOLEDOB kernel: [   22.829560] ACPI: setting ELCR to 0200 (from 0800)
Apr  5 20:39:34 MTOLEDOB kernel: [   22.831822] CPU0: Intel(R) Pentium(R) M processor 1400MHz stepping 05
Apr  5 20:39:34 MTOLEDOB kernel: [   22.831829] SMP motherboard not detected.
Apr  5 20:39:34 MTOLEDOB kernel: [   22.831832] Local APIC not detected. Using dummy APIC emulation.
Apr  5 20:39:34 MTOLEDOB kernel: [   22.831873] Brought up 1 CPUs
Apr  5 20:39:34 MTOLEDOB kernel: [   22.832011] Booting paravirtualized kernel on bare hardware
Apr  5 20:39:34 MTOLEDOB kernel: [   22.832077] Time: 20:37:11  Date: 03/05/108
Apr  5 20:39:34 MTOLEDOB kernel: [   22.832105] NET: Registered protocol family 16
Apr  5 20:39:34 MTOLEDOB kernel: [   22.832204] EISA bus registered
Apr  5 20:39:34 MTOLEDOB kernel: [   22.832217] ACPI: bus type pci registered
Apr  5 20:39:34 MTOLEDOB kernel: [   22.865895] PCI: PCI BIOS revision 2.10 entry at 0xfc96e, last bus=2
Apr  5 20:39:34 MTOLEDOB kernel: [   22.865899] PCI: Using configuration type 1
Apr  5 20:39:34 MTOLEDOB kernel: [   22.865901] Setting up standard PCI resources
Apr  5 20:39:34 MTOLEDOB kernel: [   22.868075] ACPI: EC: Look up EC in DSDT
Apr  5 20:39:34 MTOLEDOB kernel: [   22.875122] ACPI: Interpreter enabled
Apr  5 20:39:34 MTOLEDOB kernel: [   22.875126] ACPI: (supports S0 S1 S3 S4 S5)
Apr  5 20:39:34 MTOLEDOB kernel: [   22.875147] ACPI: Using PIC for interrupt routing
Apr  5 20:39:34 MTOLEDOB kernel: [   22.888262] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr  5 20:39:34 MTOLEDOB kernel: [   22.888287] PCI: Probing PCI hardware (bus 00)
Apr  5 20:39:34 MTOLEDOB kernel: [   22.888671] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
Apr  5 20:39:34 MTOLEDOB kernel: [   22.888676] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
Apr  5 20:39:34 MTOLEDOB kernel: [   22.889138] PCI: Transparent bridge - 0000:00:1e.0
Apr  5 20:39:34 MTOLEDOB kernel: [   22.889256] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr  5 20:39:34 MTOLEDOB kernel: [   22.889637] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Apr  5 20:39:34 MTOLEDOB kernel: [   22.889729] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Apr  5 20:39:34 MTOLEDOB kernel: [   22.904320] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
Apr  5 20:39:34 MTOLEDOB kernel: [   22.904436] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
Apr  5 20:39:34 MTOLEDOB kernel: [   22.904548] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
Apr  5 20:39:34 MTOLEDOB kernel: [   22.904661] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
Apr  5 20:39:34 MTOLEDOB kernel: [   22.904759] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Apr  5 20:39:34 MTOLEDOB kernel: [   22.904876] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Apr  5 20:39:34 MTOLEDOB kernel: [   22.904984] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr  5 20:39:34 MTOLEDOB kernel: [   22.904996] pnp: PnP ACPI init
Apr  5 20:39:34 MTOLEDOB kernel: [   22.905010] ACPI: bus type pnp registered
Apr  5 20:39:34 MTOLEDOB kernel: [   22.932904] pnp: PnP ACPI: found 13 devices
Apr  5 20:39:34 MTOLEDOB kernel: [   22.932907] ACPI: ACPI bus type pnp unregistered
Apr  5 20:39:34 MTOLEDOB kernel: [   22.932913] PnPBIOS: Disabled by ACPI PNP
Apr  5 20:39:34 MTOLEDOB kernel: [   22.932971] PCI: Using ACPI for IRQ routing
Apr  5 20:39:34 MTOLEDOB kernel: [   22.932975] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr  5 20:39:34 MTOLEDOB kernel: [   22.939406] NET: Registered protocol family 8
Apr  5 20:39:34 MTOLEDOB kernel: [   22.939409] NET: Registered protocol family 20
Apr  5 20:39:34 MTOLEDOB kernel: [   22.939473] pnp: 00:00: iomem range 0x0-0x9fbff could not be reserved
Apr  5 20:39:34 MTOLEDOB kernel: [   22.939478] pnp: 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
Apr  5 20:39:34 MTOLEDOB kernel: [   22.939482] pnp: 00:00: iomem range 0xc0000-0xcffff could not be reserved
Apr  5 20:39:34 MTOLEDOB kernel: [   22.939486] pnp: 00:00: iomem range 0xe0000-0xfffff could not be reserved
Apr  5 20:39:34 MTOLEDOB kernel: [   22.939493] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
Apr  5 20:39:34 MTOLEDOB kernel: [   22.939496] pnp: 00:02: ioport range 0x800-0x805 has been reserved
Apr  5 20:39:34 MTOLEDOB kernel: [   22.939500] pnp: 00:02: ioport range 0x808-0x80f has been reserved
Apr  5 20:39:34 MTOLEDOB kernel: [   22.939506] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
Apr  5 20:39:34 MTOLEDOB kernel: [   22.939510] pnp: 00:03: ioport range 0x806-0x807 has been reserved
Apr  5 20:39:34 MTOLEDOB kernel: [   22.939514] pnp: 00:03: ioport range 0x810-0x85f has been reserved
Apr  5 20:39:34 MTOLEDOB kernel: [   22.939517] pnp: 00:03: ioport range 0x860-0x87f has been reserved
Apr  5 20:39:34 MTOLEDOB kernel: [   22.939521] pnp: 00:03: ioport range 0x880-0x8bf has been reserved
Apr  5 20:39:34 MTOLEDOB kernel: [   22.939525] pnp: 00:03: ioport range 0x8c0-0x8df has been reserved
Apr  5 20:39:34 MTOLEDOB kernel: [   22.939532] pnp: 00:08: ioport range 0x900-0x97f has been reserved
Apr  5 20:39:34 MTOLEDOB kernel: [   22.942842] Time: tsc clocksource has been installed.
Apr  5 20:39:34 MTOLEDOB kernel: [   22.969861] PCI: Bridge: 0000:00:01.0
Apr  5 20:39:34 MTOLEDOB kernel: [   22.969864]   IO window: c000-cfff
Apr  5 20:39:34 MTOLEDOB kernel: [   22.969869]   MEM window: fc000000-fdffffff
Apr  5 20:39:34 MTOLEDOB kernel: [   22.969873]   PREFETCH window: e8000000-efffffff
Apr  5 20:39:34 MTOLEDOB kernel: [   22.969887] PCI: Bus 3, cardbus bridge: 0000:02:01.0
Apr  5 20:39:34 MTOLEDOB kernel: [   22.969890]   IO window: 0000d000-0000d0ff
Apr  5 20:39:34 MTOLEDOB kernel: [   22.969895]   IO window: 0000d400-0000d4ff
Apr  5 20:39:34 MTOLEDOB kernel: [   22.969900]   PREFETCH window: 30000000-33ffffff
Apr  5 20:39:34 MTOLEDOB kernel: [   22.969905]   MEM window: 3c000000-3fffffff
Apr  5 20:39:34 MTOLEDOB kernel: [   22.969909] PCI: Bus 7, cardbus bridge: 0000:02:01.1
Apr  5 20:39:34 MTOLEDOB kernel: [   22.969912]   IO window: 0000d800-0000d8ff
Apr  5 20:39:34 MTOLEDOB kernel: [   22.969916]   IO window: 0000dc00-0000dcff
Apr  5 20:39:34 MTOLEDOB kernel: [   22.969921]   PREFETCH window: 34000000-37ffffff
Apr  5 20:39:34 MTOLEDOB kernel: [   22.969926]   MEM window: 40000000-43ffffff
Apr  5 20:39:34 MTOLEDOB kernel: [   22.969930] PCI: Bridge: 0000:00:1e.0
Apr  5 20:39:34 MTOLEDOB kernel: [   22.969933]   IO window: d000-efff
Apr  5 20:39:34 MTOLEDOB kernel: [   22.969939]   MEM window: f6000000-fbffffff
Apr  5 20:39:34 MTOLEDOB kernel: [   22.969944]   PREFETCH window: 30000000-37ffffff
Apr  5 20:39:34 MTOLEDOB kernel: [   22.969960] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Apr  5 20:39:34 MTOLEDOB kernel: [   22.969974] PCI: Enabling device 0000:02:01.0 (0000 -> 0003)
Apr  5 20:39:34 MTOLEDOB kernel: [   22.970148] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Apr  5 20:39:34 MTOLEDOB kernel: [   22.970152] PCI: setting IRQ 11 as level-triggered
Apr  5 20:39:34 MTOLEDOB kernel: [   22.970156] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:39:34 MTOLEDOB kernel: [   22.970174] PCI: Enabling device 0000:02:01.1 (0000 -> 0003)
Apr  5 20:39:34 MTOLEDOB kernel: [   22.970178] ACPI: PCI Interrupt 0000:02:01.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:39:34 MTOLEDOB kernel: [   22.970198] NET: Registered protocol family 2
Apr  5 20:39:34 MTOLEDOB kernel: [   23.006884] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Apr  5 20:39:34 MTOLEDOB kernel: [   23.006934] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
Apr  5 20:39:34 MTOLEDOB kernel: [   23.007147] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
Apr  5 20:39:34 MTOLEDOB kernel: [   23.007286] TCP: Hash tables configured (established 16384 bind 16384)
Apr  5 20:39:34 MTOLEDOB kernel: [   23.007290] TCP reno registered
Apr  5 20:39:34 MTOLEDOB kernel: [   23.019005] checking if image is initramfs... it is
Apr  5 20:39:34 MTOLEDOB kernel: [   23.470863] Switched to high resolution mode on CPU 0
Apr  5 20:39:34 MTOLEDOB kernel: [   23.896499] Freeing initrd memory: 8373k freed
Apr  5 20:39:34 MTOLEDOB kernel: [   23.896921] audit: initializing netlink socket (disabled)
Apr  5 20:39:34 MTOLEDOB kernel: [   23.896942] audit(1207427831.160:1): initialized
Apr  5 20:39:34 MTOLEDOB kernel: [   23.899574] VFS: Disk quotas dquot_6.5.1
Apr  5 20:39:34 MTOLEDOB kernel: [   23.899648] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr  5 20:39:34 MTOLEDOB kernel: [   23.899773] io scheduler noop registered
Apr  5 20:39:34 MTOLEDOB kernel: [   23.899776] io scheduler anticipatory registered
Apr  5 20:39:34 MTOLEDOB kernel: [   23.899778] io scheduler deadline registered
Apr  5 20:39:34 MTOLEDOB kernel: [   23.899803] io scheduler cfq registered (default)
Apr  5 20:39:34 MTOLEDOB kernel: [   23.899884] Boot video device is 0000:01:00.0
Apr  5 20:39:34 MTOLEDOB kernel: [   23.900084] isapnp: Scanning for PnP cards...
Apr  5 20:39:34 MTOLEDOB kernel: [   24.253006] isapnp: No Plug & Play device found
Apr  5 20:39:34 MTOLEDOB kernel: [   24.290081] Real Time Clock Driver v1.12ac
Apr  5 20:39:34 MTOLEDOB kernel: [   24.290225] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr  5 20:39:34 MTOLEDOB kernel: [   24.290324] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr  5 20:39:34 MTOLEDOB kernel: [   24.291338] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr  5 20:39:34 MTOLEDOB kernel: [   24.291812] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
Apr  5 20:39:34 MTOLEDOB kernel: [   24.291816] PCI: setting IRQ 5 as level-triggered
Apr  5 20:39:34 MTOLEDOB kernel: [   24.291821] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Apr  5 20:39:34 MTOLEDOB kernel: [   24.291831] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
Apr  5 20:39:34 MTOLEDOB kernel: [   24.292489] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr  5 20:39:34 MTOLEDOB kernel: [   24.292773] input: Macintosh mouse button emulation as /class/input/input0
Apr  5 20:39:34 MTOLEDOB kernel: [   24.292863] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Apr  5 20:39:34 MTOLEDOB kernel: [   24.298654] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr  5 20:39:34 MTOLEDOB kernel: [   24.298660] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr  5 20:39:34 MTOLEDOB kernel: [   24.298877] mice: PS/2 mouse device common for all mice
Apr  5 20:39:34 MTOLEDOB kernel: [   24.299002] EISA: Probing bus 0 at eisa.0
Apr  5 20:39:34 MTOLEDOB kernel: [   24.299030] EISA: Detected 0 cards.
Apr  5 20:39:34 MTOLEDOB kernel: [   24.299159] TCP cubic registered
Apr  5 20:39:34 MTOLEDOB kernel: [   24.299184] NET: Registered protocol family 1
Apr  5 20:39:34 MTOLEDOB kernel: [   24.299219] Using IPI No-Shortcut mode
Apr  5 20:39:34 MTOLEDOB kernel: [   24.299436]   Magic number: 4:66:649
Apr  5 20:39:34 MTOLEDOB kernel: [   24.299526]   hash matches device ptyde
Apr  5 20:39:34 MTOLEDOB kernel: [   24.299940] Freeing unused kernel memory: 364k freed
Apr  5 20:39:34 MTOLEDOB kernel: [   24.334783] input: AT Translated Set 2 keyboard as /class/input/input1
Apr  5 20:39:34 MTOLEDOB kernel: [   25.518991] AppArmor: AppArmor initialized<5>audit(1207427833.160:2):  type=1505 info="AppArmor initialized" pid=1205
Apr  5 20:39:34 MTOLEDOB kernel: [   25.529382] fuse init (API version 7.8)
Apr  5 20:39:34 MTOLEDOB kernel: [   25.534910] Failure registering capabilities with primary security module.
Apr  5 20:39:34 MTOLEDOB kernel: [   25.555252] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
Apr  5 20:39:34 MTOLEDOB kernel: [   25.555260] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr  5 20:39:34 MTOLEDOB kernel: [   25.559210] ACPI: Thermal Zone [THM] (50 C)
Apr  5 20:39:34 MTOLEDOB kernel: [   26.022315] usbcore: registered new interface driver usbfs
Apr  5 20:39:34 MTOLEDOB kernel: [   26.022345] usbcore: registered new interface driver hub
Apr  5 20:39:34 MTOLEDOB kernel: [   26.022374] usbcore: registered new device driver usb
Apr  5 20:39:34 MTOLEDOB kernel: [   26.024046] USB Universal Host Controller Interface driver v3.0
Apr  5 20:39:34 MTOLEDOB kernel: [   26.024377] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
Apr  5 20:39:34 MTOLEDOB kernel: [   26.024381] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:39:34 MTOLEDOB kernel: [   26.024396] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Apr  5 20:39:34 MTOLEDOB kernel: [   26.024401] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr  5 20:39:34 MTOLEDOB kernel: [   26.024642] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Apr  5 20:39:34 MTOLEDOB kernel: [   26.024669] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
Apr  5 20:39:34 MTOLEDOB kernel: [   26.024820] usb usb1: configuration #1 chosen from 1 choice
Apr  5 20:39:34 MTOLEDOB kernel: [   26.024852] hub 1-0:1.0: USB hub found
Apr  5 20:39:34 MTOLEDOB kernel: [   26.024858] hub 1-0:1.0: 2 ports detected
Apr  5 20:39:34 MTOLEDOB kernel: [   26.126735] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:39:34 MTOLEDOB kernel: [   26.126753] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Apr  5 20:39:34 MTOLEDOB kernel: [   26.126758] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr  5 20:39:34 MTOLEDOB kernel: [   26.126787] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Apr  5 20:39:34 MTOLEDOB kernel: [   26.126814] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
Apr  5 20:39:34 MTOLEDOB kernel: [   26.126947] usb usb2: configuration #1 chosen from 1 choice
Apr  5 20:39:34 MTOLEDOB kernel: [   26.126980] hub 2-0:1.0: USB hub found
Apr  5 20:39:34 MTOLEDOB kernel: [   26.126988] hub 2-0:1.0: 2 ports detected
Apr  5 20:39:34 MTOLEDOB kernel: [   26.177726] SCSI subsystem initialized
Apr  5 20:39:34 MTOLEDOB kernel: [   26.190202] libata version 2.21 loaded.
Apr  5 20:39:34 MTOLEDOB kernel: [   26.231000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
Apr  5 20:39:34 MTOLEDOB kernel: [   26.231006] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:39:34 MTOLEDOB kernel: [   26.231021] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Apr  5 20:39:34 MTOLEDOB kernel: [   26.231026] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr  5 20:39:34 MTOLEDOB kernel: [   26.231059] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Apr  5 20:39:34 MTOLEDOB kernel: [   26.231086] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
Apr  5 20:39:34 MTOLEDOB kernel: [   26.231221] usb usb3: configuration #1 chosen from 1 choice
Apr  5 20:39:34 MTOLEDOB kernel: [   26.231255] hub 3-0:1.0: USB hub found
Apr  5 20:39:34 MTOLEDOB kernel: [   26.231263] hub 3-0:1.0: 2 ports detected
Apr  5 20:39:34 MTOLEDOB kernel: [   26.335192] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
Apr  5 20:39:34 MTOLEDOB kernel: [   26.335199] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:39:34 MTOLEDOB kernel: [   26.335215] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Apr  5 20:39:34 MTOLEDOB kernel: [   26.335220] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr  5 20:39:34 MTOLEDOB kernel: [   26.335253] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
Apr  5 20:39:34 MTOLEDOB kernel: [   26.335293] ehci_hcd 0000:00:1d.7: debug port 1
Apr  5 20:39:34 MTOLEDOB kernel: [   26.335301] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Apr  5 20:39:34 MTOLEDOB kernel: [   26.335310] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf4fffc00
Apr  5 20:39:34 MTOLEDOB kernel: [   26.339232] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Apr  5 20:39:34 MTOLEDOB kernel: [   26.339338] usb usb4: configuration #1 chosen from 1 choice
Apr  5 20:39:34 MTOLEDOB kernel: [   26.339372] hub 4-0:1.0: USB hub found
Apr  5 20:39:34 MTOLEDOB kernel: [   26.339381] hub 4-0:1.0: 6 ports detected
Apr  5 20:39:34 MTOLEDOB kernel: [   26.443455] tg3.c:v3.77 (May 31, 2007)
Apr  5 20:39:34 MTOLEDOB kernel: [   26.443482] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:39:34 MTOLEDOB kernel: [   26.483859] eth0: Tigon3 [partno(BCM95705A50) rev 3001 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000Base-T Ethernet 00:11:43:53:d5:22
Apr  5 20:39:34 MTOLEDOB kernel: [   26.483870] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
Apr  5 20:39:34 MTOLEDOB kernel: [   26.483874] eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
Apr  5 20:39:34 MTOLEDOB kernel: [   26.484477] ata_piix 0000:00:1f.1: version 2.11
Apr  5 20:39:34 MTOLEDOB kernel: [   26.484492] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
Apr  5 20:39:34 MTOLEDOB kernel: [   26.484503] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:39:34 MTOLEDOB kernel: [   26.484546] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Apr  5 20:39:34 MTOLEDOB kernel: [   26.484653] scsi0 : ata_piix
Apr  5 20:39:34 MTOLEDOB kernel: [   26.484713] scsi1 : ata_piix
Apr  5 20:39:34 MTOLEDOB kernel: [   26.485811] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
Apr  5 20:39:34 MTOLEDOB kernel: [   26.485816] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
Apr  5 20:39:34 MTOLEDOB kernel: [    4.304000] Marking TSC unstable due to: possible TSC halt in C2.
Apr  5 20:39:34 MTOLEDOB kernel: [    4.308000] Time: acpi_pm clocksource has been installed.
Apr  5 20:39:34 MTOLEDOB kernel: [    4.364000] ata1.00: ATA-6: ST980815A, 3.ALD, max UDMA/100
Apr  5 20:39:34 MTOLEDOB kernel: [    4.364000] ata1.00: 156301488 sectors, multi 8: LBA48 
Apr  5 20:39:34 MTOLEDOB kernel: [    4.380000] ata1.00: configured for UDMA/100
Apr  5 20:39:34 MTOLEDOB kernel: [    4.700000] ata2.00: ATAPI: HL-DT-STCD-RW/DVD-ROM GCC-4241N, A101, max UDMA/33
Apr  5 20:39:34 MTOLEDOB kernel: [    4.872000] ata2.00: configured for UDMA/33
Apr  5 20:39:34 MTOLEDOB kernel: [    4.872000] scsi 0:0:0:0: Direct-Access     ATA      ST980815A        3.AL PQ: 0 ANSI: 5
Apr  5 20:39:34 MTOLEDOB kernel: [    4.876000] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4241N A101 PQ: 0 ANSI: 5
Apr  5 20:39:34 MTOLEDOB kernel: [    4.900000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr  5 20:39:34 MTOLEDOB kernel: [    4.900000] sd 0:0:0:0: [sda] Write Protect is off
Apr  5 20:39:34 MTOLEDOB kernel: [    4.900000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr  5 20:39:34 MTOLEDOB kernel: [    4.900000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  5 20:39:34 MTOLEDOB kernel: [    4.900000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr  5 20:39:34 MTOLEDOB kernel: [    4.900000] sd 0:0:0:0: [sda] Write Protect is off
Apr  5 20:39:34 MTOLEDOB kernel: [    4.900000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr  5 20:39:34 MTOLEDOB kernel: [    4.900000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  5 20:39:34 MTOLEDOB kernel: [    4.900000]  sda: sda1 sda2 sda3 < sda5 >
Apr  5 20:39:34 MTOLEDOB kernel: [    4.984000] sd 0:0:0:0: [sda] Attached SCSI disk
Apr  5 20:39:34 MTOLEDOB kernel: [    4.992000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr  5 20:39:34 MTOLEDOB kernel: [    4.992000] sr 1:0:0:0: Attached scsi generic sg1 type 5
Apr  5 20:39:34 MTOLEDOB kernel: [    5.020000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Apr  5 20:39:34 MTOLEDOB kernel: [    5.020000] Uniform CD-ROM driver Revision: 3.20
Apr  5 20:39:34 MTOLEDOB kernel: [    5.020000] sr 1:0:0:0: Attached scsi CD-ROM sr0
Apr  5 20:39:34 MTOLEDOB kernel: [    5.228000] Attempting manual resume
Apr  5 20:39:34 MTOLEDOB kernel: [    5.228000] swsusp: Resume From Partition 8:5
Apr  5 20:39:34 MTOLEDOB kernel: [    5.228000] PM: Checking swsusp image.
Apr  5 20:39:34 MTOLEDOB kernel: [    5.228000] PM: Resume from disk failed.
Apr  5 20:39:34 MTOLEDOB kernel: [    5.272000] kjournald starting.  Commit interval 5 seconds
Apr  5 20:39:34 MTOLEDOB kernel: [    5.272000] EXT3-fs: mounted filesystem with ordered data mode.
Apr  5 20:39:34 MTOLEDOB kernel: [   16.008000] Linux agpgart interface v0.102 (c) Dave Jones
Apr  5 20:39:34 MTOLEDOB kernel: [   16.072000] agpgart: Detected an Intel 855PM Chipset.
Apr  5 20:39:34 MTOLEDOB kernel: [   16.080000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr  5 20:39:34 MTOLEDOB kernel: [   16.080000] agpgart: AGP aperture is 128M @ 0xe0000000
Apr  5 20:39:34 MTOLEDOB kernel: [   16.084000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr  5 20:39:34 MTOLEDOB kernel: [   17.076000] iTCO_vendor_support: vendor-support=0
Apr  5 20:39:34 MTOLEDOB kernel: [   17.208000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
Apr  5 20:39:34 MTOLEDOB kernel: [   17.208000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x0860)
Apr  5 20:39:34 MTOLEDOB kernel: [   17.208000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Apr  5 20:39:34 MTOLEDOB kernel: [   17.384000] Yenta: CardBus bridge found at 0000:02:01.0 [1028:011d]
Apr  5 20:39:34 MTOLEDOB kernel: [   17.384000] Yenta O2: res at 0x94/0xD4: 00/ea
Apr  5 20:39:34 MTOLEDOB kernel: [   17.384000] Yenta O2: enabling read prefetch/write burst
Apr  5 20:39:34 MTOLEDOB kernel: [   17.388000] ieee80211_crypt: registered algorithm 'NULL'
Apr  5 20:39:34 MTOLEDOB kernel: [   17.388000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Apr  5 20:39:34 MTOLEDOB kernel: [   17.392000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Apr  5 20:39:34 MTOLEDOB kernel: [   17.448000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
Apr  5 20:39:34 MTOLEDOB kernel: [   17.448000] ipw2100: Copyright(c) 2003-2006 Intel Corporation
Apr  5 20:39:34 MTOLEDOB kernel: [   17.448000] intel_rng: FWH not detected
Apr  5 20:39:34 MTOLEDOB kernel: [   17.512000] Yenta: ISA IRQ mask 0x0498, PCI irq 11
Apr  5 20:39:34 MTOLEDOB kernel: [   17.512000] Socket status: 30000006
Apr  5 20:39:34 MTOLEDOB kernel: [   17.512000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
Apr  5 20:39:34 MTOLEDOB kernel: [   17.512000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
Apr  5 20:39:34 MTOLEDOB kernel: [   17.512000] cs: IO port probe 0xd000-0xefff: clean.
Apr  5 20:39:34 MTOLEDOB kernel: [   17.512000] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
Apr  5 20:39:34 MTOLEDOB kernel: [   17.512000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x37ffffff
Apr  5 20:39:34 MTOLEDOB kernel: [   17.512000] Yenta: CardBus bridge found at 0000:02:01.1 [1028:011d]
Apr  5 20:39:34 MTOLEDOB kernel: [   17.640000] Yenta: ISA IRQ mask 0x0498, PCI irq 11
Apr  5 20:39:34 MTOLEDOB kernel: [   17.640000] Socket status: 30000410
Apr  5 20:39:34 MTOLEDOB kernel: [   17.640000] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
Apr  5 20:39:34 MTOLEDOB kernel: [   17.640000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
Apr  5 20:39:34 MTOLEDOB kernel: [   17.640000] cs: IO port probe 0xd000-0xefff: clean.
Apr  5 20:39:34 MTOLEDOB kernel: [   17.640000] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
Apr  5 20:39:34 MTOLEDOB kernel: [   17.640000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x37ffffff
Apr  5 20:39:34 MTOLEDOB kernel: [   17.640000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Apr  5 20:39:34 MTOLEDOB kernel: [   17.640000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
Apr  5 20:39:34 MTOLEDOB kernel: [   18.032000] input: DualPoint Stick as /class/input/input2
Apr  5 20:39:34 MTOLEDOB kernel: [   18.052000] input: AlpsPS/2 ALPS DualPoint TouchPad as /class/input/input3
Apr  5 20:39:34 MTOLEDOB kernel: [   18.060000] parport_pc 00:0c: reported by Plug and Play ACPI
Apr  5 20:39:34 MTOLEDOB kernel: [   18.060000] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Apr  5 20:39:34 MTOLEDOB kernel: [   18.060000] input: PC Speaker as /class/input/input4
Apr  5 20:39:34 MTOLEDOB kernel: [   18.276000] pccard: PCMCIA card inserted into slot 1
Apr  5 20:39:34 MTOLEDOB kernel: [   18.420000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Apr  5 20:39:34 MTOLEDOB kernel: [   18.420000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
Apr  5 20:39:34 MTOLEDOB kernel: [   18.428000] cs: memory probe 0xf6000000-0xfbffffff: excluding 0xf6000000-0xf65fffff 0xf6c00000-0xf71fffff 0xf7e00000-0xf83fffff 0xf9c00000-0xfa1fffff 0xfae00000-0xfb3fffff
Apr  5 20:39:34 MTOLEDOB kernel: [   18.440000] pcmcia: registering new device pcmcia1.0
Apr  5 20:39:34 MTOLEDOB kernel: [   18.496000] cs: IO port probe 0x100-0x3af: clean.
Apr  5 20:39:34 MTOLEDOB kernel: [   18.496000] cs: IO port probe 0x3e0-0x4ff: clean.
Apr  5 20:39:34 MTOLEDOB kernel: [   18.496000] cs: IO port probe 0x820-0x8ff: clean.
Apr  5 20:39:34 MTOLEDOB kernel: [   18.496000] cs: IO port probe 0xc00-0xcf7: clean.
Apr  5 20:39:34 MTOLEDOB kernel: [   18.500000] cs: IO port probe 0xa00-0xaff: clean.
Apr  5 20:39:34 MTOLEDOB kernel: [   18.500000] cs: IO port probe 0x100-0x3af: clean.
Apr  5 20:39:34 MTOLEDOB kernel: [   18.500000] cs: IO port probe 0x3e0-0x4ff: clean.
Apr  5 20:39:34 MTOLEDOB kernel: [   18.500000] cs: IO port probe 0x820-0x8ff: clean.
Apr  5 20:39:34 MTOLEDOB kernel: [   18.500000] cs: IO port probe 0xc00-0xcf7: clean.
Apr  5 20:39:34 MTOLEDOB kernel: [   18.500000] cs: IO port probe 0xa00-0xaff: clean.
Apr  5 20:39:34 MTOLEDOB kernel: [   19.248000] intel8x0_measure_ac97_clock: measured 55447 usecs
Apr  5 20:39:34 MTOLEDOB kernel: [   19.248000] intel8x0: clocking to 48000
Apr  5 20:39:34 MTOLEDOB kernel: [   20.220000] lp0: using parport0 (interrupt-driven).
Apr  5 20:39:34 MTOLEDOB kernel: [   20.260000] Adding 1510068k swap on /dev/sda5.  Priority:-1 extents:1 across:1510068k
Apr  5 20:39:34 MTOLEDOB kernel: [  139.336000] EXT3 FS on sda2, internal journal
Apr  5 20:39:34 MTOLEDOB kernel: [  141.816000] ACPI: AC Adapter [AC] (on-line)
Apr  5 20:39:34 MTOLEDOB kernel: [  141.876000] input: Lid Switch as /class/input/input5
Apr  5 20:39:34 MTOLEDOB kernel: [  141.880000] ACPI: Lid Switch [LID]
Apr  5 20:39:34 MTOLEDOB kernel: [  141.912000] input: Power Button (CM) as /class/input/input6
Apr  5 20:39:34 MTOLEDOB kernel: [  141.912000] ACPI: Power Button (CM) [PBTN]
Apr  5 20:39:34 MTOLEDOB kernel: [  141.956000] input: Sleep Button (CM) as /class/input/input7
Apr  5 20:39:34 MTOLEDOB kernel: [  141.956000] ACPI: Sleep Button (CM) [SBTN]
Apr  5 20:39:34 MTOLEDOB kernel: [  142.004000] ACPI: ACPI Dock Station Driver 
Apr  5 20:39:34 MTOLEDOB kernel: [  142.320000] ACPI: Battery Slot [BAT0] (battery present)
Apr  5 20:39:34 MTOLEDOB kernel: [  142.320000] ACPI: Battery Slot [BAT1] (battery absent)
Apr  5 20:39:34 MTOLEDOB kernel: [  142.364000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Apr  5 20:39:35 MTOLEDOB NetworkManager: <info>  starting... 
Apr  5 20:39:35 MTOLEDOB NetworkManager: <debug> [1207449575.824192] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_3340'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.183739] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_3341'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.184684] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_4c66'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.185327] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c2'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.185813] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.186288] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.186759] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c4'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.187258] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.187729] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.188227] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c7'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.188699] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.189167] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.189634] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24cd'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.190100] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.190568] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.191125] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.191602] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_165d'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.192072] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1217_7113'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.192542] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1217_7113_0'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.193011] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pcmcia__1__1'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.193479] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_1043'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.193945] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24cc'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.194435] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.194929] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.195421] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_scsi_device_lun0'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.195892] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_0'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.196358] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_0_scsi_device_lun0'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.196824] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.197288] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c6'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.197754] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_dock_0'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.198219] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.198683] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.199182] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.199648] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.200112] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.200574] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.201034] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.201494] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.201954] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.202413] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.202872] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.203343] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.203836] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.204302] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.204760] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.205241] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.205719] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.206180] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.206637] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.207114] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0401'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.207573] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.208031] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.208488] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.208946] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.209730] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.223092] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_11_43_53_d5_22'). 
Apr  5 20:39:36 MTOLEDOB kernel: [  145.432000] PM: Writing back config space on device 0000:02:00.0 at offset b (was 165d14e4, writing 865d1028)
Apr  5 20:39:36 MTOLEDOB kernel: [  145.432000] PM: Writing back config space on device 0000:02:00.0 at offset 3 (was 0, writing 2008)
Apr  5 20:39:36 MTOLEDOB kernel: [  145.432000] PM: Writing back config space on device 0000:02:00.0 at offset 2 (was 2000000, writing 2000001)
Apr  5 20:39:36 MTOLEDOB kernel: [  145.432000] PM: Writing back config space on device 0000:02:00.0 at offset 1 (was 2b00000, writing 2b00106)
Apr  5 20:39:36 MTOLEDOB NetworkManager: <info>  eth0: Device is fully-supported using driver 'tg3'. 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <info>  Deactivating device eth0. 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <debug> [1207449576.854835] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_0c_f1_1c_20_6b'). 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Apr  5 20:39:36 MTOLEDOB NetworkManager: <info>  eth1: Device is fully-supported using driver 'ipw2100'. 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <info>  Deactivating device eth1. 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.135751] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_scsi_device_lun0_scsi_generic'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.136421] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.136949] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_pcm_1'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.137432] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_pcm_0'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.137916] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_control__1'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.138454] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_pcm_0_0'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.138942] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_mixer__1'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.139448] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_0'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.139927] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_playback_0'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.140403] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_1'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.140878] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_2'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.141353] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_3'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.141827] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_playback_4'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.142302] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.142775] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.143362] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.143843] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.144317] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.144816] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.145295] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_3'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.145771] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.146265] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.146739] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.147228] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.147720] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.148193] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.148664] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST980815A_5LY1VWH9'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.149134] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_606C05936C0564DE'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.149624] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_241da2db_0e86_4d13_ba31_7e747e81c264'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.156040] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part3_size_1024'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.277269] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_aaabdd49_42ff_4b7f_ac15_b1a4f0ed1a87'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.418669] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT1'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.447632] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.448160] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.448631] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Apr  5 20:39:37 MTOLEDOB NetworkManager: <debug> [1207449577.453965] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_RW/DVD_GCC_4241N'). 
Apr  5 20:39:37 MTOLEDOB gdm[4927]: WARNING: Didn't understand `' (expected true or false) 
Apr  5 20:39:37 MTOLEDOB kernel: [  146.840000] ppdev: user-space parallel port driver
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Will activate connection 'eth0'. 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Device eth0 activation scheduled... 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) started... 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) failure scheduled... 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Apr  5 20:39:38 MTOLEDOB kernel: [  147.300000] tg3: eth0: Link is up at 100 Mbps, full duplex.
Apr  5 20:39:38 MTOLEDOB kernel: [  147.300000] tg3: eth0: Flow control is off for TX and off for RX.
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) failed. 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Deactivating device eth0. 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Will activate connection 'eth0'. 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Device eth0 activation scheduled... 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) started... 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) failure scheduled... 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) failed. 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Deactivating device eth0. 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Will activate connection 'eth0'. 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Device eth0 activation scheduled... 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) started... 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) failure scheduled... 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Apr  5 20:39:38 MTOLEDOB kernel: [  148.044000] [drm] Initialized drm 1.1.0 20060810
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) failed. 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Deactivating device eth0. 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Will activate connection 'eth0'. 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Device eth0 activation scheduled... 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) started... 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) failure scheduled... 
Apr  5 20:39:38 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Apr  5 20:39:38 MTOLEDOB kernel: [  148.096000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:39:38 MTOLEDOB kernel: [  148.096000] [drm] Initialized radeon 1.27.0 20060524 on minor 0
Apr  5 20:39:39 MTOLEDOB kernel: [  148.256000] audit(1207449578.691:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5026 profile="/usr/sbin/cupsd"
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) failed. 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Deactivating device eth0. 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Will activate connection 'eth0'. 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Device eth0 activation scheduled... 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) started... 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) failure scheduled... 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Apr  5 20:39:39 MTOLEDOB kernel: [  148.436000] apm: BIOS not found.
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) failed. 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Deactivating device eth0. 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Will activate connection 'eth0'. 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Device eth0 activation scheduled... 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) started... 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) failure scheduled... 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) failed. 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Deactivating device eth0. 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Will activate connection 'eth0'. 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Device eth0 activation scheduled... 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) started... 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) failure scheduled... 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) failed. 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Deactivating device eth0. 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Will activate connection 'eth0'. 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Device eth0 activation scheduled... 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) started... 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) failure scheduled... 
Apr  5 20:39:39 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Apr  5 20:39:40 MTOLEDOB NetworkManager: <info>  Activation (eth0) failed. 
Apr  5 20:39:40 MTOLEDOB NetworkManager: <info>  Deactivating device eth0. 
Apr  5 20:39:40 MTOLEDOB NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Apr  5 20:39:40 MTOLEDOB NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Apr  5 20:39:40 MTOLEDOB NetworkManager: <info>  Will activate connection 'eth0'. 
Apr  5 20:39:40 MTOLEDOB NetworkManager: <info>  Device eth0 activation scheduled... 
Apr  5 20:39:40 MTOLEDOB NetworkManager: <info>  Activation (eth0) started... 
Apr  5 20:39:40 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr  5 20:39:40 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Apr  5 20:39:40 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Apr  5 20:39:40 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Apr  5 20:39:40 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Apr  5 20:39:40 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Apr  5 20:39:40 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr  5 20:39:40 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Apr  5 20:39:40 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Apr  5 20:39:40 MTOLEDOB NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Apr  5 20:39:40 MTOLEDOB NetworkManager: <info>  Activation (eth0) failure scheduled... 
Apr  5 20:39:40 MTOLEDOB NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Apr  5 20:42:38 MTOLEDOB syslogd 1.4.1#21ubuntu3: restart.
Apr  5 20:42:38 MTOLEDOB kernel: Inspecting /boot/System.map-2.6.22-14-generic
Apr  5 20:42:38 MTOLEDOB kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Apr  5 20:42:38 MTOLEDOB kernel: Symbols match kernel version 2.6.22.
Apr  5 20:42:38 MTOLEDOB kernel: No module symbols loaded - kernel modules not enabled. 
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000] BIOS-provided physical RAM map:
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffae000 (usable)
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 000000001ffae000 - 0000000020000000 (reserved)
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fee00000 (reserved)
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000] 0MB HIGHMEM available.
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000] 511MB LOWMEM available.
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000] Entering add_active_range(0, 0, 130990) 0 entries of 256 used
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000] Zone PFN ranges:
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000]   DMA             0 ->     4096
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000]   Normal       4096 ->   130990
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000]   HighMem    130990 ->   130990
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000]     0:        0 ->   130990
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000] On node 0 totalpages: 130990
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000]   Normal zone: 991 pages used for memmap
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000]   Normal zone: 125903 pages, LIFO batch:31
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000] DMI 2.3 present.
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FDF00 checksum 0
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000] ACPI: RSDP 000FDF00, 0014 (r0 DELL  )
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000] ACPI: RSDT 1FFF0000, 002C (r1 DELL    CPi R   27D5011A ASL        61)
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000] ACPI: FACP 1FFF0400, 0074 (r1 DELL    CPi R   27D5011A ASL        61)
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000] ACPI: DSDT 1FFF0C00, 2E1A (r1 INT430 SYSFexxx     1001 MSFT  100000E)
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000] ACPI: FACS 1FFFF800, 0040
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000] ACPI: ASF! 1FFF0800, 005B (r16 DELL    CPi R   27D5011A ASL        61)
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:deda0000)
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000] Built 1 zonelists.  Total pages: 129967
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000] Kernel command line: root=UUID=241da2db-0e86-4d13-ba31-7e747e81c264 ro quiet splash
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000] mapped APIC to ffffd000 (0140d000)
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000] Initializing CPU#0
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
Apr  5 20:42:38 MTOLEDOB kernel: [    0.000000] Detected 1398.839 MHz processor.
Apr  5 20:42:38 MTOLEDOB kernel: [    8.196790] Console: colour VGA+ 80x25
Apr  5 20:42:38 MTOLEDOB kernel: [    8.197094] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr  5 20:42:38 MTOLEDOB kernel: [    8.197423] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr  5 20:42:38 MTOLEDOB kernel: [    8.215222] Memory: 506636k/523960k available (2015k kernel code, 16752k reserved, 915k data, 364k init, 0k highmem)
Apr  5 20:42:38 MTOLEDOB kernel: [    8.215235] virtual kernel memory layout:
Apr  5 20:42:38 MTOLEDOB kernel: [    8.215236]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Apr  5 20:42:38 MTOLEDOB kernel: [    8.215238]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr  5 20:42:38 MTOLEDOB kernel: [    8.215240]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
Apr  5 20:42:38 MTOLEDOB kernel: [    8.215242]     lowmem  : 0xc0000000 - 0xdffae000   ( 511 MB)
Apr  5 20:42:38 MTOLEDOB kernel: [    8.215243]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Apr  5 20:42:38 MTOLEDOB kernel: [    8.215245]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
Apr  5 20:42:38 MTOLEDOB kernel: [    8.215247]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
Apr  5 20:42:38 MTOLEDOB kernel: [    8.215251] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr  5 20:42:38 MTOLEDOB kernel: [    8.215299] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Apr  5 20:42:38 MTOLEDOB kernel: [    8.295320] Calibrating delay using timer specific routine.. 2799.71 BogoMIPS (lpj=5599425)
Apr  5 20:42:38 MTOLEDOB kernel: [    8.295352] Security Framework v1.0.0 initialized
Apr  5 20:42:38 MTOLEDOB kernel: [    8.295361] SELinux:  Disabled at boot.
Apr  5 20:42:38 MTOLEDOB kernel: [    8.295379] Mount-cache hash table entries: 512
Apr  5 20:42:38 MTOLEDOB kernel: [    8.295536] CPU: After generic identify, caps: a7e9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
Apr  5 20:42:38 MTOLEDOB kernel: [    8.295551] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr  5 20:42:38 MTOLEDOB kernel: [    8.295555] CPU: L2 cache: 1024K
Apr  5 20:42:38 MTOLEDOB kernel: [    8.295558] CPU: After all inits, caps: a7e9f9bf 00000000 00000000 00002040 00000180 00000000 00000000
Apr  5 20:42:38 MTOLEDOB kernel: [    8.295570] Compat vDSO mapped to ffffe000.
Apr  5 20:42:38 MTOLEDOB kernel: [    8.295584] Checking 'hlt' instruction... OK.
Apr  5 20:42:38 MTOLEDOB kernel: [    8.311428] SMP alternatives: switching to UP code
Apr  5 20:42:38 MTOLEDOB kernel: [    8.311609] Freeing SMP alternatives: 11k freed
Apr  5 20:42:38 MTOLEDOB kernel: [    8.311913] Early unpacking initramfs... done
Apr  5 20:42:38 MTOLEDOB kernel: [    8.756271] ACPI: Core revision 20070126
Apr  5 20:42:38 MTOLEDOB kernel: [    8.756347] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Apr  5 20:42:38 MTOLEDOB kernel: [    8.758004] ACPI: setting ELCR to 0200 (from 0800)
Apr  5 20:42:38 MTOLEDOB kernel: [    8.760123] CPU0: Intel(R) Pentium(R) M processor 1400MHz stepping 05
Apr  5 20:42:38 MTOLEDOB kernel: [    8.760131] SMP motherboard not detected.
Apr  5 20:42:38 MTOLEDOB kernel: [    8.760134] Local APIC not detected. Using dummy APIC emulation.
Apr  5 20:42:38 MTOLEDOB kernel: [    8.760174] Brought up 1 CPUs
Apr  5 20:42:38 MTOLEDOB kernel: [    8.760312] Booting paravirtualized kernel on bare hardware
Apr  5 20:42:38 MTOLEDOB kernel: [    8.760378] Time: 20:42:16  Date: 03/05/108
Apr  5 20:42:38 MTOLEDOB kernel: [    8.760406] NET: Registered protocol family 16
Apr  5 20:42:38 MTOLEDOB kernel: [    8.760505] EISA bus registered
Apr  5 20:42:38 MTOLEDOB kernel: [    8.760518] ACPI: bus type pci registered
Apr  5 20:42:38 MTOLEDOB kernel: [    8.794198] PCI: PCI BIOS revision 2.10 entry at 0xfc96e, last bus=2
Apr  5 20:42:38 MTOLEDOB kernel: [    8.794201] PCI: Using configuration type 1
Apr  5 20:42:38 MTOLEDOB kernel: [    8.794203] Setting up standard PCI resources
Apr  5 20:42:38 MTOLEDOB kernel: [    8.796379] ACPI: EC: Look up EC in DSDT
Apr  5 20:42:38 MTOLEDOB kernel: [    8.803534] ACPI: Interpreter enabled
Apr  5 20:42:38 MTOLEDOB kernel: [    8.803538] ACPI: (supports S0 S1 S3 S4 S5)
Apr  5 20:42:38 MTOLEDOB kernel: [    8.803559] ACPI: Using PIC for interrupt routing
Apr  5 20:42:38 MTOLEDOB kernel: [    8.816542] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr  5 20:42:38 MTOLEDOB kernel: [    8.816566] PCI: Probing PCI hardware (bus 00)
Apr  5 20:42:38 MTOLEDOB kernel: [    8.816944] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
Apr  5 20:42:38 MTOLEDOB kernel: [    8.816949] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
Apr  5 20:42:38 MTOLEDOB kernel: [    8.817414] PCI: Transparent bridge - 0000:00:1e.0
Apr  5 20:42:38 MTOLEDOB kernel: [    8.817533] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr  5 20:42:38 MTOLEDOB kernel: [    8.817911] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Apr  5 20:42:38 MTOLEDOB kernel: [    8.818003] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Apr  5 20:42:38 MTOLEDOB kernel: [    8.832595] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
Apr  5 20:42:38 MTOLEDOB kernel: [    8.832711] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
Apr  5 20:42:38 MTOLEDOB kernel: [    8.832823] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
Apr  5 20:42:38 MTOLEDOB kernel: [    8.832936] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
Apr  5 20:42:38 MTOLEDOB kernel: [    8.833034] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Apr  5 20:42:38 MTOLEDOB kernel: [    8.833151] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Apr  5 20:42:38 MTOLEDOB kernel: [    8.833259] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr  5 20:42:38 MTOLEDOB kernel: [    8.833271] pnp: PnP ACPI init
Apr  5 20:42:38 MTOLEDOB kernel: [    8.833284] ACPI: bus type pnp registered
Apr  5 20:42:38 MTOLEDOB kernel: [    8.861196] pnp: PnP ACPI: found 13 devices
Apr  5 20:42:38 MTOLEDOB kernel: [    8.861199] ACPI: ACPI bus type pnp unregistered
Apr  5 20:42:38 MTOLEDOB kernel: [    8.861205] PnPBIOS: Disabled by ACPI PNP
Apr  5 20:42:38 MTOLEDOB kernel: [    8.861261] PCI: Using ACPI for IRQ routing
Apr  5 20:42:38 MTOLEDOB kernel: [    8.861264] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr  5 20:42:38 MTOLEDOB kernel: [    8.867690] NET: Registered protocol family 8
Apr  5 20:42:38 MTOLEDOB kernel: [    8.867693] NET: Registered protocol family 20
Apr  5 20:42:38 MTOLEDOB kernel: [    8.867757] pnp: 00:00: iomem range 0x0-0x9fbff could not be reserved
Apr  5 20:42:38 MTOLEDOB kernel: [    8.867761] pnp: 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
Apr  5 20:42:38 MTOLEDOB kernel: [    8.867765] pnp: 00:00: iomem range 0xc0000-0xcffff could not be reserved
Apr  5 20:42:38 MTOLEDOB kernel: [    8.867769] pnp: 00:00: iomem range 0xe0000-0xfffff could not be reserved
Apr  5 20:42:38 MTOLEDOB kernel: [    8.867776] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
Apr  5 20:42:38 MTOLEDOB kernel: [    8.867780] pnp: 00:02: ioport range 0x800-0x805 has been reserved
Apr  5 20:42:38 MTOLEDOB kernel: [    8.867784] pnp: 00:02: ioport range 0x808-0x80f has been reserved
Apr  5 20:42:38 MTOLEDOB kernel: [    8.867790] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
Apr  5 20:42:38 MTOLEDOB kernel: [    8.867794] pnp: 00:03: ioport range 0x806-0x807 has been reserved
Apr  5 20:42:38 MTOLEDOB kernel: [    8.867797] pnp: 00:03: ioport range 0x810-0x85f has been reserved
Apr  5 20:42:38 MTOLEDOB kernel: [    8.867801] pnp: 00:03: ioport range 0x860-0x87f has been reserved
Apr  5 20:42:38 MTOLEDOB kernel: [    8.867805] pnp: 00:03: ioport range 0x880-0x8bf has been reserved
Apr  5 20:42:38 MTOLEDOB kernel: [    8.867808] pnp: 00:03: ioport range 0x8c0-0x8df has been reserved
Apr  5 20:42:38 MTOLEDOB kernel: [    8.867816] pnp: 00:08: ioport range 0x900-0x97f has been reserved
Apr  5 20:42:38 MTOLEDOB kernel: [    8.871313] Time: tsc clocksource has been installed.
Apr  5 20:42:38 MTOLEDOB kernel: [    8.898142] PCI: Bridge: 0000:00:01.0
Apr  5 20:42:38 MTOLEDOB kernel: [    8.898145]   IO window: c000-cfff
Apr  5 20:42:38 MTOLEDOB kernel: [    8.898149]   MEM window: fc000000-fdffffff
Apr  5 20:42:38 MTOLEDOB kernel: [    8.898153]   PREFETCH window: e8000000-efffffff
Apr  5 20:42:38 MTOLEDOB kernel: [    8.898167] PCI: Bus 3, cardbus bridge: 0000:02:01.0
Apr  5 20:42:38 MTOLEDOB kernel: [    8.898170]   IO window: 0000d000-0000d0ff
Apr  5 20:42:38 MTOLEDOB kernel: [    8.898175]   IO window: 0000d400-0000d4ff
Apr  5 20:42:38 MTOLEDOB kernel: [    8.898180]   PREFETCH window: 30000000-33ffffff
Apr  5 20:42:38 MTOLEDOB kernel: [    8.898184]   MEM window: 3c000000-3fffffff
Apr  5 20:42:38 MTOLEDOB kernel: [    8.898189] PCI: Bus 7, cardbus bridge: 0000:02:01.1
Apr  5 20:42:38 MTOLEDOB kernel: [    8.898191]   IO window: 0000d800-0000d8ff
Apr  5 20:42:38 MTOLEDOB kernel: [    8.898196]   IO window: 0000dc00-0000dcff
Apr  5 20:42:38 MTOLEDOB kernel: [    8.898201]   PREFETCH window: 34000000-37ffffff
Apr  5 20:42:38 MTOLEDOB kernel: [    8.898205]   MEM window: 40000000-43ffffff
Apr  5 20:42:38 MTOLEDOB kernel: [    8.898210] PCI: Bridge: 0000:00:1e.0
Apr  5 20:42:38 MTOLEDOB kernel: [    8.898213]   IO window: d000-efff
Apr  5 20:42:38 MTOLEDOB kernel: [    8.898219]   MEM window: f6000000-fbffffff
Apr  5 20:42:38 MTOLEDOB kernel: [    8.898224]   PREFETCH window: 30000000-37ffffff
Apr  5 20:42:38 MTOLEDOB kernel: [    8.898239] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Apr  5 20:42:38 MTOLEDOB kernel: [    8.898253] PCI: Enabling device 0000:02:01.0 (0000 -> 0003)
Apr  5 20:42:38 MTOLEDOB kernel: [    8.898425] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Apr  5 20:42:38 MTOLEDOB kernel: [    8.898429] PCI: setting IRQ 11 as level-triggered
Apr  5 20:42:38 MTOLEDOB kernel: [    8.898433] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:42:38 MTOLEDOB kernel: [    8.898451] PCI: Enabling device 0000:02:01.1 (0000 -> 0003)
Apr  5 20:42:38 MTOLEDOB kernel: [    8.898455] ACPI: PCI Interrupt 0000:02:01.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:42:38 MTOLEDOB kernel: [    8.898474] NET: Registered protocol family 2
Apr  5 20:42:38 MTOLEDOB kernel: [    8.935357] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Apr  5 20:42:38 MTOLEDOB kernel: [    8.935406] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
Apr  5 20:42:38 MTOLEDOB kernel: [    8.935614] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
Apr  5 20:42:38 MTOLEDOB kernel: [    8.935751] TCP: Hash tables configured (established 16384 bind 16384)
Apr  5 20:42:38 MTOLEDOB kernel: [    8.935755] TCP reno registered
Apr  5 20:42:38 MTOLEDOB kernel: [    8.947479] checking if image is initramfs... it is
Apr  5 20:42:38 MTOLEDOB kernel: [    9.399335] Switched to high resolution mode on CPU 0
Apr  5 20:42:38 MTOLEDOB kernel: [    9.824941] Freeing initrd memory: 8373k freed
Apr  5 20:42:38 MTOLEDOB kernel: [    9.825358] audit: initializing netlink socket (disabled)
Apr  5 20:42:38 MTOLEDOB kernel: [    9.825378] audit(1207428136.160:1): initialized
Apr  5 20:42:38 MTOLEDOB kernel: [    9.827981] VFS: Disk quotas dquot_6.5.1
Apr  5 20:42:38 MTOLEDOB kernel: [    9.828054] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr  5 20:42:38 MTOLEDOB kernel: [    9.828176] io scheduler noop registered
Apr  5 20:42:38 MTOLEDOB kernel: [    9.828179] io scheduler anticipatory registered
Apr  5 20:42:38 MTOLEDOB kernel: [    9.828182] io scheduler deadline registered
Apr  5 20:42:38 MTOLEDOB kernel: [    9.828207] io scheduler cfq registered (default)
Apr  5 20:42:38 MTOLEDOB kernel: [    9.828286] Boot video device is 0000:01:00.0
Apr  5 20:42:38 MTOLEDOB kernel: [    9.828480] isapnp: Scanning for PnP cards...
Apr  5 20:42:38 MTOLEDOB kernel: [   10.181411] isapnp: No Plug & Play device found
Apr  5 20:42:38 MTOLEDOB kernel: [   10.218552] Real Time Clock Driver v1.12ac
Apr  5 20:42:38 MTOLEDOB kernel: [   10.218693] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr  5 20:42:38 MTOLEDOB kernel: [   10.218792] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr  5 20:42:38 MTOLEDOB kernel: [   10.219820] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr  5 20:42:38 MTOLEDOB kernel: [   10.220292] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
Apr  5 20:42:38 MTOLEDOB kernel: [   10.220297] PCI: setting IRQ 5 as level-triggered
Apr  5 20:42:38 MTOLEDOB kernel: [   10.220301] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Apr  5 20:42:38 MTOLEDOB kernel: [   10.220312] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
Apr  5 20:42:38 MTOLEDOB kernel: [   10.220967] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr  5 20:42:38 MTOLEDOB kernel: [   10.221250] input: Macintosh mouse button emulation as /class/input/input0
Apr  5 20:42:38 MTOLEDOB kernel: [   10.221338] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Apr  5 20:42:38 MTOLEDOB kernel: [   10.227249] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr  5 20:42:38 MTOLEDOB kernel: [   10.227256] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr  5 20:42:38 MTOLEDOB kernel: [   10.227451] mice: PS/2 mouse device common for all mice
Apr  5 20:42:38 MTOLEDOB kernel: [   10.227576] EISA: Probing bus 0 at eisa.0
Apr  5 20:42:38 MTOLEDOB kernel: [   10.227605] EISA: Detected 0 cards.
Apr  5 20:42:38 MTOLEDOB kernel: [   10.227734] TCP cubic registered
Apr  5 20:42:38 MTOLEDOB kernel: [   10.227758] NET: Registered protocol family 1
Apr  5 20:42:38 MTOLEDOB kernel: [   10.227793] Using IPI No-Shortcut mode
Apr  5 20:42:38 MTOLEDOB kernel: [   10.228014]   Magic number: 4:169:750
Apr  5 20:42:38 MTOLEDOB kernel: [   10.228020]   hash matches device ttyS1
Apr  5 20:42:38 MTOLEDOB kernel: [   10.228527] Freeing unused kernel memory: 364k freed
Apr  5 20:42:38 MTOLEDOB kernel: [   10.259248] input: AT Translated Set 2 keyboard as /class/input/input1
Apr  5 20:42:38 MTOLEDOB kernel: [   11.447203] AppArmor: AppArmor initialized<5>audit(1207428138.160:2):  type=1505 info="AppArmor initialized" pid=1205
Apr  5 20:42:38 MTOLEDOB kernel: [   11.457631] fuse init (API version 7.8)
Apr  5 20:42:38 MTOLEDOB kernel: [   11.463201] Failure registering capabilities with primary security module.
Apr  5 20:42:38 MTOLEDOB kernel: [   11.483699] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
Apr  5 20:42:38 MTOLEDOB kernel: [   11.483708] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr  5 20:42:38 MTOLEDOB kernel: [   11.487576] ACPI: Thermal Zone [THM] (50 C)
Apr  5 20:42:38 MTOLEDOB kernel: [   11.950713] usbcore: registered new interface driver usbfs
Apr  5 20:42:38 MTOLEDOB kernel: [   11.950745] usbcore: registered new interface driver hub
Apr  5 20:42:38 MTOLEDOB kernel: [   11.950775] usbcore: registered new device driver usb
Apr  5 20:42:38 MTOLEDOB kernel: [   11.952543] USB Universal Host Controller Interface driver v3.0
Apr  5 20:42:38 MTOLEDOB kernel: [   11.952881] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
Apr  5 20:42:38 MTOLEDOB kernel: [   11.952885] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:42:38 MTOLEDOB kernel: [   11.952901] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Apr  5 20:42:38 MTOLEDOB kernel: [   11.952906] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr  5 20:42:38 MTOLEDOB kernel: [   11.953165] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Apr  5 20:42:38 MTOLEDOB kernel: [   11.953193] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
Apr  5 20:42:38 MTOLEDOB kernel: [   11.953361] usb usb1: configuration #1 chosen from 1 choice
Apr  5 20:42:38 MTOLEDOB kernel: [   11.953395] hub 1-0:1.0: USB hub found
Apr  5 20:42:38 MTOLEDOB kernel: [   11.953402] hub 1-0:1.0: 2 ports detected
Apr  5 20:42:38 MTOLEDOB kernel: [   12.057229] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:42:38 MTOLEDOB kernel: [   12.057247] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Apr  5 20:42:38 MTOLEDOB kernel: [   12.057253] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr  5 20:42:38 MTOLEDOB kernel: [   12.057281] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Apr  5 20:42:38 MTOLEDOB kernel: [   12.057308] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
Apr  5 20:42:38 MTOLEDOB kernel: [   12.057449] usb usb2: configuration #1 chosen from 1 choice
Apr  5 20:42:38 MTOLEDOB kernel: [   12.057484] hub 2-0:1.0: USB hub found
Apr  5 20:42:38 MTOLEDOB kernel: [   12.057492] hub 2-0:1.0: 2 ports detected
Apr  5 20:42:38 MTOLEDOB kernel: [   12.057916] SCSI subsystem initialized
Apr  5 20:42:38 MTOLEDOB kernel: [   12.070486] libata version 2.21 loaded.
Apr  5 20:42:38 MTOLEDOB kernel: [   12.161052] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
Apr  5 20:42:38 MTOLEDOB kernel: [   12.161059] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:42:38 MTOLEDOB kernel: [   12.161074] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Apr  5 20:42:38 MTOLEDOB kernel: [   12.161079] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr  5 20:42:38 MTOLEDOB kernel: [   12.161111] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Apr  5 20:42:38 MTOLEDOB kernel: [   12.161138] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
Apr  5 20:42:38 MTOLEDOB kernel: [   12.161272] usb usb3: configuration #1 chosen from 1 choice
Apr  5 20:42:38 MTOLEDOB kernel: [   12.161306] hub 3-0:1.0: USB hub found
Apr  5 20:42:38 MTOLEDOB kernel: [   12.161314] hub 3-0:1.0: 2 ports detected
Apr  5 20:42:38 MTOLEDOB kernel: [   12.263882] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
Apr  5 20:42:38 MTOLEDOB kernel: [   12.263888] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:42:38 MTOLEDOB kernel: [   12.263903] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Apr  5 20:42:38 MTOLEDOB kernel: [   12.263907] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr  5 20:42:38 MTOLEDOB kernel: [   12.263942] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
Apr  5 20:42:38 MTOLEDOB kernel: [   12.263981] ehci_hcd 0000:00:1d.7: debug port 1
Apr  5 20:42:38 MTOLEDOB kernel: [   12.263988] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Apr  5 20:42:38 MTOLEDOB kernel: [   12.263998] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf4fffc00
Apr  5 20:42:38 MTOLEDOB kernel: [   12.267892] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Apr  5 20:42:38 MTOLEDOB kernel: [   12.267998] usb usb4: configuration #1 chosen from 1 choice
Apr  5 20:42:38 MTOLEDOB kernel: [   12.268034] hub 4-0:1.0: USB hub found
Apr  5 20:42:38 MTOLEDOB kernel: [   12.268042] hub 4-0:1.0: 6 ports detected
Apr  5 20:42:38 MTOLEDOB kernel: [   12.371991] ata_piix 0000:00:1f.1: version 2.11
Apr  5 20:42:38 MTOLEDOB kernel: [   12.372010] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
Apr  5 20:42:38 MTOLEDOB kernel: [   12.372021] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:42:38 MTOLEDOB kernel: [   12.372069] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Apr  5 20:42:38 MTOLEDOB kernel: [   12.372233] scsi0 : ata_piix
Apr  5 20:42:38 MTOLEDOB kernel: [   12.372287] scsi1 : ata_piix
Apr  5 20:42:38 MTOLEDOB kernel: [   12.373321] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
Apr  5 20:42:38 MTOLEDOB kernel: [   12.373326] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
Apr  5 20:42:38 MTOLEDOB kernel: [    4.276000] Marking TSC unstable due to: possible TSC halt in C2.
Apr  5 20:42:38 MTOLEDOB kernel: [    4.288000] Time: acpi_pm clocksource has been installed.
Apr  5 20:42:38 MTOLEDOB kernel: [    4.324000] ata1.00: ATA-6: ST980815A, 3.ALD, max UDMA/100
Apr  5 20:42:38 MTOLEDOB kernel: [    4.324000] ata1.00: 156301488 sectors, multi 8: LBA48 
Apr  5 20:42:38 MTOLEDOB kernel: [    4.340000] ata1.00: configured for UDMA/100
Apr  5 20:42:38 MTOLEDOB kernel: [    4.660000] ata2.00: ATAPI: HL-DT-STCD-RW/DVD-ROM GCC-4241N, A101, max UDMA/33
Apr  5 20:42:38 MTOLEDOB kernel: [    4.832000] ata2.00: configured for UDMA/33
Apr  5 20:42:38 MTOLEDOB kernel: [    4.832000] scsi 0:0:0:0: Direct-Access     ATA      ST980815A        3.AL PQ: 0 ANSI: 5
Apr  5 20:42:38 MTOLEDOB kernel: [    4.836000] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4241N A101 PQ: 0 ANSI: 5
Apr  5 20:42:38 MTOLEDOB kernel: [    4.840000] tg3.c:v3.77 (May 31, 2007)
Apr  5 20:42:38 MTOLEDOB kernel: [    4.840000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:42:38 MTOLEDOB kernel: [    4.880000] eth0: Tigon3 [partno(BCM95705A50) rev 3001 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000Base-T Ethernet 00:11:43:53:d5:22
Apr  5 20:42:38 MTOLEDOB kernel: [    4.880000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
Apr  5 20:42:38 MTOLEDOB kernel: [    4.880000] eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
Apr  5 20:42:38 MTOLEDOB kernel: [    4.888000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr  5 20:42:38 MTOLEDOB kernel: [    4.888000] sd 0:0:0:0: [sda] Write Protect is off
Apr  5 20:42:38 MTOLEDOB kernel: [    4.888000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr  5 20:42:38 MTOLEDOB kernel: [    4.888000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  5 20:42:38 MTOLEDOB kernel: [    4.888000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr  5 20:42:38 MTOLEDOB kernel: [    4.888000] sd 0:0:0:0: [sda] Write Protect is off
Apr  5 20:42:38 MTOLEDOB kernel: [    4.888000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr  5 20:42:38 MTOLEDOB kernel: [    4.888000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  5 20:42:38 MTOLEDOB kernel: [    4.888000]  sda: sda1 sda2 sda3 < sda5 >
Apr  5 20:42:38 MTOLEDOB kernel: [    4.972000] sd 0:0:0:0: [sda] Attached SCSI disk
Apr  5 20:42:38 MTOLEDOB kernel: [    4.980000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr  5 20:42:38 MTOLEDOB kernel: [    4.980000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
Apr  5 20:42:38 MTOLEDOB kernel: [    5.012000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Apr  5 20:42:38 MTOLEDOB kernel: [    5.012000] Uniform CD-ROM driver Revision: 3.20
Apr  5 20:42:38 MTOLEDOB kernel: [    5.012000] sr 1:0:0:0: Attached scsi CD-ROM sr0
Apr  5 20:42:38 MTOLEDOB kernel: [    5.216000] Attempting manual resume
Apr  5 20:42:38 MTOLEDOB kernel: [    5.216000] swsusp: Resume From Partition 8:5
Apr  5 20:42:38 MTOLEDOB kernel: [    5.216000] PM: Checking swsusp image.
Apr  5 20:42:38 MTOLEDOB kernel: [    5.216000] PM: Resume from disk failed.
Apr  5 20:42:38 MTOLEDOB kernel: [    5.236000] EXT3-fs: INFO: recovery required on readonly filesystem.
Apr  5 20:42:38 MTOLEDOB kernel: [    5.236000] EXT3-fs: write access will be enabled during recovery.
Apr  5 20:42:38 MTOLEDOB kernel: [    5.824000] kjournald starting.  Commit interval 5 seconds
Apr  5 20:42:38 MTOLEDOB kernel: [    5.824000] EXT3-fs: recovery complete.
Apr  5 20:42:38 MTOLEDOB kernel: [    5.824000] EXT3-fs: mounted filesystem with ordered data mode.
Apr  5 20:42:38 MTOLEDOB kernel: [   16.284000] Linux agpgart interface v0.102 (c) Dave Jones
Apr  5 20:42:38 MTOLEDOB kernel: [   16.488000] agpgart: Detected an Intel 855PM Chipset.
Apr  5 20:42:38 MTOLEDOB kernel: [   16.496000] agpgart: AGP aperture is 128M @ 0xe0000000
Apr  5 20:42:38 MTOLEDOB kernel: [   16.556000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr  5 20:42:38 MTOLEDOB kernel: [   16.556000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr  5 20:42:38 MTOLEDOB kernel: [   16.652000] iTCO_vendor_support: vendor-support=0
Apr  5 20:42:38 MTOLEDOB kernel: [   16.656000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
Apr  5 20:42:38 MTOLEDOB kernel: [   16.656000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x0860)
Apr  5 20:42:38 MTOLEDOB kernel: [   16.656000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Apr  5 20:42:38 MTOLEDOB kernel: [   16.676000] intel_rng: FWH not detected
Apr  5 20:42:38 MTOLEDOB kernel: [   17.384000] Yenta: CardBus bridge found at 0000:02:01.0 [1028:011d]
Apr  5 20:42:38 MTOLEDOB kernel: [   17.384000] Yenta O2: res at 0x94/0xD4: 00/ea
Apr  5 20:42:38 MTOLEDOB kernel: [   17.384000] Yenta O2: enabling read prefetch/write burst
Apr  5 20:42:38 MTOLEDOB kernel: [   17.484000] input: DualPoint Stick as /class/input/input2
Apr  5 20:42:38 MTOLEDOB kernel: [   17.504000] input: AlpsPS/2 ALPS DualPoint TouchPad as /class/input/input3
Apr  5 20:42:38 MTOLEDOB kernel: [   17.512000] Yenta: ISA IRQ mask 0x0498, PCI irq 11
Apr  5 20:42:38 MTOLEDOB kernel: [   17.512000] Socket status: 30000006
Apr  5 20:42:38 MTOLEDOB kernel: [   17.512000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
Apr  5 20:42:38 MTOLEDOB kernel: [   17.512000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
Apr  5 20:42:38 MTOLEDOB kernel: [   17.512000] cs: IO port probe 0xd000-0xefff: clean.
Apr  5 20:42:38 MTOLEDOB kernel: [   17.512000] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
Apr  5 20:42:38 MTOLEDOB kernel: [   17.512000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x37ffffff
Apr  5 20:42:38 MTOLEDOB kernel: [   17.512000] Yenta: CardBus bridge found at 0000:02:01.1 [1028:011d]
Apr  5 20:42:38 MTOLEDOB kernel: [   17.576000] ieee80211_crypt: registered algorithm 'NULL'
Apr  5 20:42:38 MTOLEDOB kernel: [   17.576000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Apr  5 20:42:38 MTOLEDOB kernel: [   17.576000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Apr  5 20:42:38 MTOLEDOB kernel: [   17.640000] Yenta: ISA IRQ mask 0x0498, PCI irq 11
Apr  5 20:42:38 MTOLEDOB kernel: [   17.640000] Socket status: 30000410
Apr  5 20:42:38 MTOLEDOB kernel: [   17.640000] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
Apr  5 20:42:38 MTOLEDOB kernel: [   17.640000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
Apr  5 20:42:38 MTOLEDOB kernel: [   17.640000] cs: IO port probe 0xd000-0xefff: clean.
Apr  5 20:42:38 MTOLEDOB kernel: [   17.640000] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
Apr  5 20:42:38 MTOLEDOB kernel: [   17.640000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x37ffffff
Apr  5 20:42:38 MTOLEDOB kernel: [   17.848000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
Apr  5 20:42:38 MTOLEDOB kernel: [   17.848000] ipw2100: Copyright(c) 2003-2006 Intel Corporation
Apr  5 20:42:38 MTOLEDOB kernel: [   17.848000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Apr  5 20:42:38 MTOLEDOB kernel: [   17.848000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
Apr  5 20:42:38 MTOLEDOB kernel: [   17.856000] input: PC Speaker as /class/input/input4
Apr  5 20:42:38 MTOLEDOB kernel: [   17.864000] parport_pc 00:0c: reported by Plug and Play ACPI
Apr  5 20:42:38 MTOLEDOB kernel: [   17.864000] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Apr  5 20:42:38 MTOLEDOB kernel: [   18.276000] pccard: PCMCIA card inserted into slot 1
Apr  5 20:42:38 MTOLEDOB kernel: [   18.596000] cs: memory probe 0xf6000000-0xfbffffff: excluding 0xf6000000-0xf65fffff 0xf6c00000-0xf71fffff 0xf7e00000-0xf83fffff 0xf9c00000-0xfa1fffff 0xfae00000-0xfb3fffff
Apr  5 20:42:38 MTOLEDOB kernel: [   18.608000] pcmcia: registering new device pcmcia1.0
Apr  5 20:42:38 MTOLEDOB kernel: [   18.632000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Apr  5 20:42:38 MTOLEDOB kernel: [   18.632000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
Apr  5 20:42:38 MTOLEDOB kernel: [   18.672000] cs: IO port probe 0x100-0x3af: clean.
Apr  5 20:42:38 MTOLEDOB kernel: [   18.676000] cs: IO port probe 0x100-0x3af: clean.
Apr  5 20:42:38 MTOLEDOB kernel: [   18.676000] cs: IO port probe 0x3e0-0x4ff: clean.
Apr  5 20:42:38 MTOLEDOB kernel: [   18.676000] cs: IO port probe 0x820-0x8ff: clean.
Apr  5 20:42:38 MTOLEDOB kernel: [   18.676000] cs: IO port probe 0xc00-0xcf7: clean.
Apr  5 20:42:38 MTOLEDOB kernel: [   18.676000] cs: IO port probe 0xa00-0xaff: clean.
Apr  5 20:42:38 MTOLEDOB kernel: [   18.724000] cs: IO port probe 0x3e0-0x4ff: clean.
Apr  5 20:42:38 MTOLEDOB kernel: [   18.724000] cs: IO port probe 0x820-0x8ff: clean.
Apr  5 20:42:38 MTOLEDOB kernel: [   18.724000] cs: IO port probe 0xc00-0xcf7: clean.
Apr  5 20:42:38 MTOLEDOB kernel: [   18.724000] cs: IO port probe 0xa00-0xaff: clean.
Apr  5 20:42:38 MTOLEDOB kernel: [   19.460000] intel8x0_measure_ac97_clock: measured 55445 usecs
Apr  5 20:42:38 MTOLEDOB kernel: [   19.460000] intel8x0: clocking to 48000
Apr  5 20:42:38 MTOLEDOB kernel: [   20.308000] lp0: using parport0 (interrupt-driven).
Apr  5 20:42:38 MTOLEDOB kernel: [   20.348000] Adding 1510068k swap on /dev/sda5.  Priority:-1 extents:1 across:1510068k
Apr  5 20:42:38 MTOLEDOB kernel: [   20.644000] EXT3 FS on sda2, internal journal
Apr  5 20:42:38 MTOLEDOB kernel: [   21.736000] ACPI: AC Adapter [AC] (on-line)
Apr  5 20:42:38 MTOLEDOB kernel: [   21.796000] input: Lid Switch as /class/input/input5
Apr  5 20:42:38 MTOLEDOB kernel: [   21.804000] ACPI: Lid Switch [LID]
Apr  5 20:42:38 MTOLEDOB kernel: [   21.852000] input: Power Button (CM) as /class/input/input6
Apr  5 20:42:38 MTOLEDOB kernel: [   21.856000] ACPI: Power Button (CM) [PBTN]
Apr  5 20:42:38 MTOLEDOB kernel: [   21.904000] input: Sleep Button (CM) as /class/input/input7
Apr  5 20:42:38 MTOLEDOB kernel: [   21.908000] ACPI: Sleep Button (CM) [SBTN]
Apr  5 20:42:38 MTOLEDOB kernel: [   21.928000] ACPI: ACPI Dock Station Driver 
Apr  5 20:42:38 MTOLEDOB kernel: [   22.260000] ACPI: Battery Slot [BAT0] (battery present)
Apr  5 20:42:38 MTOLEDOB kernel: [   22.260000] ACPI: Battery Slot [BAT1] (battery absent)
Apr  5 20:42:38 MTOLEDOB kernel: [   22.304000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Apr  5 20:42:38 MTOLEDOB NetworkManager: <info>  starting... 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.154718] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_3340'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.389986] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_3341'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.390971] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_4c66'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.391706] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c2'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.392241] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.392717] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.393190] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c4'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.393661] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.394132] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.394671] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c7'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.395144] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.395613] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.396102] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24cd'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.396574] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.397043] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.397512] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.397982] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_165d'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.398450] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1217_7113'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.398962] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1217_7113_0'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.399434] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pcmcia__1__1'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.399917] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_1043'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.400385] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24cc'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.400852] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.401318] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.401785] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_scsi_device_lun0'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.402253] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_0'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.402719] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_0_scsi_device_lun0'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.403186] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.403651] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c6'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.404130] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_dock_0'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.404594] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.405059] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.405568] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.406034] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.406499] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.406963] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.407425] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.407913] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.408377] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.408840] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.409302] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.409764] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.410225] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.410686] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.411147] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.411607] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.412082] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.412542] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.413002] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.413462] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0401'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.413922] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.414380] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.414840] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.415299] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.416316] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.417102] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.451170] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_11_43_53_d5_22'). 
Apr  5 20:42:39 MTOLEDOB kernel: [   23.780000] PM: Writing back config space on device 0000:02:00.0 at offset c (was ffbf0000, writing 0)
Apr  5 20:42:39 MTOLEDOB kernel: [   23.780000] PM: Writing back config space on device 0000:02:00.0 at offset b (was 165d14e4, writing 865d1028)
Apr  5 20:42:39 MTOLEDOB kernel: [   23.780000] PM: Writing back config space on device 0000:02:00.0 at offset 3 (was 0, writing 2008)
Apr  5 20:42:39 MTOLEDOB kernel: [   23.780000] PM: Writing back config space on device 0000:02:00.0 at offset 2 (was 2000000, writing 2000001)
Apr  5 20:42:39 MTOLEDOB kernel: [   23.780000] PM: Writing back config space on device 0000:02:00.0 at offset 1 (was 2b00000, writing 2b00106)
Apr  5 20:42:39 MTOLEDOB NetworkManager: <info>  eth0: Device is fully-supported using driver 'tg3'. 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <info>  Deactivating device eth0. 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <debug> [1207449759.929803] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_0c_f1_1c_20_6b'). 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <info>  eth1: Device is fully-supported using driver 'ipw2100'. 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Apr  5 20:42:39 MTOLEDOB NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <info>  Deactivating device eth1. 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.084663] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_scsi_device_lun0_scsi_generic'). 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.085340] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.085836] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_pcm_1'). 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.086320] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_pcm_0'). 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.086802] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_control__1'). 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.087282] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_pcm_0_0'). 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.087762] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_mixer__1'). 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.088268] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_0'). 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.088746] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_playback_0'). 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.089224] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_1'). 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.089734] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_2'). 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.090214] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_3'). 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.090691] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_playback_4'). 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.091184] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.091661] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.092154] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.092644] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.093185] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.093666] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.094140] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_3'). 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.094613] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'). 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.095085] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.095556] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.096046] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.096518] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.096988] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST980815A_5LY1VWH9'). 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.173698] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_606C05936C0564DE'). 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.180247] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_241da2db_0e86_4d13_ba31_7e747e81c264'). 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.227718] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part3_size_1024'). 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.233638] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_aaabdd49_42ff_4b7f_ac15_b1a4f0ed1a87'). 
Apr  5 20:42:40 MTOLEDOB gdm[4597]: WARNING: Didn't understand `' (expected true or false) 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.344932] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT1'). 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.410067] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.410708] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.411193] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Apr  5 20:42:40 MTOLEDOB NetworkManager: <debug> [1207449760.412037] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_RW/DVD_GCC_4241N'). 
Apr  5 20:42:41 MTOLEDOB kernel: [   25.264000] [drm] Initialized drm 1.1.0 20060810
Apr  5 20:42:41 MTOLEDOB kernel: [   25.272000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:42:41 MTOLEDOB kernel: [   25.276000] [drm] Initialized radeon 1.27.0 20060524 on minor 0
Apr  5 20:44:02 MTOLEDOB syslogd 1.4.1#21ubuntu3: restart.
Apr  5 20:44:02 MTOLEDOB kernel: Inspecting /boot/System.map-2.6.22-14-generic
Apr  5 20:44:03 MTOLEDOB kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Apr  5 20:44:03 MTOLEDOB kernel: Symbols match kernel version 2.6.22.
Apr  5 20:44:03 MTOLEDOB kernel: No module symbols loaded - kernel modules not enabled. 
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000] BIOS-provided physical RAM map:
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffae000 (usable)
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 000000001ffae000 - 0000000020000000 (reserved)
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fee00000 (reserved)
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000] 0MB HIGHMEM available.
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000] 511MB LOWMEM available.
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000] Entering add_active_range(0, 0, 130990) 0 entries of 256 used
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000] Zone PFN ranges:
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000]   DMA             0 ->     4096
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000]   Normal       4096 ->   130990
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000]   HighMem    130990 ->   130990
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000]     0:        0 ->   130990
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000] On node 0 totalpages: 130990
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000]   Normal zone: 991 pages used for memmap
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000]   Normal zone: 125903 pages, LIFO batch:31
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000] DMI 2.3 present.
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FDF00 checksum 0
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000] ACPI: RSDP 000FDF00, 0014 (r0 DELL  )
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000] ACPI: RSDT 1FFF0000, 002C (r1 DELL    CPi R   27D5011A ASL        61)
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000] ACPI: FACP 1FFF0400, 0074 (r1 DELL    CPi R   27D5011A ASL        61)
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000] ACPI: DSDT 1FFF0C00, 2E1A (r1 INT430 SYSFexxx     1001 MSFT  100000E)
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000] ACPI: FACS 1FFFF800, 0040
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000] ACPI: ASF! 1FFF0800, 005B (r16 DELL    CPi R   27D5011A ASL        61)
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:deda0000)
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000] Built 1 zonelists.  Total pages: 129967
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000] Kernel command line: root=UUID=241da2db-0e86-4d13-ba31-7e747e81c264 ro single
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000] mapped APIC to ffffd000 (0140d000)
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000] Initializing CPU#0
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
Apr  5 20:44:03 MTOLEDOB kernel: [    0.000000] Detected 1398.896 MHz processor.
Apr  5 20:44:03 MTOLEDOB kernel: [   12.678137] Console: colour VGA+ 80x25
Apr  5 20:44:03 MTOLEDOB kernel: [   12.679488] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr  5 20:44:03 MTOLEDOB kernel: [   12.679851] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr  5 20:44:03 MTOLEDOB kernel: [   12.697560] Memory: 506636k/523960k available (2015k kernel code, 16752k reserved, 915k data, 364k init, 0k highmem)
Apr  5 20:44:03 MTOLEDOB kernel: [   12.697620] virtual kernel memory layout:
Apr  5 20:44:03 MTOLEDOB kernel: [   12.697622]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Apr  5 20:44:03 MTOLEDOB kernel: [   12.697624]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr  5 20:44:03 MTOLEDOB kernel: [   12.697625]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
Apr  5 20:44:03 MTOLEDOB kernel: [   12.697627]     lowmem  : 0xc0000000 - 0xdffae000   ( 511 MB)
Apr  5 20:44:03 MTOLEDOB kernel: [   12.697629]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Apr  5 20:44:03 MTOLEDOB kernel: [   12.697631]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
Apr  5 20:44:03 MTOLEDOB kernel: [   12.697632]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
Apr  5 20:44:03 MTOLEDOB kernel: [   12.697900] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr  5 20:44:03 MTOLEDOB kernel: [   12.698012] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Apr  5 20:44:03 MTOLEDOB kernel: [   12.778075] Calibrating delay using timer specific routine.. 2799.70 BogoMIPS (lpj=5599413)
Apr  5 20:44:03 MTOLEDOB kernel: [   12.778171] Security Framework v1.0.0 initialized
Apr  5 20:44:03 MTOLEDOB kernel: [   12.778212] SELinux:  Disabled at boot.
Apr  5 20:44:03 MTOLEDOB kernel: [   12.778263] Mount-cache hash table entries: 512
Apr  5 20:44:03 MTOLEDOB kernel: [   12.778450] CPU: After generic identify, caps: a7e9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
Apr  5 20:44:03 MTOLEDOB kernel: [   12.778464] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr  5 20:44:03 MTOLEDOB kernel: [   12.778523] CPU: L2 cache: 1024K
Apr  5 20:44:03 MTOLEDOB kernel: [   12.778557] CPU: After all inits, caps: a7e9f9bf 00000000 00000000 00002040 00000180 00000000 00000000
Apr  5 20:44:03 MTOLEDOB kernel: [   12.778569] Compat vDSO mapped to ffffe000.
Apr  5 20:44:03 MTOLEDOB kernel: [   12.778614] Checking 'hlt' instruction... OK.
Apr  5 20:44:03 MTOLEDOB kernel: [   12.794211] SMP alternatives: switching to UP code
Apr  5 20:44:03 MTOLEDOB kernel: [   12.794424] Freeing SMP alternatives: 11k freed
Apr  5 20:44:03 MTOLEDOB kernel: [   12.794760] Early unpacking initramfs... done
Apr  5 20:44:03 MTOLEDOB kernel: [   13.239330] ACPI: Core revision 20070126
Apr  5 20:44:03 MTOLEDOB kernel: [   13.239438] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Apr  5 20:44:03 MTOLEDOB kernel: [   13.241159] ACPI: setting ELCR to 0200 (from 0800)
Apr  5 20:44:03 MTOLEDOB kernel: [   13.243608] CPU0: Intel(R) Pentium(R) M processor 1400MHz stepping 05
Apr  5 20:44:03 MTOLEDOB kernel: [   13.243690] SMP motherboard not detected.
Apr  5 20:44:03 MTOLEDOB kernel: [   13.243725] Local APIC not detected. Using dummy APIC emulation.
Apr  5 20:44:03 MTOLEDOB kernel: [   13.243798] Brought up 1 CPUs
Apr  5 20:44:03 MTOLEDOB kernel: [   13.243967] Booting paravirtualized kernel on bare hardware
Apr  5 20:44:03 MTOLEDOB kernel: [   13.244067] Time: 20:43:32  Date: 03/05/108
Apr  5 20:44:03 MTOLEDOB kernel: [   13.244127] NET: Registered protocol family 16
Apr  5 20:44:03 MTOLEDOB kernel: [   13.244257] EISA bus registered
Apr  5 20:44:03 MTOLEDOB kernel: [   13.244301] ACPI: bus type pci registered
Apr  5 20:44:03 MTOLEDOB kernel: [   13.278013] PCI: PCI BIOS revision 2.10 entry at 0xfc96e, last bus=2
Apr  5 20:44:03 MTOLEDOB kernel: [   13.278049] PCI: Using configuration type 1
Apr  5 20:44:03 MTOLEDOB kernel: [   13.278089] Setting up standard PCI resources
Apr  5 20:44:03 MTOLEDOB kernel: [   13.280302] ACPI: EC: Look up EC in DSDT
Apr  5 20:44:03 MTOLEDOB kernel: [   13.287299] ACPI: Interpreter enabled
Apr  5 20:44:03 MTOLEDOB kernel: [   13.287335] ACPI: (supports S0 S1 S3 S4 S5)
Apr  5 20:44:03 MTOLEDOB kernel: [   13.287511] ACPI: Using PIC for interrupt routing
Apr  5 20:44:03 MTOLEDOB kernel: [   13.300580] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr  5 20:44:03 MTOLEDOB kernel: [   13.300639] PCI: Probing PCI hardware (bus 00)
Apr  5 20:44:03 MTOLEDOB kernel: [   13.301022] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
Apr  5 20:44:03 MTOLEDOB kernel: [   13.301061] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
Apr  5 20:44:03 MTOLEDOB kernel: [   13.301557] PCI: Transparent bridge - 0000:00:1e.0
Apr  5 20:44:03 MTOLEDOB kernel: [   13.301708] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr  5 20:44:03 MTOLEDOB kernel: [   13.302124] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Apr  5 20:44:03 MTOLEDOB kernel: [   13.302218] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Apr  5 20:44:03 MTOLEDOB kernel: [   13.316722] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
Apr  5 20:44:03 MTOLEDOB kernel: [   13.316975] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
Apr  5 20:44:03 MTOLEDOB kernel: [   13.317225] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
Apr  5 20:44:03 MTOLEDOB kernel: [   13.317474] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
Apr  5 20:44:03 MTOLEDOB kernel: [   13.317750] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Apr  5 20:44:03 MTOLEDOB kernel: [   13.318242] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Apr  5 20:44:03 MTOLEDOB kernel: [   13.318661] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr  5 20:44:03 MTOLEDOB kernel: [   13.318706] pnp: PnP ACPI init
Apr  5 20:44:03 MTOLEDOB kernel: [   13.318750] ACPI: bus type pnp registered
Apr  5 20:44:03 MTOLEDOB kernel: [   13.346658] pnp: PnP ACPI: found 13 devices
Apr  5 20:44:03 MTOLEDOB kernel: [   13.346694] ACPI: ACPI bus type pnp unregistered
Apr  5 20:44:03 MTOLEDOB kernel: [   13.346732] PnPBIOS: Disabled by ACPI PNP
Apr  5 20:44:03 MTOLEDOB kernel: [   13.346821] PCI: Using ACPI for IRQ routing
Apr  5 20:44:03 MTOLEDOB kernel: [   13.346857] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr  5 20:44:03 MTOLEDOB kernel: [   13.353321] NET: Registered protocol family 8
Apr  5 20:44:03 MTOLEDOB kernel: [   13.353355] NET: Registered protocol family 20
Apr  5 20:44:03 MTOLEDOB kernel: [   13.353450] pnp: 00:00: iomem range 0x0-0x9fbff could not be reserved
Apr  5 20:44:03 MTOLEDOB kernel: [   13.353488] pnp: 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
Apr  5 20:44:03 MTOLEDOB kernel: [   13.353526] pnp: 00:00: iomem range 0xc0000-0xcffff could not be reserved
Apr  5 20:44:03 MTOLEDOB kernel: [   13.353564] pnp: 00:00: iomem range 0xe0000-0xfffff could not be reserved
Apr  5 20:44:03 MTOLEDOB kernel: [   13.353605] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
Apr  5 20:44:03 MTOLEDOB kernel: [   13.353642] pnp: 00:02: ioport range 0x800-0x805 has been reserved
Apr  5 20:44:03 MTOLEDOB kernel: [   13.353679] pnp: 00:02: ioport range 0x808-0x80f has been reserved
Apr  5 20:44:03 MTOLEDOB kernel: [   13.353719] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
Apr  5 20:44:03 MTOLEDOB kernel: [   13.353756] pnp: 00:03: ioport range 0x806-0x807 has been reserved
Apr  5 20:44:03 MTOLEDOB kernel: [   13.353793] pnp: 00:03: ioport range 0x810-0x85f has been reserved
Apr  5 20:44:03 MTOLEDOB kernel: [   13.353830] pnp: 00:03: ioport range 0x860-0x87f has been reserved
Apr  5 20:44:03 MTOLEDOB kernel: [   13.353867] pnp: 00:03: ioport range 0x880-0x8bf has been reserved
Apr  5 20:44:03 MTOLEDOB kernel: [   13.353904] pnp: 00:03: ioport range 0x8c0-0x8df has been reserved
Apr  5 20:44:03 MTOLEDOB kernel: [   13.353945] pnp: 00:08: ioport range 0x900-0x97f has been reserved
Apr  5 20:44:03 MTOLEDOB kernel: [   13.354068] Time: tsc clocksource has been installed.
Apr  5 20:44:03 MTOLEDOB kernel: [   13.384356] PCI: Bridge: 0000:00:01.0
Apr  5 20:44:03 MTOLEDOB kernel: [   13.384391]   IO window: c000-cfff
Apr  5 20:44:03 MTOLEDOB kernel: [   13.384427]   MEM window: fc000000-fdffffff
Apr  5 20:44:03 MTOLEDOB kernel: [   13.384462]   PREFETCH window: e8000000-efffffff
Apr  5 20:44:03 MTOLEDOB kernel: [   13.384508] PCI: Bus 3, cardbus bridge: 0000:02:01.0
Apr  5 20:44:03 MTOLEDOB kernel: [   13.384544]   IO window: 0000d000-0000d0ff
Apr  5 20:44:03 MTOLEDOB kernel: [   13.384580]   IO window: 0000d400-0000d4ff
Apr  5 20:44:03 MTOLEDOB kernel: [   13.384616]   PREFETCH window: 30000000-33ffffff
Apr  5 20:44:03 MTOLEDOB kernel: [   13.384653]   MEM window: 3c000000-3fffffff
Apr  5 20:44:03 MTOLEDOB kernel: [   13.384689] PCI: Bus 7, cardbus bridge: 0000:02:01.1
Apr  5 20:44:03 MTOLEDOB kernel: [   13.384724]   IO window: 0000d800-0000d8ff
Apr  5 20:44:03 MTOLEDOB kernel: [   13.384760]   IO window: 0000dc00-0000dcff
Apr  5 20:44:03 MTOLEDOB kernel: [   13.384796]   PREFETCH window: 34000000-37ffffff
Apr  5 20:44:03 MTOLEDOB kernel: [   13.384833]   MEM window: 40000000-43ffffff
Apr  5 20:44:03 MTOLEDOB kernel: [   13.384869] PCI: Bridge: 0000:00:1e.0
Apr  5 20:44:03 MTOLEDOB kernel: [   13.384904]   IO window: d000-efff
Apr  5 20:44:03 MTOLEDOB kernel: [   13.384940]   MEM window: f6000000-fbffffff
Apr  5 20:44:03 MTOLEDOB kernel: [   13.384977]   PREFETCH window: 30000000-37ffffff
Apr  5 20:44:03 MTOLEDOB kernel: [   13.385024] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Apr  5 20:44:03 MTOLEDOB kernel: [   13.385038] PCI: Enabling device 0000:02:01.0 (0000 -> 0003)
Apr  5 20:44:03 MTOLEDOB kernel: [   13.385246] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Apr  5 20:44:03 MTOLEDOB kernel: [   13.385283] PCI: setting IRQ 11 as level-triggered
Apr  5 20:44:03 MTOLEDOB kernel: [   13.385287] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:44:03 MTOLEDOB kernel: [   13.385389] PCI: Enabling device 0000:02:01.1 (0000 -> 0003)
Apr  5 20:44:03 MTOLEDOB kernel: [   13.385427] ACPI: PCI Interrupt 0000:02:01.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:44:03 MTOLEDOB kernel: [   13.385531] NET: Registered protocol family 2
Apr  5 20:44:03 MTOLEDOB kernel: [   13.422112] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Apr  5 20:44:03 MTOLEDOB kernel: [   13.422197] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
Apr  5 20:44:03 MTOLEDOB kernel: [   13.422451] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
Apr  5 20:44:03 MTOLEDOB kernel: [   13.422622] TCP: Hash tables configured (established 16384 bind 16384)
Apr  5 20:44:03 MTOLEDOB kernel: [   13.422658] TCP reno registered
Apr  5 20:44:03 MTOLEDOB kernel: [   13.434230] checking if image is initramfs... it is
Apr  5 20:44:03 MTOLEDOB kernel: [   13.886090] Switched to high resolution mode on CPU 0
Apr  5 20:44:03 MTOLEDOB kernel: [   14.312061] Freeing initrd memory: 8373k freed
Apr  5 20:44:03 MTOLEDOB kernel: [   14.312519] audit: initializing netlink socket (disabled)
Apr  5 20:44:03 MTOLEDOB kernel: [   14.312574] audit(1207428212.160:1): initialized
Apr  5 20:44:03 MTOLEDOB kernel: [   14.315235] VFS: Disk quotas dquot_6.5.1
Apr  5 20:44:03 MTOLEDOB kernel: [   14.315344] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr  5 20:44:03 MTOLEDOB kernel: [   14.315502] io scheduler noop registered
Apr  5 20:44:03 MTOLEDOB kernel: [   14.315537] io scheduler anticipatory registered
Apr  5 20:44:03 MTOLEDOB kernel: [   14.315571] io scheduler deadline registered
Apr  5 20:44:03 MTOLEDOB kernel: [   14.315628] io scheduler cfq registered (default)
Apr  5 20:44:03 MTOLEDOB kernel: [   14.315740] Boot video device is 0000:01:00.0
Apr  5 20:44:03 MTOLEDOB kernel: [   14.315938] isapnp: Scanning for PnP cards...
Apr  5 20:44:03 MTOLEDOB kernel: [   14.668907] isapnp: No Plug & Play device found
Apr  5 20:44:03 MTOLEDOB kernel: [   14.705691] Real Time Clock Driver v1.12ac
Apr  5 20:44:03 MTOLEDOB kernel: [   14.705873] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr  5 20:44:03 MTOLEDOB kernel: [   14.706076] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr  5 20:44:03 MTOLEDOB kernel: [   14.707074] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr  5 20:44:03 MTOLEDOB kernel: [   14.707583] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
Apr  5 20:44:03 MTOLEDOB kernel: [   14.707621] PCI: setting IRQ 5 as level-triggered
Apr  5 20:44:03 MTOLEDOB kernel: [   14.707626] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Apr  5 20:44:03 MTOLEDOB kernel: [   14.707722] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
Apr  5 20:44:03 MTOLEDOB kernel: [   14.708412] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr  5 20:44:03 MTOLEDOB kernel: [   14.708741] input: Macintosh mouse button emulation as /class/input/input0
Apr  5 20:44:03 MTOLEDOB kernel: [   14.708867] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Apr  5 20:44:03 MTOLEDOB kernel: [   14.714475] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr  5 20:44:03 MTOLEDOB kernel: [   14.714516] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr  5 20:44:03 MTOLEDOB kernel: [   14.714746] mice: PS/2 mouse device common for all mice
Apr  5 20:44:03 MTOLEDOB kernel: [   14.714905] EISA: Probing bus 0 at eisa.0
Apr  5 20:44:03 MTOLEDOB kernel: [   14.714965] EISA: Detected 0 cards.
Apr  5 20:44:03 MTOLEDOB kernel: [   14.715124] TCP cubic registered
Apr  5 20:44:03 MTOLEDOB kernel: [   14.715190] NET: Registered protocol family 1
Apr  5 20:44:03 MTOLEDOB kernel: [   14.715258] Using IPI No-Shortcut mode
Apr  5 20:44:03 MTOLEDOB kernel: [   14.715501]   Magic number: 4:169:750
Apr  5 20:44:03 MTOLEDOB kernel: [   14.715538]   hash matches device ttyS1
Apr  5 20:44:03 MTOLEDOB kernel: [   14.716070] Freeing unused kernel memory: 364k freed
Apr  5 20:44:03 MTOLEDOB kernel: [   14.750056] input: AT Translated Set 2 keyboard as /class/input/input1
Apr  5 20:44:03 MTOLEDOB kernel: [   14.911526] AppArmor: AppArmor initialized<5>audit(1207428213.160:2):  type=1505 info="AppArmor initialized" pid=1184
Apr  5 20:44:03 MTOLEDOB kernel: [   14.922854] fuse init (API version 7.8)
Apr  5 20:44:03 MTOLEDOB kernel: [   14.928345] Failure registering capabilities with primary security module.
Apr  5 20:44:03 MTOLEDOB kernel: [   14.950634] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
Apr  5 20:44:03 MTOLEDOB kernel: [   14.950784] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr  5 20:44:03 MTOLEDOB kernel: [   14.954703] ACPI: Thermal Zone [THM] (50 C)
Apr  5 20:44:03 MTOLEDOB kernel: [   15.419243] usbcore: registered new interface driver usbfs
Apr  5 20:44:03 MTOLEDOB kernel: [   15.419313] usbcore: registered new interface driver hub
Apr  5 20:44:03 MTOLEDOB kernel: [   15.419370] usbcore: registered new device driver usb
Apr  5 20:44:03 MTOLEDOB kernel: [   15.421060] USB Universal Host Controller Interface driver v3.0
Apr  5 20:44:03 MTOLEDOB kernel: [   15.421426] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
Apr  5 20:44:03 MTOLEDOB kernel: [   15.421464] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:44:03 MTOLEDOB kernel: [   15.421563] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Apr  5 20:44:03 MTOLEDOB kernel: [   15.421567] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr  5 20:44:03 MTOLEDOB kernel: [   15.421853] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Apr  5 20:44:03 MTOLEDOB kernel: [   15.421923] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
Apr  5 20:44:03 MTOLEDOB kernel: [   15.422124] usb usb1: configuration #1 chosen from 1 choice
Apr  5 20:44:03 MTOLEDOB kernel: [   15.422188] hub 1-0:1.0: USB hub found
Apr  5 20:44:03 MTOLEDOB kernel: [   15.422226] hub 1-0:1.0: 2 ports detected
Apr  5 20:44:03 MTOLEDOB kernel: [   15.526119] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:44:03 MTOLEDOB kernel: [   15.526225] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Apr  5 20:44:03 MTOLEDOB kernel: [   15.526230] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr  5 20:44:03 MTOLEDOB kernel: [   15.526292] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Apr  5 20:44:03 MTOLEDOB kernel: [   15.526360] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
Apr  5 20:44:03 MTOLEDOB kernel: [   15.526523] usb usb2: configuration #1 chosen from 1 choice
Apr  5 20:44:03 MTOLEDOB kernel: [   15.526589] hub 2-0:1.0: USB hub found
Apr  5 20:44:03 MTOLEDOB kernel: [   15.526629] hub 2-0:1.0: 2 ports detected
Apr  5 20:44:03 MTOLEDOB kernel: [   15.583156] SCSI subsystem initialized
Apr  5 20:44:03 MTOLEDOB kernel: [   15.595670] libata version 2.21 loaded.
Apr  5 20:44:03 MTOLEDOB kernel: [   15.630340] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
Apr  5 20:44:03 MTOLEDOB kernel: [   15.630384] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:44:03 MTOLEDOB kernel: [   15.630484] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Apr  5 20:44:03 MTOLEDOB kernel: [   15.630489] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr  5 20:44:03 MTOLEDOB kernel: [   15.630554] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Apr  5 20:44:03 MTOLEDOB kernel: [   15.630623] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
Apr  5 20:44:03 MTOLEDOB kernel: [   15.630791] usb usb3: configuration #1 chosen from 1 choice
Apr  5 20:44:03 MTOLEDOB kernel: [   15.630858] hub 3-0:1.0: USB hub found
Apr  5 20:44:03 MTOLEDOB kernel: [   15.630896] hub 3-0:1.0: 2 ports detected
Apr  5 20:44:03 MTOLEDOB kernel: [   15.734821] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
Apr  5 20:44:03 MTOLEDOB kernel: [   15.734866] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:44:03 MTOLEDOB kernel: [   15.734967] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Apr  5 20:44:03 MTOLEDOB kernel: [   15.734971] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr  5 20:44:03 MTOLEDOB kernel: [   15.735040] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
Apr  5 20:44:03 MTOLEDOB kernel: [   15.735122] ehci_hcd 0000:00:1d.7: debug port 1
Apr  5 20:44:03 MTOLEDOB kernel: [   15.735161] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Apr  5 20:44:03 MTOLEDOB kernel: [   15.735170] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf4fffc00
Apr  5 20:44:03 MTOLEDOB kernel: [   15.739087] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Apr  5 20:44:03 MTOLEDOB kernel: [   15.739244] usb usb4: configuration #1 chosen from 1 choice
Apr  5 20:44:03 MTOLEDOB kernel: [   15.739316] hub 4-0:1.0: USB hub found
Apr  5 20:44:03 MTOLEDOB kernel: [   15.739355] hub 4-0:1.0: 6 ports detected
Apr  5 20:44:03 MTOLEDOB kernel: [   15.842185] tg3.c:v3.77 (May 31, 2007)
Apr  5 20:44:03 MTOLEDOB kernel: [   15.842249] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:44:03 MTOLEDOB kernel: [   15.889923] eth0: Tigon3 [partno(BCM95705A50) rev 3001 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000Base-T Ethernet 00:11:43:53:d5:22
Apr  5 20:44:03 MTOLEDOB kernel: [   15.890108] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
Apr  5 20:44:03 MTOLEDOB kernel: [   15.890154] eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
Apr  5 20:44:03 MTOLEDOB kernel: [   15.890804] ata_piix 0000:00:1f.1: version 2.11
Apr  5 20:44:03 MTOLEDOB kernel: [   15.890821] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
Apr  5 20:44:03 MTOLEDOB kernel: [   15.890867] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:44:03 MTOLEDOB kernel: [   15.890996] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Apr  5 20:44:03 MTOLEDOB kernel: [   15.891106] scsi0 : ata_piix
Apr  5 20:44:03 MTOLEDOB kernel: [   15.891193] scsi1 : ata_piix
Apr  5 20:44:03 MTOLEDOB kernel: [   15.892244] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
Apr  5 20:44:03 MTOLEDOB kernel: [   15.892292] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
Apr  5 20:44:03 MTOLEDOB kernel: [    3.304000] Marking TSC unstable due to: possible TSC halt in C2.
Apr  5 20:44:03 MTOLEDOB kernel: [    3.308000] Time: acpi_pm clocksource has been installed.
Apr  5 20:44:03 MTOLEDOB kernel: [    3.360000] ata1.00: ATA-6: ST980815A, 3.ALD, max UDMA/100
Apr  5 20:44:03 MTOLEDOB kernel: [    3.360000] ata1.00: 156301488 sectors, multi 8: LBA48 
Apr  5 20:44:03 MTOLEDOB kernel: [    3.376000] ata1.00: configured for UDMA/100
Apr  5 20:44:03 MTOLEDOB kernel: [    3.696000] ata2.00: ATAPI: HL-DT-STCD-RW/DVD-ROM GCC-4241N, A101, max UDMA/33
Apr  5 20:44:03 MTOLEDOB kernel: [    3.868000] ata2.00: configured for UDMA/33
Apr  5 20:44:03 MTOLEDOB kernel: [    3.868000] scsi 0:0:0:0: Direct-Access     ATA      ST980815A        3.AL PQ: 0 ANSI: 5
Apr  5 20:44:03 MTOLEDOB kernel: [    3.872000] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4241N A101 PQ: 0 ANSI: 5
Apr  5 20:44:03 MTOLEDOB kernel: [    3.896000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr  5 20:44:03 MTOLEDOB kernel: [    3.896000] sd 0:0:0:0: [sda] Write Protect is off
Apr  5 20:44:03 MTOLEDOB kernel: [    3.896000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr  5 20:44:03 MTOLEDOB kernel: [    3.896000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  5 20:44:03 MTOLEDOB kernel: [    3.896000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr  5 20:44:03 MTOLEDOB kernel: [    3.896000] sd 0:0:0:0: [sda] Write Protect is off
Apr  5 20:44:03 MTOLEDOB kernel: [    3.896000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr  5 20:44:03 MTOLEDOB kernel: [    3.896000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  5 20:44:03 MTOLEDOB kernel: [    3.896000]  sda: sda1 sda2 sda3 < sda5 >
Apr  5 20:44:03 MTOLEDOB kernel: [    3.944000] sd 0:0:0:0: [sda] Attached SCSI disk
Apr  5 20:44:03 MTOLEDOB kernel: [    3.948000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr  5 20:44:03 MTOLEDOB kernel: [    3.948000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
Apr  5 20:44:03 MTOLEDOB kernel: [    3.980000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Apr  5 20:44:03 MTOLEDOB kernel: [    3.980000] Uniform CD-ROM driver Revision: 3.20
Apr  5 20:44:03 MTOLEDOB kernel: [    3.980000] sr 1:0:0:0: Attached scsi CD-ROM sr0
Apr  5 20:44:03 MTOLEDOB kernel: [    4.220000] Attempting manual resume
Apr  5 20:44:03 MTOLEDOB kernel: [    4.220000] swsusp: Resume From Partition 8:5
Apr  5 20:44:03 MTOLEDOB kernel: [    4.220000] PM: Checking swsusp image.
Apr  5 20:44:03 MTOLEDOB kernel: [    4.220000] PM: Resume from disk failed.
Apr  5 20:44:03 MTOLEDOB kernel: [    4.244000] EXT3-fs: INFO: recovery required on readonly filesystem.
Apr  5 20:44:03 MTOLEDOB kernel: [    4.244000] EXT3-fs: write access will be enabled during recovery.
Apr  5 20:44:03 MTOLEDOB kernel: [    4.592000] kjournald starting.  Commit interval 5 seconds
Apr  5 20:44:03 MTOLEDOB kernel: [    4.592000] EXT3-fs: recovery complete.
Apr  5 20:44:03 MTOLEDOB kernel: [    4.604000] EXT3-fs: mounted filesystem with ordered data mode.
Apr  5 20:44:03 MTOLEDOB kernel: [   15.256000] Linux agpgart interface v0.102 (c) Dave Jones
Apr  5 20:44:03 MTOLEDOB kernel: [   15.404000] agpgart: Detected an Intel 855PM Chipset.
Apr  5 20:44:03 MTOLEDOB kernel: [   15.412000] agpgart: AGP aperture is 128M @ 0xe0000000
Apr  5 20:44:03 MTOLEDOB kernel: [   15.424000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr  5 20:44:03 MTOLEDOB kernel: [   15.428000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr  5 20:44:03 MTOLEDOB kernel: [   15.484000] iTCO_vendor_support: vendor-support=0
Apr  5 20:44:03 MTOLEDOB kernel: [   15.504000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
Apr  5 20:44:03 MTOLEDOB kernel: [   15.504000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x0860)
Apr  5 20:44:03 MTOLEDOB kernel: [   15.504000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Apr  5 20:44:03 MTOLEDOB kernel: [   15.796000] intel_rng: FWH not detected
Apr  5 20:44:03 MTOLEDOB kernel: [   15.892000] Yenta: CardBus bridge found at 0000:02:01.0 [1028:011d]
Apr  5 20:44:03 MTOLEDOB kernel: [   15.892000] Yenta O2: res at 0x94/0xD4: 00/ea
Apr  5 20:44:03 MTOLEDOB kernel: [   15.892000] Yenta O2: enabling read prefetch/write burst
Apr  5 20:44:03 MTOLEDOB kernel: [   16.020000] Yenta: ISA IRQ mask 0x0498, PCI irq 11
Apr  5 20:44:03 MTOLEDOB kernel: [   16.020000] Socket status: 30000006
Apr  5 20:44:03 MTOLEDOB kernel: [   16.020000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
Apr  5 20:44:03 MTOLEDOB kernel: [   16.020000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
Apr  5 20:44:03 MTOLEDOB kernel: [   16.020000] cs: IO port probe 0xd000-0xefff: clean.
Apr  5 20:44:03 MTOLEDOB kernel: [   16.020000] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
Apr  5 20:44:03 MTOLEDOB kernel: [   16.020000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x37ffffff
Apr  5 20:44:03 MTOLEDOB kernel: [   16.020000] Yenta: CardBus bridge found at 0000:02:01.1 [1028:011d]
Apr  5 20:44:03 MTOLEDOB kernel: [   16.148000] Yenta: ISA IRQ mask 0x0498, PCI irq 11
Apr  5 20:44:03 MTOLEDOB kernel: [   16.148000] Socket status: 30000410
Apr  5 20:44:03 MTOLEDOB kernel: [   16.148000] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
Apr  5 20:44:03 MTOLEDOB kernel: [   16.148000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
Apr  5 20:44:03 MTOLEDOB kernel: [   16.148000] cs: IO port probe 0xd000-0xefff: clean.
Apr  5 20:44:03 MTOLEDOB kernel: [   16.148000] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
Apr  5 20:44:03 MTOLEDOB kernel: [   16.148000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x37ffffff
Apr  5 20:44:03 MTOLEDOB kernel: [   16.420000] ieee80211_crypt: registered algorithm 'NULL'
Apr  5 20:44:03 MTOLEDOB kernel: [   16.440000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Apr  5 20:44:03 MTOLEDOB kernel: [   16.440000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Apr  5 20:44:03 MTOLEDOB kernel: [   16.496000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
Apr  5 20:44:03 MTOLEDOB kernel: [   16.496000] ipw2100: Copyright(c) 2003-2006 Intel Corporation
Apr  5 20:44:03 MTOLEDOB kernel: [   16.496000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Apr  5 20:44:03 MTOLEDOB kernel: [   16.496000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
Apr  5 20:44:03 MTOLEDOB kernel: [   16.784000] pccard: PCMCIA card inserted into slot 1
Apr  5 20:44:03 MTOLEDOB kernel: [   17.036000] input: PC Speaker as /class/input/input2
Apr  5 20:44:03 MTOLEDOB kernel: [   17.404000] input: DualPoint Stick as /class/input/input3
Apr  5 20:44:03 MTOLEDOB kernel: [   17.424000] input: AlpsPS/2 ALPS DualPoint TouchPad as /class/input/input4
Apr  5 20:44:03 MTOLEDOB kernel: [   17.432000] parport_pc 00:0c: reported by Plug and Play ACPI
Apr  5 20:44:03 MTOLEDOB kernel: [   17.432000] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Apr  5 20:44:03 MTOLEDOB kernel: [   17.508000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Apr  5 20:44:03 MTOLEDOB kernel: [   17.508000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
Apr  5 20:44:03 MTOLEDOB kernel: [   17.616000] cs: memory probe 0xf6000000-0xfbffffff: excluding 0xf6000000-0xf65fffff 0xf6c00000-0xf71fffff 0xf7e00000-0xf83fffff 0xf9c00000-0xfa1fffff 0xfae00000-0xfb3fffff
Apr  5 20:44:03 MTOLEDOB kernel: [   17.628000] pcmcia: registering new device pcmcia1.0
Apr  5 20:44:03 MTOLEDOB kernel: [   17.688000] cs: IO port probe 0x100-0x3af: clean.
Apr  5 20:44:03 MTOLEDOB kernel: [   17.688000] cs: IO port probe 0x3e0-0x4ff: clean.
Apr  5 20:44:03 MTOLEDOB kernel: [   17.688000] cs: IO port probe 0x820-0x8ff: clean.
Apr  5 20:44:03 MTOLEDOB kernel: [   17.688000] cs: IO port probe 0xc00-0xcf7: clean.
Apr  5 20:44:03 MTOLEDOB kernel: [   17.692000] cs: IO port probe 0xa00-0xaff: clean.
Apr  5 20:44:03 MTOLEDOB kernel: [   17.704000] cs: IO port probe 0x100-0x3af: clean.
Apr  5 20:44:03 MTOLEDOB kernel: [   17.704000] cs: IO port probe 0x3e0-0x4ff: clean.
Apr  5 20:44:03 MTOLEDOB kernel: [   17.704000] cs: IO port probe 0x820-0x8ff: clean.
Apr  5 20:44:03 MTOLEDOB kernel: [   17.704000] cs: IO port probe 0xc00-0xcf7: clean.
Apr  5 20:44:03 MTOLEDOB kernel: [   17.708000] cs: IO port probe 0xa00-0xaff: clean.
Apr  5 20:44:03 MTOLEDOB kernel: [   18.336000] intel8x0_measure_ac97_clock: measured 55443 usecs
Apr  5 20:44:03 MTOLEDOB kernel: [   18.336000] intel8x0: clocking to 48000
Apr  5 20:44:03 MTOLEDOB kernel: [   19.388000] lp0: using parport0 (interrupt-driven).
Apr  5 20:44:03 MTOLEDOB kernel: [   19.428000] Adding 1510068k swap on /dev/sda5.  Priority:-1 extents:1 across:1510068k
Apr  5 20:44:03 MTOLEDOB kernel: [   19.728000] EXT3 FS on sda2, internal journal
Apr  5 20:44:03 MTOLEDOB kernel: [   30.104000] ACPI: AC Adapter [AC] (on-line)
Apr  5 20:44:03 MTOLEDOB kernel: [   30.164000] input: Lid Switch as /class/input/input5
Apr  5 20:44:03 MTOLEDOB kernel: [   30.172000] ACPI: Lid Switch [LID]
Apr  5 20:44:03 MTOLEDOB kernel: [   30.220000] input: Power Button (CM) as /class/input/input6
Apr  5 20:44:03 MTOLEDOB kernel: [   30.224000] ACPI: Power Button (CM) [PBTN]
Apr  5 20:44:03 MTOLEDOB kernel: [   30.260000] input: Sleep Button (CM) as /class/input/input7
Apr  5 20:44:03 MTOLEDOB kernel: [   30.260000] ACPI: Sleep Button (CM) [SBTN]
Apr  5 20:44:03 MTOLEDOB kernel: [   30.296000] ACPI: ACPI Dock Station Driver 
Apr  5 20:44:03 MTOLEDOB kernel: [   30.612000] ACPI: Battery Slot [BAT0] (battery present)
Apr  5 20:44:03 MTOLEDOB kernel: [   30.612000] ACPI: Battery Slot [BAT1] (battery absent)
Apr  5 20:44:03 MTOLEDOB kernel: [   30.656000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Apr  5 20:44:03 MTOLEDOB NetworkManager: <info>  starting... 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.484646] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_3340'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.661706] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_3341'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.662699] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_4c66'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.663430] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c2'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.663964] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.664475] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.664948] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c4'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.665439] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.665914] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.666388] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c7'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.666860] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.667333] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.667804] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24cd'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.668292] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.668765] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.669235] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.669706] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_165d'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.670177] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1217_7113'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.670688] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1217_7113_0'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.671163] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pcmcia__1__1'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.671631] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_1043'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.672117] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24cc'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.672586] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.673056] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.673548] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_scsi_device_lun0'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.674018] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_0'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.674487] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_0_scsi_device_lun0'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.674972] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.675441] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c6'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.675908] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_dock_0'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.676393] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.676876] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.677344] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.677810] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.678278] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.678744] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.679208] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.679674] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.680155] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.680620] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.681085] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.681550] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.682014] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.682477] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.682939] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.683401] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.683860] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.684353] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.684815] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.685276] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0401'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.685736] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.686214] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.686676] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.687135] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.688353] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.689135] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Apr  5 20:44:03 MTOLEDOB NetworkManager: <debug> [1207449843.704276] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_11_43_53_d5_22'). 
Apr  5 20:44:04 MTOLEDOB kernel: [   32.140000] PM: Writing back config space on device 0000:02:00.0 at offset c (was ffbf0000, writing 0)
Apr  5 20:44:04 MTOLEDOB kernel: [   32.140000] PM: Writing back config space on device 0000:02:00.0 at offset b (was 165d14e4, writing 865d1028)
Apr  5 20:44:04 MTOLEDOB kernel: [   32.140000] PM: Writing back config space on device 0000:02:00.0 at offset 3 (was 0, writing 2008)
Apr  5 20:44:04 MTOLEDOB kernel: [   32.140000] PM: Writing back config space on device 0000:02:00.0 at offset 2 (was 2000000, writing 2000001)
Apr  5 20:44:04 MTOLEDOB kernel: [   32.140000] PM: Writing back config space on device 0000:02:00.0 at offset 1 (was 2b00000, writing 2b00106)
Apr  5 20:44:04 MTOLEDOB NetworkManager: <info>  eth0: Device is fully-supported using driver 'tg3'. 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <info>  Deactivating device eth0. 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.202023] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_0c_f1_1c_20_6b'). 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <info>  eth1: Device is fully-supported using driver 'ipw2100'. 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <info>  Deactivating device eth1. 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.356827] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_scsi_device_lun0_scsi_generic'). 
Apr  5 20:44:04 MTOLEDOB gdm[4820]: WARNING: Didn't understand `' (expected true or false) 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.428192] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.428776] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_pcm_1'). 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.429260] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_pcm_0'). 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.429740] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_control__1'). 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.430269] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_pcm_0_0'). 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.430751] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_mixer__1'). 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.431229] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_0'). 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.431705] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_playback_0'). 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.432201] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_1'). 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.432679] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_2'). 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.433154] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_3'). 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.433629] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_playback_4'). 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.434103] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.434575] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.435067] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.435541] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.436053] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'). 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.436562] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.437040] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.437520] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_3'). 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.437998] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.438469] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.438940] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.457121] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.457666] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST980815A_5LY1VWH9'). 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.458149] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_606C05936C0564DE'). 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.458670] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_241da2db_0e86_4d13_ba31_7e747e81c264'). 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.459149] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part3_size_1024'). 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.459620] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_aaabdd49_42ff_4b7f_ac15_b1a4f0ed1a87'). 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.460143] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT1'). 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.460616] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.461087] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.461556] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Apr  5 20:44:04 MTOLEDOB NetworkManager: <debug> [1207449844.490224] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_RW/DVD_GCC_4241N'). 
Apr  5 20:44:04 MTOLEDOB kernel: [   32.916000] ppdev: user-space parallel port driver
Apr  5 20:44:05 MTOLEDOB kernel: [   33.592000] audit(1207449845.009:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4896 profile="/usr/sbin/cupsd"
Apr  5 20:44:05 MTOLEDOB kernel: [   33.716000] apm: BIOS not found.
Apr  5 20:44:05 MTOLEDOB kernel: [   34.088000] [drm] Initialized drm 1.1.0 20060810
Apr  5 20:44:05 MTOLEDOB kernel: [   34.120000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:44:05 MTOLEDOB kernel: [   34.120000] [drm] Initialized radeon 1.27.0 20060524 on minor 0
Apr  5 20:45:11 MTOLEDOB syslogd 1.4.1#21ubuntu3: restart.
Apr  5 20:45:11 MTOLEDOB kernel: Inspecting /boot/System.map-2.6.20-12-generic
Apr  5 20:45:12 MTOLEDOB kernel: Loaded 24905 symbols from /boot/System.map-2.6.20-12-generic.
Apr  5 20:45:12 MTOLEDOB kernel: Symbols match kernel version 2.6.20.
Apr  5 20:45:12 MTOLEDOB kernel: No module symbols loaded - kernel modules not enabled. 
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000] Linux version 2.6.20-12-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Wed Mar 21 20:55:46 UTC 2007 (Ubuntu 2.6.20-12.20-generic)
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000] BIOS-provided physical RAM map:
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000] sanitize start
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000] sanitize end
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f000 end: 000000000009f000 type: 1
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000] copy_e820_map() start: 000000000009f000 size: 0000000000001000 end: 00000000000a0000 type: 2
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001feae000 end: 000000001ffae000 type: 1
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000] copy_e820_map() start: 000000001ffae000 size: 0000000000052000 end: 0000000020000000 type: 2
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000] copy_e820_map() start: 00000000feda0000 size: 0000000000060000 end: 00000000fee00000 type: 2
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000] copy_e820_map() start: 00000000ffb00000 size: 0000000000500000 end: 0000000100000000 type: 2
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffae000 (usable)
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 000000001ffae000 - 0000000020000000 (reserved)
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fee00000 (reserved)
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000] 0MB HIGHMEM available.
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000] 511MB LOWMEM available.
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000] Entering add_active_range(0, 0, 130990) 0 entries of 256 used
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000] Zone PFN ranges:
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000]   DMA             0 ->     4096
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000]   Normal       4096 ->   130990
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000]   HighMem    130990 ->   130990
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000]     0:        0 ->   130990
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000] On node 0 totalpages: 130990
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000]   Normal zone: 991 pages used for memmap
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000]   Normal zone: 125903 pages, LIFO batch:31
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000] DMI 2.3 present.
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fdf00
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000] ACPI: RSDT (v001 DELL    CPi R   0x27d5011a ASL  0x00000061) @ 0x1fff0000
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000] ACPI: FADT (v001 DELL    CPi R   0x27d5011a ASL  0x00000061) @ 0x1fff0400
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000] ACPI: ASF! (v016 DELL    CPi R   0x27d5011a ASL  0x00000061) @ 0x1fff0800
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000] ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 MSFT 0x0100000e) @ 0x00000000
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:deda0000)
Apr  5 20:45:12 MTOLEDOB kernel: [    0.000000] Detected 1398.869 MHz processor.
Apr  5 20:45:12 MTOLEDOB kernel: [   18.135650] Built 1 zonelists.  Total pages: 129967
Apr  5 20:45:12 MTOLEDOB kernel: [   18.135655] Kernel command line: root=UUID=241da2db-0e86-4d13-ba31-7e747e81c264 ro quiet splash
Apr  5 20:45:12 MTOLEDOB kernel: [   18.135868] Local APIC disabled by BIOS -- you can enable it with "lapic"
Apr  5 20:45:12 MTOLEDOB kernel: [   18.135878] mapped APIC to ffffd000 (0140b000)
Apr  5 20:45:12 MTOLEDOB kernel: [   18.135882] Enabling fast FPU save and restore... done.
Apr  5 20:45:12 MTOLEDOB kernel: [   18.135886] Enabling unmasked SIMD FPU exception support... done.
Apr  5 20:45:12 MTOLEDOB kernel: [   18.135897] Initializing CPU#0
Apr  5 20:45:12 MTOLEDOB kernel: [   18.135969] PID hash table entries: 2048 (order: 11, 8192 bytes)
Apr  5 20:45:12 MTOLEDOB kernel: [   18.137047] Console: colour VGA+ 80x25
Apr  5 20:45:12 MTOLEDOB kernel: [   18.137343] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr  5 20:45:12 MTOLEDOB kernel: [   18.137663] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr  5 20:45:12 MTOLEDOB kernel: [   18.155487] Memory: 508480k/523960k available (1990k kernel code, 14956k reserved, 890k data, 328k init, 0k highmem)
Apr  5 20:45:12 MTOLEDOB kernel: [   18.155501] virtual kernel memory layout:
Apr  5 20:45:12 MTOLEDOB kernel: [   18.155503]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
Apr  5 20:45:12 MTOLEDOB kernel: [   18.155505]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr  5 20:45:12 MTOLEDOB kernel: [   18.155506]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
Apr  5 20:45:12 MTOLEDOB kernel: [   18.155508]     lowmem  : 0xc0000000 - 0xdffae000   ( 511 MB)
Apr  5 20:45:12 MTOLEDOB kernel: [   18.155510]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
Apr  5 20:45:12 MTOLEDOB kernel: [   18.155511]       .data : 0xc02f1b04 - 0xc03d06d4   ( 890 kB)
Apr  5 20:45:12 MTOLEDOB kernel: [   18.155513]       .text : 0xc0100000 - 0xc02f1b04   (1990 kB)
Apr  5 20:45:12 MTOLEDOB kernel: [   18.155517] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr  5 20:45:12 MTOLEDOB kernel: [   18.231974] Calibrating delay using timer specific routine.. 2799.68 BogoMIPS (lpj=5599374)
Apr  5 20:45:12 MTOLEDOB kernel: [   18.232027] Security Framework v1.0.0 initialized
Apr  5 20:45:12 MTOLEDOB kernel: [   18.232036] SELinux:  Disabled at boot.
Apr  5 20:45:12 MTOLEDOB kernel: [   18.232058] Mount-cache hash table entries: 512
Apr  5 20:45:12 MTOLEDOB kernel: [   18.232229] CPU: After generic identify, caps: a7e9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
Apr  5 20:45:12 MTOLEDOB kernel: [   18.232243] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr  5 20:45:12 MTOLEDOB kernel: [   18.232247] CPU: L2 cache: 1024K
Apr  5 20:45:12 MTOLEDOB kernel: [   18.232250] CPU: After all inits, caps: a7e9f9bf 00000000 00000000 00002040 00000180 00000000 00000000
Apr  5 20:45:12 MTOLEDOB kernel: [   18.232262] Compat vDSO mapped to ffffe000.
Apr  5 20:45:12 MTOLEDOB kernel: [   18.232267] Remapping vsyscall page to ffffe000
Apr  5 20:45:12 MTOLEDOB kernel: [   18.232280] Checking 'hlt' instruction... OK.
Apr  5 20:45:12 MTOLEDOB kernel: [   18.248074] SMP alternatives: switching to UP code
Apr  5 20:45:12 MTOLEDOB kernel: [   18.248254] Freeing SMP alternatives: 11k freed
Apr  5 20:45:12 MTOLEDOB kernel: [   18.248461] Early unpacking initramfs... done
Apr  5 20:45:12 MTOLEDOB kernel: [   18.654952] ACPI: Core revision 20060707
Apr  5 20:45:12 MTOLEDOB kernel: [   18.661850] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Apr  5 20:45:12 MTOLEDOB kernel: [   18.663513] ACPI: setting ELCR to 0200 (from 0800)
Apr  5 20:45:12 MTOLEDOB kernel: [   18.665785] CPU0: Intel(R) Pentium(R) M processor 1400MHz stepping 05
Apr  5 20:45:12 MTOLEDOB kernel: [   18.665791] SMP motherboard not detected.
Apr  5 20:45:12 MTOLEDOB kernel: [   18.665794] Local APIC not detected. Using dummy APIC emulation.
Apr  5 20:45:12 MTOLEDOB kernel: [   18.665836] Brought up 1 CPUs
Apr  5 20:45:12 MTOLEDOB kernel: [   18.666122] Booting paravirtualized kernel on bare hardware
Apr  5 20:45:12 MTOLEDOB kernel: [   18.666191] Time: 20:44:48  Date: 03/05/108
Apr  5 20:45:12 MTOLEDOB kernel: [   18.666225] NET: Registered protocol family 16
Apr  5 20:45:12 MTOLEDOB kernel: [   18.666325] EISA bus registered
Apr  5 20:45:12 MTOLEDOB kernel: [   18.666330] ACPI: bus type pci registered
Apr  5 20:45:12 MTOLEDOB kernel: [   18.699898] PCI: PCI BIOS revision 2.10 entry at 0xfc96e, last bus=2
Apr  5 20:45:12 MTOLEDOB kernel: [   18.699901] PCI: Using configuration type 1
Apr  5 20:45:12 MTOLEDOB kernel: [   18.699903] Setting up standard PCI resources
Apr  5 20:45:12 MTOLEDOB kernel: [   18.711994] ACPI: Interpreter enabled
Apr  5 20:45:12 MTOLEDOB kernel: [   18.711998] ACPI: Using PIC for interrupt routing
Apr  5 20:45:12 MTOLEDOB kernel: [   18.713438] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr  5 20:45:12 MTOLEDOB kernel: [   18.713449] PCI: Probing PCI hardware (bus 00)
Apr  5 20:45:12 MTOLEDOB kernel: [   18.713591] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
Apr  5 20:45:12 MTOLEDOB kernel: [   18.719751] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
Apr  5 20:45:12 MTOLEDOB kernel: [   18.719756] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
Apr  5 20:45:12 MTOLEDOB kernel: [   18.719989] Boot video device is 0000:01:00.0
Apr  5 20:45:12 MTOLEDOB kernel: [   18.720242] PCI: Transparent bridge - 0000:00:1e.0
Apr  5 20:45:12 MTOLEDOB kernel: [   18.720306] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
Apr  5 20:45:12 MTOLEDOB kernel: [   18.720309] Please report the result to linux-kernel to fix this permanently
Apr  5 20:45:12 MTOLEDOB kernel: [   18.720354] PCI: Bus #07 (-#0a) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
Apr  5 20:45:12 MTOLEDOB kernel: [   18.720357] Please report the result to linux-kernel to fix this permanently
Apr  5 20:45:12 MTOLEDOB kernel: [   18.720376] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr  5 20:45:12 MTOLEDOB kernel: [   18.746709] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
Apr  5 20:45:12 MTOLEDOB kernel: [   18.746997] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
Apr  5 20:45:12 MTOLEDOB kernel: [   18.747281] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
Apr  5 20:45:12 MTOLEDOB kernel: [   18.747573] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
Apr  5 20:45:12 MTOLEDOB kernel: [   18.747843] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Apr  5 20:45:12 MTOLEDOB kernel: [   18.748151] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Apr  5 20:45:12 MTOLEDOB kernel: [   18.749459] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Apr  5 20:45:12 MTOLEDOB kernel: [   18.750286] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Apr  5 20:45:12 MTOLEDOB kernel: [   18.751393] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr  5 20:45:12 MTOLEDOB kernel: [   18.751410] pnp: PnP ACPI init
Apr  5 20:45:12 MTOLEDOB kernel: [   18.784575] pnp: PnP ACPI: found 13 devices
Apr  5 20:45:12 MTOLEDOB kernel: [   18.784582] PnPBIOS: Disabled by ACPI PNP
Apr  5 20:45:12 MTOLEDOB kernel: [   18.784638] PCI: Using ACPI for IRQ routing
Apr  5 20:45:12 MTOLEDOB kernel: [   18.784642] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr  5 20:45:12 MTOLEDOB kernel: [   18.791060] NET: Registered protocol family 8
Apr  5 20:45:12 MTOLEDOB kernel: [   18.791063] NET: Registered protocol family 20
Apr  5 20:45:12 MTOLEDOB kernel: [   18.796951] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
Apr  5 20:45:12 MTOLEDOB kernel: [   18.796955] pnp: 00:02: ioport range 0x800-0x805 could not be reserved
Apr  5 20:45:12 MTOLEDOB kernel: [   18.796959] pnp: 00:02: ioport range 0x808-0x80f could not be reserved
Apr  5 20:45:12 MTOLEDOB kernel: [   18.796966] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
Apr  5 20:45:12 MTOLEDOB kernel: [   18.796969] pnp: 00:03: ioport range 0x806-0x807 has been reserved
Apr  5 20:45:12 MTOLEDOB kernel: [   18.796973] pnp: 00:03: ioport range 0x810-0x85f could not be reserved
Apr  5 20:45:12 MTOLEDOB kernel: [   18.796977] pnp: 00:03: ioport range 0x860-0x87f has been reserved
Apr  5 20:45:12 MTOLEDOB kernel: [   18.796980] pnp: 00:03: ioport range 0x880-0x8bf has been reserved
Apr  5 20:45:12 MTOLEDOB kernel: [   18.796984] pnp: 00:03: ioport range 0x8c0-0x8df has been reserved
Apr  5 20:45:12 MTOLEDOB kernel: [   18.796992] pnp: 00:08: ioport range 0x900-0x97f has been reserved
Apr  5 20:45:12 MTOLEDOB kernel: [   18.797295] PCI: Bridge: 0000:00:01.0
Apr  5 20:45:12 MTOLEDOB kernel: [   18.797298]   IO window: c000-cfff
Apr  5 20:45:12 MTOLEDOB kernel: [   18.797303]   MEM window: fc000000-fdffffff
Apr  5 20:45:12 MTOLEDOB kernel: [   18.797308]   PREFETCH window: e8000000-efffffff
Apr  5 20:45:12 MTOLEDOB kernel: [   18.797322] PCI: Bus 3, cardbus bridge: 0000:02:01.0
Apr  5 20:45:12 MTOLEDOB kernel: [   18.797325]   IO window: 0000d000-0000d0ff
Apr  5 20:45:12 MTOLEDOB kernel: [   18.797329]   IO window: 0000d400-0000d4ff
Apr  5 20:45:12 MTOLEDOB kernel: [   18.797334]   PREFETCH window: 30000000-33ffffff
Apr  5 20:45:12 MTOLEDOB kernel: [   18.797339]   MEM window: 3c000000-3fffffff
Apr  5 20:45:12 MTOLEDOB kernel: [   18.797343] PCI: Bus 7, cardbus bridge: 0000:02:01.1
Apr  5 20:45:12 MTOLEDOB kernel: [   18.797346]   IO window: 0000d800-0000d8ff
Apr  5 20:45:12 MTOLEDOB kernel: [   18.797351]   IO window: 0000dc00-0000dcff
Apr  5 20:45:12 MTOLEDOB kernel: [   18.797355]   PREFETCH window: 34000000-37ffffff
Apr  5 20:45:12 MTOLEDOB kernel: [   18.797360]   MEM window: 40000000-43ffffff
Apr  5 20:45:12 MTOLEDOB kernel: [   18.797364] PCI: Bridge: 0000:00:1e.0
Apr  5 20:45:12 MTOLEDOB kernel: [   18.797368]   IO window: d000-efff
Apr  5 20:45:12 MTOLEDOB kernel: [   18.797373]   MEM window: f6000000-fbffffff
Apr  5 20:45:12 MTOLEDOB kernel: [   18.797378]   PREFETCH window: 30000000-37ffffff
Apr  5 20:45:12 MTOLEDOB kernel: [   18.797395] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Apr  5 20:45:12 MTOLEDOB kernel: [   18.797408] PCI: Enabling device 0000:02:01.0 (0000 -> 0003)
Apr  5 20:45:12 MTOLEDOB kernel: [   18.797617] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Apr  5 20:45:12 MTOLEDOB kernel: [   18.797621] PCI: setting IRQ 11 as level-triggered
Apr  5 20:45:12 MTOLEDOB kernel: [   18.797625] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:45:12 MTOLEDOB kernel: [   18.797642] PCI: Enabling device 0000:02:01.1 (0000 -> 0003)
Apr  5 20:45:12 MTOLEDOB kernel: [   18.797647] ACPI: PCI Interrupt 0000:02:01.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:45:12 MTOLEDOB kernel: [   18.797683] NET: Registered protocol family 2
Apr  5 20:45:12 MTOLEDOB kernel: [   18.836046] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Apr  5 20:45:12 MTOLEDOB kernel: [   18.836139] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Apr  5 20:45:12 MTOLEDOB kernel: [   18.836274] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
Apr  5 20:45:12 MTOLEDOB kernel: [   18.836343] TCP: Hash tables configured (established 16384 bind 8192)
Apr  5 20:45:12 MTOLEDOB kernel: [   18.836347] TCP reno registered
Apr  5 20:45:12 MTOLEDOB kernel: [   18.848108] checking if image is initramfs... it is
Apr  5 20:45:12 MTOLEDOB kernel: [   19.646916] Freeing initrd memory: 6761k freed
Apr  5 20:45:12 MTOLEDOB kernel: [   19.647395] audit: initializing netlink socket (disabled)
Apr  5 20:45:12 MTOLEDOB kernel: [   19.647415] audit(1207428289.696:1): initialized
Apr  5 20:45:12 MTOLEDOB kernel: [   19.647583] VFS: Disk quotas dquot_6.5.1
Apr  5 20:45:12 MTOLEDOB kernel: [   19.647610] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr  5 20:45:12 MTOLEDOB kernel: [   19.647676] io scheduler noop registered
Apr  5 20:45:12 MTOLEDOB kernel: [   19.647680] io scheduler anticipatory registered
Apr  5 20:45:12 MTOLEDOB kernel: [   19.647683] io scheduler deadline registered
Apr  5 20:45:12 MTOLEDOB kernel: [   19.647697] io scheduler cfq registered (default)
Apr  5 20:45:12 MTOLEDOB kernel: [   19.648082] isapnp: Scanning for PnP cards...
Apr  5 20:45:12 MTOLEDOB kernel: [   20.001014] isapnp: No Plug & Play device found
Apr  5 20:45:12 MTOLEDOB kernel: [   20.037003] Real Time Clock Driver v1.12ac
Apr  5 20:45:12 MTOLEDOB kernel: [   20.037071] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr  5 20:45:12 MTOLEDOB kernel: [   20.037203] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr  5 20:45:12 MTOLEDOB kernel: [   20.038083] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr  5 20:45:12 MTOLEDOB kernel: [   20.038598] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
Apr  5 20:45:12 MTOLEDOB kernel: [   20.038604] PCI: setting IRQ 5 as level-triggered
Apr  5 20:45:12 MTOLEDOB kernel: [   20.038608] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Apr  5 20:45:12 MTOLEDOB kernel: [   20.038619] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
Apr  5 20:45:12 MTOLEDOB kernel: [   20.038707] mice: PS/2 mouse device common for all mice
Apr  5 20:45:12 MTOLEDOB kernel: [   20.039360] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr  5 20:45:12 MTOLEDOB kernel: [   20.039660] input: Macintosh mouse button emulation as /class/input/input0
Apr  5 20:45:12 MTOLEDOB kernel: [   20.039699] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Apr  5 20:45:12 MTOLEDOB kernel: [   20.039704] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Apr  5 20:45:12 MTOLEDOB kernel: [   20.039903] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Apr  5 20:45:12 MTOLEDOB kernel: [   20.045766] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr  5 20:45:12 MTOLEDOB kernel: [   20.045772] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr  5 20:45:12 MTOLEDOB kernel: [   20.045968] EISA: Probing bus 0 at eisa.0
Apr  5 20:45:12 MTOLEDOB kernel: [   20.045996] EISA: Detected 0 cards.
Apr  5 20:45:12 MTOLEDOB kernel: [   20.076113] TCP cubic registered
Apr  5 20:45:12 MTOLEDOB kernel: [   20.076126] NET: Registered protocol family 1
Apr  5 20:45:12 MTOLEDOB kernel: [   20.076154] Using IPI No-Shortcut mode
Apr  5 20:45:12 MTOLEDOB kernel: [   20.076225] ACPI: (supports S0 S1 S3 S4 S5)
Apr  5 20:45:12 MTOLEDOB kernel: [   20.076277]   Magic number: 4:169:750
Apr  5 20:45:12 MTOLEDOB kernel: [   20.076281]   hash matches device ttyS1
Apr  5 20:45:12 MTOLEDOB kernel: [   20.076749] Freeing unused kernel memory: 328k freed
Apr  5 20:45:12 MTOLEDOB kernel: [   20.078456] input: AT Translated Set 2 keyboard as /class/input/input1
Apr  5 20:45:12 MTOLEDOB kernel: [   20.079955] Time: tsc clocksource has been installed.
Apr  5 20:45:12 MTOLEDOB kernel: [   21.311250] Capability LSM initialized
Apr  5 20:45:12 MTOLEDOB kernel: [   21.353397] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
Apr  5 20:45:12 MTOLEDOB kernel: [   21.353406] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr  5 20:45:12 MTOLEDOB kernel: [   21.357553] ACPI: Thermal Zone [THM] (54 C)
Apr  5 20:45:12 MTOLEDOB kernel: [   21.744102] usbcore: registered new interface driver usbfs
Apr  5 20:45:12 MTOLEDOB kernel: [   21.744130] usbcore: registered new interface driver hub
Apr  5 20:45:12 MTOLEDOB kernel: [   21.744153] usbcore: registered new device driver usb
Apr  5 20:45:12 MTOLEDOB kernel: [   21.745857] USB Universal Host Controller Interface driver v3.0
Apr  5 20:45:12 MTOLEDOB kernel: [   21.746202] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
Apr  5 20:45:12 MTOLEDOB kernel: [   21.746206] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:45:12 MTOLEDOB kernel: [   21.746221] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Apr  5 20:45:12 MTOLEDOB kernel: [   21.746225] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr  5 20:45:12 MTOLEDOB kernel: [   21.746429] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Apr  5 20:45:12 MTOLEDOB kernel: [   21.746455] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
Apr  5 20:45:12 MTOLEDOB kernel: [   21.746576] usb usb1: configuration #1 chosen from 1 choice
Apr  5 20:45:12 MTOLEDOB kernel: [   21.746604] hub 1-0:1.0: USB hub found
Apr  5 20:45:12 MTOLEDOB kernel: [   21.746610] hub 1-0:1.0: 2 ports detected
Apr  5 20:45:12 MTOLEDOB kernel: [   21.815113] SCSI subsystem initialized
Apr  5 20:45:12 MTOLEDOB kernel: [   21.826754] libata version 2.20 loaded.
Apr  5 20:45:12 MTOLEDOB kernel: [   21.848134] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:45:12 MTOLEDOB kernel: [   21.848151] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Apr  5 20:45:12 MTOLEDOB kernel: [   21.848156] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr  5 20:45:12 MTOLEDOB kernel: [   21.848182] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Apr  5 20:45:12 MTOLEDOB kernel: [   21.848208] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
Apr  5 20:45:12 MTOLEDOB kernel: [   21.848317] usb usb2: configuration #1 chosen from 1 choice
Apr  5 20:45:12 MTOLEDOB kernel: [   21.848349] hub 2-0:1.0: USB hub found
Apr  5 20:45:12 MTOLEDOB kernel: [   21.848356] hub 2-0:1.0: 2 ports detected
Apr  5 20:45:12 MTOLEDOB kernel: [   21.952400] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
Apr  5 20:45:12 MTOLEDOB kernel: [   21.952406] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:45:12 MTOLEDOB kernel: [   21.952421] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Apr  5 20:45:12 MTOLEDOB kernel: [   21.952426] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr  5 20:45:12 MTOLEDOB kernel: [   21.952456] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Apr  5 20:45:12 MTOLEDOB kernel: [   21.952483] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
Apr  5 20:45:12 MTOLEDOB kernel: [   21.952599] usb usb3: configuration #1 chosen from 1 choice
Apr  5 20:45:12 MTOLEDOB kernel: [   21.952630] hub 3-0:1.0: USB hub found
Apr  5 20:45:12 MTOLEDOB kernel: [   21.952642] hub 3-0:1.0: 2 ports detected
Apr  5 20:45:12 MTOLEDOB kernel: [   22.057297] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
Apr  5 20:45:12 MTOLEDOB kernel: [   22.057304] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:45:12 MTOLEDOB kernel: [   22.057323] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Apr  5 20:45:12 MTOLEDOB kernel: [   22.057327] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr  5 20:45:12 MTOLEDOB kernel: [   22.057371] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
Apr  5 20:45:12 MTOLEDOB kernel: [   22.057411] ehci_hcd 0000:00:1d.7: debug port 1
Apr  5 20:45:12 MTOLEDOB kernel: [   22.057418] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Apr  5 20:45:12 MTOLEDOB kernel: [   22.057429] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf4fffc00
Apr  5 20:45:12 MTOLEDOB kernel: [   22.061316] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Apr  5 20:45:12 MTOLEDOB kernel: [   22.061415] usb usb4: configuration #1 chosen from 1 choice
Apr  5 20:45:12 MTOLEDOB kernel: [   22.061457] hub 4-0:1.0: USB hub found
Apr  5 20:45:12 MTOLEDOB kernel: [   22.061466] hub 4-0:1.0: 6 ports detected
Apr  5 20:45:12 MTOLEDOB kernel: [    4.012000] Time: acpi_pm clocksource has been installed.
Apr  5 20:45:12 MTOLEDOB kernel: [    4.032000] ata_piix 0000:00:1f.1: version 2.10ac1
Apr  5 20:45:12 MTOLEDOB kernel: [    4.032000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
Apr  5 20:45:12 MTOLEDOB kernel: [    4.032000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:45:12 MTOLEDOB kernel: [    4.032000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Apr  5 20:45:12 MTOLEDOB kernel: [    4.032000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
Apr  5 20:45:12 MTOLEDOB kernel: [    4.032000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
Apr  5 20:45:12 MTOLEDOB kernel: [    4.032000] scsi0 : ata_piix
Apr  5 20:45:12 MTOLEDOB kernel: [    4.196000] ata1.00: ATA-6: ST980815A, 3.ALD, max UDMA/100
Apr  5 20:45:12 MTOLEDOB kernel: [    4.196000] ata1.00: 156301488 sectors, multi 8: LBA48 
Apr  5 20:45:12 MTOLEDOB kernel: [    4.204000] ata1.00: configured for UDMA/100
Apr  5 20:45:12 MTOLEDOB kernel: [    4.204000] scsi1 : ata_piix
Apr  5 20:45:12 MTOLEDOB kernel: [    4.524000] ata2.00: ATAPI, max UDMA/33
Apr  5 20:45:12 MTOLEDOB kernel: [    4.688000] ata2.00: configured for UDMA/33
Apr  5 20:45:12 MTOLEDOB kernel: [    4.688000] scsi 0:0:0:0: Direct-Access     ATA      ST980815A        3.AL PQ: 0 ANSI: 5
Apr  5 20:45:12 MTOLEDOB kernel: [    4.692000] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4241N A101 PQ: 0 ANSI: 5
Apr  5 20:45:12 MTOLEDOB kernel: [    4.700000] tg3.c:v3.72 (January 8, 2007)
Apr  5 20:45:12 MTOLEDOB kernel: [    4.700000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:45:12 MTOLEDOB kernel: [    4.740000] eth0: Tigon3 [partno(BCM95705A50) rev 3001 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000Base-T Ethernet 00:11:43:53:d5:22
Apr  5 20:45:12 MTOLEDOB kernel: [    4.740000] eth0: RXcsums[1] LinkChgREG[1] MIirq[1] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
Apr  5 20:45:12 MTOLEDOB kernel: [    4.740000] eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
Apr  5 20:45:12 MTOLEDOB kernel: [    4.744000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
Apr  5 20:45:12 MTOLEDOB kernel: [    4.744000] sda: Write Protect is off
Apr  5 20:45:12 MTOLEDOB kernel: [    4.744000] sda: Mode Sense: 00 3a 00 00
Apr  5 20:45:12 MTOLEDOB kernel: [    4.744000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  5 20:45:12 MTOLEDOB kernel: [    4.744000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
Apr  5 20:45:12 MTOLEDOB kernel: [    4.744000] sda: Write Protect is off
Apr  5 20:45:12 MTOLEDOB kernel: [    4.744000] sda: Mode Sense: 00 3a 00 00
Apr  5 20:45:12 MTOLEDOB kernel: [    4.744000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  5 20:45:12 MTOLEDOB kernel: [    4.744000]  sda: sda1 sda2 sda3 < sda5 >
Apr  5 20:45:12 MTOLEDOB kernel: [    4.800000] sd 0:0:0:0: Attached scsi disk sda
Apr  5 20:45:12 MTOLEDOB kernel: [    4.804000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr  5 20:45:12 MTOLEDOB kernel: [    4.804000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
Apr  5 20:45:12 MTOLEDOB kernel: [    4.828000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Apr  5 20:45:12 MTOLEDOB kernel: [    4.828000] Uniform CD-ROM driver Revision: 3.20
Apr  5 20:45:12 MTOLEDOB kernel: [    4.828000] sr 1:0:0:0: Attached scsi CD-ROM sr0
Apr  5 20:45:12 MTOLEDOB kernel: [    5.108000] Attempting manual resume
Apr  5 20:45:12 MTOLEDOB kernel: [    5.108000] swsusp: Resume From Partition 8:5
Apr  5 20:45:12 MTOLEDOB kernel: [    5.108000] PM: Checking swsusp image.
Apr  5 20:45:12 MTOLEDOB kernel: [    5.108000] PM: Resume from disk failed.
Apr  5 20:45:12 MTOLEDOB kernel: [    5.128000] EXT3-fs: INFO: recovery required on readonly filesystem.
Apr  5 20:45:12 MTOLEDOB kernel: [    5.128000] EXT3-fs: write access will be enabled during recovery.
Apr  5 20:45:12 MTOLEDOB kernel: [    5.616000] kjournald starting.  Commit interval 5 seconds
Apr  5 20:45:12 MTOLEDOB kernel: [    5.616000] EXT3-fs: recovery complete.
Apr  5 20:45:12 MTOLEDOB kernel: [    5.624000] EXT3-fs: mounted filesystem with ordered data mode.
Apr  5 20:45:12 MTOLEDOB kernel: [   17.336000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr  5 20:45:12 MTOLEDOB kernel: [   17.336000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr  5 20:45:12 MTOLEDOB kernel: [   17.672000] iTCO_vendor_support: vendor-support=0
Apr  5 20:45:12 MTOLEDOB kernel: [   17.672000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
Apr  5 20:45:12 MTOLEDOB kernel: [   17.672000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x0860)
Apr  5 20:45:12 MTOLEDOB kernel: [   17.672000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Apr  5 20:45:12 MTOLEDOB kernel: [   17.684000] intel_rng: FWH not detected
Apr  5 20:45:12 MTOLEDOB kernel: [   18.348000] Linux agpgart interface v0.101 (c) Dave Jones
Apr  5 20:45:12 MTOLEDOB kernel: [   18.352000] agpgart: Detected an Intel 855PM Chipset.
Apr  5 20:45:12 MTOLEDOB kernel: [   18.360000] agpgart: AGP aperture is 128M @ 0xe0000000
Apr  5 20:45:12 MTOLEDOB kernel: [   18.396000] Yenta: CardBus bridge found at 0000:02:01.0 [1028:011d]
Apr  5 20:45:12 MTOLEDOB kernel: [   18.396000] Yenta O2: res at 0x94/0xD4: 00/ea
Apr  5 20:45:12 MTOLEDOB kernel: [   18.396000] Yenta O2: enabling read prefetch/write burst
Apr  5 20:45:12 MTOLEDOB kernel: [   18.524000] Yenta: ISA IRQ mask 0x0498, PCI irq 11
Apr  5 20:45:12 MTOLEDOB kernel: [   18.524000] Socket status: 30000006
Apr  5 20:45:12 MTOLEDOB kernel: [   18.524000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
Apr  5 20:45:12 MTOLEDOB kernel: [   18.524000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
Apr  5 20:45:12 MTOLEDOB kernel: [   18.524000] cs: IO port probe 0xd000-0xefff: clean.
Apr  5 20:45:12 MTOLEDOB kernel: [   18.524000] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
Apr  5 20:45:12 MTOLEDOB kernel: [   18.524000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x37ffffff
Apr  5 20:45:12 MTOLEDOB kernel: [   18.524000] Yenta: CardBus bridge found at 0000:02:01.1 [1028:011d]
Apr  5 20:45:12 MTOLEDOB kernel: [   18.652000] Yenta: ISA IRQ mask 0x0498, PCI irq 11
Apr  5 20:45:12 MTOLEDOB kernel: [   18.652000] Socket status: 30000410
Apr  5 20:45:12 MTOLEDOB kernel: [   18.652000] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
Apr  5 20:45:12 MTOLEDOB kernel: [   18.652000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
Apr  5 20:45:12 MTOLEDOB kernel: [   18.652000] cs: IO port probe 0xd000-0xefff: clean.
Apr  5 20:45:12 MTOLEDOB kernel: [   18.652000] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
Apr  5 20:45:12 MTOLEDOB kernel: [   18.652000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x37ffffff
Apr  5 20:45:12 MTOLEDOB kernel: [   18.760000] input: PC Speaker as /class/input/input2
Apr  5 20:45:12 MTOLEDOB kernel: [   18.796000] parport: PnPBIOS parport detected.
Apr  5 20:45:12 MTOLEDOB kernel: [   18.796000] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Apr  5 20:45:12 MTOLEDOB kernel: [   18.812000] ieee80211_crypt: registered algorithm 'NULL'
Apr  5 20:45:12 MTOLEDOB kernel: [   18.836000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Apr  5 20:45:12 MTOLEDOB kernel: [   18.836000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Apr  5 20:45:12 MTOLEDOB kernel: [   19.016000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
Apr  5 20:45:12 MTOLEDOB kernel: [   19.016000] ipw2100: Copyright(c) 2003-2006 Intel Corporation
Apr  5 20:45:12 MTOLEDOB kernel: [   19.016000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Apr  5 20:45:12 MTOLEDOB kernel: [   19.016000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
Apr  5 20:45:12 MTOLEDOB kernel: [   19.288000] pccard: PCMCIA card inserted into slot 1
Apr  5 20:45:12 MTOLEDOB kernel: [   19.348000] input: DualPoint Stick as /class/input/input3
Apr  5 20:45:12 MTOLEDOB kernel: [   19.368000] input: AlpsPS/2 ALPS DualPoint TouchPad as /class/input/input4
Apr  5 20:45:12 MTOLEDOB kernel: [   19.404000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Apr  5 20:45:12 MTOLEDOB kernel: [   19.404000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
Apr  5 20:45:12 MTOLEDOB kernel: [   19.464000] cs: memory probe 0xf6000000-0xfbffffff: excluding 0xf6000000-0xf65fffff 0xf6c00000-0xf71fffff 0xf7e00000-0xf83fffff 0xf9c00000-0xfa1fffff 0xfae00000-0xfb3fffff
Apr  5 20:45:12 MTOLEDOB kernel: [   19.476000] pcmcia: registering new device pcmcia1.0
Apr  5 20:45:12 MTOLEDOB kernel: [   19.544000] cs: IO port probe 0x100-0x3af: clean.
Apr  5 20:45:12 MTOLEDOB kernel: [   19.568000] cs: IO port probe 0x3e0-0x4ff: clean.
Apr  5 20:45:12 MTOLEDOB kernel: [   19.568000] cs: IO port probe 0x820-0x8ff: clean.
Apr  5 20:45:12 MTOLEDOB kernel: [   19.568000] cs: IO port probe 0xc00-0xcf7: clean.
Apr  5 20:45:12 MTOLEDOB kernel: [   19.568000] cs: IO port probe 0xa00-0xaff: clean.
Apr  5 20:45:12 MTOLEDOB kernel: [   19.572000] cs: IO port probe 0x100-0x3af: clean.
Apr  5 20:45:12 MTOLEDOB kernel: [   19.572000] cs: IO port probe 0x3e0-0x4ff: clean.
Apr  5 20:45:12 MTOLEDOB kernel: [   19.572000] cs: IO port probe 0x820-0x8ff: clean.
Apr  5 20:45:12 MTOLEDOB kernel: [   19.572000] cs: IO port probe 0xc00-0xcf7: clean.
Apr  5 20:45:12 MTOLEDOB kernel: [   19.572000] cs: IO port probe 0xa00-0xaff: clean.
Apr  5 20:45:12 MTOLEDOB kernel: [   20.224000] intel8x0_measure_ac97_clock: measured 55464 usecs
Apr  5 20:45:12 MTOLEDOB kernel: [   20.224000] intel8x0: clocking to 48000
Apr  5 20:45:12 MTOLEDOB kernel: [   20.680000] fuse init (API version 7.8)
Apr  5 20:45:12 MTOLEDOB kernel: [   20.720000] lp0: using parport0 (interrupt-driven).
Apr  5 20:45:12 MTOLEDOB kernel: [   20.756000] Adding 1510068k swap on /dev/sda5.  Priority:-1 extents:1 across:1510068k
Apr  5 20:45:12 MTOLEDOB kernel: [   21.064000] EXT3 FS on sda2, internal journal
Apr  5 20:45:12 MTOLEDOB kernel: [   22.024000] ACPI: AC Adapter [AC] (on-line)
Apr  5 20:45:12 MTOLEDOB kernel: [   22.088000] input: Lid Switch as /class/input/input5
Apr  5 20:45:12 MTOLEDOB kernel: [   22.092000] ACPI: Lid Switch [LID]
Apr  5 20:45:12 MTOLEDOB kernel: [   22.140000] input: Power Button (CM) as /class/input/input6
Apr  5 20:45:12 MTOLEDOB kernel: [   22.144000] ACPI: Power Button (CM) [PBTN]
Apr  5 20:45:12 MTOLEDOB kernel: [   22.188000] input: Sleep Button (CM) as /class/input/input7
Apr  5 20:45:12 MTOLEDOB kernel: [   22.196000] ACPI: Sleep Button (CM) [SBTN]
Apr  5 20:45:12 MTOLEDOB kernel: [   22.220000] ACPI: ACPI Dock Station Driver 
Apr  5 20:45:12 MTOLEDOB kernel: [   22.628000] ACPI: Battery Slot [BAT0] (battery present)
Apr  5 20:45:12 MTOLEDOB kernel: [   22.628000] ACPI: Battery Slot [BAT1] (battery absent)
Apr  5 20:45:12 MTOLEDOB kernel: [   22.640000] Using specific hotkey driver
Apr  5 20:45:12 MTOLEDOB kernel: [   22.672000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Apr  5 20:45:12 MTOLEDOB kernel: [   22.740000] ibm_acpi: ec object not found
Apr  5 20:45:12 MTOLEDOB kernel: [   22.792000] pcc_acpi: loading...
Apr  5 20:45:12 MTOLEDOB NetworkManager: <info>  starting... 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.457296] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_3340'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.697439] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_3341'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.698520] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_4c66'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.700314] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c2'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.700872] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.701349] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.701818] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c4'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.702287] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.702756] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.703242] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c7'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.703710] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.704178] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.704646] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24cd'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.705113] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.705580] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.706083] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.706570] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_165d'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.707052] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1217_7113'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.707520] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1217_7113_0'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.707987] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pcmcia__1__1'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.708451] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_1043'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.708916] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24cc'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.709381] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.709845] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.710309] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_scsi_device_lun0'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.710774] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_0'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.711275] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_0_scsi_device_lun0'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.711743] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.712206] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c6'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.712669] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_dock_0'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.713130] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.713593] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.714054] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.714518] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.714990] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.715453] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.715913] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.716374] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_vesafb_0'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.716852] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.717333] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.717796] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.718255] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.718714] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.719183] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.719641] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.720099] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.720557] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.721014] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.721470] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.721926] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.722401] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0401'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.722860] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.723360] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.723819] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.724275] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.724731] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.725722] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Apr  5 20:45:12 MTOLEDOB NetworkManager: <debug> [1207449912.785202] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_11_43_53_d5_22'). 
Apr  5 20:45:13 MTOLEDOB kernel: [   24.444000] PM: Writing back config space on device 0000:02:00.0 at offset c (was ffbf0000, writing 0)
Apr  5 20:45:13 MTOLEDOB kernel: [   24.444000] PM: Writing back config space on device 0000:02:00.0 at offset b (was 165d14e4, writing 865d1028)
Apr  5 20:45:13 MTOLEDOB kernel: [   24.444000] PM: Writing back config space on device 0000:02:00.0 at offset 3 (was 0, writing 2008)
Apr  5 20:45:13 MTOLEDOB kernel: [   24.444000] PM: Writing back config space on device 0000:02:00.0 at offset 2 (was 2000000, writing 2000001)
Apr  5 20:45:13 MTOLEDOB kernel: [   24.444000] PM: Writing back config space on device 0000:02:00.0 at offset 1 (was 2b00000, writing 2b00106)
Apr  5 20:45:13 MTOLEDOB NetworkManager: <info>  eth0: Device is fully-supported using driver 'tg3'. 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <info>  Deactivating device eth0. 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.229950] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_0c_f1_1c_20_6b'). 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <info>  eth1: Device is fully-supported using driver 'ipw2100'. 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <info>  Deactivating device eth1. 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.395722] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_scsi_device_lun0_scsi_generic'). 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.396409] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.396894] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_pcm_1'). 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.397369] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_pcm_0'). 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.397843] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_control__1'). 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.398316] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_pcm_0_0'). 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.398786] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_mixer__1'). 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.399271] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_0'). 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.399740] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_playback_0'). 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.400209] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_1'). 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.400710] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_2'). 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.401181] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_3'). 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.401650] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_playback_4'). 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.402116] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.402585] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.403216] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.403715] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.404253] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.404730] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.405220] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_3'). 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.405697] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'). 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.406164] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.406629] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.407104] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.407571] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.408036] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST980815A_5LY1VWH9'). 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.465951] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_606C05936C0564DE'). 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.472361] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_241da2db_0e86_4d13_ba31_7e747e81c264'). 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.509031] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part3_size_1024'). 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.514861] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_aaabdd49_42ff_4b7f_ac15_b1a4f0ed1a87'). 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.637704] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT1'). 
Apr  5 20:45:13 MTOLEDOB gdm[4561]: WARNING: Didn't understand `' (expected true or false) 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.714683] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.715337] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.715814] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Apr  5 20:45:13 MTOLEDOB NetworkManager: <debug> [1207449913.716606] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_RW/DVD_GCC_4241N'). 
Apr  5 20:45:14 MTOLEDOB kernel: [   25.932000] [drm] Initialized drm 1.1.0 20060810
Apr  5 20:45:14 MTOLEDOB kernel: [   25.944000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:45:14 MTOLEDOB kernel: [   25.944000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
Apr  5 20:46:41 MTOLEDOB syslogd 1.4.1#21ubuntu3: restart.
Apr  5 20:46:41 MTOLEDOB kernel: Inspecting /boot/System.map-2.6.22-14-generic
Apr  5 20:46:41 MTOLEDOB kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Apr  5 20:46:41 MTOLEDOB kernel: Symbols match kernel version 2.6.22.
Apr  5 20:46:41 MTOLEDOB kernel: No module symbols loaded - kernel modules not enabled. 
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000] BIOS-provided physical RAM map:
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffae000 (usable)
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 000000001ffae000 - 0000000020000000 (reserved)
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fee00000 (reserved)
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000] 0MB HIGHMEM available.
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000] 511MB LOWMEM available.
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000] Entering add_active_range(0, 0, 130990) 0 entries of 256 used
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000] Zone PFN ranges:
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000]   DMA             0 ->     4096
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000]   Normal       4096 ->   130990
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000]   HighMem    130990 ->   130990
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000]     0:        0 ->   130990
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000] On node 0 totalpages: 130990
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000]   Normal zone: 991 pages used for memmap
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000]   Normal zone: 125903 pages, LIFO batch:31
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000] DMI 2.3 present.
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FDF00 checksum 0
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000] ACPI: RSDP 000FDF00, 0014 (r0 DELL  )
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000] ACPI: RSDT 1FFF0000, 002C (r1 DELL    CPi R   27D5011A ASL        61)
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000] ACPI: FACP 1FFF0400, 0074 (r1 DELL    CPi R   27D5011A ASL        61)
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000] ACPI: DSDT 1FFF0C00, 2E1A (r1 INT430 SYSFexxx     1001 MSFT  100000E)
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000] ACPI: FACS 1FFFF800, 0040
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000] ACPI: ASF! 1FFF0800, 005B (r16 DELL    CPi R   27D5011A ASL        61)
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:deda0000)
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000] Built 1 zonelists.  Total pages: 129967
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000] Kernel command line: root=UUID=241da2db-0e86-4d13-ba31-7e747e81c264 ro quiet splash
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000] mapped APIC to ffffd000 (0140d000)
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000] Initializing CPU#0
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
Apr  5 20:46:41 MTOLEDOB kernel: [    0.000000] Detected 1398.892 MHz processor.
Apr  5 20:46:41 MTOLEDOB kernel: [   10.478067] Console: colour VGA+ 80x25
Apr  5 20:46:41 MTOLEDOB kernel: [   10.478369] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr  5 20:46:41 MTOLEDOB kernel: [   10.478692] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr  5 20:46:41 MTOLEDOB kernel: [   10.496362] Memory: 506636k/523960k available (2015k kernel code, 16752k reserved, 915k data, 364k init, 0k highmem)
Apr  5 20:46:41 MTOLEDOB kernel: [   10.496375] virtual kernel memory layout:
Apr  5 20:46:41 MTOLEDOB kernel: [   10.496376]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Apr  5 20:46:41 MTOLEDOB kernel: [   10.496378]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr  5 20:46:41 MTOLEDOB kernel: [   10.496380]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
Apr  5 20:46:41 MTOLEDOB kernel: [   10.496382]     lowmem  : 0xc0000000 - 0xdffae000   ( 511 MB)
Apr  5 20:46:41 MTOLEDOB kernel: [   10.496383]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Apr  5 20:46:41 MTOLEDOB kernel: [   10.496385]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
Apr  5 20:46:41 MTOLEDOB kernel: [   10.496387]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
Apr  5 20:46:41 MTOLEDOB kernel: [   10.496391] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr  5 20:46:41 MTOLEDOB kernel: [   10.496441] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Apr  5 20:46:41 MTOLEDOB kernel: [   10.576460] Calibrating delay using timer specific routine.. 2799.71 BogoMIPS (lpj=5599420)
Apr  5 20:46:41 MTOLEDOB kernel: [   10.576492] Security Framework v1.0.0 initialized
Apr  5 20:46:41 MTOLEDOB kernel: [   10.576501] SELinux:  Disabled at boot.
Apr  5 20:46:41 MTOLEDOB kernel: [   10.576519] Mount-cache hash table entries: 512
Apr  5 20:46:41 MTOLEDOB kernel: [   10.576676] CPU: After generic identify, caps: a7e9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
Apr  5 20:46:41 MTOLEDOB kernel: [   10.576690] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr  5 20:46:41 MTOLEDOB kernel: [   10.576694] CPU: L2 cache: 1024K
Apr  5 20:46:41 MTOLEDOB kernel: [   10.576697] CPU: After all inits, caps: a7e9f9bf 00000000 00000000 00002040 00000180 00000000 00000000
Apr  5 20:46:41 MTOLEDOB kernel: [   10.576709] Compat vDSO mapped to ffffe000.
Apr  5 20:46:41 MTOLEDOB kernel: [   10.576723] Checking 'hlt' instruction... OK.
Apr  5 20:46:41 MTOLEDOB kernel: [   10.592569] SMP alternatives: switching to UP code
Apr  5 20:46:41 MTOLEDOB kernel: [   10.592750] Freeing SMP alternatives: 11k freed
Apr  5 20:46:41 MTOLEDOB kernel: [   10.593056] Early unpacking initramfs... done
Apr  5 20:46:41 MTOLEDOB kernel: [   11.037662] ACPI: Core revision 20070126
Apr  5 20:46:41 MTOLEDOB kernel: [   11.037738] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Apr  5 20:46:41 MTOLEDOB kernel: [   11.039396] ACPI: setting ELCR to 0200 (from 0800)
Apr  5 20:46:41 MTOLEDOB kernel: [   11.041897] CPU0: Intel(R) Pentium(R) M processor 1400MHz stepping 05
Apr  5 20:46:41 MTOLEDOB kernel: [   11.041905] SMP motherboard not detected.
Apr  5 20:46:41 MTOLEDOB kernel: [   11.041908] Local APIC not detected. Using dummy APIC emulation.
Apr  5 20:46:41 MTOLEDOB kernel: [   11.041948] Brought up 1 CPUs
Apr  5 20:46:41 MTOLEDOB kernel: [   11.042085] Booting paravirtualized kernel on bare hardware
Apr  5 20:46:41 MTOLEDOB kernel: [   11.042153] Time: 20:46:19  Date: 03/05/108
Apr  5 20:46:41 MTOLEDOB kernel: [   11.042180] NET: Registered protocol family 16
Apr  5 20:46:41 MTOLEDOB kernel: [   11.042280] EISA bus registered
Apr  5 20:46:41 MTOLEDOB kernel: [   11.042292] ACPI: bus type pci registered
Apr  5 20:46:41 MTOLEDOB kernel: [   11.075972] PCI: PCI BIOS revision 2.10 entry at 0xfc96e, last bus=2
Apr  5 20:46:41 MTOLEDOB kernel: [   11.075976] PCI: Using configuration type 1
Apr  5 20:46:41 MTOLEDOB kernel: [   11.075978] Setting up standard PCI resources
Apr  5 20:46:41 MTOLEDOB kernel: [   11.078148] ACPI: EC: Look up EC in DSDT
Apr  5 20:46:41 MTOLEDOB kernel: [   11.085309] ACPI: Interpreter enabled
Apr  5 20:46:41 MTOLEDOB kernel: [   11.085313] ACPI: (supports S0 S1 S3 S4 S5)
Apr  5 20:46:41 MTOLEDOB kernel: [   11.085333] ACPI: Using PIC for interrupt routing
Apr  5 20:46:41 MTOLEDOB kernel: [   11.098368] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr  5 20:46:41 MTOLEDOB kernel: [   11.098392] PCI: Probing PCI hardware (bus 00)
Apr  5 20:46:41 MTOLEDOB kernel: [   11.098775] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
Apr  5 20:46:41 MTOLEDOB kernel: [   11.098780] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
Apr  5 20:46:41 MTOLEDOB kernel: [   11.099242] PCI: Transparent bridge - 0000:00:1e.0
Apr  5 20:46:41 MTOLEDOB kernel: [   11.099360] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr  5 20:46:41 MTOLEDOB kernel: [   11.099742] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Apr  5 20:46:41 MTOLEDOB kernel: [   11.099834] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Apr  5 20:46:41 MTOLEDOB kernel: [   11.114280] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
Apr  5 20:46:41 MTOLEDOB kernel: [   11.114396] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
Apr  5 20:46:41 MTOLEDOB kernel: [   11.114509] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
Apr  5 20:46:41 MTOLEDOB kernel: [   11.114622] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
Apr  5 20:46:41 MTOLEDOB kernel: [   11.114720] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Apr  5 20:46:41 MTOLEDOB kernel: [   11.114837] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Apr  5 20:46:41 MTOLEDOB kernel: [   11.114945] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr  5 20:46:41 MTOLEDOB kernel: [   11.114958] pnp: PnP ACPI init
Apr  5 20:46:41 MTOLEDOB kernel: [   11.114971] ACPI: bus type pnp registered
Apr  5 20:46:41 MTOLEDOB kernel: [   11.142809] pnp: PnP ACPI: found 13 devices
Apr  5 20:46:41 MTOLEDOB kernel: [   11.142812] ACPI: ACPI bus type pnp unregistered
Apr  5 20:46:41 MTOLEDOB kernel: [   11.142818] PnPBIOS: Disabled by ACPI PNP
Apr  5 20:46:41 MTOLEDOB kernel: [   11.142876] PCI: Using ACPI for IRQ routing
Apr  5 20:46:41 MTOLEDOB kernel: [   11.142879] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr  5 20:46:41 MTOLEDOB kernel: [   11.149316] NET: Registered protocol family 8
Apr  5 20:46:41 MTOLEDOB kernel: [   11.149319] NET: Registered protocol family 20
Apr  5 20:46:41 MTOLEDOB kernel: [   11.149383] pnp: 00:00: iomem range 0x0-0x9fbff could not be reserved
Apr  5 20:46:41 MTOLEDOB kernel: [   11.149387] pnp: 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
Apr  5 20:46:41 MTOLEDOB kernel: [   11.149391] pnp: 00:00: iomem range 0xc0000-0xcffff could not be reserved
Apr  5 20:46:41 MTOLEDOB kernel: [   11.149395] pnp: 00:00: iomem range 0xe0000-0xfffff could not be reserved
Apr  5 20:46:41 MTOLEDOB kernel: [   11.149402] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
Apr  5 20:46:41 MTOLEDOB kernel: [   11.149406] pnp: 00:02: ioport range 0x800-0x805 has been reserved
Apr  5 20:46:41 MTOLEDOB kernel: [   11.149410] pnp: 00:02: ioport range 0x808-0x80f has been reserved
Apr  5 20:46:41 MTOLEDOB kernel: [   11.149416] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
Apr  5 20:46:41 MTOLEDOB kernel: [   11.149420] pnp: 00:03: ioport range 0x806-0x807 has been reserved
Apr  5 20:46:41 MTOLEDOB kernel: [   11.149423] pnp: 00:03: ioport range 0x810-0x85f has been reserved
Apr  5 20:46:41 MTOLEDOB kernel: [   11.149427] pnp: 00:03: ioport range 0x860-0x87f has been reserved
Apr  5 20:46:41 MTOLEDOB kernel: [   11.149431] pnp: 00:03: ioport range 0x880-0x8bf has been reserved
Apr  5 20:46:41 MTOLEDOB kernel: [   11.149434] pnp: 00:03: ioport range 0x8c0-0x8df has been reserved
Apr  5 20:46:41 MTOLEDOB kernel: [   11.149442] pnp: 00:08: ioport range 0x900-0x97f has been reserved
Apr  5 20:46:41 MTOLEDOB kernel: [   11.152455] Time: tsc clocksource has been installed.
Apr  5 20:46:41 MTOLEDOB kernel: [   11.179767] PCI: Bridge: 0000:00:01.0
Apr  5 20:46:41 MTOLEDOB kernel: [   11.179770]   IO window: c000-cfff
Apr  5 20:46:41 MTOLEDOB kernel: [   11.179775]   MEM window: fc000000-fdffffff
Apr  5 20:46:41 MTOLEDOB kernel: [   11.179779]   PREFETCH window: e8000000-efffffff
Apr  5 20:46:41 MTOLEDOB kernel: [   11.179793] PCI: Bus 3, cardbus bridge: 0000:02:01.0
Apr  5 20:46:41 MTOLEDOB kernel: [   11.179796]   IO window: 0000d000-0000d0ff
Apr  5 20:46:41 MTOLEDOB kernel: [   11.179801]   IO window: 0000d400-0000d4ff
Apr  5 20:46:41 MTOLEDOB kernel: [   11.179806]   PREFETCH window: 30000000-33ffffff
Apr  5 20:46:41 MTOLEDOB kernel: [   11.179810]   MEM window: 3c000000-3fffffff
Apr  5 20:46:41 MTOLEDOB kernel: [   11.179815] PCI: Bus 7, cardbus bridge: 0000:02:01.1
Apr  5 20:46:41 MTOLEDOB kernel: [   11.179818]   IO window: 0000d800-0000d8ff
Apr  5 20:46:41 MTOLEDOB kernel: [   11.179822]   IO window: 0000dc00-0000dcff
Apr  5 20:46:41 MTOLEDOB kernel: [   11.179827]   PREFETCH window: 34000000-37ffffff
Apr  5 20:46:41 MTOLEDOB kernel: [   11.179832]   MEM window: 40000000-43ffffff
Apr  5 20:46:41 MTOLEDOB kernel: [   11.179836] PCI: Bridge: 0000:00:1e.0
Apr  5 20:46:41 MTOLEDOB kernel: [   11.179839]   IO window: d000-efff
Apr  5 20:46:41 MTOLEDOB kernel: [   11.179845]   MEM window: f6000000-fbffffff
Apr  5 20:46:41 MTOLEDOB kernel: [   11.179850]   PREFETCH window: 30000000-37ffffff
Apr  5 20:46:41 MTOLEDOB kernel: [   11.179866] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Apr  5 20:46:41 MTOLEDOB kernel: [   11.179880] PCI: Enabling device 0000:02:01.0 (0000 -> 0003)
Apr  5 20:46:41 MTOLEDOB kernel: [   11.180052] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Apr  5 20:46:41 MTOLEDOB kernel: [   11.180056] PCI: setting IRQ 11 as level-triggered
Apr  5 20:46:41 MTOLEDOB kernel: [   11.180060] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:46:41 MTOLEDOB kernel: [   11.180078] PCI: Enabling device 0000:02:01.1 (0000 -> 0003)
Apr  5 20:46:41 MTOLEDOB kernel: [   11.180082] ACPI: PCI Interrupt 0000:02:01.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:46:41 MTOLEDOB kernel: [   11.180102] NET: Registered protocol family 2
Apr  5 20:46:41 MTOLEDOB kernel: [   11.216496] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Apr  5 20:46:41 MTOLEDOB kernel: [   11.216549] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
Apr  5 20:46:41 MTOLEDOB kernel: [   11.216762] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
Apr  5 20:46:41 MTOLEDOB kernel: [   11.216903] TCP: Hash tables configured (established 16384 bind 16384)
Apr  5 20:46:41 MTOLEDOB kernel: [   11.216906] TCP reno registered
Apr  5 20:46:41 MTOLEDOB kernel: [   11.228616] checking if image is initramfs... it is
Apr  5 20:46:41 MTOLEDOB kernel: [   11.680475] Switched to high resolution mode on CPU 0
Apr  5 20:46:41 MTOLEDOB kernel: [   12.106552] Freeing initrd memory: 8373k freed
Apr  5 20:46:41 MTOLEDOB kernel: [   12.106970] audit: initializing netlink socket (disabled)
Apr  5 20:46:41 MTOLEDOB kernel: [   12.106990] audit(1207428380.160:1): initialized
Apr  5 20:46:41 MTOLEDOB kernel: [   12.109626] VFS: Disk quotas dquot_6.5.1
Apr  5 20:46:41 MTOLEDOB kernel: [   12.109700] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr  5 20:46:41 MTOLEDOB kernel: [   12.109824] io scheduler noop registered
Apr  5 20:46:41 MTOLEDOB kernel: [   12.109827] io scheduler anticipatory registered
Apr  5 20:46:41 MTOLEDOB kernel: [   12.109830] io scheduler deadline registered
Apr  5 20:46:41 MTOLEDOB kernel: [   12.109855] io scheduler cfq registered (default)
Apr  5 20:46:41 MTOLEDOB kernel: [   12.109935] Boot video device is 0000:01:00.0
Apr  5 20:46:41 MTOLEDOB kernel: [   12.110135] isapnp: Scanning for PnP cards...
Apr  5 20:46:41 MTOLEDOB kernel: [   12.463057] isapnp: No Plug & Play device found
Apr  5 20:46:41 MTOLEDOB kernel: [   12.499558] Real Time Clock Driver v1.12ac
Apr  5 20:46:41 MTOLEDOB kernel: [   12.499701] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr  5 20:46:41 MTOLEDOB kernel: [   12.499801] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr  5 20:46:41 MTOLEDOB kernel: [   12.500796] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr  5 20:46:41 MTOLEDOB kernel: [   12.501270] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
Apr  5 20:46:41 MTOLEDOB kernel: [   12.501275] PCI: setting IRQ 5 as level-triggered
Apr  5 20:46:41 MTOLEDOB kernel: [   12.501280] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Apr  5 20:46:41 MTOLEDOB kernel: [   12.501290] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
Apr  5 20:46:41 MTOLEDOB kernel: [   12.501942] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr  5 20:46:41 MTOLEDOB kernel: [   12.502226] input: Macintosh mouse button emulation as /class/input/input0
Apr  5 20:46:41 MTOLEDOB kernel: [   12.502318] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Apr  5 20:46:41 MTOLEDOB kernel: [   12.507968] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr  5 20:46:41 MTOLEDOB kernel: [   12.507974] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr  5 20:46:41 MTOLEDOB kernel: [   12.508173] mice: PS/2 mouse device common for all mice
Apr  5 20:46:41 MTOLEDOB kernel: [   12.508298] EISA: Probing bus 0 at eisa.0
Apr  5 20:46:41 MTOLEDOB kernel: [   12.508327] EISA: Detected 0 cards.
Apr  5 20:46:41 MTOLEDOB kernel: [   12.508478] TCP cubic registered
Apr  5 20:46:41 MTOLEDOB kernel: [   12.508503] NET: Registered protocol family 1
Apr  5 20:46:41 MTOLEDOB kernel: [   12.508538] Using IPI No-Shortcut mode
Apr  5 20:46:41 MTOLEDOB kernel: [   12.508759]   Magic number: 4:719:800
Apr  5 20:46:41 MTOLEDOB kernel: [   12.508920]   hash matches device ptyr8
Apr  5 20:46:41 MTOLEDOB kernel: [   12.509263] Freeing unused kernel memory: 364k freed
Apr  5 20:46:41 MTOLEDOB kernel: [   12.540440] input: AT Translated Set 2 keyboard as /class/input/input1
Apr  5 20:46:41 MTOLEDOB kernel: [   13.727906] AppArmor: AppArmor initialized<5>audit(1207428382.160:2):  type=1505 info="AppArmor initialized" pid=1205
Apr  5 20:46:41 MTOLEDOB kernel: [   13.738388] fuse init (API version 7.8)
Apr  5 20:46:41 MTOLEDOB kernel: [   13.743914] Failure registering capabilities with primary security module.
Apr  5 20:46:41 MTOLEDOB kernel: [   13.764918] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
Apr  5 20:46:41 MTOLEDOB kernel: [   13.764926] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr  5 20:46:41 MTOLEDOB kernel: [   13.768885] ACPI: Thermal Zone [THM] (54 C)
Apr  5 20:46:41 MTOLEDOB kernel: [   14.256513] usbcore: registered new interface driver usbfs
Apr  5 20:46:41 MTOLEDOB kernel: [   14.256545] usbcore: registered new interface driver hub
Apr  5 20:46:41 MTOLEDOB kernel: [   14.256575] usbcore: registered new device driver usb
Apr  5 20:46:41 MTOLEDOB kernel: [   14.258276] USB Universal Host Controller Interface driver v3.0
Apr  5 20:46:41 MTOLEDOB kernel: [   14.258602] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
Apr  5 20:46:41 MTOLEDOB kernel: [   14.258606] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:46:41 MTOLEDOB kernel: [   14.258622] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Apr  5 20:46:41 MTOLEDOB kernel: [   14.258626] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr  5 20:46:41 MTOLEDOB kernel: [   14.258862] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Apr  5 20:46:41 MTOLEDOB kernel: [   14.258890] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
Apr  5 20:46:41 MTOLEDOB kernel: [   14.259054] usb usb1: configuration #1 chosen from 1 choice
Apr  5 20:46:41 MTOLEDOB kernel: [   14.259088] hub 1-0:1.0: USB hub found
Apr  5 20:46:41 MTOLEDOB kernel: [   14.259095] hub 1-0:1.0: 2 ports detected
Apr  5 20:46:41 MTOLEDOB kernel: [   14.332497] SCSI subsystem initialized
Apr  5 20:46:41 MTOLEDOB kernel: [   14.345121] libata version 2.21 loaded.
Apr  5 20:46:41 MTOLEDOB kernel: [   14.360446] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:46:41 MTOLEDOB kernel: [   14.360463] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Apr  5 20:46:41 MTOLEDOB kernel: [   14.360468] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr  5 20:46:41 MTOLEDOB kernel: [   14.360497] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Apr  5 20:46:41 MTOLEDOB kernel: [   14.360524] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
Apr  5 20:46:41 MTOLEDOB kernel: [   14.360661] usb usb2: configuration #1 chosen from 1 choice
Apr  5 20:46:41 MTOLEDOB kernel: [   14.360695] hub 2-0:1.0: USB hub found
Apr  5 20:46:41 MTOLEDOB kernel: [   14.360703] hub 2-0:1.0: 2 ports detected
Apr  5 20:46:41 MTOLEDOB kernel: [   14.464650] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
Apr  5 20:46:41 MTOLEDOB kernel: [   14.464657] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:46:41 MTOLEDOB kernel: [   14.464671] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Apr  5 20:46:41 MTOLEDOB kernel: [   14.464676] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr  5 20:46:41 MTOLEDOB kernel: [   14.464706] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Apr  5 20:46:41 MTOLEDOB kernel: [   14.464732] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
Apr  5 20:46:41 MTOLEDOB kernel: [   14.464864] usb usb3: configuration #1 chosen from 1 choice
Apr  5 20:46:41 MTOLEDOB kernel: [   14.464897] hub 3-0:1.0: USB hub found
Apr  5 20:46:41 MTOLEDOB kernel: [   14.464904] hub 3-0:1.0: 2 ports detected
Apr  5 20:46:41 MTOLEDOB kernel: [   14.568790] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
Apr  5 20:46:41 MTOLEDOB kernel: [   14.568796] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:46:41 MTOLEDOB kernel: [   14.568813] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Apr  5 20:46:41 MTOLEDOB kernel: [   14.568817] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr  5 20:46:41 MTOLEDOB kernel: [   14.568850] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
Apr  5 20:46:41 MTOLEDOB kernel: [   14.568892] ehci_hcd 0000:00:1d.7: debug port 1
Apr  5 20:46:41 MTOLEDOB kernel: [   14.568899] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Apr  5 20:46:41 MTOLEDOB kernel: [   14.568909] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf4fffc00
Apr  5 20:46:41 MTOLEDOB kernel: [   14.572809] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Apr  5 20:46:41 MTOLEDOB kernel: [   14.572915] usb usb4: configuration #1 chosen from 1 choice
Apr  5 20:46:41 MTOLEDOB kernel: [   14.572948] hub 4-0:1.0: USB hub found
Apr  5 20:46:41 MTOLEDOB kernel: [   14.572957] hub 4-0:1.0: 6 ports detected
Apr  5 20:46:41 MTOLEDOB kernel: [   14.676595] ata_piix 0000:00:1f.1: version 2.11
Apr  5 20:46:41 MTOLEDOB kernel: [   14.676614] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
Apr  5 20:46:41 MTOLEDOB kernel: [   14.676624] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:46:41 MTOLEDOB kernel: [   14.676670] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Apr  5 20:46:41 MTOLEDOB kernel: [   14.676786] scsi0 : ata_piix
Apr  5 20:46:41 MTOLEDOB kernel: [   14.676833] scsi1 : ata_piix
Apr  5 20:46:41 MTOLEDOB kernel: [   14.677859] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
Apr  5 20:46:41 MTOLEDOB kernel: [   14.677864] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
Apr  5 20:46:41 MTOLEDOB kernel: [    4.216000] Marking TSC unstable due to: possible TSC halt in C2.
Apr  5 20:46:41 MTOLEDOB kernel: [    4.220000] Time: acpi_pm clocksource has been installed.
Apr  5 20:46:41 MTOLEDOB kernel: [    4.348000] ata1.00: ATA-6: ST980815A, 3.ALD, max UDMA/100
Apr  5 20:46:41 MTOLEDOB kernel: [    4.348000] ata1.00: 156301488 sectors, multi 8: LBA48 
Apr  5 20:46:41 MTOLEDOB kernel: [    4.364000] ata1.00: configured for UDMA/100
Apr  5 20:46:41 MTOLEDOB kernel: [    4.684000] ata2.00: ATAPI: HL-DT-STCD-RW/DVD-ROM GCC-4241N, A101, max UDMA/33
Apr  5 20:46:41 MTOLEDOB kernel: [    4.856000] ata2.00: configured for UDMA/33
Apr  5 20:46:41 MTOLEDOB kernel: [    4.856000] scsi 0:0:0:0: Direct-Access     ATA      ST980815A        3.AL PQ: 0 ANSI: 5
Apr  5 20:46:41 MTOLEDOB kernel: [    4.860000] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4241N A101 PQ: 0 ANSI: 5
Apr  5 20:46:41 MTOLEDOB kernel: [    4.864000] tg3.c:v3.77 (May 31, 2007)
Apr  5 20:46:41 MTOLEDOB kernel: [    4.864000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:46:41 MTOLEDOB kernel: [    4.904000] eth0: Tigon3 [partno(BCM95705A50) rev 3001 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000Base-T Ethernet 00:11:43:53:d5:22
Apr  5 20:46:41 MTOLEDOB kernel: [    4.904000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
Apr  5 20:46:41 MTOLEDOB kernel: [    4.904000] eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
Apr  5 20:46:41 MTOLEDOB kernel: [    4.908000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr  5 20:46:41 MTOLEDOB kernel: [    4.908000] sd 0:0:0:0: [sda] Write Protect is off
Apr  5 20:46:41 MTOLEDOB kernel: [    4.908000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr  5 20:46:41 MTOLEDOB kernel: [    4.908000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  5 20:46:41 MTOLEDOB kernel: [    4.908000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr  5 20:46:41 MTOLEDOB kernel: [    4.908000] sd 0:0:0:0: [sda] Write Protect is off
Apr  5 20:46:41 MTOLEDOB kernel: [    4.908000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr  5 20:46:41 MTOLEDOB kernel: [    4.908000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  5 20:46:41 MTOLEDOB kernel: [    4.908000]  sda: sda1 sda2 sda3 < sda5 >
Apr  5 20:46:41 MTOLEDOB kernel: [    4.964000] sd 0:0:0:0: [sda] Attached SCSI disk
Apr  5 20:46:41 MTOLEDOB kernel: [    4.968000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr  5 20:46:41 MTOLEDOB kernel: [    4.968000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
Apr  5 20:46:41 MTOLEDOB kernel: [    5.000000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Apr  5 20:46:41 MTOLEDOB kernel: [    5.000000] Uniform CD-ROM driver Revision: 3.20
Apr  5 20:46:41 MTOLEDOB kernel: [    5.004000] sr 1:0:0:0: Attached scsi CD-ROM sr0
Apr  5 20:46:41 MTOLEDOB kernel: [    5.240000] Attempting manual resume
Apr  5 20:46:41 MTOLEDOB kernel: [    5.240000] swsusp: Resume From Partition 8:5
Apr  5 20:46:41 MTOLEDOB kernel: [    5.240000] PM: Checking swsusp image.
Apr  5 20:46:41 MTOLEDOB kernel: [    5.240000] PM: Resume from disk failed.
Apr  5 20:46:41 MTOLEDOB kernel: [    5.264000] EXT3-fs: INFO: recovery required on readonly filesystem.
Apr  5 20:46:41 MTOLEDOB kernel: [    5.264000] EXT3-fs: write access will be enabled during recovery.
Apr  5 20:46:41 MTOLEDOB kernel: [    5.676000] kjournald starting.  Commit interval 5 seconds
Apr  5 20:46:41 MTOLEDOB kernel: [    5.676000] EXT3-fs: recovery complete.
Apr  5 20:46:41 MTOLEDOB kernel: [    5.684000] EXT3-fs: mounted filesystem with ordered data mode.
Apr  5 20:46:41 MTOLEDOB kernel: [   15.720000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr  5 20:46:41 MTOLEDOB kernel: [   15.732000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr  5 20:46:41 MTOLEDOB kernel: [   15.748000] Linux agpgart interface v0.102 (c) Dave Jones
Apr  5 20:46:41 MTOLEDOB kernel: [   15.752000] agpgart: Detected an Intel 855PM Chipset.
Apr  5 20:46:41 MTOLEDOB kernel: [   15.760000] agpgart: AGP aperture is 128M @ 0xe0000000
Apr  5 20:46:41 MTOLEDOB kernel: [   16.580000] iTCO_vendor_support: vendor-support=0
Apr  5 20:46:41 MTOLEDOB kernel: [   16.752000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
Apr  5 20:46:41 MTOLEDOB kernel: [   16.752000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x0860)
Apr  5 20:46:41 MTOLEDOB kernel: [   16.752000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Apr  5 20:46:41 MTOLEDOB kernel: [   17.124000] Yenta: CardBus bridge found at 0000:02:01.0 [1028:011d]
Apr  5 20:46:41 MTOLEDOB kernel: [   17.124000] Yenta O2: res at 0x94/0xD4: 00/ea
Apr  5 20:46:41 MTOLEDOB kernel: [   17.124000] Yenta O2: enabling read prefetch/write burst
Apr  5 20:46:41 MTOLEDOB kernel: [   17.252000] Yenta: ISA IRQ mask 0x0498, PCI irq 11
Apr  5 20:46:41 MTOLEDOB kernel: [   17.252000] Socket status: 30000006
Apr  5 20:46:41 MTOLEDOB kernel: [   17.252000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
Apr  5 20:46:41 MTOLEDOB kernel: [   17.252000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
Apr  5 20:46:41 MTOLEDOB kernel: [   17.252000] cs: IO port probe 0xd000-0xefff: clean.
Apr  5 20:46:41 MTOLEDOB kernel: [   17.252000] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
Apr  5 20:46:41 MTOLEDOB kernel: [   17.252000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x37ffffff
Apr  5 20:46:41 MTOLEDOB kernel: [   17.252000] Yenta: CardBus bridge found at 0000:02:01.1 [1028:011d]
Apr  5 20:46:41 MTOLEDOB kernel: [   17.328000] intel_rng: FWH not detected
Apr  5 20:46:41 MTOLEDOB kernel: [   17.380000] Yenta: ISA IRQ mask 0x0498, PCI irq 11
Apr  5 20:46:41 MTOLEDOB kernel: [   17.380000] Socket status: 30000410
Apr  5 20:46:41 MTOLEDOB kernel: [   17.380000] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
Apr  5 20:46:41 MTOLEDOB kernel: [   17.380000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
Apr  5 20:46:41 MTOLEDOB kernel: [   17.380000] cs: IO port probe 0xd000-0xefff: clean.
Apr  5 20:46:41 MTOLEDOB kernel: [   17.380000] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
Apr  5 20:46:41 MTOLEDOB kernel: [   17.380000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x37ffffff
Apr  5 20:46:41 MTOLEDOB kernel: [   17.404000] input: PC Speaker as /class/input/input2
Apr  5 20:46:41 MTOLEDOB kernel: [   17.432000] ieee80211_crypt: registered algorithm 'NULL'
Apr  5 20:46:41 MTOLEDOB kernel: [   17.436000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Apr  5 20:46:41 MTOLEDOB kernel: [   17.436000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Apr  5 20:46:41 MTOLEDOB kernel: [   17.628000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
Apr  5 20:46:41 MTOLEDOB kernel: [   17.628000] ipw2100: Copyright(c) 2003-2006 Intel Corporation
Apr  5 20:46:41 MTOLEDOB kernel: [   17.628000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Apr  5 20:46:41 MTOLEDOB kernel: [   17.628000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
Apr  5 20:46:41 MTOLEDOB kernel: [   17.732000] input: DualPoint Stick as /class/input/input3
Apr  5 20:46:41 MTOLEDOB kernel: [   17.752000] input: AlpsPS/2 ALPS DualPoint TouchPad as /class/input/input4
Apr  5 20:46:41 MTOLEDOB kernel: [   17.760000] parport_pc 00:0c: reported by Plug and Play ACPI
Apr  5 20:46:41 MTOLEDOB kernel: [   17.760000] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Apr  5 20:46:41 MTOLEDOB kernel: [   18.032000] pccard: PCMCIA card inserted into slot 1
Apr  5 20:46:41 MTOLEDOB kernel: [   18.172000] cs: memory probe 0xf6000000-0xfbffffff: excluding 0xf6000000-0xf65fffff 0xf6c00000-0xf71fffff 0xf7e00000-0xf83fffff 0xf9c00000-0xfa1fffff 0xfae00000-0xfb3fffff
Apr  5 20:46:41 MTOLEDOB kernel: [   18.184000] pcmcia: registering new device pcmcia1.0
Apr  5 20:46:41 MTOLEDOB kernel: [   18.244000] cs: IO port probe 0x100-0x3af: clean.
Apr  5 20:46:41 MTOLEDOB kernel: [   18.244000] cs: IO port probe 0x3e0-0x4ff: clean.
Apr  5 20:46:41 MTOLEDOB kernel: [   18.244000] cs: IO port probe 0x820-0x8ff: clean.
Apr  5 20:46:41 MTOLEDOB kernel: [   18.244000] cs: IO port probe 0xc00-0xcf7: clean.
Apr  5 20:46:41 MTOLEDOB kernel: [   18.244000] cs: IO port probe 0xa00-0xaff: clean.
Apr  5 20:46:41 MTOLEDOB kernel: [   18.268000] cs: IO port probe 0x100-0x3af: clean.
Apr  5 20:46:41 MTOLEDOB kernel: [   18.272000] cs: IO port probe 0x3e0-0x4ff: clean.
Apr  5 20:46:41 MTOLEDOB kernel: [   18.272000] cs: IO port probe 0x820-0x8ff: clean.
Apr  5 20:46:41 MTOLEDOB kernel: [   18.272000] cs: IO port probe 0xc00-0xcf7: clean.
Apr  5 20:46:41 MTOLEDOB kernel: [   18.272000] cs: IO port probe 0xa00-0xaff: clean.
Apr  5 20:46:41 MTOLEDOB kernel: [   18.292000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Apr  5 20:46:41 MTOLEDOB kernel: [   18.292000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
Apr  5 20:46:41 MTOLEDOB kernel: [   19.120000] intel8x0_measure_ac97_clock: measured 55450 usecs
Apr  5 20:46:41 MTOLEDOB kernel: [   19.120000] intel8x0: clocking to 48000
Apr  5 20:46:41 MTOLEDOB kernel: [   19.944000] lp0: using parport0 (interrupt-driven).
Apr  5 20:46:41 MTOLEDOB kernel: [   19.984000] Adding 1510068k swap on /dev/sda5.  Priority:-1 extents:1 across:1510068k
Apr  5 20:46:41 MTOLEDOB kernel: [   20.280000] EXT3 FS on sda2, internal journal
Apr  5 20:46:41 MTOLEDOB kernel: [   21.384000] ACPI: AC Adapter [AC] (on-line)
Apr  5 20:46:41 MTOLEDOB kernel: [   21.448000] input: Lid Switch as /class/input/input5
Apr  5 20:46:41 MTOLEDOB kernel: [   21.452000] ACPI: Lid Switch [LID]
Apr  5 20:46:41 MTOLEDOB kernel: [   21.500000] input: Power Button (CM) as /class/input/input6
Apr  5 20:46:41 MTOLEDOB kernel: [   21.504000] ACPI: Power Button (CM) [PBTN]
Apr  5 20:46:41 MTOLEDOB kernel: [   21.552000] input: Sleep Button (CM) as /class/input/input7
Apr  5 20:46:41 MTOLEDOB kernel: [   21.556000] ACPI: Sleep Button (CM) [SBTN]
Apr  5 20:46:41 MTOLEDOB kernel: [   21.576000] ACPI: ACPI Dock Station Driver 
Apr  5 20:46:41 MTOLEDOB kernel: [   21.904000] ACPI: Battery Slot [BAT0] (battery present)
Apr  5 20:46:41 MTOLEDOB kernel: [   21.904000] ACPI: Battery Slot [BAT1] (battery absent)
Apr  5 20:46:41 MTOLEDOB kernel: [   21.948000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Apr  5 20:46:41 MTOLEDOB NetworkManager: <info>  starting... 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.208530] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_3340'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.512524] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_3341'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.513529] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_4c66'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.514259] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c2'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.514787] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.515303] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.515777] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c4'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.516246] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.516716] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.517186] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c7'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.517674] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.518144] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.518717] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24cd'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.519190] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.519659] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.520125] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.520591] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_165d'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.521058] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1217_7113'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.521523] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1217_7113_0'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.521989] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pcmcia__1__1'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.522454] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_1043'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.522938] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24cc'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.523403] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.523868] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.524354] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_scsi_device_lun0'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.524824] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_0'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.525289] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_0_scsi_device_lun0'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.525756] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.526219] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c6'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.526717] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_dock_0'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.527183] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.527648] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.528114] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.528633] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.529101] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.529565] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.530027] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.530505] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.530970] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.531432] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.531894] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.532356] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.532817] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.533279] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.533740] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.534200] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.534677] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.535138] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.535614] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.536075] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0401'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.536535] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.536996] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.537475] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.537937] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.538796] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.552457] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_11_43_53_d5_22'). 
Apr  5 20:46:42 MTOLEDOB kernel: [   23.480000] PM: Writing back config space on device 0000:02:00.0 at offset c (was ffbf0000, writing 0)
Apr  5 20:46:42 MTOLEDOB kernel: [   23.480000] PM: Writing back config space on device 0000:02:00.0 at offset b (was 165d14e4, writing 865d1028)
Apr  5 20:46:42 MTOLEDOB kernel: [   23.480000] PM: Writing back config space on device 0000:02:00.0 at offset 3 (was 0, writing 2008)
Apr  5 20:46:42 MTOLEDOB kernel: [   23.480000] PM: Writing back config space on device 0000:02:00.0 at offset 2 (was 2000000, writing 2000001)
Apr  5 20:46:42 MTOLEDOB kernel: [   23.480000] PM: Writing back config space on device 0000:02:00.0 at offset 1 (was 2b00000, writing 2b00106)
Apr  5 20:46:42 MTOLEDOB NetworkManager: <info>  eth0: Device is fully-supported using driver 'tg3'. 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <info>  Deactivating device eth0. 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <debug> [1207450002.996330] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_0c_f1_1c_20_6b'). 
Apr  5 20:46:42 MTOLEDOB NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <info>  eth1: Device is fully-supported using driver 'ipw2100'. 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <info>  Deactivating device eth1. 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.151253] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_scsi_device_lun0_scsi_generic'). 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.151912] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.152403] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_pcm_1'). 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.152882] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_pcm_0'). 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.153362] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_control__1'). 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.153839] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_pcm_0_0'). 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.154314] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_mixer__1'). 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.154812] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_0'). 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.155325] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_playback_0'). 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.155835] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_1'). 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.156312] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_2'). 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.156805] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_3'). 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.157297] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_playback_4'). 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.157771] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.158243] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.158802] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.159277] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.159748] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.160243] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.160719] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.161194] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_3'). 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.161719] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'). 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.162194] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.162681] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.163155] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.163625] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.164095] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST980815A_5LY1VWH9'). 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.164565] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_606C05936C0564DE'). 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.165035] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_241da2db_0e86_4d13_ba31_7e747e81c264'). 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.179093] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part3_size_1024'). 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.185055] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_aaabdd49_42ff_4b7f_ac15_b1a4f0ed1a87'). 
Apr  5 20:46:43 MTOLEDOB gdm[4595]: WARNING: Didn't understand `' (expected true or false) 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.284318] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT1'). 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.333577] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.334173] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.334692] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Apr  5 20:46:43 MTOLEDOB NetworkManager: <debug> [1207450003.335508] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_RW/DVD_GCC_4241N'). 
Apr  5 20:46:43 MTOLEDOB kernel: [   24.844000] [drm] Initialized drm 1.1.0 20060810
Apr  5 20:46:44 MTOLEDOB kernel: [   24.852000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:46:44 MTOLEDOB kernel: [   24.856000] [drm] Initialized radeon 1.27.0 20060524 on minor 0
Apr  5 20:46:44 MTOLEDOB kernel: [   25.268000] ppdev: user-space parallel port driver
Apr  5 20:52:59 MTOLEDOB syslogd 1.4.1#21ubuntu3: restart.
Apr  5 20:53:00 MTOLEDOB kernel: Inspecting /boot/System.map-2.6.20-12-generic
Apr  5 20:53:00 MTOLEDOB kernel: Loaded 24905 symbols from /boot/System.map-2.6.20-12-generic.
Apr  5 20:53:00 MTOLEDOB kernel: Symbols match kernel version 2.6.20.
Apr  5 20:53:00 MTOLEDOB kernel: No module symbols loaded - kernel modules not enabled. 
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000] Linux version 2.6.20-12-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Wed Mar 21 20:55:46 UTC 2007 (Ubuntu 2.6.20-12.20-generic)
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000] BIOS-provided physical RAM map:
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000] sanitize start
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000] sanitize end
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f000 end: 000000000009f000 type: 1
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000] copy_e820_map() start: 000000000009f000 size: 0000000000001000 end: 00000000000a0000 type: 2
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001feae000 end: 000000001ffae000 type: 1
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000] copy_e820_map() start: 000000001ffae000 size: 0000000000052000 end: 0000000020000000 type: 2
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000] copy_e820_map() start: 00000000feda0000 size: 0000000000060000 end: 00000000fee00000 type: 2
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000] copy_e820_map() start: 00000000ffb00000 size: 0000000000500000 end: 0000000100000000 type: 2
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffae000 (usable)
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 000000001ffae000 - 0000000020000000 (reserved)
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fee00000 (reserved)
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000] 0MB HIGHMEM available.
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000] 511MB LOWMEM available.
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000] Entering add_active_range(0, 0, 130990) 0 entries of 256 used
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000] Zone PFN ranges:
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000]   DMA             0 ->     4096
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000]   Normal       4096 ->   130990
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000]   HighMem    130990 ->   130990
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000]     0:        0 ->   130990
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000] On node 0 totalpages: 130990
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000]   Normal zone: 991 pages used for memmap
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000]   Normal zone: 125903 pages, LIFO batch:31
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000] DMI 2.3 present.
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fdf00
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000] ACPI: RSDT (v001 DELL    CPi R   0x27d5011a ASL  0x00000061) @ 0x1fff0000
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000] ACPI: FADT (v001 DELL    CPi R   0x27d5011a ASL  0x00000061) @ 0x1fff0400
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000] ACPI: ASF! (v016 DELL    CPi R   0x27d5011a ASL  0x00000061) @ 0x1fff0800
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000] ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 MSFT 0x0100000e) @ 0x00000000
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:deda0000)
Apr  5 20:53:00 MTOLEDOB kernel: [    0.000000] Detected 1398.903 MHz processor.
Apr  5 20:53:00 MTOLEDOB kernel: [   12.304643] Built 1 zonelists.  Total pages: 129967
Apr  5 20:53:00 MTOLEDOB kernel: [   12.304649] Kernel command line: root=UUID=241da2db-0e86-4d13-ba31-7e747e81c264 ro single
Apr  5 20:53:00 MTOLEDOB kernel: [   12.304861] Local APIC disabled by BIOS -- you can enable it with "lapic"
Apr  5 20:53:00 MTOLEDOB kernel: [   12.304871] mapped APIC to ffffd000 (0140b000)
Apr  5 20:53:00 MTOLEDOB kernel: [   12.304875] Enabling fast FPU save and restore... done.
Apr  5 20:53:00 MTOLEDOB kernel: [   12.304878] Enabling unmasked SIMD FPU exception support... done.
Apr  5 20:53:00 MTOLEDOB kernel: [   12.304891] Initializing CPU#0
Apr  5 20:53:00 MTOLEDOB kernel: [   12.304963] PID hash table entries: 2048 (order: 11, 8192 bytes)
Apr  5 20:53:00 MTOLEDOB kernel: [   12.306019] Console: colour VGA+ 80x25
Apr  5 20:53:00 MTOLEDOB kernel: [   12.307485] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr  5 20:53:00 MTOLEDOB kernel: [   12.307831] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr  5 20:53:00 MTOLEDOB kernel: [   12.325607] Memory: 508480k/523960k available (1990k kernel code, 14956k reserved, 890k data, 328k init, 0k highmem)
Apr  5 20:53:00 MTOLEDOB kernel: [   12.325667] virtual kernel memory layout:
Apr  5 20:53:00 MTOLEDOB kernel: [   12.325669]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
Apr  5 20:53:00 MTOLEDOB kernel: [   12.325671]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr  5 20:53:00 MTOLEDOB kernel: [   12.325672]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
Apr  5 20:53:00 MTOLEDOB kernel: [   12.325674]     lowmem  : 0xc0000000 - 0xdffae000   ( 511 MB)
Apr  5 20:53:00 MTOLEDOB kernel: [   12.325676]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
Apr  5 20:53:00 MTOLEDOB kernel: [   12.325677]       .data : 0xc02f1b04 - 0xc03d06d4   ( 890 kB)
Apr  5 20:53:00 MTOLEDOB kernel: [   12.325679]       .text : 0xc0100000 - 0xc02f1b04   (1990 kB)
Apr  5 20:53:00 MTOLEDOB kernel: [   12.325947] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr  5 20:53:00 MTOLEDOB kernel: [   12.404966] Calibrating delay using timer specific routine.. 2799.68 BogoMIPS (lpj=5599361)
Apr  5 20:53:00 MTOLEDOB kernel: [   12.405085] Security Framework v1.0.0 initialized
Apr  5 20:53:00 MTOLEDOB kernel: [   12.405126] SELinux:  Disabled at boot.
Apr  5 20:53:00 MTOLEDOB kernel: [   12.405180] Mount-cache hash table entries: 512
Apr  5 20:53:00 MTOLEDOB kernel: [   12.405380] CPU: After generic identify, caps: a7e9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
Apr  5 20:53:00 MTOLEDOB kernel: [   12.405395] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr  5 20:53:00 MTOLEDOB kernel: [   12.405454] CPU: L2 cache: 1024K
Apr  5 20:53:00 MTOLEDOB kernel: [   12.405488] CPU: After all inits, caps: a7e9f9bf 00000000 00000000 00002040 00000180 00000000 00000000
Apr  5 20:53:00 MTOLEDOB kernel: [   12.405499] Compat vDSO mapped to ffffe000.
Apr  5 20:53:00 MTOLEDOB kernel: [   12.405536] Remapping vsyscall page to ffffe000
Apr  5 20:53:00 MTOLEDOB kernel: [   12.405581] Checking 'hlt' instruction... OK.
Apr  5 20:53:00 MTOLEDOB kernel: [   12.421094] SMP alternatives: switching to UP code
Apr  5 20:53:00 MTOLEDOB kernel: [   12.421307] Freeing SMP alternatives: 11k freed
Apr  5 20:53:00 MTOLEDOB kernel: [   12.421545] Early unpacking initramfs... done
Apr  5 20:53:00 MTOLEDOB kernel: [   12.828082] ACPI: Core revision 20060707
Apr  5 20:53:00 MTOLEDOB kernel: [   12.834935] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Apr  5 20:53:00 MTOLEDOB kernel: [   12.836663] ACPI: setting ELCR to 0200 (from 0800)
Apr  5 20:53:00 MTOLEDOB kernel: [   12.839071] CPU0: Intel(R) Pentium(R) M processor 1400MHz stepping 05
Apr  5 20:53:00 MTOLEDOB kernel: [   12.839153] SMP motherboard not detected.
Apr  5 20:53:00 MTOLEDOB kernel: [   12.839188] Local APIC not detected. Using dummy APIC emulation.
Apr  5 20:53:00 MTOLEDOB kernel: [   12.839262] Brought up 1 CPUs
Apr  5 20:53:00 MTOLEDOB kernel: [   12.839579] Booting paravirtualized kernel on bare hardware
Apr  5 20:53:00 MTOLEDOB kernel: [   12.839680] Time: 20:52:34  Date: 03/05/108
Apr  5 20:53:00 MTOLEDOB kernel: [   12.839746] NET: Registered protocol family 16
Apr  5 20:53:00 MTOLEDOB kernel: [   12.839877] EISA bus registered
Apr  5 20:53:00 MTOLEDOB kernel: [   12.839913] ACPI: bus type pci registered
Apr  5 20:53:00 MTOLEDOB kernel: [   12.873519] PCI: PCI BIOS revision 2.10 entry at 0xfc96e, last bus=2
Apr  5 20:53:00 MTOLEDOB kernel: [   12.873556] PCI: Using configuration type 1
Apr  5 20:53:00 MTOLEDOB kernel: [   12.873590] Setting up standard PCI resources
Apr  5 20:53:00 MTOLEDOB kernel: [   12.885622] ACPI: Interpreter enabled
Apr  5 20:53:00 MTOLEDOB kernel: [   12.885658] ACPI: Using PIC for interrupt routing
Apr  5 20:53:00 MTOLEDOB kernel: [   12.887144] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr  5 20:53:00 MTOLEDOB kernel: [   12.887187] PCI: Probing PCI hardware (bus 00)
Apr  5 20:53:00 MTOLEDOB kernel: [   12.887329] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
Apr  5 20:53:00 MTOLEDOB kernel: [   12.893543] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
Apr  5 20:53:00 MTOLEDOB kernel: [   12.893582] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
Apr  5 20:53:00 MTOLEDOB kernel: [   12.893822] Boot video device is 0000:01:00.0
Apr  5 20:53:00 MTOLEDOB kernel: [   12.894075] PCI: Transparent bridge - 0000:00:1e.0
Apr  5 20:53:00 MTOLEDOB kernel: [   12.894170] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
Apr  5 20:53:00 MTOLEDOB kernel: [   12.894218] Please report the result to linux-kernel to fix this permanently
Apr  5 20:53:00 MTOLEDOB kernel: [   12.894297] PCI: Bus #07 (-#0a) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
Apr  5 20:53:00 MTOLEDOB kernel: [   12.894344] Please report the result to linux-kernel to fix this permanently
Apr  5 20:53:00 MTOLEDOB kernel: [   12.894397] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr  5 20:53:00 MTOLEDOB kernel: [   12.920754] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
Apr  5 20:53:00 MTOLEDOB kernel: [   12.921195] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
Apr  5 20:53:00 MTOLEDOB kernel: [   12.921615] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
Apr  5 20:53:00 MTOLEDOB kernel: [   12.922040] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
Apr  5 20:53:00 MTOLEDOB kernel: [   12.922486] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Apr  5 20:53:00 MTOLEDOB kernel: [   12.923128] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Apr  5 20:53:00 MTOLEDOB kernel: [   12.924714] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Apr  5 20:53:00 MTOLEDOB kernel: [   12.925557] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Apr  5 20:53:00 MTOLEDOB kernel: [   12.926552] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr  5 20:53:00 MTOLEDOB kernel: [   12.926602] pnp: PnP ACPI init
Apr  5 20:53:00 MTOLEDOB kernel: [   12.959797] pnp: PnP ACPI: found 13 devices
Apr  5 20:53:00 MTOLEDOB kernel: [   12.959835] PnPBIOS: Disabled by ACPI PNP
Apr  5 20:53:00 MTOLEDOB kernel: [   12.959921] PCI: Using ACPI for IRQ routing
Apr  5 20:53:00 MTOLEDOB kernel: [   12.959956] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr  5 20:53:00 MTOLEDOB kernel: [   12.966423] NET: Registered protocol family 8
Apr  5 20:53:00 MTOLEDOB kernel: [   12.966458] NET: Registered protocol family 20
Apr  5 20:53:00 MTOLEDOB kernel: [   12.972370] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
Apr  5 20:53:00 MTOLEDOB kernel: [   12.972408] pnp: 00:02: ioport range 0x800-0x805 could not be reserved
Apr  5 20:53:00 MTOLEDOB kernel: [   12.972446] pnp: 00:02: ioport range 0x808-0x80f could not be reserved
Apr  5 20:53:00 MTOLEDOB kernel: [   12.972486] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
Apr  5 20:53:00 MTOLEDOB kernel: [   12.972524] pnp: 00:03: ioport range 0x806-0x807 has been reserved
Apr  5 20:53:00 MTOLEDOB kernel: [   12.972561] pnp: 00:03: ioport range 0x810-0x85f could not be reserved
Apr  5 20:53:00 MTOLEDOB kernel: [   12.972598] pnp: 00:03: ioport range 0x860-0x87f has been reserved
Apr  5 20:53:00 MTOLEDOB kernel: [   12.972635] pnp: 00:03: ioport range 0x880-0x8bf has been reserved
Apr  5 20:53:00 MTOLEDOB kernel: [   12.972672] pnp: 00:03: ioport range 0x8c0-0x8df has been reserved
Apr  5 20:53:00 MTOLEDOB kernel: [   12.972713] pnp: 00:08: ioport range 0x900-0x97f has been reserved
Apr  5 20:53:00 MTOLEDOB kernel: [   12.973057] PCI: Bridge: 0000:00:01.0
Apr  5 20:53:00 MTOLEDOB kernel: [   12.973092]   IO window: c000-cfff
Apr  5 20:53:00 MTOLEDOB kernel: [   12.973128]   MEM window: fc000000-fdffffff
Apr  5 20:53:00 MTOLEDOB kernel: [   12.973163]   PREFETCH window: e8000000-efffffff
Apr  5 20:53:00 MTOLEDOB kernel: [   12.973210] PCI: Bus 3, cardbus bridge: 0000:02:01.0
Apr  5 20:53:00 MTOLEDOB kernel: [   12.973245]   IO window: 0000d000-0000d0ff
Apr  5 20:53:00 MTOLEDOB kernel: [   12.973281]   IO window: 0000d400-0000d4ff
Apr  5 20:53:00 MTOLEDOB kernel: [   12.973317]   PREFETCH window: 30000000-33ffffff
Apr  5 20:53:00 MTOLEDOB kernel: [   12.973354]   MEM window: 3c000000-3fffffff
Apr  5 20:53:00 MTOLEDOB kernel: [   12.973390] PCI: Bus 7, cardbus bridge: 0000:02:01.1
Apr  5 20:53:00 MTOLEDOB kernel: [   12.973425]   IO window: 0000d800-0000d8ff
Apr  5 20:53:00 MTOLEDOB kernel: [   12.973461]   IO window: 0000dc00-0000dcff
Apr  5 20:53:00 MTOLEDOB kernel: [   12.973497]   PREFETCH window: 34000000-37ffffff
Apr  5 20:53:00 MTOLEDOB kernel: [   12.973534]   MEM window: 40000000-43ffffff
Apr  5 20:53:00 MTOLEDOB kernel: [   12.973570] PCI: Bridge: 0000:00:1e.0
Apr  5 20:53:00 MTOLEDOB kernel: [   12.973604]   IO window: d000-efff
Apr  5 20:53:00 MTOLEDOB kernel: [   12.973641]   MEM window: f6000000-fbffffff
Apr  5 20:53:00 MTOLEDOB kernel: [   12.973677]   PREFETCH window: 30000000-37ffffff
Apr  5 20:53:00 MTOLEDOB kernel: [   12.973725] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Apr  5 20:53:00 MTOLEDOB kernel: [   12.973740] PCI: Enabling device 0000:02:01.0 (0000 -> 0003)
Apr  5 20:53:00 MTOLEDOB kernel: [   12.973981] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Apr  5 20:53:00 MTOLEDOB kernel: [   12.974017] PCI: setting IRQ 11 as level-triggered
Apr  5 20:53:00 MTOLEDOB kernel: [   12.974021] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:53:00 MTOLEDOB kernel: [   12.974123] PCI: Enabling device 0000:02:01.1 (0000 -> 0003)
Apr  5 20:53:00 MTOLEDOB kernel: [   12.974160] ACPI: PCI Interrupt 0000:02:01.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:53:00 MTOLEDOB kernel: [   12.974283] NET: Registered protocol family 2
Apr  5 20:53:00 MTOLEDOB kernel: [   13.009039] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Apr  5 20:53:00 MTOLEDOB kernel: [   13.009167] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Apr  5 20:53:00 MTOLEDOB kernel: [   13.009345] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
Apr  5 20:53:00 MTOLEDOB kernel: [   13.009449] TCP: Hash tables configured (established 16384 bind 8192)
Apr  5 20:53:00 MTOLEDOB kernel: [   13.009485] TCP reno registered
Apr  5 20:53:00 MTOLEDOB kernel: [   13.021101] checking if image is initramfs... it is
Apr  5 20:53:00 MTOLEDOB kernel: [   13.820083] Freeing initrd memory: 6761k freed
Apr  5 20:53:00 MTOLEDOB kernel: [   13.820600] audit: initializing netlink socket (disabled)
Apr  5 20:53:00 MTOLEDOB kernel: [   13.820654] audit(1207428754.696:1): initialized
Apr  5 20:53:00 MTOLEDOB kernel: [   13.820853] VFS: Disk quotas dquot_6.5.1
Apr  5 20:53:00 MTOLEDOB kernel: [   13.820913] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr  5 20:53:00 MTOLEDOB kernel: [   13.821036] io scheduler noop registered
Apr  5 20:53:00 MTOLEDOB kernel: [   13.821092] io scheduler anticipatory registered
Apr  5 20:53:00 MTOLEDOB kernel: [   13.821148] io scheduler deadline registered
Apr  5 20:53:00 MTOLEDOB kernel: [   13.821215] io scheduler cfq registered (default)
Apr  5 20:53:00 MTOLEDOB kernel: [   13.821650] isapnp: Scanning for PnP cards...
Apr  5 20:53:00 MTOLEDOB kernel: [   14.174619] isapnp: No Plug & Play device found
Apr  5 20:53:00 MTOLEDOB kernel: [   14.211045] Real Time Clock Driver v1.12ac
Apr  5 20:53:00 MTOLEDOB kernel: [   14.211152] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr  5 20:53:00 MTOLEDOB kernel: [   14.211328] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr  5 20:53:00 MTOLEDOB kernel: [   14.212260] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr  5 20:53:00 MTOLEDOB kernel: [   14.212818] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
Apr  5 20:53:00 MTOLEDOB kernel: [   14.212857] PCI: setting IRQ 5 as level-triggered
Apr  5 20:53:00 MTOLEDOB kernel: [   14.212861] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Apr  5 20:53:00 MTOLEDOB kernel: [   14.213009] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
Apr  5 20:53:00 MTOLEDOB kernel: [   14.213129] mice: PS/2 mouse device common for all mice
Apr  5 20:53:00 MTOLEDOB kernel: [   14.213786] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr  5 20:53:00 MTOLEDOB kernel: [   14.214123] input: Macintosh mouse button emulation as /class/input/input0
Apr  5 20:53:00 MTOLEDOB kernel: [   14.214198] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Apr  5 20:53:00 MTOLEDOB kernel: [   14.214236] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Apr  5 20:53:00 MTOLEDOB kernel: [   14.214480] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Apr  5 20:53:00 MTOLEDOB kernel: [   14.220333] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr  5 20:53:00 MTOLEDOB kernel: [   14.220373] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr  5 20:53:00 MTOLEDOB kernel: [   14.220553] EISA: Probing bus 0 at eisa.0
Apr  5 20:53:00 MTOLEDOB kernel: [   14.220613] EISA: Detected 0 cards.
Apr  5 20:53:00 MTOLEDOB kernel: [   14.250759] TCP cubic registered
Apr  5 20:53:00 MTOLEDOB kernel: [   14.250803] NET: Registered protocol family 1
Apr  5 20:53:00 MTOLEDOB kernel: [   14.250863] Using IPI No-Shortcut mode
Apr  5 20:53:00 MTOLEDOB kernel: [   14.250965] ACPI: (supports S0 S1 S3 S4 S5)
Apr  5 20:53:00 MTOLEDOB kernel: [   14.251173]   Magic number: 4:822:901
Apr  5 20:53:00 MTOLEDOB kernel: [   14.251349]   hash matches device ptyve
Apr  5 20:53:00 MTOLEDOB kernel: [   14.252434] Freeing unused kernel memory: 328k freed
Apr  5 20:53:00 MTOLEDOB kernel: [   14.252949] Time: tsc clocksource has been installed.
Apr  5 20:53:00 MTOLEDOB kernel: [   14.254192] input: AT Translated Set 2 keyboard as /class/input/input1
Apr  5 20:53:00 MTOLEDOB kernel: [   14.444001] Capability LSM initialized
Apr  5 20:53:00 MTOLEDOB kernel: [   14.486804] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
Apr  5 20:53:00 MTOLEDOB kernel: [   14.486955] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr  5 20:53:00 MTOLEDOB kernel: [   14.491277] ACPI: Thermal Zone [THM] (51 C)
Apr  5 20:53:00 MTOLEDOB kernel: [   14.890405] usbcore: registered new interface driver usbfs
Apr  5 20:53:00 MTOLEDOB kernel: [   14.890473] usbcore: registered new interface driver hub
Apr  5 20:53:00 MTOLEDOB kernel: [   14.890536] usbcore: registered new device driver usb
Apr  5 20:53:00 MTOLEDOB kernel: [   14.892282] USB Universal Host Controller Interface driver v3.0
Apr  5 20:53:00 MTOLEDOB kernel: [   14.892663] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
Apr  5 20:53:00 MTOLEDOB kernel: [   14.892701] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:53:00 MTOLEDOB kernel: [   14.892800] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Apr  5 20:53:00 MTOLEDOB kernel: [   14.892805] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr  5 20:53:00 MTOLEDOB kernel: [   14.893061] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Apr  5 20:53:00 MTOLEDOB kernel: [   14.893130] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
Apr  5 20:53:00 MTOLEDOB kernel: [   14.893290] usb usb1: configuration #1 chosen from 1 choice
Apr  5 20:53:00 MTOLEDOB kernel: [   14.893351] hub 1-0:1.0: USB hub found
Apr  5 20:53:00 MTOLEDOB kernel: [   14.893388] hub 1-0:1.0: 2 ports detected
Apr  5 20:53:00 MTOLEDOB kernel: [   14.968421] SCSI subsystem initialized
Apr  5 20:53:00 MTOLEDOB kernel: [   14.980078] libata version 2.20 loaded.
Apr  5 20:53:00 MTOLEDOB kernel: [   14.997121] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:53:00 MTOLEDOB kernel: [   14.997228] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Apr  5 20:53:00 MTOLEDOB kernel: [   14.997233] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr  5 20:53:00 MTOLEDOB kernel: [   14.997293] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Apr  5 20:53:00 MTOLEDOB kernel: [   14.997360] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
Apr  5 20:53:00 MTOLEDOB kernel: [   14.997512] usb usb2: configuration #1 chosen from 1 choice
Apr  5 20:53:00 MTOLEDOB kernel: [   14.997575] hub 2-0:1.0: USB hub found
Apr  5 20:53:00 MTOLEDOB kernel: [   14.997614] hub 2-0:1.0: 2 ports detected
Apr  5 20:53:00 MTOLEDOB kernel: [   15.101402] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
Apr  5 20:53:00 MTOLEDOB kernel: [   15.101447] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:53:00 MTOLEDOB kernel: [   15.101546] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Apr  5 20:53:00 MTOLEDOB kernel: [   15.101551] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr  5 20:53:00 MTOLEDOB kernel: [   15.101613] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Apr  5 20:53:00 MTOLEDOB kernel: [   15.101683] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
Apr  5 20:53:00 MTOLEDOB kernel: [   15.101829] usb usb3: configuration #1 chosen from 1 choice
Apr  5 20:53:00 MTOLEDOB kernel: [   15.101893] hub 3-0:1.0: USB hub found
Apr  5 20:53:00 MTOLEDOB kernel: [   15.101933] hub 3-0:1.0: 2 ports detected
Apr  5 20:53:00 MTOLEDOB kernel: [   15.206314] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
Apr  5 20:53:00 MTOLEDOB kernel: [   15.206359] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:53:00 MTOLEDOB kernel: [   15.206463] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Apr  5 20:53:00 MTOLEDOB kernel: [   15.206468] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr  5 20:53:00 MTOLEDOB kernel: [   15.206552] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
Apr  5 20:53:00 MTOLEDOB kernel: [   15.206632] ehci_hcd 0000:00:1d.7: debug port 1
Apr  5 20:53:00 MTOLEDOB kernel: [   15.206671] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Apr  5 20:53:00 MTOLEDOB kernel: [   15.206683] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf4fffc00
Apr  5 20:53:00 MTOLEDOB kernel: [   15.210599] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Apr  5 20:53:00 MTOLEDOB kernel: [   15.210745] usb usb4: configuration #1 chosen from 1 choice
Apr  5 20:53:00 MTOLEDOB kernel: [   15.210812] hub 4-0:1.0: USB hub found
Apr  5 20:53:00 MTOLEDOB kernel: [   15.210851] hub 4-0:1.0: 6 ports detected
Apr  5 20:53:00 MTOLEDOB kernel: [    2.984000] Time: acpi_pm clocksource has been installed.
Apr  5 20:53:00 MTOLEDOB kernel: [    3.008000] ata_piix 0000:00:1f.1: version 2.10ac1
Apr  5 20:53:00 MTOLEDOB kernel: [    3.008000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
Apr  5 20:53:00 MTOLEDOB kernel: [    3.008000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:53:00 MTOLEDOB kernel: [    3.008000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Apr  5 20:53:00 MTOLEDOB kernel: [    3.008000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
Apr  5 20:53:00 MTOLEDOB kernel: [    3.008000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
Apr  5 20:53:00 MTOLEDOB kernel: [    3.008000] scsi0 : ata_piix
Apr  5 20:53:00 MTOLEDOB kernel: [    3.172000] ata1.00: ATA-6: ST980815A, 3.ALD, max UDMA/100
Apr  5 20:53:00 MTOLEDOB kernel: [    3.172000] ata1.00: 156301488 sectors, multi 8: LBA48 
Apr  5 20:53:00 MTOLEDOB kernel: [    3.180000] ata1.00: configured for UDMA/100
Apr  5 20:53:00 MTOLEDOB kernel: [    3.180000] scsi1 : ata_piix
Apr  5 20:53:00 MTOLEDOB kernel: [    3.500000] ata2.00: ATAPI, max UDMA/33
Apr  5 20:53:00 MTOLEDOB kernel: [    3.664000] ata2.00: configured for UDMA/33
Apr  5 20:53:00 MTOLEDOB kernel: [    3.664000] scsi 0:0:0:0: Direct-Access     ATA      ST980815A        3.AL PQ: 0 ANSI: 5
Apr  5 20:53:00 MTOLEDOB kernel: [    3.668000] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4241N A101 PQ: 0 ANSI: 5
Apr  5 20:53:00 MTOLEDOB kernel: [    3.676000] tg3.c:v3.72 (January 8, 2007)
Apr  5 20:53:00 MTOLEDOB kernel: [    3.676000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:53:00 MTOLEDOB kernel: [    3.724000] eth0: Tigon3 [partno(BCM95705A50) rev 3001 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000Base-T Ethernet 00:11:43:53:d5:22
Apr  5 20:53:00 MTOLEDOB kernel: [    3.724000] eth0: RXcsums[1] LinkChgREG[1] MIirq[1] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
Apr  5 20:53:00 MTOLEDOB kernel: [    3.724000] eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
Apr  5 20:53:00 MTOLEDOB kernel: [    3.728000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
Apr  5 20:53:00 MTOLEDOB kernel: [    3.728000] sda: Write Protect is off
Apr  5 20:53:00 MTOLEDOB kernel: [    3.728000] sda: Mode Sense: 00 3a 00 00
Apr  5 20:53:00 MTOLEDOB kernel: [    3.728000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  5 20:53:00 MTOLEDOB kernel: [    3.728000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
Apr  5 20:53:00 MTOLEDOB kernel: [    3.728000] sda: Write Protect is off
Apr  5 20:53:00 MTOLEDOB kernel: [    3.728000] sda: Mode Sense: 00 3a 00 00
Apr  5 20:53:00 MTOLEDOB kernel: [    3.728000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  5 20:53:00 MTOLEDOB kernel: [    3.728000]  sda: sda1 sda2 sda3 < sda5 >
Apr  5 20:53:00 MTOLEDOB kernel: [    3.776000] sd 0:0:0:0: Attached scsi disk sda
Apr  5 20:53:00 MTOLEDOB kernel: [    3.784000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr  5 20:53:00 MTOLEDOB kernel: [    3.784000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
Apr  5 20:53:00 MTOLEDOB kernel: [    3.804000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Apr  5 20:53:00 MTOLEDOB kernel: [    3.804000] Uniform CD-ROM driver Revision: 3.20
Apr  5 20:53:00 MTOLEDOB kernel: [    3.804000] sr 1:0:0:0: Attached scsi CD-ROM sr0
Apr  5 20:53:00 MTOLEDOB kernel: [    4.076000] Attempting manual resume
Apr  5 20:53:00 MTOLEDOB kernel: [    4.076000] swsusp: Resume From Partition 8:5
Apr  5 20:53:00 MTOLEDOB kernel: [    4.076000] PM: Checking swsusp image.
Apr  5 20:53:00 MTOLEDOB kernel: [    4.076000] PM: Resume from disk failed.
Apr  5 20:53:00 MTOLEDOB kernel: [    4.100000] EXT3-fs: INFO: recovery required on readonly filesystem.
Apr  5 20:53:00 MTOLEDOB kernel: [    4.100000] EXT3-fs: write access will be enabled during recovery.
Apr  5 20:53:00 MTOLEDOB kernel: [    4.456000] kjournald starting.  Commit interval 5 seconds
Apr  5 20:53:00 MTOLEDOB kernel: [    4.456000] EXT3-fs: recovery complete.
Apr  5 20:53:00 MTOLEDOB kernel: [    4.464000] EXT3-fs: mounted filesystem with ordered data mode.
Apr  5 20:53:00 MTOLEDOB kernel: [   17.200000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr  5 20:53:00 MTOLEDOB kernel: [   17.204000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr  5 20:53:00 MTOLEDOB kernel: [   17.500000] iTCO_vendor_support: vendor-support=0
Apr  5 20:53:00 MTOLEDOB kernel: [   17.504000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
Apr  5 20:53:00 MTOLEDOB kernel: [   17.504000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x0860)
Apr  5 20:53:00 MTOLEDOB kernel: [   17.504000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Apr  5 20:53:00 MTOLEDOB kernel: [   17.528000] intel_rng: FWH not detected
Apr  5 20:53:00 MTOLEDOB kernel: [   18.280000] Yenta: CardBus bridge found at 0000:02:01.0 [1028:011d]
Apr  5 20:53:00 MTOLEDOB kernel: [   18.280000] Yenta O2: res at 0x94/0xD4: 00/ea
Apr  5 20:53:00 MTOLEDOB kernel: [   18.280000] Yenta O2: enabling read prefetch/write burst
Apr  5 20:53:00 MTOLEDOB kernel: [   18.336000] Linux agpgart interface v0.101 (c) Dave Jones
Apr  5 20:53:00 MTOLEDOB kernel: [   18.360000] agpgart: Detected an Intel 855PM Chipset.
Apr  5 20:53:00 MTOLEDOB kernel: [   18.368000] agpgart: AGP aperture is 128M @ 0xe0000000
Apr  5 20:53:00 MTOLEDOB kernel: [   18.408000] Yenta: ISA IRQ mask 0x0498, PCI irq 11
Apr  5 20:53:00 MTOLEDOB kernel: [   18.408000] Socket status: 30000006
Apr  5 20:53:00 MTOLEDOB kernel: [   18.408000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
Apr  5 20:53:00 MTOLEDOB kernel: [   18.408000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
Apr  5 20:53:00 MTOLEDOB kernel: [   18.408000] cs: IO port probe 0xd000-0xefff: clean.
Apr  5 20:53:00 MTOLEDOB kernel: [   18.408000] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
Apr  5 20:53:00 MTOLEDOB kernel: [   18.408000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x37ffffff
Apr  5 20:53:00 MTOLEDOB kernel: [   18.408000] Yenta: CardBus bridge found at 0000:02:01.1 [1028:011d]
Apr  5 20:53:00 MTOLEDOB kernel: [   18.536000] Yenta: ISA IRQ mask 0x0498, PCI irq 11
Apr  5 20:53:00 MTOLEDOB kernel: [   18.536000] Socket status: 30000410
Apr  5 20:53:00 MTOLEDOB kernel: [   18.536000] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
Apr  5 20:53:00 MTOLEDOB kernel: [   18.536000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
Apr  5 20:53:00 MTOLEDOB kernel: [   18.536000] cs: IO port probe 0xd000-0xefff: clean.
Apr  5 20:53:00 MTOLEDOB kernel: [   18.536000] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
Apr  5 20:53:00 MTOLEDOB kernel: [   18.536000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x37ffffff
Apr  5 20:53:00 MTOLEDOB kernel: [   18.636000] ieee80211_crypt: registered algorithm 'NULL'
Apr  5 20:53:00 MTOLEDOB kernel: [   18.692000] input: PC Speaker as /class/input/input2
Apr  5 20:53:00 MTOLEDOB kernel: [   18.840000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Apr  5 20:53:00 MTOLEDOB kernel: [   18.840000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Apr  5 20:53:00 MTOLEDOB kernel: [   18.876000] parport: PnPBIOS parport detected.
Apr  5 20:53:00 MTOLEDOB kernel: [   18.876000] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Apr  5 20:53:00 MTOLEDOB kernel: [   18.896000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
Apr  5 20:53:00 MTOLEDOB kernel: [   18.896000] ipw2100: Copyright(c) 2003-2006 Intel Corporation
Apr  5 20:53:00 MTOLEDOB kernel: [   18.896000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Apr  5 20:53:00 MTOLEDOB kernel: [   18.896000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
Apr  5 20:53:00 MTOLEDOB kernel: [   19.172000] pccard: PCMCIA card inserted into slot 1
Apr  5 20:53:00 MTOLEDOB kernel: [   19.276000] cs: memory probe 0xf6000000-0xfbffffff: excluding 0xf6000000-0xf65fffff 0xf6c00000-0xf71fffff 0xf7e00000-0xf83fffff 0xf9c00000-0xfa1fffff<6>input: DualPoint Stick as /class/input/input3
Apr  5 20:53:00 MTOLEDOB kernel: [   19.288000]  0xfae00000-0xfb3fffff
Apr  5 20:53:00 MTOLEDOB kernel: [   19.288000] pcmcia: registering new device pcmcia1.0
Apr  5 20:53:00 MTOLEDOB kernel: [   19.308000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Apr  5 20:53:00 MTOLEDOB kernel: [   19.308000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
Apr  5 20:53:00 MTOLEDOB kernel: [   19.308000] input: AlpsPS/2 ALPS DualPoint TouchPad as /class/input/input4
Apr  5 20:53:00 MTOLEDOB kernel: [   19.348000] cs: IO port probe 0x100-0x3af: clean.
Apr  5 20:53:00 MTOLEDOB kernel: [   19.348000] cs: IO port probe 0x3e0-0x4ff: clean.
Apr  5 20:53:00 MTOLEDOB kernel: [   19.352000] cs: IO port probe 0x820-0x8ff: clean.
Apr  5 20:53:00 MTOLEDOB kernel: [   19.352000] cs: IO port probe 0xc00-0xcf7: clean.
Apr  5 20:53:00 MTOLEDOB kernel: [   19.352000] cs: IO port probe 0xa00-0xaff: clean.
Apr  5 20:53:00 MTOLEDOB kernel: [   19.368000] cs: IO port probe 0x100-0x3af: clean.
Apr  5 20:53:00 MTOLEDOB kernel: [   19.368000] cs: IO port probe 0x3e0-0x4ff: clean.
Apr  5 20:53:00 MTOLEDOB kernel: [   19.368000] cs: IO port probe 0x820-0x8ff: clean.
Apr  5 20:53:00 MTOLEDOB kernel: [   19.368000] cs: IO port probe 0xc00-0xcf7: clean.
Apr  5 20:53:00 MTOLEDOB kernel: [   19.368000] cs: IO port probe 0xa00-0xaff: clean.
Apr  5 20:53:00 MTOLEDOB kernel: [   20.128000] intel8x0_measure_ac97_clock: measured 55460 usecs
Apr  5 20:53:00 MTOLEDOB kernel: [   20.128000] intel8x0: clocking to 48000
Apr  5 20:53:00 MTOLEDOB kernel: [   20.560000] fuse init (API version 7.8)
Apr  5 20:53:00 MTOLEDOB kernel: [   20.600000] lp0: using parport0 (interrupt-driven).
Apr  5 20:53:00 MTOLEDOB kernel: [   20.636000] Adding 1510068k swap on /dev/sda5.  Priority:-1 extents:1 across:1510068k
Apr  5 20:53:00 MTOLEDOB kernel: [   20.944000] EXT3 FS on sda2, internal journal
Apr  5 20:53:00 MTOLEDOB kernel: [   25.028000] ACPI: AC Adapter [AC] (on-line)
Apr  5 20:53:00 MTOLEDOB kernel: [   25.088000] input: Lid Switch as /class/input/input5
Apr  5 20:53:00 MTOLEDOB kernel: [   25.092000] ACPI: Lid Switch [LID]
Apr  5 20:53:00 MTOLEDOB kernel: [   25.140000] input: Power Button (CM) as /class/input/input6
Apr  5 20:53:00 MTOLEDOB kernel: [   25.144000] ACPI: Power Button (CM) [PBTN]
Apr  5 20:53:00 MTOLEDOB kernel: [   25.192000] input: Sleep Button (CM) as /class/input/input7
Apr  5 20:53:00 MTOLEDOB kernel: [   25.196000] ACPI: Sleep Button (CM) [SBTN]
Apr  5 20:53:00 MTOLEDOB kernel: [   25.220000] ACPI: ACPI Dock Station Driver 
Apr  5 20:53:00 MTOLEDOB kernel: [   25.628000] ACPI: Battery Slot [BAT0] (battery present)
Apr  5 20:53:00 MTOLEDOB kernel: [   25.628000] ACPI: Battery Slot [BAT1] (battery absent)
Apr  5 20:53:00 MTOLEDOB kernel: [   25.640000] Using specific hotkey driver
Apr  5 20:53:00 MTOLEDOB kernel: [   25.672000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Apr  5 20:53:00 MTOLEDOB kernel: [   25.732000] ibm_acpi: ec object not found
Apr  5 20:53:00 MTOLEDOB kernel: [   25.780000] pcc_acpi: loading...
Apr  5 20:53:00 MTOLEDOB NetworkManager: <info>  starting... 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.672358] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_3340'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.958789] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_3341'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.959771] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_4c66'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.960518] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c2'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.961051] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.961539] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.962020] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c4'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.962498] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.962975] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.963453] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c7'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.963929] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.964407] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.964976] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24cd'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.965459] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.965936] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.966412] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.966887] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_165d'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.967361] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1217_7113'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.967836] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1217_7113_0'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.968309] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pcmcia__1__1'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.968848] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_1043'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.969324] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24cc'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.969798] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.970287] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.970758] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_scsi_device_lun0'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.971229] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_0'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.971702] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_0_scsi_device_lun0'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.972174] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.972642] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c6'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.973122] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_dock_0'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.973592] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.974062] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.974529] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.974999] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.975469] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.975937] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.976444] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.976923] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_vesafb_0'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.977392] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.977859] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.978326] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.978792] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.979258] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.979723] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.980217] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.980683] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.981158] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.981639] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.982103] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.982567] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.983029] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0401'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.983492] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.983956] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.984417] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.984887] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.985748] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Apr  5 20:53:00 MTOLEDOB NetworkManager: <debug> [1207450380.990210] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <debug> [1207450381.003671] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_11_43_53_d5_22'). 
Apr  5 20:53:01 MTOLEDOB kernel: [   27.532000] PM: Writing back config space on device 0000:02:00.0 at offset c (was ffbf0000, writing 0)
Apr  5 20:53:01 MTOLEDOB kernel: [   27.532000] PM: Writing back config space on device 0000:02:00.0 at offset b (was 165d14e4, writing 865d1028)
Apr  5 20:53:01 MTOLEDOB kernel: [   27.532000] PM: Writing back config space on device 0000:02:00.0 at offset 3 (was 0, writing 2008)
Apr  5 20:53:01 MTOLEDOB kernel: [   27.532000] PM: Writing back config space on device 0000:02:00.0 at offset 2 (was 2000000, writing 2000001)
Apr  5 20:53:01 MTOLEDOB kernel: [   27.532000] PM: Writing back config space on device 0000:02:00.0 at offset 1 (was 2b00000, writing 2b00106)
Apr  5 20:53:01 MTOLEDOB NetworkManager: <info>  eth0: Device is fully-supported using driver 'tg3'. 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Apr  5 20:53:01 MTOLEDOB gdm[4786]: WARNING: Didn't understand `' (expected true or false) 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <info>  Deactivating device eth0. 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <debug> [1207450381.444110] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_0c_f1_1c_20_6b'). 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <info>  eth1: Device is fully-supported using driver 'ipw2100'. 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <info>  Deactivating device eth1. 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <debug> [1207450381.621653] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_scsi_device_lun0_scsi_generic'). 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <debug> [1207450381.622352] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <debug> [1207450381.622847] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_pcm_1'). 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <debug> [1207450381.623349] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_pcm_0'). 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <debug> [1207450381.623829] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_control__1'). 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <debug> [1207450381.624306] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_pcm_0_0'). 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <debug> [1207450381.624784] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_mixer__1'). 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <debug> [1207450381.625274] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_0'). 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <debug> [1207450381.625748] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_playback_0'). 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <debug> [1207450381.626223] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_1'). 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <debug> [1207450381.626697] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_2'). 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <debug> [1207450381.627173] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_3'). 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <debug> [1207450381.627648] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_playback_4'). 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <debug> [1207450381.628123] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <debug> [1207450381.628597] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <debug> [1207450381.629205] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <debug> [1207450381.629691] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <debug> [1207450381.630164] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <debug> [1207450381.630642] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <debug> [1207450381.631118] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_3'). 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <debug> [1207450381.631593] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'). 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <debug> [1207450381.632064] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <debug> [1207450381.632554] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <debug> [1207450381.633122] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <debug> [1207450381.633598] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <debug> [1207450381.634068] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST980815A_5LY1VWH9'). 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <debug> [1207450381.837531] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_606C05936C0564DE'). 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <debug> [1207450381.843915] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_241da2db_0e86_4d13_ba31_7e747e81c264'). 
Apr  5 20:53:01 MTOLEDOB kernel: [   28.408000] ppdev: user-space parallel port driver
Apr  5 20:53:01 MTOLEDOB NetworkManager: <debug> [1207450381.969542] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part3_size_1024'). 
Apr  5 20:53:01 MTOLEDOB NetworkManager: <debug> [1207450381.975467] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_aaabdd49_42ff_4b7f_ac15_b1a4f0ed1a87'). 
Apr  5 20:53:02 MTOLEDOB NetworkManager: <debug> [1207450382.260172] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT1'). 
Apr  5 20:53:02 MTOLEDOB NetworkManager: <debug> [1207450382.321608] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Apr  5 20:53:02 MTOLEDOB NetworkManager: <debug> [1207450382.322354] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Apr  5 20:53:02 MTOLEDOB NetworkManager: <debug> [1207450382.322834] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Apr  5 20:53:02 MTOLEDOB NetworkManager: <debug> [1207450382.328364] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_RW/DVD_GCC_4241N'). 
Apr  5 20:53:02 MTOLEDOB kernel: [   29.224000] [drm] Initialized drm 1.1.0 20060810
Apr  5 20:53:02 MTOLEDOB kernel: [   29.252000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Apr  5 20:53:02 MTOLEDOB kernel: [   29.256000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
Apr  5 20:53:02 MTOLEDOB kernel: [   29.308000] apm: BIOS not found.
Apr  5 20:53:04 MTOLEDOB kernel: [   30.456000] Capability LSM initialized
Apr  5 20:53:04 MTOLEDOB avahi-daemon[5367]: Found user 'avahi' (UID 105) and group 'avahi' (GID 109).
Apr  5 20:53:04 MTOLEDOB avahi-daemon[5367]: Successfully dropped root privileges.
Apr  5 20:53:04 MTOLEDOB avahi-daemon[5367]: avahi-daemon 0.6.20 starting up.
Apr  5 20:53:04 MTOLEDOB avahi-daemon[5367]: Successfully called chroot().
Apr  5 20:53:04 MTOLEDOB avahi-daemon[5367]: Successfully dropped remaining capabilities.
Apr  5 20:53:04 MTOLEDOB avahi-daemon[5367]: No service file found in /etc/avahi/services.
Apr  5 20:53:04 MTOLEDOB avahi-daemon[5367]: Network interface enumeration completed.
Apr  5 20:53:04 MTOLEDOB avahi-daemon[5367]: Registering HINFO record with values 'I686'/'LINUX'.
Apr  5 20:53:04 MTOLEDOB avahi-daemon[5367]: Server startup complete. Host name is MTOLEDOB.local. Local service cookie is 2447953358.
Apr  5 20:53:04 MTOLEDOB dhcdbd: Started up.
Apr  5 20:53:04 MTOLEDOB hcid[5406]: Bluetooth HCI daemon
Apr  5 20:53:04 MTOLEDOB NetworkManager: <debug> [1207450384.243852] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Apr  5 20:53:04 MTOLEDOB kernel: [   30.672000] Bluetooth: Core ver 2.11
Apr  5 20:53:04 MTOLEDOB kernel: [   30.672000] NET: Registered protocol family 31
Apr  5 20:53:04 MTOLEDOB kernel: [   30.672000] Bluetooth: HCI device and connection manager initialized
Apr  5 20:53:04 MTOLEDOB kernel: [   30.672000] Bluetooth: HCI socket layer initialized
Apr  5 20:53:04 MTOLEDOB hcid[5406]: Starting SDP server
Apr  5 20:53:04 MTOLEDOB kernel: [   30.740000] Bluetooth: L2CAP ver 2.8
Apr  5 20:53:04 MTOLEDOB kernel: [   30.740000] Bluetooth: L2CAP socket layer initialized
Apr  5 20:53:04 MTOLEDOB hcid[5406]: Created local server at unix:abstract=/var/run/dbus-bkVbdVOZiL,guid=dc2491617b11ba789966750047f83b10
Apr  5 20:53:04 MTOLEDOB audio[5419]: Bluetooth Audio daemon
Apr  5 20:53:04 MTOLEDOB audio[5419]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Apr  5 20:53:04 MTOLEDOB audio[5419]: Unix socket created: 5
Apr  5 20:53:04 MTOLEDOB input[5420]: Bluetooth Input daemon
Apr  5 20:53:04 MTOLEDOB input[5420]: Registered input manager path:/org/bluez/input
Apr  5 20:53:04 MTOLEDOB kernel: [   30.856000] Bluetooth: RFCOMM socket layer initialized
Apr  5 20:53:04 MTOLEDOB kernel: [   30.856000] Bluetooth: RFCOMM TTY layer initialized
Apr  5 20:53:04 MTOLEDOB kernel: [   30.856000] Bluetooth: RFCOMM ver 1.8
Apr  5 20:53:04 MTOLEDOB audio[5419]: add_service_record: got record id 0x10000
Apr  5 20:53:04 MTOLEDOB audio[5419]: add_service_record: got record id 0x10001
Apr  5 20:53:04 MTOLEDOB audio[5419]: Registered manager path:/org/bluez/audio
Apr  5 20:53:04 MTOLEDOB anacron[5451]: Anacron 2.3 started on 2008-04-05
Apr  5 20:53:04 MTOLEDOB anacron[5451]: Normal exit (0 jobs run)
Apr  5 21:06:59 MTOLEDOB syslogd 1.4.1#21ubuntu3: restart.
Apr  5 21:06:59 MTOLEDOB kernel: Inspecting /boot/System.map-2.6.22-14-generic
Apr  5 21:06:59 MTOLEDOB NetworkManager: <info>  starting... 
Apr  5 21:06:59 MTOLEDOB kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Apr  5 21:06:59 MTOLEDOB kernel: Symbols match kernel version 2.6.22.
Apr  5 21:06:59 MTOLEDOB kernel: No module symbols loaded - kernel modules not enabled. 
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000] BIOS-provided physical RAM map:
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffae000 (usable)
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 000000001ffae000 - 0000000020000000 (reserved)
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fee00000 (reserved)
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000] 0MB HIGHMEM available.
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000] 511MB LOWMEM available.
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000] Entering add_active_range(0, 0, 130990) 0 entries of 256 used
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000] Zone PFN ranges:
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000]   DMA             0 ->     4096
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000]   Normal       4096 ->   130990
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000]   HighMem    130990 ->   130990
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000]     0:        0 ->   130990
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000] On node 0 totalpages: 130990
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000]   Normal zone: 991 pages used for memmap
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000]   Normal zone: 125903 pages, LIFO batch:31
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000] DMI 2.3 present.
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FDF00 checksum 0
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000] ACPI: RSDP 000FDF00, 0014 (r0 DELL  )
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000] ACPI: RSDT 1FFF0000, 002C (r1 DELL    CPi R   27D5011A ASL        61)
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000] ACPI: FACP 1FFF0400, 0074 (r1 DELL    CPi R   27D5011A ASL        61)
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000] ACPI: DSDT 1FFF0C00, 2E1A (r1 INT430 SYSFexxx     1001 MSFT  100000E)
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000] ACPI: FACS 1FFFF800, 0040
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000] ACPI: ASF! 1FFF0800, 005B (r16 DELL    CPi R   27D5011A ASL        61)
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:deda0000)
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000] Built 1 zonelists.  Total pages: 129967
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000] Kernel command line: root=UUID=241da2db-0e86-4d13-ba31-7e747e81c264 ro quiet splash
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000] mapped APIC to ffffd000 (0140d000)
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000] Initializing CPU#0
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
Apr  5 21:06:59 MTOLEDOB kernel: [    0.000000] Detected 1398.884 MHz processor.
Apr  5 21:06:59 MTOLEDOB kernel: [  587.554416] Console: colour VGA+ 80x25
Apr  5 21:06:59 MTOLEDOB kernel: [  587.554727] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr  5 21:06:59 MTOLEDOB kernel: [  587.555041] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr  5 21:06:59 MTOLEDOB kernel: [  587.572750] Memory: 506636k/523960k available (2015k kernel code, 16752k reserved, 915k data, 364k init, 0k highmem)
Apr  5 21:06:59 MTOLEDOB kernel: [  587.572763] virtual kernel memory layout:
Apr  5 21:06:59 MTOLEDOB kernel: [  587.572765]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Apr  5 21:06:59 MTOLEDOB kernel: [  587.572767]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr  5 21:06:59 MTOLEDOB kernel: [  587.572769]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
Apr  5 21:06:59 MTOLEDOB kernel: [  587.572770]     lowmem  : 0xc0000000 - 0xdffae000   ( 511 MB)
Apr  5 21:06:59 MTOLEDOB kernel: [  587.572772]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Apr  5 21:06:59 MTOLEDOB kernel: [  587.572774]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
Apr  5 21:06:59 MTOLEDOB kernel: [  587.572776]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
Apr  5 21:06:59 MTOLEDOB kernel: [  587.572780] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr  5 21:06:59 MTOLEDOB kernel: [  587.572829] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Apr  5 21:06:59 MTOLEDOB kernel: [  587.652850] Calibrating delay using timer specific routine.. 2799.71 BogoMIPS (lpj=5599422)
Apr  5 21:06:59 MTOLEDOB kernel: [  587.652882] Security Framework v1.0.0 initialized
Apr  5 21:06:59 MTOLEDOB kernel: [  587.652890] SELinux:  Disabled at boot.
Apr  5 21:06:59 MTOLEDOB kernel: [  587.652909] Mount-cache hash table entries: 512
Apr  5 21:06:59 MTOLEDOB kernel: [  587.653064] CPU: After generic identify, caps: a7e9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
Apr  5 21:06:59 MTOLEDOB kernel: [  587.653079] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr  5 21:06:59 MTOLEDOB kernel: [  587.653083] CPU: L2 cache: 1024K
Apr  5 21:06:59 MTOLEDOB kernel: [  587.653086] CPU: After all inits, caps: a7e9f9bf 00000000 00000000 00002040 00000180 00000000 00000000
Apr  5 21:06:59 MTOLEDOB kernel: [  587.653098] Compat vDSO mapped to ffffe000.
Apr  5 21:06:59 MTOLEDOB kernel: [  587.653111] Checking 'hlt' instruction... OK.
Apr  5 21:06:59 MTOLEDOB kernel: [  587.668957] SMP alternatives: switching to UP code
Apr  5 21:06:59 MTOLEDOB kernel: [  587.669138] Freeing SMP alternatives: 11k freed
Apr  5 21:06:59 MTOLEDOB kernel: [  587.669444] Early unpacking initramfs... done
Apr  5 21:06:59 MTOLEDOB kernel: [  588.115706] ACPI: Core revision 20070126
Apr  5 21:06:59 MTOLEDOB kernel: [  588.115781] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Apr  5 21:06:59 MTOLEDOB kernel: [  588.117447] ACPI: setting ELCR to 0200 (from 0800)
Apr  5 21:06:59 MTOLEDOB kernel: [  588.119695] CPU0: Intel(R) Pentium(R) M processor 1400MHz stepping 05
Apr  5 21:06:59 MTOLEDOB kernel: [  588.119703] SMP motherboard not detected.
Apr  5 21:06:59 MTOLEDOB kernel: [  588.119706] Local APIC not detected. Using dummy APIC emulation.
Apr  5 21:06:59 MTOLEDOB kernel: [  588.119746] Brought up 1 CPUs
Apr  5 21:06:59 MTOLEDOB kernel: [  588.119883] Booting paravirtualized kernel on bare hardware
Apr  5 21:06:59 MTOLEDOB kernel: [  588.119952] Time: 21:06:37  Date: 03/05/108
Apr  5 21:06:59 MTOLEDOB kernel: [  588.119980] NET: Registered protocol family 16
Apr  5 21:06:59 MTOLEDOB kernel: [  588.120076] EISA bus registered
Apr  5 21:06:59 MTOLEDOB kernel: [  588.120089] ACPI: bus type pci registered
Apr  5 21:06:59 MTOLEDOB kernel: [  588.153771] PCI: PCI BIOS revision 2.10 entry at 0xfc96e, last bus=2
Apr  5 21:06:59 MTOLEDOB kernel: [  588.153774] PCI: Using configuration type 1
Apr  5 21:06:59 MTOLEDOB kernel: [  588.153776] Setting up standard PCI resources
Apr  5 21:06:59 MTOLEDOB kernel: [  588.155957] ACPI: EC: Look up EC in DSDT
Apr  5 21:06:59 MTOLEDOB kernel: [  588.163049] ACPI: Interpreter enabled
Apr  5 21:06:59 MTOLEDOB kernel: [  588.163054] ACPI: (supports S0 S1 S3 S4 S5)
Apr  5 21:06:59 MTOLEDOB kernel: [  588.163074] ACPI: Using PIC for interrupt routing
Apr  5 21:06:59 MTOLEDOB kernel: [  588.176207] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr  5 21:06:59 MTOLEDOB kernel: [  588.176232] PCI: Probing PCI hardware (bus 00)
Apr  5 21:06:59 MTOLEDOB kernel: [  588.176613] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
Apr  5 21:06:59 MTOLEDOB kernel: [  588.176618] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
Apr  5 21:06:59 MTOLEDOB kernel: [  588.177116] PCI: Transparent bridge - 0000:00:1e.0
Apr  5 21:06:59 MTOLEDOB kernel: [  588.177234] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr  5 21:06:59 MTOLEDOB kernel: [  588.177616] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Apr  5 21:06:59 MTOLEDOB kernel: [  588.177709] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Apr  5 21:06:59 MTOLEDOB kernel: [  588.192160] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
Apr  5 21:06:59 MTOLEDOB kernel: [  588.192276] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
Apr  5 21:06:59 MTOLEDOB kernel: [  588.192389] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
Apr  5 21:06:59 MTOLEDOB kernel: [  588.192501] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
Apr  5 21:06:59 MTOLEDOB kernel: [  588.192599] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Apr  5 21:06:59 MTOLEDOB kernel: [  588.192716] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Apr  5 21:06:59 MTOLEDOB kernel: [  588.192824] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr  5 21:06:59 MTOLEDOB kernel: [  588.192836] pnp: PnP ACPI init
Apr  5 21:06:59 MTOLEDOB kernel: [  588.192870] ACPI: bus type pnp registered
Apr  5 21:06:59 MTOLEDOB kernel: [  588.220736] pnp: PnP ACPI: found 13 devices
Apr  5 21:06:59 MTOLEDOB kernel: [  588.220740] ACPI: ACPI bus type pnp unregistered
Apr  5 21:06:59 MTOLEDOB kernel: [  588.220746] PnPBIOS: Disabled by ACPI PNP
Apr  5 21:06:59 MTOLEDOB kernel: [  588.220803] PCI: Using ACPI for IRQ routing
Apr  5 21:06:59 MTOLEDOB kernel: [  588.220807] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr  5 21:06:59 MTOLEDOB kernel: [  588.227232] NET: Registered protocol family 8
Apr  5 21:06:59 MTOLEDOB kernel: [  588.227235] NET: Registered protocol family 20
Apr  5 21:06:59 MTOLEDOB kernel: [  588.227298] pnp: 00:00: iomem range 0x0-0x9fbff could not be reserved
Apr  5 21:06:59 MTOLEDOB kernel: [  588.227302] pnp: 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
Apr  5 21:06:59 MTOLEDOB kernel: [  588.227306] pnp: 00:00: iomem range 0xc0000-0xcffff could not be reserved
Apr  5 21:06:59 MTOLEDOB kernel: [  588.227310] pnp: 00:00: iomem range 0xe0000-0xfffff could not be reserved
Apr  5 21:06:59 MTOLEDOB kernel: [  588.227318] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
Apr  5 21:06:59 MTOLEDOB kernel: [  588.227321] pnp: 00:02: ioport range 0x800-0x805 has been reserved
Apr  5 21:06:59 MTOLEDOB kernel: [  588.227325] pnp: 00:02: ioport range 0x808-0x80f has been reserved
Apr  5 21:06:59 MTOLEDOB kernel: [  588.227332] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
Apr  5 21:06:59 MTOLEDOB kernel: [  588.227335] pnp: 00:03: ioport range 0x806-0x807 has been reserved
Apr  5 21:06:59 MTOLEDOB kernel: [  588.227339] pnp: 00:03: ioport range 0x810-0x85f has been reserved
Apr  5 21:06:59 MTOLEDOB kernel: [  588.227343] pnp: 00:03: ioport range 0x860-0x87f has been reserved
Apr  5 21:06:59 MTOLEDOB kernel: [  588.227346] pnp: 00:03: ioport range 0x880-0x8bf has been reserved
Apr  5 21:06:59 MTOLEDOB kernel: [  588.227350] pnp: 00:03: ioport range 0x8c0-0x8df has been reserved
Apr  5 21:06:59 MTOLEDOB kernel: [  588.227358] pnp: 00:08: ioport range 0x900-0x97f has been reserved
Apr  5 21:06:59 MTOLEDOB kernel: [  588.228844] Time: tsc clocksource has been installed.
Apr  5 21:06:59 MTOLEDOB kernel: [  588.257690] PCI: Bridge: 0000:00:01.0
Apr  5 21:06:59 MTOLEDOB kernel: [  588.257693]   IO window: c000-cfff
Apr  5 21:06:59 MTOLEDOB kernel: [  588.257698]   MEM window: fc000000-fdffffff
Apr  5 21:06:59 MTOLEDOB kernel: [  588.257702]   PREFETCH window: e8000000-efffffff
Apr  5 21:06:59 MTOLEDOB kernel: [  588.257716] PCI: Bus 3, cardbus bridge: 0000:02:01.0
Apr  5 21:06:59 MTOLEDOB kernel: [  588.257719]   IO window: 0000d000-0000d0ff
Apr  5 21:06:59 MTOLEDOB kernel: [  588.257724]   IO window: 0000d400-0000d4ff
Apr  5 21:06:59 MTOLEDOB kernel: [  588.257729]   PREFETCH window: 30000000-33ffffff
Apr  5 21:06:59 MTOLEDOB kernel: [  588.257733]   MEM window: 3c000000-3fffffff
Apr  5 21:06:59 MTOLEDOB kernel: [  588.257738] PCI: Bus 7, cardbus bridge: 0000:02:01.1
Apr  5 21:06:59 MTOLEDOB kernel: [  588.257741]   IO window: 0000d800-0000d8ff
Apr  5 21:06:59 MTOLEDOB kernel: [  588.257745]   IO window: 0000dc00-0000dcff
Apr  5 21:06:59 MTOLEDOB kernel: [  588.257750]   PREFETCH window: 34000000-37ffffff
Apr  5 21:06:59 MTOLEDOB kernel: [  588.257755]   MEM window: 40000000-43ffffff
Apr  5 21:06:59 MTOLEDOB kernel: [  588.257759] PCI: Bridge: 0000:00:1e.0
Apr  5 21:06:59 MTOLEDOB kernel: [  588.257763]   IO window: d000-efff
Apr  5 21:06:59 MTOLEDOB kernel: [  588.257768]   MEM window: f6000000-fbffffff
Apr  5 21:06:59 MTOLEDOB kernel: [  588.257773]   PREFETCH window: 30000000-37ffffff
Apr  5 21:06:59 MTOLEDOB kernel: [  588.257789] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Apr  5 21:06:59 MTOLEDOB kernel: [  588.257803] PCI: Enabling device 0000:02:01.0 (0000 -> 0003)
Apr  5 21:06:59 MTOLEDOB kernel: [  588.257975] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Apr  5 21:06:59 MTOLEDOB kernel: [  588.257978] PCI: setting IRQ 11 as level-triggered
Apr  5 21:06:59 MTOLEDOB kernel: [  588.257983] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Apr  5 21:06:59 MTOLEDOB kernel: [  588.258000] PCI: Enabling device 0000:02:01.1 (0000 -> 0003)
Apr  5 21:06:59 MTOLEDOB kernel: [  588.258004] ACPI: PCI Interrupt 0000:02:01.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Apr  5 21:06:59 MTOLEDOB kernel: [  588.258024] NET: Registered protocol family 2
Apr  5 21:06:59 MTOLEDOB kernel: [  588.296885] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Apr  5 21:06:59 MTOLEDOB kernel: [  588.296936] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
Apr  5 21:06:59 MTOLEDOB kernel: [  588.297150] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
Apr  5 21:06:59 MTOLEDOB kernel: [  588.297289] TCP: Hash tables configured (established 16384 bind 16384)
Apr  5 21:06:59 MTOLEDOB kernel: [  588.297292] TCP reno registered
Apr  5 21:06:59 MTOLEDOB kernel: [  588.309006] checking if image is initramfs... it is
Apr  5 21:06:59 MTOLEDOB kernel: [  588.760865] Switched to high resolution mode on CPU 0
Apr  5 21:06:59 MTOLEDOB kernel: [  589.186305] Freeing initrd memory: 8373k freed
Apr  5 21:06:59 MTOLEDOB kernel: [  589.186723] audit: initializing netlink socket (disabled)
Apr  5 21:06:59 MTOLEDOB kernel: [  589.186743] audit(1207429597.160:1): initialized
Apr  5 21:06:59 MTOLEDOB kernel: [  589.189346] VFS: Disk quotas dquot_6.5.1
Apr  5 21:06:59 MTOLEDOB kernel: [  589.189419] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr  5 21:06:59 MTOLEDOB kernel: [  589.189544] io scheduler noop registered
Apr  5 21:06:59 MTOLEDOB kernel: [  589.189547] io scheduler anticipatory registered
Apr  5 21:06:59 MTOLEDOB kernel: [  589.189550] io scheduler deadline registered
Apr  5 21:06:59 MTOLEDOB kernel: [  589.189576] io scheduler cfq registered (default)
Apr  5 21:06:59 MTOLEDOB kernel: [  589.189655] Boot video device is 0000:01:00.0
Apr  5 21:06:59 MTOLEDOB kernel: [  589.189846] isapnp: Scanning for PnP cards...
Apr  5 21:06:59 MTOLEDOB kernel: [  589.542771] isapnp: No Plug & Play device found
Apr  5 21:06:59 MTOLEDOB kernel: [  589.579976] Real Time Clock Driver v1.12ac
Apr  5 21:06:59 MTOLEDOB kernel: [  589.580120] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr  5 21:06:59 MTOLEDOB kernel: [  589.580219] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr  5 21:06:59 MTOLEDOB kernel: [  589.581224] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr  5 21:06:59 MTOLEDOB kernel: [  589.581702] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
Apr  5 21:06:59 MTOLEDOB kernel: [  589.581707] PCI: setting IRQ 5 as level-triggered
Apr  5 21:06:59 MTOLEDOB kernel: [  589.581711] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Apr  5 21:06:59 MTOLEDOB kernel: [  589.581722] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
Apr  5 21:06:59 MTOLEDOB kernel: [  589.582375] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr  5 21:06:59 MTOLEDOB kernel: [  589.582659] input: Macintosh mouse button emulation as /class/input/input0
Apr  5 21:06:59 MTOLEDOB kernel: [  589.582749] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Apr  5 21:06:59 MTOLEDOB kernel: [  589.588614] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr  5 21:06:59 MTOLEDOB kernel: [  589.588621] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr  5 21:06:59 MTOLEDOB kernel: [  589.588839] mice: PS/2 mouse device common for all mice
Apr  5 21:06:59 MTOLEDOB kernel: [  589.588964] EISA: Probing bus 0 at eisa.0
Apr  5 21:06:59 MTOLEDOB kernel: [  589.588993] EISA: Detected 0 cards.
Apr  5 21:06:59 MTOLEDOB kernel: [  589.589123] TCP cubic registered
Apr  5 21:06:59 MTOLEDOB kernel: [  589.589147] NET: Registered protocol family 1
Apr  5 21:06:59 MTOLEDOB kernel: [  589.589182] Using IPI No-Shortcut mode
Apr  5 21:06:59 MTOLEDOB kernel: [  589.589400]   Magic number: 4:654:145
Apr  5 21:06:59 MTOLEDOB kernel: [  589.589609]   hash matches device device:16
Apr  5 21:06:59 MTOLEDOB kernel: [  589.589899] Freeing unused kernel memory: 364k freed
Apr  5 21:06:59 MTOLEDOB kernel: [  589.620823] input: AT Translated Set 2 keyboard as /class/input/input1
Apr  5 21:06:59 MTOLEDOB kernel: [  590.808306] AppArmor: AppArmor initialized<5>audit(1207429599.160:2):  type=1505 info="AppArmor initialized" pid=1205
Apr  5 21:06:59 MTOLEDOB kernel: [  590.818785] fuse init (API version 7.8)
Apr  5 21:06:59 MTOLEDOB kernel: [  590.824325] Failure registering capabilities with primary security module.
Apr  5 21:06:59 MTOLEDOB kernel: [  590.845285] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
Apr  5 21:06:59 MTOLEDOB kernel: [  590.845294] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr  5 21:06:59 MTOLEDOB kernel: [  590.849184] ACPI: Thermal Zone [THM] (61 C)
Apr  5 21:06:59 MTOLEDOB kernel: [  591.310275] usbcore: registered new interface driver usbfs
Apr  5 21:06:59 MTOLEDOB kernel: [  591.310306] usbcore: registered new interface driver hub
Apr  5 21:06:59 MTOLEDOB kernel: [  591.310335] usbcore: registered new device driver usb
Apr  5 21:06:59 MTOLEDOB kernel: [  591.311994] USB Universal Host Controller Interface driver v3.0
Apr  5 21:06:59 MTOLEDOB kernel: [  591.312325] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
Apr  5 21:06:59 MTOLEDOB kernel: [  591.312330] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Apr  5 21:06:59 MTOLEDOB kernel: [  591.312344] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Apr  5 21:06:59 MTOLEDOB kernel: [  591.312349] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr  5 21:06:59 MTOLEDOB kernel: [  591.312597] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Apr  5 21:06:59 MTOLEDOB kernel: [  591.312647] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
Apr  5 21:06:59 MTOLEDOB kernel: [  591.312803] usb usb1: configuration #1 chosen from 1 choice
Apr  5 21:06:59 MTOLEDOB kernel: [  591.312834] hub 1-0:1.0: USB hub found
Apr  5 21:06:59 MTOLEDOB kernel: [  591.312841] hub 1-0:1.0: 2 ports detected
Apr  5 21:06:59 MTOLEDOB kernel: [  591.418774] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Apr  5 21:06:59 MTOLEDOB kernel: [  591.418792] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Apr  5 21:06:59 MTOLEDOB kernel: [  591.418797] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr  5 21:06:59 MTOLEDOB kernel: [  591.418827] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Apr  5 21:06:59 MTOLEDOB kernel: [  591.418853] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
Apr  5 21:06:59 MTOLEDOB kernel: [  591.418995] usb usb2: configuration #1 chosen from 1 choice
Apr  5 21:06:59 MTOLEDOB kernel: [  591.419029] hub 2-0:1.0: USB hub found
Apr  5 21:06:59 MTOLEDOB kernel: [  591.419038] hub 2-0:1.0: 2 ports detected
Apr  5 21:06:59 MTOLEDOB kernel: [  591.419459] SCSI subsystem initialized
Apr  5 21:06:59 MTOLEDOB kernel: [  591.432058] libata version 2.21 loaded.
Apr  5 21:06:59 MTOLEDOB kernel: [  591.521078] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
Apr  5 21:06:59 MTOLEDOB kernel: [  591.521085] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Apr  5 21:06:59 MTOLEDOB kernel: [  591.521100] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Apr  5 21:06:59 MTOLEDOB kernel: [  591.521105] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr  5 21:06:59 MTOLEDOB kernel: [  591.521136] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Apr  5 21:06:59 MTOLEDOB kernel: [  591.521162] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
Apr  5 21:06:59 MTOLEDOB kernel: [  591.521294] usb usb3: configuration #1 chosen from 1 choice
Apr  5 21:06:59 MTOLEDOB kernel: [  591.521328] hub 3-0:1.0: USB hub found
Apr  5 21:06:59 MTOLEDOB kernel: [  591.521336] hub 3-0:1.0: 2 ports detected
Apr  5 21:06:59 MTOLEDOB kernel: [  591.625590] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
Apr  5 21:06:59 MTOLEDOB kernel: [  591.625596] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
Apr  5 21:06:59 MTOLEDOB kernel: [  591.625612] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Apr  5 21:06:59 MTOLEDOB kernel: [  591.625617] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr  5 21:06:59 MTOLEDOB kernel: [  591.625653] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
Apr  5 21:06:59 MTOLEDOB kernel: [  591.625692] ehci_hcd 0000:00:1d.7: debug port 1
Apr  5 21:06:59 MTOLEDOB kernel: [  591.625700] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Apr  5 21:06:59 MTOLEDOB kernel: [  591.625709] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf4fffc00
Apr  5 21:06:59 MTOLEDOB kernel: [  591.629594] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Apr  5 21:06:59 MTOLEDOB kernel: [  591.629700] usb usb4: configuration #1 chosen from 1 choice
Apr  5 21:06:59 MTOLEDOB kernel: [  591.629734] hub 4-0:1.0: USB hub found
Apr  5 21:06:59 MTOLEDOB kernel: [  591.629743] hub 4-0:1.0: 6 ports detected
Apr  5 21:06:59 MTOLEDOB kernel: [  591.733535] ata_piix 0000:00:1f.1: version 2.11
Apr  5 21:06:59 MTOLEDOB kernel: [  591.733553] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
Apr  5 21:06:59 MTOLEDOB kernel: [  591.733565] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Apr  5 21:06:59 MTOLEDOB kernel: [  591.733611] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Apr  5 21:06:59 MTOLEDOB kernel: [  591.733722] scsi0 : ata_piix
Apr  5 21:06:59 MTOLEDOB kernel: [  591.733777] scsi1 : ata_piix
Apr  5 21:06:59 MTOLEDOB kernel: [  591.734804] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
Apr  5 21:06:59 MTOLEDOB kernel: [  591.734809] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
Apr  5 21:06:59 MTOLEDOB kernel: [    4.252000] Marking TSC unstable due to: possible TSC halt in C2.
Apr  5 21:06:59 MTOLEDOB kernel: [    4.256000] Time: acpi_pm clocksource has been installed.
Apr  5 21:06:59 MTOLEDOB kernel: [    4.328000] ata1.00: ATA-6: ST980815A, 3.ALD, max UDMA/100
Apr  5 21:06:59 MTOLEDOB kernel: [    4.328000] ata1.00: 156301488 sectors, multi 8: LBA48 
Apr  5 21:06:59 MTOLEDOB kernel: [    4.344000] ata1.00: configured for UDMA/100
Apr  5 21:06:59 MTOLEDOB kernel: [    4.664000] ata2.00: ATAPI: HL-DT-STCD-RW/DVD-ROM GCC-4241N, A101, max UDMA/33
Apr  5 21:06:59 MTOLEDOB kernel: [    4.836000] ata2.00: configured for UDMA/33
Apr  5 21:06:59 MTOLEDOB kernel: [    4.836000] scsi 0:0:0:0: Direct-Access     ATA      ST980815A        3.AL PQ: 0 ANSI: 5
Apr  5 21:06:59 MTOLEDOB kernel: [    4.840000] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4241N A101 PQ: 0 ANSI: 5
Apr  5 21:06:59 MTOLEDOB kernel: [    4.844000] tg3.c:v3.77 (May 31, 2007)
Apr  5 21:06:59 MTOLEDOB kernel: [    4.844000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Apr  5 21:06:59 MTOLEDOB kernel: [    4.892000] eth0: Tigon3 [partno(BCM95705A50) rev 3001 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000Base-T Ethernet 00:11:43:53:d5:22
Apr  5 21:06:59 MTOLEDOB kernel: [    4.892000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
Apr  5 21:06:59 MTOLEDOB kernel: [    4.892000] eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
Apr  5 21:06:59 MTOLEDOB kernel: [    4.896000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr  5 21:06:59 MTOLEDOB kernel: [    4.896000] sd 0:0:0:0: [sda] Write Protect is off
Apr  5 21:06:59 MTOLEDOB kernel: [    4.896000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr  5 21:06:59 MTOLEDOB kernel: [    4.896000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  5 21:06:59 MTOLEDOB kernel: [    4.896000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr  5 21:06:59 MTOLEDOB kernel: [    4.896000] sd 0:0:0:0: [sda] Write Protect is off
Apr  5 21:06:59 MTOLEDOB kernel: [    4.896000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr  5 21:06:59 MTOLEDOB kernel: [    4.896000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  5 21:06:59 MTOLEDOB kernel: [    4.896000]  sda: sda1 sda2 sda3 < sda5 >
Apr  5 21:06:59 MTOLEDOB kernel: [    4.984000] sd 0:0:0:0: [sda] Attached SCSI disk
Apr  5 21:06:59 MTOLEDOB kernel: [    4.992000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr  5 21:06:59 MTOLEDOB kernel: [    4.992000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
Apr  5 21:06:59 MTOLEDOB kernel: [    5.024000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Apr  5 21:06:59 MTOLEDOB kernel: [    5.024000] Uniform CD-ROM driver Revision: 3.20
Apr  5 21:06:59 MTOLEDOB kernel: [    5.024000] sr 1:0:0:0: Attached scsi CD-ROM sr0
Apr  5 21:06:59 MTOLEDOB kernel: [    5.228000] Attempting manual resume
Apr  5 21:06:59 MTOLEDOB kernel: [    5.228000] swsusp: Resume From Partition 8:5
Apr  5 21:06:59 MTOLEDOB kernel: [    5.228000] PM: Checking swsusp image.
Apr  5 21:06:59 MTOLEDOB kernel: [    5.228000] PM: Resume from disk failed.
Apr  5 21:06:59 MTOLEDOB kernel: [    5.252000] EXT3-fs: INFO: recovery required on readonly filesystem.
Apr  5 21:06:59 MTOLEDOB kernel: [    5.252000] EXT3-fs: write access will be enabled during recovery.
Apr  5 21:06:59 MTOLEDOB kernel: [    5.876000] kjournald starting.  Commit interval 5 seconds
Apr  5 21:06:59 MTOLEDOB kernel: [    5.876000] EXT3-fs: recovery complete.
Apr  5 21:06:59 MTOLEDOB kernel: [    5.880000] EXT3-fs: mounted filesystem with ordered data mode.
Apr  5 21:06:59 MTOLEDOB kernel: [   16.068000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr  5 21:06:59 MTOLEDOB kernel: [   16.072000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr  5 21:06:59 MTOLEDOB kernel: [   16.296000] Linux agpgart interface v0.102 (c) Dave Jones
Apr  5 21:06:59 MTOLEDOB kernel: [   16.520000] agpgart: Detected an Intel 855PM Chipset.
Apr  5 21:06:59 MTOLEDOB kernel: [   16.528000] agpgart: AGP aperture is 128M @ 0xe0000000
Apr  5 21:06:59 MTOLEDOB kernel: [   16.544000] iTCO_vendor_support: vendor-support=0
Apr  5 21:06:59 MTOLEDOB kernel: [   16.548000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
Apr  5 21:06:59 MTOLEDOB kernel: [   16.548000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x0860)
Apr  5 21:06:59 MTOLEDOB kernel: [   16.548000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Apr  5 21:06:59 MTOLEDOB kernel: [   16.568000] intel_rng: FWH not detected
Apr  5 21:06:59 MTOLEDOB kernel: [   16.688000] Yenta: CardBus bridge found at 0000:02:01.0 [1028:011d]
Apr  5 21:06:59 MTOLEDOB kernel: [   16.688000] Yenta O2: res at 0x94/0xD4: 00/ea
Apr  5 21:06:59 MTOLEDOB kernel: [   16.688000] Yenta O2: enabling read prefetch/write burst
Apr  5 21:06:59 MTOLEDOB kernel: [   16.764000] ieee80211_crypt: registered algorithm 'NULL'
Apr  5 21:06:59 MTOLEDOB kernel: [   16.776000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Apr  5 21:06:59 MTOLEDOB kernel: [   16.776000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Apr  5 21:06:59 MTOLEDOB kernel: [   16.816000] Yenta: ISA IRQ mask 0x0498, PCI irq 11
Apr  5 21:06:59 MTOLEDOB kernel: [   16.816000] Socket status: 30000006
Apr  5 21:06:59 MTOLEDOB kernel: [   16.816000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
Apr  5 21:06:59 MTOLEDOB kernel: [   16.816000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
Apr  5 21:06:59 MTOLEDOB kernel: [   16.816000] cs: IO port probe 0xd000-0xefff: clean.
Apr  5 21:06:59 MTOLEDOB kernel: [   16.816000] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
Apr  5 21:06:59 MTOLEDOB kernel: [   16.816000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x37ffffff
Apr  5 21:06:59 MTOLEDOB kernel: [   16.816000] Yenta: CardBus bridge found at 0000:02:01.1 [1028:011d]
Apr  5 21:06:59 MTOLEDOB kernel: [   16.944000] Yenta: ISA IRQ mask 0x0498, PCI irq 11
Apr  5 21:06:59 MTOLEDOB kernel: [   16.944000] Socket status: 30000410
Apr  5 21:06:59 MTOLEDOB kernel: [   16.944000] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
Apr  5 21:06:59 MTOLEDOB kernel: [   16.944000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
Apr  5 21:06:59 MTOLEDOB kernel: [   16.944000] cs: IO port probe 0xd000-0xefff: clean.
Apr  5 21:06:59 MTOLEDOB kernel: [   16.944000] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
Apr  5 21:06:59 MTOLEDOB kernel: [   16.944000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x37ffffff
Apr  5 21:06:59 MTOLEDOB kernel: [   17.032000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
Apr  5 21:06:59 MTOLEDOB kernel: [   17.032000] ipw2100: Copyright(c) 2003-2006 Intel Corporation
Apr  5 21:06:59 MTOLEDOB kernel: [   17.032000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Apr  5 21:06:59 MTOLEDOB kernel: [   17.032000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
Apr  5 21:06:59 MTOLEDOB kernel: [   17.580000] pccard: PCMCIA card inserted into slot 1
Apr  5 21:06:59 MTOLEDOB kernel: [   17.844000] input: PC Speaker as /class/input/input2
Apr  5 21:06:59 MTOLEDOB kernel: [   18.256000] input: DualPoint Stick as /class/input/input3
Apr  5 21:06:59 MTOLEDOB kernel: [   18.276000] input: AlpsPS/2 ALPS DualPoint TouchPad as /class/input/input4
Apr  5 21:06:59 MTOLEDOB kernel: [   18.284000] parport_pc 00:0c: reported by Plug and Play ACPI
Apr  5 21:06:59 MTOLEDOB kernel: [   18.284000] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Apr  5 21:06:59 MTOLEDOB kernel: [   18.320000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Apr  5 21:06:59 MTOLEDOB kernel: [   18.320000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
Apr  5 21:06:59 MTOLEDOB kernel: [   18.568000] cs: memory probe 0xf6000000-0xfbffffff: excluding 0xf6000000-0xf65fffff 0xf6c00000-0xf71fffff 0xf7e00000-0xf83fffff 0xf9c00000-0xfa1fffff 0xfae00000-0xfb3fffff
Apr  5 21:06:59 MTOLEDOB kernel: [   18.588000] pcmcia: registering new device pcmcia1.0
Apr  5 21:06:59 MTOLEDOB kernel: [   18.644000] cs: IO port probe 0x100-0x3af: clean.
Apr  5 21:06:59 MTOLEDOB kernel: [   18.644000] cs: IO port probe 0x3e0-0x4ff: clean.
Apr  5 21:06:59 MTOLEDOB kernel: [   18.644000] cs: IO port probe 0x820-0x8ff: clean.
Apr  5 21:06:59 MTOLEDOB kernel: [   18.644000] cs: IO port probe 0xc00-0xcf7: clean.
Apr  5 21:06:59 MTOLEDOB kernel: [   18.644000] cs: IO port probe 0xa00-0xaff: clean.
Apr  5 21:06:59 MTOLEDOB kernel: [   18.648000] cs: IO port probe 0x100-0x3af: clean.
Apr  5 21:06:59 MTOLEDOB kernel: [   18.648000] cs: IO port probe 0x3e0-0x4ff: clean.
Apr  5 21:06:59 MTOLEDOB kernel: [   18.648000] cs: IO port probe 0x820-0x8ff: clean.
Apr  5 21:06:59 MTOLEDOB kernel: [   18.648000] cs: IO port probe 0xc00-0xcf7: clean.
Apr  5 21:06:59 MTOLEDOB kernel: [   18.648000] cs: IO port probe 0xa00-0xaff: clean.
Apr  5 21:06:59 MTOLEDOB kernel: [   19.148000] intel8x0_measure_ac97_clock: measured 55450 usecs
Apr  5 21:06:59 MTOLEDOB kernel: [   19.148000] intel8x0: clocking to 48000
Apr  5 21:06:59 MTOLEDOB kernel: [   20.276000] lp0: using parport0 (interrupt-driven).
Apr  5 21:06:59 MTOLEDOB kernel: [   20.320000] Adding 1510068k swap on /dev/sda5.  Priority:-1 extents:1 across:1510068k
Apr  5 21:06:59 MTOLEDOB kernel: [   20.616000] EXT3 FS on sda2, internal journal
Apr  5 21:06:59 MTOLEDOB kernel: [   21.808000] ACPI: AC Adapter [AC] (on-line)
Apr  5 21:06:59 MTOLEDOB kernel: [   21.868000] input: Lid Switch as /class/input/input5
Apr  5 21:06:59 MTOLEDOB kernel: [   21.872000] ACPI: Lid Switch [LID]
Apr  5 21:06:59 MTOLEDOB kernel: [   21.920000] input: Power Button (CM) as /class/input/input6
Apr  5 21:06:59 MTOLEDOB kernel: [   21.924000] ACPI: Power Button (CM) [PBTN]
Apr  5 21:06:59 MTOLEDOB kernel: [   21.972000] input: Sleep Button (CM) as /class/input/input7
Apr  5 21:06:59 MTOLEDOB kernel: [   21.976000] ACPI: Sleep Button (CM) [SBTN]
Apr  5 21:06:59 MTOLEDOB kernel: [   22.000000] ACPI: ACPI Dock Station Driver 
Apr  5 21:06:59 MTOLEDOB kernel: [   22.328000] ACPI: Battery Slot [BAT0] (battery present)
Apr  5 21:06:59 MTOLEDOB kernel: [   22.328000] ACPI: Battery Slot [BAT1] (battery absent)
Apr  5 21:06:59 MTOLEDOB kernel: [   22.372000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.318719] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_3340'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.560938] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_3341'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.561879] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_4c66'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.562512] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c2'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.562992] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.563461] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.563927] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c4'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.564394] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.564884] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.565351] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c7'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.565816] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.566281] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.566746] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24cd'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.567209] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.567674] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.568138] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.568635] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_165d'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.569118] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1217_7113'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.569582] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1217_7113_0'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.570046] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pcmcia__1__1'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.570508] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_1043'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.570969] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24cc'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.571432] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.571933] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.572398] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_scsi_device_lun0'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.572879] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_0'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.573341] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_0_scsi_device_lun0'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.573803] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.574263] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c6'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.574724] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_dock_0'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.575184] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.575645] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.576105] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.576565] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.577039] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.577497] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.577954] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.578412] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.578870] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.579346] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.579806] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.580263] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.580737] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.581195] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.581651] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.582108] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.582564] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.583048] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.583506] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.583961] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0401'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.584416] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.584888] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.585347] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.585803] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.586644] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.591331] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Apr  5 21:07:00 MTOLEDOB NetworkManager: <debug> [1207451220.608460] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_11_43_53_d5_22'). 
Apr  5 21:07:01 MTOLEDOB kernel: [   23.908000] PM: Writing back config space on device 0000:02:00.0 at offset c (was ffbf0000, writing 0)
Apr  5 21:07:01 MTOLEDOB kernel: [   23.908000] PM: Writing back config space on device 0000:02:00.0 at offset b (was 165d14e4, writing 865d1028)
Apr  5 21:07:01 MTOLEDOB kernel: [   23.908000] PM: Writing back config space on device 0000:02:00.0 at offset 3 (was 0, writing 2008)
Apr  5 21:07:01 MTOLEDOB kernel: [   23.908000] PM: Writing back config space on device 0000:02:00.0 at offset 2 (was 2000000, writing 2000001)
Apr  5 21:07:01 MTOLEDOB kernel: [   23.908000] PM: Writing back config space on device 0000:02:00.0 at offset 1 (was 2b00000, writing 2b00106)
Apr  5 21:07:01 MTOLEDOB NetworkManager: <info>  eth0: Device is fully-supported using driver 'tg3'. 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <info>  Deactivating device eth0. 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.086639] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_0c_f1_1c_20_6b'). 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <info>  eth1: Device is fully-supported using driver 'ipw2100'. 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <info>  Deactivating device eth1. 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.245425] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_scsi_device_lun0_scsi_generic'). 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.246136] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24ca_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.246627] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_pcm_1'). 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.247103] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_pcm_0'). 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.247578] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_control__1'). 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.248072] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_pcm_0_0'). 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.248547] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_mixer__1'). 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.249045] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_0'). 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.249519] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_playback_0'). 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.249991] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_1'). 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.250462] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_2'). 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.250933] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_3'). 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.251403] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_playback_4'). 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.251872] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.252341] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.252826] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.253296] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.253764] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.254239] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.254711] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_3'). 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.255183] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'). 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.255651] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.256118] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.256602] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.257109] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.257578] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST980815A_5LY1VWH9'). 
Apr  5 21:07:01 MTOLEDOB gdm[4595]: WARNING: Didn't understand `' (expected true or false) 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.490730] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_606C05936C0564DE'). 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.497213] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_241da2db_0e86_4d13_ba31_7e747e81c264'). 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.555951] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part3_size_1024'). 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.561861] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_aaabdd49_42ff_4b7f_ac15_b1a4f0ed1a87'). 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.658686] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT1'). 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.708652] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.709215] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.709684] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Apr  5 21:07:01 MTOLEDOB NetworkManager: <debug> [1207451221.715447] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_RW/DVD_GCC_4241N'). 
Apr  5 21:07:02 MTOLEDOB kernel: [   25.392000] [drm] Initialized drm 1.1.0 20060810
Apr  5 21:07:02 MTOLEDOB kernel: [   25.400000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Apr  5 21:07:02 MTOLEDOB kernel: [   25.404000] [drm] Initialized radeon 1.27.0 20060524 on minor 0

```

---

### Post by Reshuken on 2008-04-06
Bump

---

### Post by Rocket2DMn on 2008-04-07
Hey, have you tried reconfiguring X?  It does indeed sound like a video driver problem, so here is a guide for you - [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)

---

### Post by Reshuken on 2008-04-16
Thanks for the last answer, but I can't seem to get into anything after I press CTRL+ALT+F1... the system just stays there and nothing comes up. What I noticed though, is that if I press the combination during the splash screen, the normal boot up text comes up and after a while I can see how the monitor turns off. This happens a command later (which is something like "Starting Common Unix Printing...") after "Starting Gnome Desktop Manager".

Sorry I wasn't able to reply sooner, but I was away from my computer for a while so... anyway, any other advice that you can give me is appreciated.

---

### Post by Rocket2DMn on 2008-04-16
You can also reconfigure X from the Recovery Mode terminal, the second option at the GRUB menu.  It's the same command, but without sudo.
```
dpkg-reconfigure xserver-xorg
reboot
```
See if that helps.  Otherwise please tell us what video card make/model you have and what drivers you were using before (restricted? if so, how did you install them?).

---

### Post by Reshuken on 2008-04-16
Thank you very much!!! That answer was helpful and completely solved my problem. Took a little over a week, but now I can get into Ubuntu again! Now I'm prepared for Hardy:)

---

### Post by oilchangeguy on 2008-04-16
> **Reshuken said:**
> Thank you very much!!! That answer was helpful and completely solved my problem. Took a little over a week, but now I can get into Ubuntu again! Now I'm prepared for Hardy:)

it's good you got your problem solved. but why would you want to layer 3 operating systems on top of each other? i'm sure most will agree, it's better to back up your data, and do a fresh install, rather than layer.

---

### Post by Reshuken on 2008-04-17
Yeah, I know what you mean. In the time I wasn't able to figure a solution to my problem, I thought seriously about reinstalling all over again. The thing is, the computer I run Ubuntu on is not only mine, but my sister's too; that and I dual boot WinXP (well, actually it's her). So it's a lot of information to back up and right now I don't have the means to do it.

On the other hand, this has been like my first real experience with Linux, so whenever something happens I try my best to learn, instead of the easy way out. Oh, and I never upgraded to a new version so I wanted to see how it was done and to see that everything went fine; quite a surprise to see that I couldn't boot into my system after that. Anyway, when I get another computer, I will do a better installation i.e.  I will put my home in another partition so reinstalling won't be a problem at all. In any case, thanks for your advice, as I too think it's better do to a fresh install.

---

