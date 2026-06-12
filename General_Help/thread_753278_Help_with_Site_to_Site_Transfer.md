---
title: "Help with Site to Site Transfer"
date: 2008-04-12
forum: General Help
---

### Post by NetTripper on 2008-04-12
Would apperciate basic instructions using a windoze based app called FlashFXP. I am attempting to transfer a 30gig backup from my old provider. Going the lunar pages to the planet.

Or need further help figuring out a solid method of transfering this mega file from site to site. I am using Gutsy will all the current updates. Kinda meandering with this issue. Thanks in advance for any help you can provide.

P.S. I am trying to stay away from ssh tranfers. Need to be able to watch the speed or length of transfer time or percent completed ?      :confused:

---

### Post by tamoneya on 2008-04-12
FlashFXP uses FTP to transfer files over the network.  You will need to make sure that you have an FTP server install on the server box and you will need to know the IP address, username and password.  I am not familiar with the FlashFXP gui but I took a quick look [here]("http://www.flashfxp.com/tutorials.php?s=2") and I would try to use the quick connect option.  Follow the tutorial and you should be set.


> **NetTripper said:**
> Going the lunar pages to the planet.
I think i missed something there?

---

### Post by NetTripper on 2008-04-12
I meant to say i was moving from Lunar Pages to The Planet web hosting company. Was trying to be specific as there may be differences in what either company allows. I will attempt the transfer soon though. As i have till the 19th to move all the data from one host to another.

---

### Post by Olav on 2008-04-12
For FTP in Ubuntu/Linux, there is always [gFTP]("http://gftp.seul.org") ([screenshot]("http://gftp.seul.org/screenshots.html")). It's available through apt (synaptic will do fine). From what I have seen of FlashFXP, it is almost the same thing.

---

