---
title: "Can't get internet something with TCP/IP"
date: 2007-02-15
forum: General Help
---

### Post by hubey on 2007-02-15
I've installed Ubuntu 6.10 to a computer
But I can't get internet because the internet requires static TCP/IP
How can I configure the computer so I can get Internet?:confused:

---

### Post by mssever on 2007-02-15
Is this wired or wireless?

If it's wired, then go to System > Administration > Networking. You should be able to configure it from there.

---

### Post by hubey on 2007-02-15
It is wired... I've configure it, but I can't get any website open. When I enter [www.google.com](www.google.com) to the address bar, I get "Connecting to www.google.com" and status bar goes on 50% and then nothing happens.

---

### Post by phork on 2007-02-15
If you've configured your computer with a static IP, odds are you didn't enter any DNS server information, and thus can't resolve anything.  You can manually edit /etc/resolv.conf with the IPs of your ISPs recommended servers (or do this through the same GUI), or use public nameservers such as OpenDNS's, which are:
208.67.222.222
208.67.220.220

Hope that helps.. cheers.

---

### Post by dcstar on 2007-02-15
> **phork said:**
> If you've configured your computer with a static IP, odds are you didn't enter any DNS server information, and thus can't resolve anything.  You can manually edit /etc/resolv.conf with the IPs of your ISPs recommended servers (or do this through the same GUI), or use public nameservers such as OpenDNS's, which are:
208.67.222.222
208.67.220.220

Hope that helps.. cheers.

Or you can go: System-Administration-Networking and put them in the DNS section there.

---

### Post by mssever on 2007-02-16
Here's a general tip for configuring networking: Use ```
ping yahoo.com
``` to check for network connectivity (or ping some other relavant  host, such as your router). ping gives more useful information than Firefox.

---

### Post by Bartolomeo on 2008-01-15
> If you've configured your computer with a static IP, odds are you didn't enter any DNS server information, and thus can't resolve anything. You can manually edit /etc/resolv.conf with the IPs of your ISPs recommended servers (or do this through the same GUI), or use public nameservers such as OpenDNS's, which are:
208.67.222.222
208.67.220.220

Thanks for the information. It helped me.

---

