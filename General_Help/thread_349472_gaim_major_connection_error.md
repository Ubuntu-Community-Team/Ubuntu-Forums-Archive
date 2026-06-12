---
title: "gaim major connection error"
date: 2007-01-30
forum: General Help
---

### Post by ivanmt42 on 2007-01-30
Can someone please give me a hand. I can't seem to get gaim to connect to AIM. Here is what I get when I run the following command:

>gaim -d | grep oscar

plugins: probing /usr/lib/gaim/liboscar.so
oscar: oscar_login: gc = 0x8455ab8
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
oscar: aim_conn_addhandler: adding for ffff/0003
oscar: aim_conn_addhandler: adding for 0017/0003
oscar: aim_conn_addhandler: adding for 0017/0007
oscar: aim_conn_addhandler: adding for 0017/000a
dns: Got response for 'login.oscar.aol.com'
proxy: Connecting to login.oscar.aol.com:5190 with no proxy
oscar: Screen name sent, waiting for response
oscar: inside auth_resp (Screen name: Mike I Kanoodle)
oscar: Reg status: 3
oscar: E-mail: [email]mikei@corp.kanoodle.com[/email]
oscar: BOSIP: 192.168.226.26:5191
oscar: Closing auth connection...
oscar: aim_conn_addhandler: adding for ffff/0003
oscar: aim_conn_addhandler: adding for ffff/0006
oscar: aim_conn_addhandler: adding for 0009/0003
oscar: aim_conn_addhandler: adding for 0001/0005
oscar: aim_conn_addhandler: adding for 0002/0003
oscar: aim_conn_addhandler: adding for 0003/0003
oscar: aim_conn_addhandler: adding for 0003/000b
oscar: aim_conn_addhandler: adding for 0003/000c
oscar: aim_conn_addhandler: adding for 0004/0007
oscar: aim_conn_addhandler: adding for 0002/0001
oscar: aim_conn_addhandler: adding for 0004/000a
oscar: aim_conn_addhandler: adding for 0004/000b
oscar: aim_conn_addhandler: adding for 0001/000a
oscar: aim_conn_addhandler: adding for 0001/0010
oscar: aim_conn_addhandler: adding for 000a/0001
oscar: aim_conn_addhandler: adding for 000a/0003
oscar: aim_conn_addhandler: adding for 0004/0001
oscar: aim_conn_addhandler: adding for 0004/0014
oscar: aim_conn_addhandler: adding for 0002/0006
oscar: aim_conn_addhandler: adding for 0002/fffe
oscar: aim_conn_addhandler: adding for 0002/fffd
oscar: aim_conn_addhandler: adding for 0004/000c
oscar: aim_conn_addhandler: adding for 0001/0013
oscar: aim_conn_addhandler: adding for 0004/0005
oscar: aim_conn_addhandler: adding for 0001/0001
oscar: aim_conn_addhandler: adding for 0003/0001
oscar: aim_conn_addhandler: adding for 0009/0001
oscar: aim_conn_addhandler: adding for 0001/001f
oscar: aim_conn_addhandler: adding for 0001/000f
oscar: aim_conn_addhandler: adding for 0001/0021
oscar: aim_conn_addhandler: adding for 0015/00f0
oscar: aim_conn_addhandler: adding for 0015/00f1
oscar: aim_conn_addhandler: adding for 0008/0002
oscar: aim_conn_addhandler: adding for 0015/00f3
oscar: aim_conn_addhandler: adding for 0015/00f2
oscar: aim_conn_addhandler: adding for 0013/0001
oscar: aim_conn_addhandler: adding for 0013/0003
oscar: aim_conn_addhandler: adding for 0013/0006
oscar: aim_conn_addhandler: adding for 0013/000f
oscar: aim_conn_addhandler: adding for 0013/000e
oscar: aim_conn_addhandler: adding for 0013/0008
oscar: aim_conn_addhandler: adding for 0013/0015
oscar: aim_conn_addhandler: adding for 0013/0019
oscar: aim_conn_addhandler: adding for 0013/001b
oscar: aim_conn_addhandler: adding for 0013/001c
oscar: Major connection error (invalid data was received on the oscar TCP stream).
oscar: Signed off.

---

