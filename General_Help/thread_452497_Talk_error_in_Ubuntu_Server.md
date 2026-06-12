---
title: "Talk error in Ubuntu Server"
date: 2007-05-23
forum: General Help
---

### Post by TheodoreWard on 2007-05-23
I am getting a strange problem. I am running Ubuntu Server and I have the talk service running. It usually works fine, but I have unable to talk to a particular user (jwinesburg below). He is logged on and active but when I enter "talk jwinesburg" talk tells me my party is not logged on.
I don't see anything useful in any log files.
Maybe his username is too long? I can't figure this one out.

[FONT="Courier New"]root@itd-saint:/proc# who
jwinesburg pts/0        2007-05-23 09:30 (xxxx.ok.ok.cox.net)
root     pts/2        2007-05-23 09:35 (xxxx.edu)
tward    pts/3        2007-05-23 10:28 (xxxx.edu)
root@itd-saint:/proc# talk jwinesburg

root@itd-saint:/proc# uname -a
Linux itd-saint 2.6.15-23-server #1 SMP Tue May 23 15:10:35 UTC 2006 i686 GNU/Linux
[/FONT]

Thanks for any insight.
Ted Ward

---

