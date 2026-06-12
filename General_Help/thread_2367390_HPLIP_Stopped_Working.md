---
title: "HPLIP Stopped Working"
date: 2017-07-29
forum: General Help
---

### Post by Quarkrad on 2017-07-29
I have two machines, both running 16.04 (Mate) and fully up to date.  They connect to a wireless printer independently (what I mean by this is they are not on a LAN).  All has been well with said printer since 12.04, when I think I bought the printer and various iterations of hplip. As the printer is the common link I have reset it both via the wireless wizard and configuring it with a static ip (static ip is the normal set up).  I have tried various versions of hplip on both machines and for some reason I am getting the same issue on both machines no matter what version of hplip I use.  I configure the printer via either the GUI or command during the hplip set-up phase and the printer is recognised, I can print to it and scan a doc - all is well.   When I reboot and look in HP Device Manager I see the printer then after about 3 or 4 seconds a red X appears and I get a Desktop notification of a communication error (printer.png).  Googling this error points to a hplip bug dating back to 2012/13 but nothing recent - this has only started happening to me today(?). I have uninstalled and reinstalled a number of times using either HPLIP or ubuntu's Control Centre/Printers to setup the printer (actually, even cups) but all result in the same issue.  Everything works first time but not on reboot.  Printer2.png shows the relevant output from **hp-doctor** - there are some underlying issues but why suddenly today? (I have changed permissions of the ppd file from root to myself but it makes no difference).  Any help appreciated - wife cannot print!

---

### Post by vocx on 2017-07-29
> **Quarkrad said:**
> I have two machines, both running 16.04 (Mate) and fully up to date.  They connect to a wireless printer independently **(what I mean by this is they are not on a LAN).**  All has been well with said printer since 12.04, when I think I bought the printer and various iterations of hplip. As the printer is the common link I have reset it both via the wireless wizard and configuring it with a static ip (static ip is the normal set up).  I have tried various versions of hplip on both machines and for some reason I am getting the same issue on both machines no matter what version of hplip I use.  I configure the printer via either the GUI or command during the hplip set-up phase and the printer is recognised, I can print to it and scan a doc - all is well.   When I reboot and look in HP Device Manager I see the printer then after about 3 or 4 seconds a red X appears and I get a Desktop notification of a communication error (printer.png).  Googling this error points to a hplip bug dating back to 2012/13 but nothing recent - this has only started happening to me today(?). I have uninstalled and reinstalled a number of times using either HPLIP or ubuntu's Control Centre/Printers to setup the printer (actually, even cups) but all result in the same issue.  Everything works first time but not on reboot.  Printer2.png shows the relevant output from **hp-doctor** - there are some underlying issues but why suddenly today? (I have changed permissions of the ppd file from root to myself but it makes no difference).  Any help appreciated - wife cannot print!
I had a couple of issues in the past where the red X in the HP GUI manager would show. I did not do anything special to solve it, just turn on and off the printer, reinstall with "hp-setup", use a different static IP, etc. I honestly think sometimes wireless networks tend to act in strange ways, and suddenly they work again without problem. It's puzzling.

What I find strange is that they "connect independently". How is that? Also, why are they not in a LAN? Don't you use a router for your Wifi Internet? I think that using a router would improve the connectivity with the printer, because the router would be responsible dealing with the name and address resolving and so on, of all machines.

---

### Post by Quarkrad on 2017-07-30
Apologies, I didn't want to get into too much detail re my set-up (having two PCs).  The PCs are under my desk and share the same monitor/ketboard via a kvm switch, each pc is hard wired to my router.  Hence, the wireless printer is connected to each PC via my router as you suggest.  Perhaps I should not have mentioned having two PC's but it is odd the same fault is appearing (identically) on both PCs.  I will try and configure the printer to have a different ip address and see if that makes a difference. Although I think(?) in theory it should make no difference.

---

### Post by Quarkrad on 2017-07-30
Hmm.. think I have sorted it - changed the printer ip address from 192.168.1.2 to 192.168.1.160.  The default gateway address is 192.168.1.1 so I guess the old printer address was too close. Surely, in theory I can have any address(?) - anyway, appears to be rock solid now.

---

### Post by vocx on 2017-07-30
> **Quarkrad said:**
> Hmm.. think I have sorted it - changed the printer ip address from 192.168.1.2 to 192.168.1.160.  The default gateway address is 192.168.1.1 so I guess the old printer address was too close. Surely, in theory I can have any address(?) - anyway, appears to be rock solid now.
That's what I mean about networking being sometimes tricky. Yes, in theory it should work with any address. Why should 192.168.1.160 work better than 192.168.1.2? There is no reason. They should work the same. However, sometimes just resetting the router, unplugging and plugging back the cable, or things like that, just make it work again perfectly.

Some people say, "naaa, networking works perfectly 99% of the time", and I agree, but sometimes you have random errors caused by electromagnetic interference, cosmic rays, and God, and you really cannot explain these.

And yes, your description of the network is confusing. Everything connected to the same router, either with a wired cable, or a wireless connection, is in the same local area network (LAN).

---

### Post by deadflowr on 2017-07-30
> **Quarkrad said:**
> Hmm.. think I have sorted it - changed the printer ip address from 192.168.1.2 to 192.168.1.160.  The default gateway address is 192.168.1.1 so I guess the old printer address was too close. Surely, in theory I can have any address(?) - anyway, appears to be rock solid now.

Typically routers have a set default dhcp LAN address range, depending on the router it could be anywhere from 192.168.1.50 to usually 192.168.1.250 or so.
Your devices would need to be within this range in order to be seen properly within the LAN.
You can usually see the set range by logging into the router's home page from any local web browser.
Just look for LAN settings and inside that setting should tell of a range.

Some routers, or most, have the ability to change the range or set a range or specific addresses which works best for you or your needs.
But this takes a basic understanding of how networking works.

---

