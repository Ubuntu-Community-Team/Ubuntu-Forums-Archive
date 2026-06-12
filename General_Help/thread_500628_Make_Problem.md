---
title: "Make Problem"
date: 2007-07-14
forum: General Help
---

### Post by Jpitcairn on 2007-07-14
Hey, im a linux newbie and just getting used to Ubuntu. Im trying to install the serial monkey rt73 drivers for my wireless card following the instructions on this website. When i try to run "sudo make" i get this problem

```

jordan@jordan-laptop:/usr/src/rt73-cvs-2007071403/Module$ sudo make
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /usr/src/rt73-cvs-2007071403/Module/rtmp_main.o
In file included from /usr/src/rt73-cvs-2007071403/Module/rt_config.h:187,
                 from /usr/src/rt73-cvs-2007071403/Module/rtmp_main.c:36:
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:819: error: expected identifier or ‘(’ before ‘{’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:819: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:821: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:823: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:823: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:826: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:826: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:826: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:830: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:832: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:832: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:835: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:837: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:837: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:840: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:842: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:842: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:845: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:847: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:847: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:850: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:850: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:853: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:853: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:853: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:857: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:857: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:860: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:860: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:863: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:863: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:866: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:868: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:868: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_def.h:868: error: expected identifier or ‘(’ before ‘}’ token
/usr/src/rt73-cvs-2007071403/Module/rtmp_main.c:71: error: expected expression before ‘;’ token
make[2]: *** [/usr/src/rt73-cvs-2007071403/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/usr/src/rt73-cvs-2007071403/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
rt73.ko failed to build!
make: *** [module] Error 1

```

can anyone help me out?

---

### Post by munder on 2007-07-14
Hi

I'm also a complete newbie, so please take what follows with a shedload of salt, as I confess I haven't a clue what I'm doing.

Last night I had the same problem as you. I took a chance and edited the last section of rtmp_def.h so that it now looks like this:

//-------------------
// VID/PID
//-------------------

#define RT73_USB_DEVICES { \
 {USB_DEVICE(0x050d,0x705a)}, \
 {USB_DEVICE(0,0)}} /* end marker */

#endif	// __RTMP_DEF_H__

The "0x050d,0x705a" is some sort of ID of my Belkin USB wireless dongle thingy. It may have been revealed to me by the command lsusb, but I'm afraid I can't recall.

Anyway, once I'd made that change, everything compiled OK. Once that was done, I could scan and find the network access point.  

Actually getting beyond that stage, however, has taken a day of no progress. Still, I did take a break to watch the Tour de France and it's rubbish weather here anyway.

Good luck.

Mick

---

### Post by munder on 2007-07-15
A follow-up:

I came across a post somewhere which said that my Belkin USB dongle would work straight out of the box with the earlier version of Ubuntu (Edgy Eft), so I scrapped Feisty Frog or whatever it's called and installed that earlier version. But it didn't work straight out of the box.

So I installed the Ralink drivers and couldn't get them to work either, following the instructions in the readme. However, I explored the file named iwpriv_usage.txt and came across the following:

        1. iwpriv wlan0 set NetworkType=Infra
	2. iwpriv wlan0 set AuthMode=WPAPSK
	3. iwpriv wlan0 set EncrypType=TKIP
	4. iwpriv wlan0 set SSID="AP's SSID"
	5. iwpriv wlan0 set WPAPSK="12345678"
	6. iwpriv wlan0 set SSID="AP's SSID"

That sequence of instructions is slightly different from that given in the readme. It's enough to get it working, though. So I'm now connected. Maybe it would work with Feisty too?

Best of luck

Mick

---

