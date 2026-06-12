---
title: "How Can I manage the bandwidth of aptitude, for example?"
date: 2007-03-30
forum: General Help
---

### Post by Davigetto on 2007-03-30
Well, I have a 100 KB Connection, but of these 100 KB, I only must use 50 KB as maximum, because there are more PC in LAN.

Well, when I execute "sudo aptitude upgrade", for example, ubuntu takes all bandwidth, the 100 Kbps, causing lag problems on all network, and I would want to use only 50 Kbps when I run my Internet programas like aptitude.

I have used trickle but it doesn't work. Any tips?

Greetings

---

### Post by FakeOutdoorsman on 2007-03-31
Your router might provide Quality of Service (QoS).  I'm using a Linksys with the excellent [DD-WRT]("http://www.dd-wrt.com/") firmware.  Under Applications & Gaming -> QoS you can specify an upload/download limit and give some applications or services a high or low priority.  For example you can exempt HTTP traffic from any QoS limiting while limiting bittorrent traffic.

---

### Post by mufflon on 2008-04-30
> **Davigetto said:**
> 

I have used trickle but it doesn't work. Any tips?



Hmmm... trickle SHOULD work just fine. I used trickle and apt-get some years ago on Debian.

I *think* stand-alone-mode didn't work for me. 
When not using stand-alone-mode you have to make sure that you have trickled running before using trickle.
Like this:
```

trickled
sudo trickle -d [MAX DOWNLOAD IN KB/s] aptitude safe-upgrade

```

Works for me on Hardy Heron.

---

