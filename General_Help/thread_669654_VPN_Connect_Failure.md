---
title: "VPN Connect Failure"
date: 2008-01-16
forum: General Help
---

### Post by mbaucsoft on 2008-01-16
My VPN setup has stopped working.  I thought it might have been related to some updates I had recently applied, so I did a system upgrade to 7.10.  That didn't help.  I'm getting VPN Connect Failure.

I have 7.10 installed on another computer, which is working, and compared the settings to make sure they are the same.

Below is part of entries from syslog (with some of the data changed for security reasons).  

Any suggestions?

Jan 16 15:02:41 mbubuntu pppd[15926]: Plugin nm-pppd-plugin.so loaded.
Jan 16 15:02:41 mbubuntu pppd[15926]: nm-pppd-plugin: plugin initialized.
Jan 16 15:02:41 mbubuntu pppd[15928]: pppd 2.4.4 started by root, uid 0
Jan 16 15:02:41 mbubuntu pptp[15930]: anon log[main:pptp.c:267]: The synchronous pptp option is NOT activated 
Jan 16 15:02:41 mbubuntu pppd[15928]: using channel 2
Jan 16 15:02:41 mbubuntu pppd[15928]: Using interface ppp0
Jan 16 15:02:41 mbubuntu pppd[15928]: Connect: ppp0 <--> /dev/pts/0
Jan 16 15:02:41 mbubuntu pptp[15933]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Jan 16 15:02:41 mbubuntu pptp[15933]: anon log[ctrlp_disp:pptp_ctrl.c:738]: Received Start Control Connection Reply
Jan 16 15:02:41 mbubuntu pptp[15933]: anon log[ctrlp_disp:pptp_ctrl.c:772]: Client connection established.
Jan 16 15:02:42 mbubuntu pppd[15928]: nm-pppd-plugin: CHAP check hook.
Jan 16 15:02:42 mbubuntu pppd[15928]: sent [LCP ConfReq id=0x1 <mru 1416> <asyncmap 0x0> <magic 0xxxxx> <pcomp> <accomp>]
Jan 16 15:02:42 mbubuntu pptp[15933]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Jan 16 15:02:42 mbubuntu pptp[15933]: anon log[ctrlp_disp:pptp_ctrl.c:857]: Received Outgoing Call Reply.
Jan 16 15:02:42 mbubuntu pptp[15933]: anon log[ctrlp_disp:pptp_ctrl.c:896]: Outgoing call established (call ID 0, peer's call ID 3). 
Jan 16 15:02:45 mbubuntu pppd[15928]: sent [LCP ConfReq id=0x1 <mru 1416> <asyncmap 0x0> <magic 0xxxxx> <pcomp> <accomp>]
Jan 16 15:02:51 mbubuntu last message repeated 2 times
Jan 16 15:02:52 mbubuntu pppd[15928]: Terminating on signal 15
Jan 16 15:02:52 mbubuntu pppd[15928]: sent [LCP TermReq id=0x2 "User request"]
Jan 16 15:02:52 mbubuntu pptp[15933]: anon log[callmgr_main:pptp_callmgr.c:255]: Closing connection (shutdown)
Jan 16 15:02:52 mbubuntu pptp[15933]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Jan 16 15:02:52 mbubuntu pptp[15933]: anon log[call_callback:pptp_callmgr.c:78]: Closing connection (call state)
Jan 16 15:02:52 mbubuntu NetworkManager: <WARN>  nm_vpn_service_process_signal(): VPN failed for service 'org.freedesktop.NetworkManager.ppp_starter', signal 'ConnectFailed', with message 'VPN Connection failed'. 
Jan 16 15:02:52 mbubuntu NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 3 -> 5. 
Jan 16 15:02:52 mbubuntu NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 5 -> 6. 
Jan 16 15:02:52 mbubuntu NetworkManager: <WARN>  nm_vpn_service_stop_connection(): (VPN Service org.freedesktop.NetworkManager.ppp_starter): could not stop connection 'ASI' because service was 6. 
Jan 16 15:02:52 mbubuntu pppd[15928]: Modem hangup
Jan 16 15:02:52 mbubuntu pppd[15928]: Connection terminated.
Jan 16 15:02:52 mbubuntu pppd[15928]: Child process /usr/sbin/pptp xxxxx --nolaunchpppd (pid 15929) terminated with signal 15
Jan 16 15:02:52 mbubuntu pppd[15928]: Exit.

---

### Post by buggs187 on 2008-03-26
Thats the same log that I get as well useing Ubuntu 7.10 trying to connect to a VPN. Does anyone know if this is a bug. and if so how to report it? Or is this fixed already with the Beta of 8.04.

---

### Post by LanceM on 2008-03-26
Is there a log on the other end that shows the connection attempt?

---

