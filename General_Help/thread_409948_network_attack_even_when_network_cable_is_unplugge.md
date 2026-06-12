---
title: "network attack even when network cable is unplugged"
date: 2007-04-15
forum: General Help
---

### Post by hiteshchopra on 2007-04-15
i use ubuntu dapper 6.06 lts..now ive been having this strange problem that my networks being attacked even when its disconnected. i use firestarter as a firewall and its shows that am constantly attacked whether am connected or disconnected. usually when am connected all the bandwith is taken away by the attacks and am not able to open any site or use any messenger ..i am able ot utilize only 1% of the availabel network speed.. i shifted to windows ot check if its happening there too and the end result was da same..my network provider clearly stated that his networks running fine and it isnt from hsi network. i reinstalled my drivers again but no improvement..the more i restart my comp it gets wors..

below r lsited soem of the ips which keep on attacking at a regular interval(as of now its every 17 minutes..logged on or off)..and goes upto an attack every 1 second too...

Time: Apr 15 14:29:43 Source: 172.35.15.78 Destination: 133.100.11.8 In IF: Out IF: eth0 Port: 123 Length: 76 ToS: 0x10 Protocol: UDP Service: NTP

Time: Apr 15 14:29:46 Source: 172.35.15.78 Destination: 193.62.22.98 In IF: Out IF: eth0 Port: 123 Length: 76 ToS: 0x10 Protocol: UDP Service: NTP

Time: Apr 15 14:46:47 Source: 172.35.15.78 Destination: 133.100.11.8 In IF: Out IF: eth0 Port: 123 Length: 76 ToS: 0x10 Protocol: UDP Service: NTP

Time: Apr 15 14:46:49 Source: 172.35.15.78 Destination: 193.62.22.98 In IF: Out IF: eth0 Port: 123 Length: 76 ToS: 0x10 Protocol: UDP Service: NTP

ive used the firetstarter policy to block the above 2 ips.

other ips that have been craeting problems are

63.245.209.31
133.100.11.8
193.62.22.98
clock.tl.fukuoka.ac.jp
ntp2.ja.net


and there r many more like these..please help me out...can it be a hardware problem..can a virus reside on the lan card?

NEED URGENT HELP!!!

Thanks .
Edit/Delete Message

---

### Post by alexandrul on 2007-04-15
it seems to me that the packets are generated on your pc - could be an attempt to access some time servers using ntp protocol - and it is not an attack
  IMHO, the lack of network access is caused by something else

---

### Post by dexter on 2007-04-15
Do you have vmware installed ? That creates new (virtual) connections that might show up in your firewall.

---

### Post by pointone on 2007-04-15
63.245.209.31 = dyna-addons.nslb.sj.mozilla.com (as in something to do with Mozilla add-ons)
133.100.11.8 = clock.tl.fukuoka-u.ac.jp (as in setting your system clock from an NTP server)
193.62.22.98 = ntp2.ja.net (as in setting your system clock from an NTP server)

172.xxx.xxx.xxx is an internal IP address, so this is likely some other program or process doing something or other.

I don't think you're having any security problems here. Everything is working as it should.

---

