---
title: "DNS affected by mozilla?"
date: 2007-04-09
forum: General Help
---

### Post by foleybri on 2007-04-09
Hello,

I have a pretty basic install of 6.06 LTS, with all software updates installed.

I have four tabs set as my homepage in mozilla, but the DNS for these websites seem to get mixed up on an intermittent basis (I am working on a laptop, so tend to reboot regularly).

For example, today I cannot visit [http://reddit.com](http://reddit.com).  When I use "ping" from an xterm, I see the following:
```

brianf@BriansLaptop:~$ ping reddit.com
PING reddit.com (212.58.224.82) 56(84) bytes of data.
64 bytes from www.bbc.co.uk (212.58.224.82): icmp_seq=1 ttl=247 time=11.4 ms
64 bytes from www.bbc.co.uk (212.58.224.82): icmp_seq=2 ttl=247 time=15.6 ms

```

reddit.com somehow is mapped to bbc.co.uk

Can somebody help me troubleshoot this problem?  I do not know much about DNS, and checking ping is about the limit of my expertise.

Thanks,

Brian.

---

### Post by bettlebrox on 2007-04-09
Either your /etc/resolv.conf is messed up, or someone point reddit.com to the BBC in your /etc/hosts . 

Post both files please.

---

### Post by foleybri on 2007-04-10
> **bettlebrox said:**
> Either your /etc/resolv.conf is messed up, or someone point reddit.com to the BBC in your /etc/hosts . 

Post both files please.

/etc/resolv.conf
```

search home
nameserver 192.168.1.1

```

/etc/hosts
```

127.0.0.1 localhost BriansLaptop
127.0.1.1 BriansLaptop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

As I said, the problem seems to be intermittent.  Today, I can access reddit.com from within mozilla, but slashdot.org redirects to [http://reddit.com/noreddit](http://reddit.com/noreddit) (from within mozilla)...

It's only the four websites that I have as my homepage in mozilla that seem to cause problems (slashdot, reddit, bbc & netcraft).

Do the two files above give you any clues?

Thanks,

Brian.

---

