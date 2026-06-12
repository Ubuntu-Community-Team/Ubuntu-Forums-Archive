---
title: "pdf viewer slow"
date: 2013-02-01
forum: General Help
---

### Post by thorbs on 2013-02-01
I dont know if it allways been like this, but I dont think so. On my xubuntu box the pdf viewer is unbelivable slow. And even with just 20 pages. It takes more than a minute to open. And if I move to quickly in it, it becomes completely blank and have to wait and load. It is as close to useless as possible. What to do?

---

### Post by srekcahrai on 2013-02-01
switch to okular
```
sudo apt-get install okular
```

---

### Post by orb9220 on 2013-02-01
> On my xubuntu box

Which specs are?
As doing pdf's on limited or older machines with minimum horsepower or ram.
And what kind of video chipset and drivers used. As if drivers don't support 3d rendering 
then it all has to be done by the Cpu & Ram.

Can be problematic. 
.

---

### Post by Impavidus on 2013-02-02
Number of pages is irrelevant. I just checked with my default pdf reader (evince) and it opens a 912 page 7,771,729 byte pdf with mostly text instantaniously, but needs up to several seconds (depending on the complexity of the page) to open a 63 page 41,285,775 byte pdf with lots of both raster and vector images (photographs, plots with thousands of data points). I have plenty of RAM and no graphics driver problems, so I think you just tried a very complicated pdf. Do some tests with pdfs with few bytes per page.

Loading pdfs is CPU limited, unless you don't have enough memory to cache a rendered page at the resolution you want. Graphics cards are optimized for raster graphics, they may not be of much help for vector graphics that need more complicated things than matrix multiplication and filling of triangles.

You could try a different viewer (okular, gv if you like a bare-bones look; it has good zooming functions). Maybe they do a slightly better job by first rendering the page you want to view and then continue by pre-drawing surrounding/subsequent pages and caching pages in RAM. Scrolling down could prove much faster than scrolling up.

---

### Post by Gotti on 2013-02-02
mupdf!!

No bells and whistles...but quite efficient. I use it on my fluxbox setup.

```
sudo apt-get install mupdf
```

---

### Post by bigdes on 2013-02-02
Sorry for high jacking this thread but I'm new to this and don't know how to start a new post. I have upgraded my computer. My old system has ubuntu + xfce = xubuntu. I have the option to choose what system I want to load up before I enter my password. I have loaded the xubuntu into my new computer but it is only giving me the option of xubuntu or xfce on the drop down bar below the password. I have tried to download different ISO's but they are all the same. I'm looking xubuntu 13.04 with the option of the three different ISO's. Can anyone help me please? ):P

---

### Post by Gotti on 2013-02-02
Xubuntu is Ubuntu with XFCE installed rather then Gnome. If you want to use gnome, just install ubuntu. If you want to try different window managers, most can be installed through the repositories. (For example, I use fluxbox, which can be installed using the command "sudo apt-get install fluxbox.") After installing a new window manager, it should be in the list along with Xubuntu and XFCE.

Afterthought - Xubuntu and XFCE are essentially going to be the same thing. IIRC Xubuntu is just XFCE with some ubuntu-esque modifications made.

I'd give this site a looksee: [http://xwinman.org/](http://xwinman.org/)

And for future reference, hit the "New Post" button to make a new thread. Hijacking other threads not only will annoy the OP, but will make it harder for your issue to be resolved.

---

### Post by thorbs on 2013-02-02
My box is a t61 with 3gb ram.

I installed Okular and it works like a charm. When I try the same pdfs with document viewer they are pretty much unusable. 

Unless there is something I missed the document viewer program, is really not worthy of an official release.


t.

---

### Post by andrew.46 on 2013-02-20
There is always Xpdf which is *very* basic but usable on low end machines....

---

