---
title: "[SOLVED] Firewall Problems"
date: 2008-03-01
forum: General Help
---

### Post by flippedup on 2008-03-01
Having some problems getting my firewall to accept on any port.  I'm have Network-Manager installed but disabled it's handling of my interface eth0 to try to get iptables working correctly.  The following is what I have currently configured for iptables:

system@five/14:14:02:~$ sudo iptables -L -v
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    2   144 ACCEPT     0    --  lo     any     anywhere             anywhere            
 3543 2329K ACCEPT     0    --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:ssh 
    3   136 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:6114 
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            udp dpt:6114 
   24  5752 DROP       0    --  any    any     anywhere             anywhere            

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 3604 packets, 542K bytes)
 pkts bytes target     prot opt in     out     source               destination 



However, when I use nmap to see which ports are open on my system (all done with computer behind my router), I get the following:

system@five/14:14:08:~$ nmap five

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2008-03-01 14:15 MST
Interesting ports on five (127.0.1.1):
Not shown: 1695 closed ports
PORT    STATE SERVICE
111/tcp open  rpcbind
631/tcp open  ipp

Nmap finished: 1 IP address (1 host up) scanned in 0.159 seconds


Is there any reason why iptables doesn't want to play nicely?

---

### Post by euler_fan on 2008-03-01
You might try using Firewall Builder to build your firewall policy rather than hand-writing your IPTables rules. You can get it in Synaptic.

---

### Post by flippedup on 2008-03-01
Thanks for the advice - I tried installing firestarter and setting up the appropriate rules, but that didn't work either.  Nevertheless, I have rules setup on my web server that are working fine.  Could it be a conflict with Network-Manager?

---

### Post by flippedup on 2008-03-01
Seems like Ubuntu's install comes with all ports closed so adding a firewall is redundant.  Also, as you install software, ports will open up automatically.  I'm currently running a game under Wine and would like to host games (which requires me to open up tcp/udp port 6114).  If I don't have to configure a firewall (since the default is to accept everything), how can I open up port 6114?

Any help will be much appreciated!

Thanks -

EDIT ===========

Nevermind, seems like you can't host games in the newest version of Wine for Warcraft 3 (III)

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3126](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3126)

Hope this helps someone else.

---

