---
title: "NAT Problem in Vuze using Vidalia on Ubuntu 12.04"
date: 2013-06-13
forum: General Help
---

### Post by hsincredible on 2013-06-13
[COLOR=#000000][FONT=Arial]I got vuze working through vidalia in Ubuntu12.04, and torrents are downloading, but speed is slow. I have yellow smileys with the torrent, and its because of some NAT problem. My listen port was set to 28729. I used Help->NAT/Firewall Test to test the port, and it gives me - Testing port 28729 ... NAT Error - Connect attempt to 77.247.181.162:28729 (your computer) timed out after 20 seconds. This means your port is probably closed.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Then, I changed the port to 45000(randomly), and again it said- Testing port 45000 ... NAT Error - Connection to 173.254.216.68:45000 (your computer) refused.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Before testing, I manually allowed the ports through firewall by command- sudo ufw allow 45000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Please help me through this. Thanks![/FONT][/COLOR]

---

### Post by sanderj on 2013-06-13
Probable cause: een modem/router doing NAT

---

