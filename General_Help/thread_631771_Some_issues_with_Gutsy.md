---
title: "Some issues with Gutsy"
date: 2007-12-04
forum: General Help
---

### Post by Boule on 2007-12-04
I just installed gutsy, I had edgy before (never really used feisty), and I have some issues/questions I hope you can help me with...

1. I can't share files with other windows computers on my network. I can't see them, they can't see me.

2. The connection to the router drops very frequently. I can't ping it anymore, but ifconfig shows that the correct configuration is still there (I don't use DHCP, I manually set a fixed IP)

3. I'm used to Beryl, I'm just getting acquainted with compiz fusion. Beryl had a feature I really liked, the transparent cube. I'm not able to find it now, does it still exist ? How about emerald themes ? Compiz doesn't really come with new themes.

4. Is there a way to have only removable devices (like USB hard drives...) show on the desktop ? I didn't find how to this on edgy as well.

5. In compiz general options, I can't enable maximize horizontally and vertically. When I assign a shortcut, it doesn't save it., though it works for other shortcuts.

Thanks for your help !

---

### Post by davidgarcin on 2007-12-04
1.  For file sharing, are you using Samba?  See this how-to: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_public_folders_with_read_only_permission_.28Authentication.3DNo.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_public_folders_with_read_only_permission_.28Authentication.3DNo.29)
It's for Feisty, but it worked fine for me in Gutsy in the same situation.  There are also instructions for read/write access, or authenticated, etc.

3.  Install compizconfig-settings-manager with Synaptic.  It will allow you to customize more Compiz settings than you'll ever use (I'm not for sure, but I think the setting you want will be in there).  It will install a new GUI config for you under Preferences,  Advanced Desktop Settings I think it's called.

Hope that helps.
-Dave

---

### Post by Boule on 2007-12-04
1. I used to be able to see the computers on the windows network right after installing... That was the case for both edgy and feisty. With gutsy, I can't even see a computer even if I manually connect to it ! I googled the problem a bit, found a thread with the same issue, the poster said it was a firewall problem without giving much details.

3. I did install that, but I still can't find the transparency thing. And it's in that GUI that I can't set maximize horizontally and vertically

---

### Post by nqsonk9 on 2007-12-04
@Boule
1. Are you sure that you're going the same way as you did with feisty and gutsy. Follow stricky to the samba guide, remember to configure the samba.conf and everything'll be fine.

2. Can you show us your ipconfig /all ?

3,5. I'm pretty sure that compizconfig-settings-manager can do almost everything Beryl could. To set the transparent, go to **cube** or **rote** option. And for maximize horizontally and vertically, you cant use Ubuntu shortcut key instead, it works for me.

4. Yes it it, go to /etc/fstab, mount your partition to /mnt instead of /media, leave the removeable storge static so that your USB will be mount to /media --> appear on Desktop
If you simply want to prevent every partitions to apprear on your desk, just go to gconf-editor, search for app/nautilus/desktop, than you'll find the keys 

Hope i did help :)

---

### Post by Boule on 2007-12-04
1. Yes I was able to access my laptop running windows just after installing. And it worked in Places->Connect to server

2. Here's the ifconfig... It looks fine, networking is working, but it randomly drops, and it does so quite often. If I /etc/init.d/networking restart, it goes back up.
```
eth0      Link encap:Ethernet  HWaddr 00:0C:6E:7D:8F:FF  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:26:54:10:DB:57  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:54ff:fe10:db57/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3713 errors:0 dropped:0 overruns:1 frame:0
          TX packets:3306 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3133363 (2.9 MB)  TX bytes:534451 (521.9 KB)
          Interrupt:18 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

3. I found the transparency, thanks ! I can't believe I missed it !
5. You mean Super+h and Super+v ? Super+v seems to maximize the window both ways, super+h doesn't do much

4. I only see "volumes_visible" in the config editor, and it works for both my partitions and usb drives. I guess it just shows everything in /media


Another feature that I can't find, when the mouse went to upper right corner, it will show all the windows from all the viewports.

Thanks for the help !

---

### Post by davidgarcin on 2007-12-04
the networking issues are pretty weird, and almost point to the router being the source of the problem.  Have you tried restarting the router?  It works wonders for me sometimes.

Sorry, that's all I've got :-)

---

### Post by Boule on 2007-12-04
Well the other computers are still online when the linux one goes down. Also there isn't any interruption on the windows partition of the same computer...

---

### Post by Boule on 2007-12-05
The thread was already in page 10 !! Any new ideas before it gets completely forgotten ?

---

### Post by davidgarcin on 2007-12-05
The reason I suggest rebooting the router is that it really has helped me in the exact same situation:  all other Windows boxes connecting fine, including the one on the other partition, but my Ubuntu just refused to connect, or connected and then got booted.  Reset the router, it has no problem.  I know it doesn't seem like a likely fix, but it's easy to try, so don't just throw the suggestion out the window.  If you did try it and it didn't work, please say so.

Sorry I can't be of more help.  I would suggest posting each of your unresolved issues individually in the proper thread areas (e.g. Networking & Wireless) with descriptive subjects such as "Gutsy wireless network connection dropping".   "Some issues with Gutsy" and other such vague subjects will not attract many views because they are neither specific nor descriptive.

---

