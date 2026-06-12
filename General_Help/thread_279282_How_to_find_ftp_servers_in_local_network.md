---
title: "How to find ftp servers in local network?"
date: 2006-10-17
forum: General Help
---

### Post by adma on 2006-10-17
I can use findsmb to find samba servers in my local network.

Can I do this to find ftp servers in my local network?

A solution to this issue could be a method to scan for existing servers given an ip address range...

Thanks!

---

### Post by JonahRowley on 2006-10-17
**sudo apt-get install nmap** then **nmap -p 21 192.168.0.0/24**  Replace 192.168.0.0/24 with your network address and network mask.  You can also use an address like 192.168.0.0-10 to scan host addresses 0 through 10.

---

### Post by adma on 2006-10-17
That worked great! Thank you very much!

---

