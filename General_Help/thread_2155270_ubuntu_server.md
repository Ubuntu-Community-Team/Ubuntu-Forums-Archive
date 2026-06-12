---
title: "ubuntu server"
date: 2013-06-17
forum: General Help
---

### Post by dublindoc on 2013-06-17
I have a self construted computer running Umbutu server 12.04.  It is in a home network.  It was working well until my modem failed.  Comcast provided an Arris TG862 modem/router and my network is functioning normally.  When evrything was finally reset, I discovered my server was completely wiped out.  No loss of any really important data, but I have reformatted all disks, reinstalled umbutu 12.04 and other server programs(samba, webadmin, etc).  I now cannot use Windows IE 9 to open webasmin in the address *.*.*.*:10000 to administer the computer.  I keep getting a security certificate error when I try to connect.  All computers are visible on the network but I cannot access my server for use.  

The new modem is using adress 10.0.0.1 instead of the more familiar 192.168.1.1.

I am much more familiar with Windows than Umbutu, but I had it working well once.  Thought I should be able to do it again, but----.

Any help would be appreciated.

---

### Post by Vitsliputsli on 2013-06-18
What is your local network? 192.168.1.0/24?
And show network settings on server:
ip a; ip r; cat /etc/resolv.conf

---

