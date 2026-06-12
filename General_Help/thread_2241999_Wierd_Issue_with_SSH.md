---
title: "Wierd Issue with SSH"
date: 2014-08-29
forum: General Help
---

### Post by nick140 on 2014-08-29
Hello All ,

I have a weird issue with logging into ssh on one 10.04 server. Sometimes it refuses my login with a  Connection Timed out. Other times it brings me to the Login as and then times out, other times its lets me login, but within 2 to 15 seconds i get a network Error:Software caused connection abort. sometime when I restart the ssh service it lets me login for up to 20  seconds before booting me. And occasionally, it keeps me logged in, but  the system locks up and does not take keyboard command till i exit

Now i have commented out in the ssh_config 
#GSSAPIauthentication
#GSSAPIDelegateCredentials 

And i have added

UseDNS no
ServerAliveInterval 15
ServerAliveCount 3

Theese have no fixed the issue. i have disabled the iptables , and my customer put fail2ban and i disabled that also, still no luck.

I have tried SSH using Putty from a windows box, and also from a server CentOS box on the same LAN, everything has the same behavior.

Now i have console access to the server and it performs normally. Nothing indicating a issue with the server. The server is a web server and it still serves pages perfectly fine.

I have done a arp search to see if there was a ip conflict for ipv4 and it comes clear, but there is a ip6 conflict message in the /var/log/messages, even though we didnt setup IPV6. Could this cause this behavior even though im using ipv4 address to get in.

Kinda stumped here. Anyone have any ideas?

---

