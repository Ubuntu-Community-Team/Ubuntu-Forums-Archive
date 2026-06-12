---
title: "Gutsy wont let a remote user dialin"
date: 2007-11-02
forum: General Help
---

### Post by KhurramF on 2007-11-02
I have set up Gutsy on my pc at home. I would like to dial into the system from my laptop. I have followed the instructions from "HOWTO dialin PPP server, RAS server " in the "Tutorial & Tips" section. But I am having trouble connecting from the laptop. I can see from the log that I am authenticated, but pppd then just exits. The following is the relevant excerpt from the log:
> pppd[6668]: pppd 2.4.4 started by , uid 0
pppd[6668]: Using interface ppp0
pppd[6668]: Connect: ppp0 <--> /dev/ttyS0
pppd[6668]: user xxxx logged in
pppd[6668]: PAP peer authentication succeeded for xxxx
pppd[6668]: Connect time 0.1 minutes.
pppd[6668]: Sent 103 bytes, received 129 bytes.
pppd[6668]: Hangup (SIGHUP)
pppd[6668]: Modem hangup
pppd[6668]: Connection terminated.
pppd[6668]: Connect time 0.2 minutes.
pppd[6668]: Sent 175 bytes, received 129 bytes.
pppd[6668]: Exit.

I know the modem is okay because I can dial my ISP from home without any problems.

Can someone please help me out?

Thanks.

---

### Post by KhurramF on 2007-11-13
I finally found the answer. I needed to remove the '-detach' line from ppp options file.

---

