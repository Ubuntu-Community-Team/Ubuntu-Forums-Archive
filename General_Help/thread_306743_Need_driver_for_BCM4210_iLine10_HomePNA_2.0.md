---
title: "Need driver for BCM4210 iLine10 HomePNA 2.0"
date: 2006-11-25
forum: General Help
---

### Post by Lord Elliott on 2006-11-25
I'm trying to find a driver for the Broadcom "BCM4210 iLine10 HomePNA 2.0". It is a pci card for connecting to a network via your phone lines. I think that's how it works at least. It all goes to a router and a DSL line. It's a few years old or more, so it's not even listed on Broadcom's site anymore. If I can't get a Linux driver for this, then there's no way I'll be able to connect to the internet on that OS. I tried looking for it myself with google, but I just got a bunch of useless references to some sort of "pciids" project list, which didn't help. I'm new to Linux, so I'm hopeing someone else who is more familar with it will know where to find old drivers like this one, if it even exists.

-Lord Elliott

---

### Post by ReaderRat on 2006-11-25
See if anything [**[color=red]HERE[/color]**](https://wiki.ubuntu.com/FindPage?action=fullsearch&titlesearch=1&value=network) helps.


EDIT: BTW, it's considered uncool to double-post a thread.

---

### Post by Lord Elliott on 2006-11-26
Thanks, that did help some. I found a beta driver from Linksys on [http://en.opensuse.org/Wishlist_Drivers](http://en.opensuse.org/Wishlist_Drivers).

linux_hpna2_0_v2_34_0_2.exe
Listed as "Broadcom HPNA Hybrid Driver from Linksys"

Then I found a page on YA-Faq that had some explanation and many helpful links on it.

[http://ccfaq.valar.co.uk/modules.php?name=News&file=article&sid=199](http://ccfaq.valar.co.uk/modules.php?name=News&file=article&sid=199)

I just have one problem still. When I double click on the exe file to install the driver, an error pops up that says:

Error: no suitable application

Cannot open /home/lordelliott/Desktop/linux_full_binary_2_33.exe: No application suitable for automatic installation is available for handling this kind of file.

Am I missing something? (probably)

EDIT: Sorry about double posting. Won't do it again.

---

### Post by ReaderRat on 2006-11-27
a ".exe" file is a Windoze exectuable file (binary), and is not an exectuable in Linux. You need a Linux executable (.bin) or package (.deb) to install. Sorry, I cannot help more, never had this problem....

---

