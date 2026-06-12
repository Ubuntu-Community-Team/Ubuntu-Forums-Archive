---
title: "help! help!!!!!!!!!"
date: 2007-11-12
forum: General Help
---

### Post by xuxinwu on 2007-11-12
Help..help!
I cann't connect with internet!
Please give me a solution !
Thank you very much!

xuxinwu@xuxinwu:~$ sudo pppoeconf 
[sudo] password for xuxinwu: 
Plugin rp-pppoe.so loaded. 
xuxinwu@xuxinwu:~$ plog 
Nov 11 16:23:45 xuxinwu pppd[7848]: Plugin rp-pppoe.so loaded. 
Nov 11 16:23:45 xuxinwu pppd[7850]: pppd 2.4.4 started by root, uid 0 
Nov 11 16:23:45 xuxinwu pppd[7850]: PPP session is 4852 
Nov 11 16:23:45 xuxinwu pppd[7850]: Using interface ppp0 
Nov 11 16:23:45 xuxinwu pppd[7850]: Connect: ppp0 <--> eth0 
Nov 11 16:23:45 xuxinwu pppd[7850]: Remote message: 46;No Service response 
Nov 11 16:23:45 xuxinwu pppd[7850]: PAP authentication failed 
Nov 11 16:23:45 xuxinwu pppd[7850]: Connection terminated. 
xuxinwu@xuxinwu:~$ ifconfig ppp0 
ppp0: error fetching interface information: Device not found 
xuxinwu@xuxinwu:~$

---

### Post by Green_Star on 2007-11-12
there is a useless poll in your post, you may want to delete that.

Can we have 'ifconfig' output? And you did not mention how you are connecting to internet? are you behand the firewall or router etc?

---

