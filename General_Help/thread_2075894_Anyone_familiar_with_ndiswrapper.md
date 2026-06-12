---
title: "Anyone familiar with ndiswrapper?"
date: 2012-10-24
forum: General Help
---

### Post by Laize on 2012-10-24
I seem to be having problems getting it to work.

I've installed, what I believe to be, the proper drivers (bcmwl5 for pciid 14e4:4329).

The problem is that when I go to activate ndiswrapper ($ sudo modprobe ndiswrapper) the terminal will hang until I Ctrl+C.

ndiswrapper is pretty much my last opportunity to get this NIC working without having to buy a new one.  Any help would be appreciated.

---

### Post by angry_johnnie on 2012-10-24
Try installing ndisgtk and using that to load your driver instead.

That particular card, however, seems to be quite troublesome for many.

---

### Post by Laize on 2012-10-25
> **angry_johnnie said:**
> Try installing ndisgtk and using that to load your driver instead.

That particular card, however, seems to be quite troublesome for many.

Using ndisgtk produces the same result.

A hang in the terminal will hang using the GUI just the same.

---

### Post by plucky on 2012-10-25
After I upgraded to 12.04,I had to install ndiswrapper-dkms to get it working again for a Netgear pcmcia card with the windows driver.

There is a bug report about this,but I cannot find it at the moment.

Use a wired connection to install ndiswrapper-dkms.

Good Luck

[Bug Report](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/986064)

---

### Post by Laize on 2012-10-25
> **plucky said:**
> After I upgraded to 12.04,I had to install ndiswrapper-dkms to get it working again for a Netgear pcmcia card with the windows driver.

There is a bug report about this,but I cannot find it at the moment.

Use a wired connection to install ndiswrapper-dkms.

Good Luck

I'll give that a shot but I wasn't getting any dependency errors regarding ndiswrapper-dkms.

---

