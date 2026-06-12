---
title: "Quick Question about Hosts File"
date: 2007-11-03
forum: General Help
---

### Post by mkswanson on 2007-11-03
I'm confused about what is going on, and hope someone can point me in the right direction.

When I ping my internal IP address (172.168.0.103), I get a successful ping:
64 bytes from 172.168.0.103...

When I ping my external IP address (75.59.128.116), I get a successful ping (sometimes):
64 bytes from adsl-75-59-128-116.dsl.applwi.sbc.global.net...

When I set my my hostname and point it to the internal IP address in the hosts file, I get:
From ACA80067.ipt.aol.com (172.168.0.103)...Destination Host Unreachable

When I run ifconfig /flushdns, I get:
/flushdns: error fetching interface information: Device not found

I am confused as to wht I am getting a reply from anything AOL since I shouldn't be communicating with AOL at all.  I have the server running on a VMWare session bridged with a dedicated NIC card for this VM Machine only.  I use AT&T DSL, so I woudln't think I sholdn't be touching an AOL network to ping my own IP address.

I am also confused about the /flushdns (I've never actually tried running this command in Lnux before, but figured it couldn't hurt...) and the error "device not found."  If this is referring to my NIC, and it can't find it, then wouldn't I be unable to ping the outside world?  I can successfully ping google.com by name and IP...

Please help!

---

### Post by dcstar on 2007-11-03
> **mkswanson said:**
> I'm confused about what is going on, and hope someone can point me in the right direction.

When I ping my internal IP address (172.168.0.103), I get a successful ping:
64 bytes from 172.168.0.103...

When I ping my external IP address (75.59.128.116), I get a successful ping (sometimes):
64 bytes from adsl-75-59-128-116.dsl.applwi.sbc.global.net...

When I set my my hostname and point it to the internal IP address in the hosts file, I get:
From ACA80067.ipt.aol.com (172.168.0.103)...Destination Host Unreachable

When I run ifconfig /flushdns, I get:
/flushdns: error fetching interface information: Device not found

I am confused as to wht I am getting a reply from anything AOL since I shouldn't be communicating with AOL at all.  I have the server running on a VMWare session bridged with a dedicated NIC card for this VM Machine only.  I use AT&T DSL, so I woudln't think I sholdn't be touching an AOL network to ping my own IP address.

I am also confused about the /flushdns (I've never actually tried running this command in Lnux before, but figured it couldn't hurt...) and the error "device not found."  If this is referring to my NIC, and it can't find it, then wouldn't I be unable to ping the outside world?  I can successfully ping google.com by name and IP...

Please help!

172.168.x is a PUBLIC IP address range, you should not be using it.

Use 192.168.x.x

---

### Post by bingoUV on 2007-11-03
What do you want to achieve by ifconfig /flushdns ?

I don't think it does what you want it to do. If you have nscd, maybe you want 
```

sudo /etc/init.d/nscd restart

```

but I am not sure

---

