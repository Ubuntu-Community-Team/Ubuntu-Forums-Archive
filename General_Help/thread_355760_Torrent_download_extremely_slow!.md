---
title: "Torrent download extremely slow!"
date: 2007-02-07
forum: General Help
---

### Post by sohaibma on 2007-02-07
I am using Siemens SpeedStream router with my dapper system. I have tried to use two torrent clients, azureus and bittornado. Both download at very low speeds (not more than 5kb/s, in Windows XP i reach about 50-60kb/s), the health status is yellow in both.
Azureus indicates a NAT problem.
Bittornado cshows a firewall problem.

Since, I am new to ubuntu and networking, please someone guide me through the solution to this problem.
How do i increase my download speed.

---

### Post by taurus on 2007-02-07
Maybe you want to install firestarter and use it to config the firewall on your machine.  Open whatever port azureus is using so the button for NAT is green.  Of course, you have to open the same port on your router or else you would get a poor download speed.

---

### Post by WinterWeaver on 2007-02-07
You need to forward the ports which you are using in your programs. This you do on the router setup page.
If you are unsure on where to do it on your router, use this link: [www.portforward.com](www.portforward.com)

Something you should also be aware of, some ISP's actually block some of the mainstream Port's used for torrents. If you follow the Azuereus help, it will tell you what port range is the best to use.

After setting up my ports, I didn't have any NAT problems.

Also remember, that your download speed is based on how many peers and seeds you are connected to, and their upload speeds.

Hope this helps... ^_^

WW

---

