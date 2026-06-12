---
title: "Ubuntu clients not registering i ddns"
date: 2008-04-17
forum: General Help
---

### Post by lwh on 2008-04-17
SOLVED


Hi

Some one must have a answer for this small issue ;-)

Im have a dhcp3-server working with ddns and bind9... (config following the guide on howtoforge)

when I look in my dns, the only two devices registered in the dns with their hostnames, is my linksys wireless and switch..
these two devices is also the only two with extra entries in the dhcpd.leases file on the dhcp server.

Why is my Ubuntu laptops not getting registered correctly with hostname in the dhcpd.leases file and in the dns ?? 
Doo I need to install a extra package or something ????  samba, winwind ????

sample form the dhcpd.leases file.....

lease 172.xxx.xx.236 {
  starts 4 2008/04/17 18:24:05;
  ends 4 2008/04/17 22:24:05;
  binding state active;
  next binding state free;
  hardware ethernet 00:1c:10:f4:a7:5b;
  uid "\001\000\034\020\364\247[";
  set ddns-rev-name = "236.xx.xxx.172.1.16.172.in-addr.arpa.";
  set ddns-txt = "316bcf3d10fd1009a8b21cd01912f6a3a3";
  set ddns-fwd-name = "hostname.domain.local";
  client-hostname "hostname";
}
lease 172.16.1.244 {
  starts 4 2007/12/06 16:27:46;
  ends 4 2007/12/06 20:27:46;
  tstp 4 2007/12/06 20:27:46;
  binding state free;
  hardware ethernet 00:0c:29:8f:a9:02;
}

FYI.  both BIND9 and dhcp3-server is working with no problems, serving my sbs test-setup at home.

---

### Post by lwh on 2008-04-17
Sorry did not doo my home work well enought before posting

solution is in the dhclient.conf  where i need to enable
"send host-name" with the correct hostname .-(  and it's no dynamic  :-(

---

