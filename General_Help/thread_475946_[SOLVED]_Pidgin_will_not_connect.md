---
title: "[SOLVED] Pidgin will not connect"
date: 2007-06-16
forum: General Help
---

### Post by letubenaiah on 2007-06-16
I'm new to linux and am running Ubuntu 7.04 and I and I have installed pidgin 2.0.2 but it will not connect to any of the protocols.  I also tried using gaim but I have the same problem on that.  I am running pidgin on a windows machine and having no problem there. I also have no problems connecting to the internet with firefox (I am posting this from the same machine).  

Here is a copy of the Debug screen when I try to connect to AIM. 

17:25:49) util: Writing file prefs.xml to directory /home/benaiah/.purple
(17:25:49) autorecon: do_signon called
(17:25:49) autorecon: calling purple_account_connect
(17:25:49) account: Connecting to account [email](my email)[/email]
(17:25:49) connection: Connecting. gc = 0x8581180
(17:25:49) msn: new httpconn (0x856d488)
(17:25:49) g_log: file dnsquery.c: line 618 (purple_dnsquery_a): should not be reached
(17:25:49) autorecon: done calling purple_account_connect
(17:25:49) account: Disconnecting account 0x813b630
(17:25:49) connection: Disconnecting connection 0x8581180
(17:25:49) msn: destroy httpconn (0x856d488)
(17:25:49) connection: Destroying connection 0x8581180
(17:25:53) account: Connecting to account letubenaiah
(17:25:53) connection: Connecting. gc = 0x859f4a8
(17:25:53) oscar: registered module misc (family 0xffff, version = 0x0000, tool 0x0000, tool version 0x0000)
(17:25:53) oscar: registered module oservice (family 0x0001, version = 0x0003, tool 0x0110, tool version 0x0629)
(17:25:53) oscar: registered module locate (family 0x0002, version = 0x0001, tool 0x0110, tool version 0x0629)
(17:25:53) oscar: registered module buddy (family 0x0003, version = 0x0001, tool 0x0110, tool version 0x0629)
(17:25:53) oscar: registered module messaging (family 0x0004, version = 0x0001, tool 0x0110, tool version 0x0629)
(17:25:53) oscar: registered module admin (family 0x0007, version = 0x0001, tool 0x0010, tool version 0x0629)
(17:25:53) oscar: registered module popup (family 0x0008, version = 0x0001, tool 0x0104, tool version 0x0001)
(17:25:53) oscar: registered module bos (family 0x0009, version = 0x0001, tool 0x0110, tool version 0x0629)
(17:25:53) oscar: registered module userlookup (family 0x000a, version = 0x0001, tool 0x0110, tool version 0x0629)
(17:25:53) oscar: registered module stats (family 0x000b, version = 0x0001, tool 0x0104, tool version 0x0001)
(17:25:53) oscar: registered module chatnav (family 0x000d, version = 0x0001, tool 0x0010, tool version 0x0629)
(17:25:53) oscar: registered module chat (family 0x000e, version = 0x0001, tool 0x0010, tool version 0x0629)
(17:25:53) oscar: registered module odir (family 0x000f, version = 0x0001, tool 0x0010, tool version 0x0629)
(17:25:53) oscar: registered module bart (family 0x0010, version = 0x0001, tool 0x0010, tool version 0x0629)
(17:25:53) oscar: registered module feedbag (family 0x0013, version = 0x0004, tool 0x0110, tool version 0x0629)
(17:25:53) oscar: registered module icq (family 0x0015, version = 0x0001, tool 0x0110, tool version 0x047c)
(17:25:53) oscar: registered module auth (family 0x0017, version = 0x0000, tool 0x0000, tool version 0x0000)
(17:25:53) oscar: registered module alert (family 0x0018, version = 0x0001, tool 0x0010, tool version 0x0629)
(17:25:53) oscar: Adding handler for ffff/0003
(17:25:53) oscar: Adding handler for ffff/0006
(17:25:53) oscar: Adding handler for 0007/0003
(17:25:53) oscar: Adding handler for 0007/0005
(17:25:53) oscar: Adding handler for 0007/0007
(17:25:53) oscar: Adding handler for 0018/0001
(17:25:53) oscar: Adding handler for 0018/0007
(17:25:53) oscar: Adding handler for 0017/0003
(17:25:53) oscar: Adding handler for 0017/0007
(17:25:53) oscar: Adding handler for 0017/000a
(17:25:53) oscar: Adding handler for 0010/0001
(17:25:53) oscar: Adding handler for 0010/0005
(17:25:53) oscar: Adding handler for 0009/0001
(17:25:53) oscar: Adding handler for 0009/0003
(17:25:53) oscar: Adding handler for 0003/0001
(17:25:53) oscar: Adding handler for 0003/0003
(17:25:53) oscar: Adding handler for 0003/000b
(17:25:53) oscar: Adding handler for 0003/000c
(17:25:53) oscar: Adding handler for 000e/0001
(17:25:53) oscar: Adding handler for 000e/0003
(17:25:53) oscar: Adding handler for 000e/0004
(17:25:53) oscar: Adding handler for 000e/0002
(17:25:53) oscar: Adding handler for 000e/0006
(17:25:53) oscar: Adding handler for 000d/0001
(17:25:53) oscar: Adding handler for 000d/0009
(17:25:53) oscar: Adding handler for 0013/0001
(17:25:53) oscar: Adding handler for 0013/0003
(17:25:53) oscar: Adding handler for 0013/0006
(17:25:53) oscar: Adding handler for 0013/000e
(17:25:53) oscar: Adding handler for 0013/0008
(17:25:53) oscar: Adding handler for 0013/0015
(17:25:53) oscar: Adding handler for 0013/0019
(17:25:53) oscar: Adding handler for 0013/001b
(17:25:53) oscar: Adding handler for 0013/001c
(17:25:53) oscar: Adding handler for 0004/0005
(17:25:53) oscar: Adding handler for 0004/0007
(17:25:53) oscar: Adding handler for 0004/000a
(17:25:53) oscar: Adding handler for 0004/000b
(17:25:53) oscar: Adding handler for 0004/0001
(17:25:53) oscar: Adding handler for 0004/0014
(17:25:53) oscar: Adding handler for 0004/000c
(17:25:53) oscar: Adding handler for 0015/00f0
(17:25:53) oscar: Adding handler for 0015/00f1
(17:25:53) oscar: Adding handler for 0015/00f3
(17:25:53) oscar: Adding handler for 0015/00f2
(17:25:53) oscar: Adding handler for 0002/0003
(17:25:53) oscar: Adding handler for 0002/0006
(17:25:53) oscar: Adding handler for 0002/0001
(17:25:53) oscar: Adding handler for 0002/fffd
(17:25:53) oscar: Adding handler for 0001/0001
(17:25:53) oscar: Adding handler for 0001/000f
(17:25:53) oscar: Adding handler for 0001/001f
(17:25:53) oscar: Adding handler for 0001/0021
(17:25:53) oscar: Adding handler for 0001/000a
(17:25:53) oscar: Adding handler for 0001/0005
(17:25:53) oscar: Adding handler for 0001/0013
(17:25:53) oscar: Adding handler for 0001/0010
(17:25:53) oscar: Adding handler for 0008/0002
(17:25:53) oscar: Adding handler for 000a/0001
(17:25:53) oscar: Adding handler for 000a/0003
(17:25:53) oscar: oscar_login: gc = 0x859f4a8
(17:25:53) g_log: file dnsquery.c: line 618 (purple_dnsquery_a): should not be reached
(17:25:53) account: Disconnecting account 0x813e4b0
(17:25:53) connection: Disconnecting connection 0x859f4a8
(17:25:53) oscar: Destroying oscar connection of type 0x0017
(17:25:53) oscar: Signed off.
(17:25:53) connection: Destroying connection 0x859f4a8
(17:25:54) autorecon: do_signon called
(17:25:54) autorecon: calling purple_account_connect
(17:25:54) account: Connecting to account [email](my email)[/email]
(17:25:54) connection: Connecting. gc = 0x859d1a0
(17:25:54) g_log: file dnsquery.c: line 618 (purple_dnsquery_a): should not be reached
(17:25:54) autorecon: done calling purple_account_connect
(17:25:54) util: Writing file accounts.xml to directory /home/benaiah/.purple
(17:25:54) account: Disconnecting account 0x81428f8
(17:25:54) connection: Disconnecting connection 0x859d1a0
(17:25:54) connection: Destroying connection 0x859d1a0

Any suggestions would be greatly appreciated!

Benaiah

---

### Post by dbbolton on 2007-06-16
are you using a proxy with pidgin?

---

### Post by letubenaiah on 2007-06-16
Thanks.  I had just figured out that I had some wrong proxy settings.  Fixed them and everything is working wonderfully!  Thanks again!

---

### Post by dbbolton on 2007-06-16
> **letubenaiah said:**
> Thanks.  I had just figured out that I had some wrong proxy settings.  Fixed them and everything is working wonderfully!  Thanks again!
quite welcome

---

