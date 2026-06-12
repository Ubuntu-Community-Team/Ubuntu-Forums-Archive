---
title: "Recommended Modems?"
date: 2005-11-02
forum: General Help
---

### Post by bobthebiscuit on 2005-11-02
I'm having trouble with an Intel537 winmodem, and in case that bugger refuses to install, what are some recommended, relatively inexpensive modems?

Specifically, what could I buy that Ubuntu would just "get"? I'd love to hear your success story... or, you cuold help me get the Intel working.

Thanks!

---

### Post by zenwhen on 2005-11-02
[http://www.usr.com/support/product-template.asp?prod=5610b](http://www.usr.com/support/product-template.asp?prod=5610b)

This one works perfectly, and is supported in the kernel. This is true because it is a real modem and not a Winmodem.

---

### Post by az on 2005-11-02
If you can install gcc-3.4 linux-headers-2.6.12-9-386 and build-essential, you can try compiling the sl-modem-source (from multiverse).  The smartlink driver often supports intel chipsets.

---

### Post by trash on 2005-11-02
[QUOTE=zenwhen][http://www.usr.com/support/product-template.asp?prod=5610b](http://www.usr.com/support/product-template.asp?prod=5610b)

This one works perfectly, and is supported in the kernel. This is true because it is a real modem and not a Winmodem.[/QUOTE]

Personally i'd never buy another USR modem, I have 3-4 upgradable externals that they will no longer supply the upgrades for. Their reply email was 'buy a new one if you want 56k', which is rediculous since the word upgradable is marked on the modem.

---

### Post by bobthebiscuit on 2005-11-03
neither the smartlink drivers nor the intel drivers resulted in a successful install of the Intel modem. I might be doing something wrong, but I need some help going through those error messages to make sense of it...

and the USR 5610 doesn't seem to be a currently sold product; in fact, there seems to be one heck of a shortage of newer, less expensive hardmodems (the cheapest retail price I found was $80!).

---

### Post by bobthebiscuit on 2005-11-04
Actually, I found an inexpensive OEM version of the USR 5610 at NewEgg: [http://www.newegg.com/Product/Product.asp?Item=N82E16825104119](http://www.newegg.com/Product/Product.asp?Item=N82E16825104119)


Googling info on the modem shows it should be reliable, it's a hardware modem, and since I just need it for faxing, this should work.

The Intel537EP **never** worked. That was several hours of work wasted.


So it seems that hardware modems are still the best bet for Linux, though it sure would be nice if (a) more hardware modem choices were available, and (b) manufacturers of softmodems would open up to the Linux community better (those Intel Linux drivers? psh. forget it.).

---

### Post by SickTwist on 2005-11-04
I think all external serial port modems are a safe bet. You may be able to find a used one for a good price at a local computer parts dealer.

I'm not sure about external USB modems.

---

### Post by Lab on 2005-11-04
[QUOTE=bobthebiscuit]So it seems that hardware modems are still the best bet for Linux, though it sure would be nice if (a) more hardware modem choices were available, and (b) manufacturers of softmodems would open up to the Linux community better (those Intel Linux drivers? psh. forget it.).[/QUOTE]

People have been hoping that these horrible manufacturers of windmodems would actually provide drivers for their products for years now. Don't hold your breath ](*,)

---

### Post by bobthebiscuit on 2008-04-29
Old thread... surprising how long it's been since I built the computer I originally came here for. For anyone wondering, this Hylafax-based Ubuntu Fax Server computer has been running flawlessly with an OEM version of the USR Performance Pro modem... no surprise, since it is an actual, controller-based modem.

BUT!

I am building the successor to that fax server (for backup and upgrade reasons), and have found an even more cost-friendly modem recently released:
Zoom 3095 V.92 USB Mini External ( [http://www.zoom.com/products/dial_up_external_usb.html](http://www.zoom.com/products/dial_up_external_usb.html) )

Winmodems just aren't getting the support they need to make Linux truly viable in predominantly-dialup areas, so it's good to see modems like these coming out... it might cost a little more than a softmodem that MIGHT eventually work, BUT it'd be worth it for people not looking for a hassle.

I share only because I want manufacturers to see the demand for fully-functioning modems in non-Windows applications... also, I'll post the results of my installation.

---

