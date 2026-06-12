---
title: "some websites unreachable"
date: 2013-06-25
forum: General Help
---

### Post by HiImTye on 2013-06-25
I've had this issue for a few Ubuntu releases now. some websites, such as [http://www.ffmpeg.org](http://www.ffmpeg.org) are unreachable.

note: it's not a DNS issue, as I'm getting the correct IP; and it's not an MTU issue, as I've adjusted it up and down with no change.

---

### Post by HiImTye on 2013-06-26
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
the bumpty dance is your chance to do the bump.

---

### Post by fantab on 2013-06-26
I can confirm that the address is working from 'Saucy Salamander'.
Does this happen only with Ubuntu? It could be an issue with your ISP itself.

---

### Post by HiImTye on 2013-06-26
the addresses are reachable for the other computers/devices, so long as they're not using my squid3 + privoxy proxy

also reachable, strangely enough, inside a WinXP VM on the same box (but it's running headless so I don't know if I can access the VM in an rdp session). inb4 it's your proxy: they are also unreachable over unproxied connections (on the Ubuntu box).
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by MidnightGrey on 2013-06-26
what happens when you **ping**? does it just timeout?
if ping doesnt time out can you pull down these webpages with **wget**?

---

### Post by HiImTye on 2013-06-26
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
yeah, that's whst I meant by unreachable - I can't access them whatsoever, using browsers, squid3/privoxy, ping, nothing. when I dig I'm getting the correct IP, so it's def. not a DNS issue

---

### Post by Zill on 2013-06-26
> **HiImTye said:**
> I've had this issue for a few Ubuntu releases now. some websites, such as [http://www.ffmpeg.org](http://www.ffmpeg.org) are unreachable...
[http://www.ffmpeg.org](http://www.ffmpeg.org) is working fine here.

Does MTR give any clues about where your network connection is failing?
```
mtr --report ffmpeg.org
```

---

### Post by HiImTye on 2013-06-27
mtr didn't have any info at all, but I noticed that wget gives a 'no route' error```
 01:41:30 up 1 day,  1:33,  load average: 1.07, 1.07, 1.00
[ tye@Tab: ~ ]$ cd temp
[ tye@Tab: ~/temp ]$ ffmpeg=$(jping ffmpeg.org | grep -o '[0-9.]\+$'); wget http://$ffmpeg
Connecting to 192.190.173.45 (192.190.173.45:80)
index.html           100% |********************************************************************************************************************************************************************|    63   0:00:00 ETA
[ tye@Tab: ~/temp ]$ sshl
ssh: TCP forward failed: Error listening: Address already in use
ssh: Failed local port forward 3390:localhost:3389
Welcome to Ubuntu 12.10 (GNU/Linux 3.5.0-34-generic x86_64)
New release '13.04' available.
Run 'do-release-upgrade' to upgrade to it.
21:56:29 up 11:27,  1 user,  load average: 0.15, 0.12, 0.11
tye      pts/0    192.168.1.3      21:56    1.00s  0.08s  0.00s tmux new -n tye
1: 1 windows (created Wed Jun 26 21:56:28 2013) [213x30] (attached)
0: tye [213x30] [layout a85e,213x30,0,0] (active)
0: [213x30] [history 0/2000, 0 bytes] %1 (active)
Adapter: ACPI interface
Vcore Voltage:       +1.12 V  (min =  +0.85 V, max =  +1.60 V)
 +3.3 Voltage:       +3.20 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:         +4.89 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:       +12.20 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:      2205 RPM  (min =    0 RPM)
CHASSIS1 FAN Speed:    0 RPM  (min =  800 RPM)
CHASSIS2 FAN Speed:    0 RPM  (min =  800 RPM)
POWER FAN Speed:     992 RPM  (min =  800 RPM)
CPU Temperature:     +54.5C  (high = +60.0C, crit = +95.0C)
MB Temperature:      +34.0C  (high = +45.0C, crit = +95.0C)
Adapter: ISA adapter
Core 0:       +78.0C  (high = +84.0C, crit = +100.0C)  ALARM (CRIT)
Core 1:       +75.0C  (high = +84.0C, crit = +100.0C)
Adapter: nVidia GeForce 210
GPU:     90C
[ tye@T: ~ ]$ cd temp
[ tye@T: ~/temp ]$ wget -d ffmpeg.org
DEBUG output created by Wget 1.13.4 on linux-gnu.

URI encoding = `UTF-8'
--2013-06-26 21:57:38--  http://ffmpeg.org/
Resolving ffmpeg.org (ffmpeg.org)... 192.190.173.45
Caching ffmpeg.org => 192.190.173.45
Connecting to ffmpeg.org (ffmpeg.org)|192.190.173.45|:80... Closed fd 3
failed: No route to host.
Releasing 0x0000000000866ef0 (new refcount 1).
[ tye@T: ~/temp ]$
```seems to support mtr's output of a giant empty screen
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by HiImTye on 2013-06-27
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
I noticed that the sites I was having trouble with all had IPs starting with 192 so I checked my subnet mask and it was 255.0.0.0 even though I had set it to 255.255.255.0 when I added the connection. to fix it, I had to edit ```
/etc/NetworkManager/system-connections/connectionName
``` and change the line```
addresses1=192.168.1.2;8;192.168.1.254;
```to```
addresses1=192.168.1.2;24;192.168.1.254;
```

---

