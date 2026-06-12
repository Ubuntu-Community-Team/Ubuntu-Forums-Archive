---
title: "Iptables logging in Ubuntu 20.04"
date: 2022-10-16
forum: General Help
---

### Post by jakesinthebakes on 2022-10-16
I have set up Cowrie (2222) and SSH (2233) on a Ubuntu server. To block all traffic except Cowrie and SSH, I have run the following commands:


iptables -A INPUT -p tcp --dport 2222 -j ACCEPT
iptables -A INPUT -p tcp --dport 2233 -j ACCEPT
iptables -P INPUT DROP


I now need to log all SSH, Honeypot and Cowrie traffic with the following prefix


"SSH_Traffic, Honeypot_Traffic, Blocked_Traffic".


I believe I need to do something like this:
 
iptables -A INPUT -j LOG
iptables -A INPUT -j LOG --log-prefix "Blocked_Traffic" --log=level 4


But, I am struggling with resources for iptables logging and would appreciate if someone could help?

---

### Post by Doug S on 2022-10-17
See [my answer over on ask]("https://askubuntu.com/questions/1435670/iptables-logging-in-ubuntu/1435712#1435712").

---

