---
title: "shutdown hangs-up"
date: 2008-05-16
forum: General Help
---

### Post by weltenkind on 2008-05-16
hello since I upgraded to kubuntu 8.04 my laptop does not shutdown properly. It hangs-up befor the shut-down screen is displayed. Only be using th three-finger-salute I can switch of the system. Has anybody the same or a similar problem, that he solved.
Thanks for your help

---

### Post by Xiong Chiamiov on 2008-05-17
[Yep, we have.]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/138691")  There are a few options for fixing at the bottom, if it is indeed the Network Manager hang problem that you're having.

---

### Post by weltenkind on 2008-05-18
I think my problem is somewhat diffrent. To illustrate I have added a copy of the relevate lines in the syslog. Am I right? Where else coul someone look to findout more about such problems?
another thing is that the problem only occures with the kernel-version 2.6.24-16, but not with the kernel 2.6.22-14 of Kubuntu 8.04. 

Thankx for your help

syslog:
May 18 12:09:58 XuserX console-kit-daemon[5659]: WARNING: Unable to activate console: No such device or address 
May 18 12:09:58 XuserX kernel: [  729.959919] [fglrx] interrupt source 10000000 successfully disabled!
May 18 12:09:58 XuserX kernel: [  729.959932] [fglrx] enable ID = 0x00000000
May 18 12:09:58 XuserX kernel: [  729.959942] [fglrx] Receive disable interrupt message with irqEnableMask: 10000000; dwIRQEnableId: 00000004
May 18 12:11:20 XuserX init: tty4 main process (4743) killed by TERM signal
May 18 12:11:20 XuserX init: tty5 main process (4744) killed by TERM signal
May 18 12:11:20 XuserX init: tty2 main process (4746) killed by TERM signal
May 18 12:11:20 XuserX init: tty3 main process (4749) killed by TERM signal
May 18 12:11:20 XuserX init: tty6 main process (4750) killed by TERM signal
May 18 12:11:20 XuserX init: tty1 main process (6076) killed by TERM signal
May 18 12:11:27 XuserX avahi-daemon[5306]: Got SIGTERM, quitting.
May 18 12:11:27 XuserX avahi-daemon[5306]: Leaving mDNS multicast group on interface ath0.IPv4 with address 169.254.7.1.
May 18 12:11:27 XuserX avahi-daemon[5306]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.123.133.
May 18 12:11:28 XuserX avahi-autoipd(ath0)[6646]: SIOCSIFFLAGS failed: Permission denied
May 18 12:11:28 XuserX dhclient: receive_packet failed on ath0: Network is down
May 18 12:11:28 XuserX avahi-autoipd(ath0)[6646]: Callout STOP, address 169.254.7.1 on interface ath0
May 18 12:11:28 XuserX avahi-autoipd(ath0)[6647]: client: RTNETLINK answers: No such process
May 18 12:11:30 XuserX kernel: [  821.754924] ip6_tables: (C) 2000-2006 Netfilter Core Team
May 18 12:11:31 XuserX exiting on signal 15
May 18 12:13:09 XuserX syslogd 1.5.0#1ubuntu1: restart.

---

### Post by mbeach on 2008-05-18
I had a similar problem on a remote machine which would not reboot.  It would hang on the very last step and not kick over.

using the reboot=b kernal option worked for me.

[http://ubuntuforums.org/showthread.php?p=3033005](http://ubuntuforums.org/showthread.php?p=3033005)
[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Hang_on_reboot](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Hang_on_reboot)
[http://www.google.com/search?q=dell+ubuntu+hang+on+restart+reboot%3Db&sourceid=navclient-ff&ie=UTF-8&rls=GGGL,GGGL:2006-41,GGGL:en](http://www.google.com/search?q=dell+ubuntu+hang+on+restart+reboot%3Db&sourceid=navclient-ff&ie=UTF-8&rls=GGGL,GGGL:2006-41,GGGL:en)

Not sure if this is your problem or not, but possibly an option to try.

mb.

---

