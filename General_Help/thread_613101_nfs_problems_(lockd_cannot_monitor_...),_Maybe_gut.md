---
title: "nfs problems (lockd: cannot monitor ...), Maybe gutsy regression."
date: 2007-11-14
forum: General Help
---

### Post by ernstkl on 2007-11-14
Hello!

I configured an nfs server and a client machine (at home for family).
I followed the advice given in [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo) very closely.

Now there are a lot of error messages in the syslogs of the the client and of the server.

on Client (which is 192.168.0.5)
--------------------------------------------
Nov 14 21:15:57 rechner5 rpc.statd[9864]: Call to statd from non-local host 192.168.0.5
Nov 14 21:15:57 rechner5 rpc.statd[9864]: STAT_FAIL to rechner5 for SM_MON of 192.168.0.4
Nov 14 21:15:57 rechner5 kernel: [ 6179.061529] lockd: cannot monitor 192.168.0.4

on Server (which is 192.168.0.4)
----------------------------------------------
Nov 14 21:28:19 rechner4 rpc.statd[4769]: Call to statd from non-local host 192.168.0.4
Nov 14 21:28:19 rechner4 rpc.statd[4769]: STAT_FAIL to rechner4 for SM_MON of 192.168.0.5
Nov 14 21:28:19 rechner4 kernel: [ 6943.682459] lockd: cannot monitor rechner5

Strangely, the messages are symmetric. But only rechner4 is an nfs server.

I cannot remember to have seen such messages before the upgrade from feisty to gutsy and they first appear in the syslogs on oct 14, where I maybe upgraded to gutsy beta.

Are there any ideas?

---

