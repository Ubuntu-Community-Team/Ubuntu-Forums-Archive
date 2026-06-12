---
title: "Flash Downloading VERRRY Slow"
date: 2008-05-16
forum: General Help
---

### Post by remmyshroomo on 2008-05-16
So, after much frustration I have given up and completed a fresh install of Hardy Heron. I should of done this sooner because everything is running a bit faster now... Except for one stumbling block.

I don't know what the hell can be the cause but when I started flashplugin-nonfree to download it's crawling through the download. When I say crawl, i mean less that 100 BITS a SECOND.

I tried downloading the tar.gz through firefox and yielded the same results. Only when I would cancel the download and resume after a minute the download would pickup speed after about 200kb is received then slowdown to a timeout idle. I painstakingly completed the tar.gz downloaded through firefox faster than through terminal. Only after an hour of my life was wasted.

Now when I try to install through terminal it tells me "Your architecture, \'x86_64\', is not supported by Adobe Flash Player installer"

So how the heck can I get this installed without waiting 4 hours for 100bit/sec download to finish on a 30MB/sec line?


Ryan

---

### Post by SPr on 2008-05-16
Downloading flash has always been slooooow for me too. Have patience and it will complete eventually.

When I used Windows the download speeds were abominable and I always used to get it from FileHippo instead.
```

sudo apt-get install flashplugin-nonfree

```

---

### Post by remmyshroomo on 2008-05-16
yea thats the command i'm using..  it yields these speed results

 0K .......... .......... .......... .......... ..........  1%  364.34 KB/s
   50K .......... .......... .......... .......... ..........  3%  870.15 KB/s
  100K .......... .......... .......... .......... ..........  5%  850.96 KB/s
  150K .......... .......... .......... .......... ..........  6%   15.71 KB/s
  200K .......... .......... .......... .......... ..........  8%   18.69 KB/s
  250K .......... .......... .......... .......... .......... 10%    7.77 KB/s
  300K .......... .......... .......... .......... .......... 11%  399.19 B/s
  350K .......... .......... .......... .......... .......... 13%  165.65 B/s
  400K .......... .......... .......... .......... .......... 15%   85.31 B/s
  450K .......... .......... .......... .......... .......... 16%  426.18 B/s
  500K .......... .......... .......... .......... .......... 18%  106.65 B/s
  550K .......... .......... .......... .......... .......... 20%   42.66 B/s
  600K .......... .......... .......... .......... .......... 21%  106.61 B/s

When I ping macromedia.com i receive a 40 ping but its very delayed in the response time. 6 packets take 2000ms while pinging google.com would produce a 70 ping but deliver 10 packets in 800ms... something is terribly wrong here... Broadcomm driver?

oh sob.. i just reset the download by ctl+c.. doh.. well maybe when i get back from work it'll just finish downloading.


Ryan

---

