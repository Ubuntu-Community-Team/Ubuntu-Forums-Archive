---
title: "Gaim not connecting"
date: 2007-06-03
forum: General Help
---

### Post by ph33r213 on 2007-06-03
I've been trying to connect to aim through gaim, but it just wouldn't connect, same with msn. It was working hours ago and then when I restarted my computer it just stopped. 

When I run gaim with  $ gaim -d | grep oscar  I get:

plugins: probing /usr/lib/gaim/liboscar.so
plugins: /usr/lib/gaim/liboscar.so is not usable because the 'gaim_init_plugin' symbol could not be found.  Does the plugin call the GAIM_INIT_PLUGIN() macro?
oscar: registered module misc (family 0xffff, version = 0x0000, tool 0x0000, tool version 0x0000)
oscar: registered module oservice (family 0x0001, version = 0x0003, tool 0x0110, tool version 0x0629)
oscar: registered module locate (family 0x0002, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module buddy (family 0x0003, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module messaging (family 0x0004, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module advert (family 0x0005, version = 0x0001, tool 0x0001, tool version 0x0001)
oscar: registered module invite (family 0x0006, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module admin (family 0x0007, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module popup (family 0x0008, version = 0x0001, tool 0x0104, tool version 0x0001)
oscar: registered module bos (family 0x0009, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module userlookup (family 0x000a, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module stats (family 0x000b, version = 0x0001, tool 0x0104, tool version 0x0001)
oscar: registered module translate (family 0x000c, version = 0x0001, tool 0x0104, tool version 0x0001)
oscar: registered module chatnav (family 0x000d, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module chat (family 0x000e, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module odir (family 0x000f, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module bart (family 0x0010, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module feedbag (family 0x0013, version = 0x0004, tool 0x0110, tool version 0x0629)
oscar: registered module icq (family 0x0015, version = 0x0001, tool 0x0110, tool version 0x047c)
oscar: registered module auth (family 0x0017, version = 0x0000, tool 0x0000, tool version 0x0000)
oscar: registered module alert (family 0x0018, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: Adding handler for ffff/0003
oscar: Adding handler for ffff/0006
oscar: Adding handler for 0007/0003
oscar: Adding handler for 0007/0005
oscar: Adding handler for 0007/0007
oscar: Adding handler for 0018/0001
oscar: Adding handler for 0018/0007
oscar: Adding handler for 0017/0003
oscar: Adding handler for 0017/0007
oscar: Adding handler for 0017/000a
oscar: Adding handler for 0010/0001
oscar: Adding handler for 0010/0005
oscar: Adding handler for 0009/0001
oscar: Adding handler for 0009/0003
oscar: Adding handler for 0003/0001
oscar: Adding handler for 0003/0003
oscar: Adding handler for 0003/000b
oscar: Adding handler for 0003/000c
oscar: Adding handler for 000e/0001
oscar: Adding handler for 000e/0003
oscar: Adding handler for 000e/0004
oscar: Adding handler for 000e/0002
oscar: Adding handler for 000e/0006
oscar: Adding handler for 000d/0001
oscar: Adding handler for 000d/0009
oscar: Adding handler for 0013/0001
oscar: Adding handler for 0013/0003
oscar: Adding handler for 0013/0006
oscar: Adding handler for 0013/000e
oscar: Adding handler for 0013/0008
oscar: Adding handler for 0013/0015
oscar: Adding handler for 0013/0019
oscar: Adding handler for 0013/001b
oscar: Adding handler for 0013/001c
oscar: Adding handler for 0004/0005
oscar: Adding handler for 0004/0007
oscar: Adding handler for 0004/000a
oscar: Adding handler for 0004/000b
oscar: Adding handler for 0004/0001
oscar: Adding handler for 0004/0014
oscar: Adding handler for 0004/000c
oscar: Adding handler for 0015/00f0
oscar: Adding handler for 0015/00f1
oscar: Adding handler for 0015/00f3
oscar: Adding handler for 0015/00f2
oscar: Adding handler for 0002/0003
oscar: Adding handler for 0002/0006
oscar: Adding handler for 0002/0001
oscar: Adding handler for 0002/fffd
oscar: Adding handler for 0001/0001
oscar: Adding handler for 0001/000f
oscar: Adding handler for 0001/001f
oscar: Adding handler for 0001/0021
oscar: Adding handler for 0001/000a
oscar: Adding handler for 0001/0005
oscar: Adding handler for 0001/0013
oscar: Adding handler for 0001/0010
oscar: Adding handler for 0008/0002
oscar: Adding handler for 000a/0001
oscar: Adding handler for 000a/0003
oscar: oscar_login: gc = 0x84b80e8
dns: DNS query for 'login.oscar.aol.com' queued
dns: Got response for 'login.oscar.aol.com'
dnsquery: IP resolved for login.oscar.aol.com
proxy: Connecting to login.oscar.aol.com:5190 with no proxy
oscar: unable to connect FLAP server of type 0x0017
oscar: Destroying oscar connection of type 0x0017
oscar: Signed off.

I think it has something to do with "plugins: /usr/lib/gaim/liboscar.so is not usable because the 'gaim_init_plugin' symbol could not be found.  Does the plugin call the GAIM_INIT_PLUGIN() macro?" but kopete doesn't work either. Can anybody help? : D

---

### Post by ph33r213 on 2007-06-03
Resetting my router seemed to have fixed it. Oops. :P

I saw other people had the same problem when I first searched for my problem. So I guess of what fixed other people's gaims doesn't work for you. Try resetting your router. :P

---

