---
title: "Failed to upload public key"
date: 2016-04-19
forum: General Help
---

### Post by marco1725 on 2016-04-19
Hello 
I bought vps server and now I want to upload openssh public key. 

With this command: ssh-copy-id username@ipaddress
 the result is:
 /usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed 
/usr/bin/ssh-copy-id: ERROR: ssh: connect to host xxxxxxxxx port 22: connection timed out  

with this command: cat ~/.ssh/id_rsa.pub | ssh username@ipaddress "mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys" 
the result is:
 ssh: connect to host xxxxxxxxx port 22: connection timed out 
 
also with this: 
ssh username@ipaddress 
the result is: 
ssh: connect to host xxxxxxxxx port 22: connection timed out  

With ssh -v root@your-vps-ipaddress 
debug1: Reading configuration data /etc/ssh/ssh_config 
debug1: /etc/ssh/ssh_config line 19: Applying option for * 
debug1: Connect to xxxxxxx port 22 
debug1: Connect to address xxxxxxx port 22: Connection refused 
ssh: connect to host xxxxxxx port 22: Connection refused  

with sudo iptables -L 
Chain INPUT (policy ACCEPT) 
target       prot opt source      destination 
fail2ban-ssh tcp -- anywhere anywhere multiport dport 
s ssh 

 Chain FORWARD (policy ACCEPT) 
target      prot opt source     destination  

Chain OUTPUT (policy ACCEPT) 
target     prot opt source       destination   

Chain fail2ban-ssh (1 reference) 
target      prot opt source      destination 
RETURN all --- anywhere anywhere 

 Regards

---

