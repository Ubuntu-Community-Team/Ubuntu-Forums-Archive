---
title: "Networking Or Wireless"
date: 2007-03-21
forum: General Help
---

### Post by mouseboyx on 2007-03-21
Are there any personaly known cards wireless or networking to automaticaly work with ubuntu 6.10 and if so which one would be the best?

---

### Post by DapperMe17 on 2007-03-21
I've had automatic, out-of-the-box success with a Belkin F5D7000 v5 PCI card, as well as a Linksys WUSB54G V4 USB adapter.

Both work like a charm.


WPA encryption will require some futzing with NDISwrapper & the original drivers, but will work perfectly with some time & effort on both of these cards.

---

### Post by mouseboyx on 2007-03-21
im actualy using a Belkin F5D7000 pci card but i dont know which version it is.

---

### Post by DapperMe17 on 2007-03-21
I'm very surprised it's not working for you, although Linux can be very picky with the version#, because of the different chipset makers for one model card.

With v5, all I needed to do was enable wireless & add the network name in the network menu of Ubuntu & whaaaalllaaa.


If you're running an older PC, say 6+ years old, sometimes the motherboards will not acknowledge "G" PCI cards. I ran into that issue with an older HP, which would only accept "B" cards. In that case, I went to the WUSB54G & it worked like a charm. There have been no disconnects or any issues at all with the USB adapter. If you're running a USB 1.1 card, off course  you're internet speed will be 1/2 of normal. It's nothing a new USB 2.0 card can't solve. But, I tried a Zonet card & it caused my Ubuntu 6.10 to be slooooooow. Not knowing if it was a motherboard issue, or USB 2.0 issue with Ubuntu, I just left it attached to the USB 1.1 card. It's not a problem if you run the faster DSL or cable.

Ubuntu edgy 6.10 is pretty good at detection.

Don't get discouraged as I was a Linux noobie once too. Stick with it, you'll never look back to Windows.

---

### Post by gm333tb on 2007-03-22
Hello.  First post.  Had enough with windows.  I'm determined to learn Linux as well or better than I know windows.  Just installed ubuntu 6.10 on my pc.  Installed a Linksys WMP54G wireless PCI adapter in the PC after Linux was installed.  Tried to use the Linksys install CD but Linux can't run it.  I've tried to use the network settings with no luck.  Can anyone give me some help?  Any and all input is appreciated.

GM

---

