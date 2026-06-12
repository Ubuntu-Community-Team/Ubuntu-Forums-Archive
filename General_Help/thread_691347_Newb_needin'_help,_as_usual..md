---
title: "Newb needin' help, as usual."
date: 2008-02-08
forum: General Help
---

### Post by Atlas84 on 2008-02-08
I(first time linux user) just recently installed ubuntu 7.10 on my PC the other day and I'm having some problems. My PC is a HP Pavilion A1250n and here is a link to my PC specs: 

[http://shopper.cnet.com/desktops/hp-pavilion-a1250n-athlon/4014-3118_9-31533898.html?info=specs#more-info](http://shopper.cnet.com/desktops/hp-pavilion-a1250n-athlon/4014-3118_9-31533898.html?info=specs#more-info)

The first thing I am having problems with is getting on the internet. I cannot get ubuntu to work with my intergrated ethernet network adapter. I have only been able to get from the point where FireFox tells me that I am unable to load the page IMMEDIATLY, to the point where it thinks about finding the site for a few minutes. 

I have entered my IP, DNS, Gateway, and Netmask, but that doesnt work, so, I'm at a loss.

Now, when it comes to my wireless card(DWA-552), it doesn't even see it.

The second problem I have is that ubuntu will not let me use the restricted driver for my video card. It is a GeForce 5600 or 6600, cant remember off the top of my head. It sees it, but wont let me use it.

Any help would be appreciated! Thanks!

P.S. Been looking through several forums for several days and I have found nothing that helps so far.

---

### Post by nemilar on 2008-02-08
Can you please post the output of the command:
```
lspci | grep -i net
```

---

### Post by Atlas84 on 2008-02-08
I will as soon as I get home from work here in 4hrs.

---

### Post by forrestcupp on 2008-02-08
According to your link, your video is an ATI Radeon Xpress X200.  If that's true, you were way off.  If you can't get the RDM to work for your video card, you could try [Envy](http://albertomilone.com/nvidia_scripts1.html).  It will automatically install the latest ATI proprietary drivers from their web site, which are much better than the ones that the restricted drivers manager have.  I checked and the latest ATI fglrx drivers do support the Radeon Xpress X200.

But that doesn't do you much good if you can't connect to the internet with it.

---

### Post by Atlas84 on 2008-02-08
> **forrestcupp said:**
> According to your link, your video is an ATI Radeon Xpress X200.  If that's true, you were way off.  If you can't get the RDM to work for your video card, you could try [Envy](http://albertomilone.com/nvidia_scripts1.html).  It will automatically install the latest ATI proprietary drivers from their web site, which are much better than the ones that the restricted drivers manager have.  I checked and the latest ATI fglrx drivers do support the Radeon Xpress X200.

But that doesn't do you much good if you can't connect to the internet with it.

I also installed a video card in my pc so I wouldnt have to run my monitor off of my integrated video card. The one I have installed is a nvidia geforce 5600 or 6600.

---

### Post by Atlas84 on 2008-02-08
> **nemilar said:**
> Can you please post the output of the command:
```
lspci | grep -i net
```

This is what I got:

Code:
lspci | grep -i net


02:00.0 Network controller: Atheros Communications, Inc. AR5416 802.11a/b/g/n Wireless PCI Adapter (rev 01)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


Edit: 
Ohh, and my video card is the Nvidia GeForce 6600.

---

