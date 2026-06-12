---
title: "Checking Baned IP's"
date: 2007-03-12
forum: General Help
---

### Post by ComputerGuy56 on 2007-03-12
I know how to ban a IP:
sudo iptables -I INPUT -s 192.168.0.0 -j DROP

And Unban:
sudo iptables -D INPUT -s 192.168.0.0 -j DROP

I sometimes block a IP cause it's flooding my firewall, then want to un-ban it and I completely forgot the IP. Is there a way to check which IP's are banned/blocked?

---

### Post by thesoothsayer on 2007-03-15
sudo iptables --list

---

### Post by ComputerGuy56 on 2007-03-17
Just what I was looking for, Thanks.:)

---

