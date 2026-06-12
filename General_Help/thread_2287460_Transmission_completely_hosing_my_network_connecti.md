---
title: "Transmission completely hosing my network connection"
date: 2015-07-19
forum: General Help
---

### Post by Evil Wayz on 2015-07-19
I posted this on the transmission forum but noone bit. 

I am running Ubuntu 14.04.2 gnome and using Transmission version 2.82 (14160). When I woke up this morning and checked my downloads I noticed that nothing was downloading but I was seeding just fine. Then I discovered I couldn't use the internet, all my pages either resulted in timeouts, dns lookup errors, or dns probe no internet errors. A couple of times after a really long pause with " resolving host" at the bottom of the page, I would randomly get a page, but it wasn't formatted or loaded correctly. I also couldn't connect any of my portable devices through wifi. When I turned off transmission and restarted my browser, everything was fine. I haven't touched the settings, and I didn't pay attention to see if transmission had updated when I let Ubuntu update. 

When I restart transmission, it seeds immediately, but when i check on the partially downloaded files, all of them say "queued for more peers" but they never do, even if i use the "ask tracker for more peers" option.

I've been using transmission for as long as I've been using Linux, and i've never had a problem with using transmission and going about my business on the internet at the same time. I don't have any idea where to start because i've been using these settings for as long as I can remember as well.

Oh, and it's just this computer, I just downloaded a torrent on my laptop just fine.

---

### Post by Dalequedale on 2016-07-09
I had the exact same problem, and I think I managed to solve it.

MY ENVIRONMENT:
```
$ uname -srvio
Linux 4.2.0-27-generic #32~14.04.1-Ubuntu SMP Fri Jan 22 15:32:26 UTC 2016 x86_64 GNU/Linux

$ cat /etc/issue
Ubuntu 14.04.4 LTS \n \l

$ lspci -v | grep -A 5 -i network | egrep -e 'Network|driver'
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
    Kernel driver in use: b43-pci-bridge

$ dpkg -l "*transmission*" | grep ^ii
ii  transmission-common   2.82-1.1ubuntu3 all             lightweight BitTorrent client (common files)
ii  transmission-gtk      2.82-1.1ubuntu3 amd64           lightweight BitTorrent client (GTK+ interface)
```

MY PROBLEM: Very soon after starting Transmission and downloading just 1 torrent (which, by the way, only had 1 seed and 0 leechers but me), my laptop would lose Internet connection, I would get time-outs whenever I tried to access any Internet resource, and I had the restart my ADSL router to be able to access the Internet again . However, I could access without any problem other machines in my local network, and also from those other machines in my local network the Internet access would work flawlessly. I could reproduce the problem consistently: just start Transmission, and bye bye Internet connection in my Ubuntu laptop. I am running Transmission with default settings (maximum peers per torrent: 50; maximum peers overall: 200; lowering those settings did not solve the problem). Also, I have set the speed limits in Transmission well below my Internet connection speed, for both upload and download.

MY SOLUTION: Just disable the option "Enable uTP for peer communication", in the Network tab of Transmission Preferences. I get rock solid Internet performance with Transmission after that.

MY GUESS: I think this problem happens because my ADSL router's NAT support cannot manage the UDP connections Transmission tries to use when that option is enabled, therefore breaking the NAT which allows my Ubuntu laptop to go to the Internet. My router is a "Zyxel P-662HW-D1" running "ZyNOS Firmware Version: V3.40(AGZ.6)| 08/30/2007".

More information about uTP: [https://trac.transmissionbt.com/ticket/2338](https://trac.transmissionbt.com/ticket/2338)

---

