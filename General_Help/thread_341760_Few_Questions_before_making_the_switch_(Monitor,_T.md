---
title: "Few Questions before making the switch (Monitor, Tunneling, etc)"
date: 2007-01-19
forum: General Help
---

### Post by stuartornum on 2007-01-19
Hi,

I am fed up with windows, 

I have been trying to make the switch for a year or two but always come back due to the fact I cannot seem to find a bit of software that is as good as windows variant.

So I have a few questions that I reckon you could easily clear up.

1. I have a dual screen 2 x Acer AL1916W (19in Widescreen 1440 x 900) and one Geforce FX 5200 and one nVidia Riva TNT Model 64, not great but I can get both working fine at 1440 x 900 under Windows XP. I have tried no end to get X to work dual screening on this config but am at a loss.

2. I am behind a proxy / firewall, so I use bitvise tunnelier alot under windows, is the a linux version of a very similiar product?

3. Netlimiter, also excellent under Windows, is the a Linux version that is as good?

**Thats it!!**

Everything else is super using Ubuntu.

If you could help me out on one or two I would really appreciate it.

Thanks

---

### Post by darrenm on 2007-01-19
1. I've heard of lots of people with very strange configurations with dual monitor set ups in Linux these days. AFAIK all the res configs that work in Windows should work with Xorg now. It's only limited by the driver and you have a few choices in that respect.

2. Never heard of it sorry, what does it do?

3. Again, what does it do?

---

### Post by stuartornum on 2007-01-19
Hi darrenm,

Thanks for the reply.

Is there a good guide for setting up dual screen, with a sample xorg.conf similiar to my setup?

Bitvise tunnelier [HTML]http://www.bitvise.com/tunnelier[/HTML] a bit of software that connects to a remote server (SSH) and you change your browser to your local socks server that tunnelier creates, therefore all traffic is sent out to the remote server (through the proxy encrypted) and out to the world on the remote servers IP.

Netlimiter, useful when wanting to limit bandwidth on a program, say bit torrents...

Thanks

---

### Post by darrenm on 2007-01-19
1. This one any good? [https://help.ubuntu.com/community/XineramaHowTo](https://help.ubuntu.com/community/XineramaHowTo)

2. Oh is that all it does? I just generally use ssh my.remote.server -L3128:localhost:3128 ;) (assuming the remote proxy is running on port 3128 )

3. Umm, there's gotta be some Perl scripts or something to do it. Its all built into the kernel, you just need a front end. Search Google for bandwidth shaping etc. or wait around for someone to suggest something else :)

---

