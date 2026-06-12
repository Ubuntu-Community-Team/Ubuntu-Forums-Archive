---
title: "Ubuntu friendly video card?"
date: 2013-04-18
forum: General Help
---

### Post by decrepit on 2013-04-18
This box is getting a bit unreliable so I'm thinking of replacing it. So far I've relied on onboard video, the only 3D on this computer is Google Earth.

I've noticed a lot of posts about nvidia trouble, so I'm a bit reluctant to buy a computer with a nvidia card.
So my question is, if you don't play games, is it worth getting a graphics card, and if so what is the most ubuntu friendly?

---

### Post by CatKiller on 2013-04-18
Not really, no. Intel graphics are fine for desktop effects and similar. The drivers are included in the kernel, so you don't get Windows-driver-based weirdness like you do with closed-source drivers that try to keep a unified code-base between both platforms. The biggest performance boost you'll see as a non-gamer is by installing an SSD and plenty of RAM.

If you do get a dedicated graphics card, Nvidia is the sensible choice, but avoid Optimus if you can.

---

### Post by 3rdalbum on 2013-04-18
With a graphics card, you will find Unity will run faster, video playback will be smoother and you will be able to play the occasional game.

Nvidia cards start with the letters GT or GTX, a series digit and then a two digit number giving you an indication of relative performance. For instance, my card is a GTX260, which is faster than a GT220.

If you are on a budget, any current Nvidia card will do very nicely. The last two digits can be low as long as the first digit is the current Nvidia generation.

---

### Post by CatKiller on 2013-04-18
> **3rdalbum said:**
> With a graphics card, you will find Unity will run faster, video playback will be smoother and you will be able to play the occasional game.

I don't think that's true anymore. Ivy Bridge graphics get you all of those things. Ivy Bridge and Haswell have pretty much got the budget end sewn up since you're paying for it anyway with the processor. New games or games with lots of detail are too much for the integrated graphics to handle, certainly, but the OP hasn't expressed an interest in those.

To get more than the integrated graphics can provide you really need to go at least mid-range dedicated graphics (with the associated cost & closed-source drivers) and if you're doing that then you probably already know what you need.

My advice would be to stick with integrated. If you find that you need more it's simple to add it in later and prices for the equivalent level of performance will have come down in the meantime.

---

### Post by SeijiSensei on 2013-04-18
> **decrepit said:**
> This box is getting a bit unreliable so I'm thinking of replacing it. 

If you are thinking of replacing the entire computer, then as Catkiller says even Intel motherboard graphics are probably a substantial upgrade from what you have now.

if, however, you just want to spend some money on a new graphics card, then I would definitely suggest buying an NVIDIA card.  The hybrid Optimus technology on laptops is a pain, but if you are simply upgrading the graphics in a desktop machine even a low-priced NVIDIA adapter would make a big difference.  I can't help with sales in Australia, but here's a page of [potential candidates at NewEgg]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709%20600030348%204025%20600007321&IsNodeId=1&name=GeForce%20G%2fGT%20series&Order=REVIEWS&Pagesize=20").

---

### Post by tornadof3 on 2013-04-18
I think the nVidia cards are generally very easy to use and install. I put an nVidia GeForce 210 (1Gb) into my ubuntu 12.10 box. This is an older card now; it cost me about £20 online, and my computer can now do everything with graphics that I had ever wanted.

---

### Post by decrepit on 2013-06-24
OK I went with an intel G2020 processor and it gives me all the graphics I need. Google earth is about 10x faster now.

---

