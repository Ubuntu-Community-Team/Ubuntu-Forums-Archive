---
title: "Azureus and NAT."
date: 2005-11-02
forum: General Help
---

### Post by xmastree on 2005-11-02
I've started using azureus for bittorrenting and it works well except that I can't get the green face. It's always yellow, indicating a NAT problem.
Having searched the forums, it seems I need to enable port forwarding or something.

Tools > NAT / Firewall Test gives:
```
Testing port 6881 ... NAT Error
```
Following [this]("http://www.ubuntuforums.org/showpost.php?p=365965&postcount=5") post I did the pcflank.com advanced port scan on 6881:
```
Port:  	 	Status       	Service       	Description
6881 	  	closed             n/a              n/a
```

My internet connection is via Wi Fi. My NIC is connected to a small box supplied by the isp (see picture) which is connected to a rooftop antenna. Somewhere in there is a DHCP server, and it all works perfectly. However, I have no idea how to set anything up inside it.

This is way over my head. :confused: 

How can I open that port? I'm not running any firewall here.

Is it a big deal anyway, since I seem to be able to torrent files in both directions?

---

### Post by skydvrgrl on 2005-11-02
Yup you have to forward your ports....NAT error means you are downloading but it also means that other users cannot properly access your computer to download parts of the torrent you are downloading ie you are leeching, but as you arent connected properly you wont be getting full speed available to you either. (I think that should make sense!)

As for port forwarding there is a good guide at [http://www.portforward.com](http://www.portforward.com)

Just look for your hardware and follow the instructions.

Cheers

---

### Post by xmastree on 2005-11-02
[QUOTE=skydvrgrl]Just look for your hardware and follow the instructions.[/QUOTE]Ah, yes... well...
Trouble is I have no idea what this thing is or who made it. :rolleyes: 

There are two stickers on it, one for [meridian]("http://www.meridiantelekoms.com/") and one with NTC model number AC100/220V. As this one has the country's flag, I suspect it's something like National Telecommunications Council or similar.

So I've no idea who the manufacturer is.

---

### Post by xmastree on 2005-11-04
Well, although it seems to be working, While I'm seeding a completed download I continually get errors, which **all** need to be acknowledged. So if I go out for the day, I have to click a myriad windows when I return.
Is there a way to stop it from reporting all this?
```
UPnP: Lost connection to service 'WAPNIPConnection' on 
UPnP device '192.168.232.44'
```followed by:```
UPnP: Mapping 'UDP tracker client port (UDP/6881)' failed
``````
UPnP: Mapping 'Incoming Peer Data Port (TCP/6881)' failed
```Another thing, what's that 192.168.232.44 about? My machine is 192.168.232.214 :confused:

---

