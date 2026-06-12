---
title: "Dell C1765nfw network printer under Linux"
date: 2013-08-16
forum: General Help
---

### Post by estratos2 on 2013-08-16
I purchased a Dell C1765nfw network printer some days ago thinking that its support from CUPS should be straightforward. I was obviously wrong and now I find myself unable to locate a valid driver fro Linux.

Anyone able to bring some good news? Thanks!

---

### Post by beatljuice on 2013-08-23
I would love an answer to this also.

---

### Post by estratos2 on 2013-08-27
I found [this post]("http://www.fixya.com/support/r14214253-as_linux_driver_dell_1355cnw_one_xerox"), which is related to the 1355cnw printer but it's worth trying. My printer is now boxed and waiting for a replacement since printing from an USB stick is not working either. (my printer is unable to recognize any pdf).

---

### Post by lokmij on 2013-09-02
I got mine to work via wireless, buy using the Dell 1355 Foomatic/foo2hbpl2 driver.  After that go into your printer preferences and change color mode to "color"  and bam!  it supported it :)

I did this under Mint KDE but I assume its the same for other distros :)

---

### Post by changeableface on 2014-01-09
Can confirm using Dell 1355 driver works on Ubuntu 13.10. :)

---

### Post by nilandsplace on 2014-11-24
There is a Ubuntu printer driver that will work. I have my Dell C1765nfw set to use Dell 1355 Foomatic/foo2hbpl2 (recommended). mine is a hard wired network, so the URI is set to socket://192.168.0.7:9100. The operative part is the socket:// and the port :9100. you can change the IP to whatever you need. since I am on a router I have set a dedicated IP for the printer. How To do this depends on your router. mine is a modem/router tg862G from TWC and I set the DHCP and the printer to the same IP. If you do not set a dedicated IP you will have to change the Printer IP all the time. Or at least every time the router changes your IP
For the printer IP press the menu button then select system >> admin >> network >> TCP/IP >> IPv4 >> select "get IP address panel" and set your IP and subnet mask (255.255.255.0) on the same screen. the final step is to turn off the printer and back on to set your settings. One last thing the driver is foo2zjs.tar.gz and support files. For synaptic just search for printer foo. You will need the DB files to. the only thing available in the Ubuntu Software center is the Foomatic GUI
James Niland
[http://nilandsplace.com](http://nilandsplace.com)

---

### Post by cfuser on 2014-12-09
Is there any joy in getting the scanner to work?

---

