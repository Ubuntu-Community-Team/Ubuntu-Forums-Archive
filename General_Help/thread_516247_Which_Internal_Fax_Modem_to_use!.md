---
title: "Which Internal Fax Modem to use!"
date: 2007-08-02
forum: General Help
---

### Post by Chilongola on 2007-08-02
Looking for a straight up answer.  Which fax modem "really" works in Ubuntu 7.04

---

### Post by Chilongola on 2007-08-03
I sent an e-mail to the folks at Nexxt ref their Agere modem:

Hi, I bought one of your Data Fax modems.  I am an  Linux user - 
Ubuntu.  The cd brings some Linux drivers but none work on ubuntu.  Or 
am I doing something that may be wrong.

Tks for any help you can offer.


THERE REPLY:

Sorry, our PCI modem card does not support Linux Ubuntu OS, 
But, it supports to following Linux OS.
1.       Linux RedHat 8.0
2.       Linux RedHat 9.0
3.       Linux Mandrake 10.1
4.       Linux Fedora 3.0
5.       Linux Fedora 4.0
6.       Linux SuSe 9.1
7.       Linux Suse 9.2

The files on the cd are as recent as June 2006???????????? So....

---

### Post by Chilongola on 2007-08-04
Will this modem work in Ubuntu???

[http://www.wholesalepdas.com/browseproducts/HP---Aztech-V.92-USB-e-modem-NEW-P-N-5065-2509-UM9100-U-56K-Travel-Modem.HTML](http://www.wholesalepdas.com/browseproducts/HP---Aztech-V.92-USB-e-modem-NEW-P-N-5065-2509-UM9100-U-56K-Travel-Modem.HTML)

---

### Post by Chilongola on 2007-08-04
**UBUNTU 7.04**

Modem is a Pctel 789

I used this set of drivers:   pctel-0.9.7-9-rht-7.tar.gz

tar zxvf pctel-0.9.7-9-rht-7.tar.gz

Ran lspci  and got things like this:
root@zzzzzzzz:/home/xxxxx# lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0d.0 Display controller [0303]: PCTel Inc HSP MicroModem 56 (rev 02)

cd pctel/

./setup

and got this:

checking for running kernel version...2.6.20
checking for ptserial...ptserial-2.6.c
checking for gcc...4.1.2
checking for kernel gcc version...4.1.2
searching for kernel includes...found at /lib/modules/2.6.20-16-generic/build/include
checking for autoconf.h.../lib/modules/2.6.20-16-generic/build/include/linux/autoconf.h
checking for asm/mach-default...yes
checking for kernel version in utsrelease.h...UTS_RELEASE is 2.6.20-16-generic
checking type of tty_struct.count...int
checking for presence of udev...present (kernel version 2.6.13 or later)
detecting your modem...found. Your modem is a pct789 type modem.

compilation done

installation done

modem activated:guitar:

GNOME PPP  dected this ttyS_PCTEL0  (zero)

In eFax I now have: - ttyS_PCTEL0 as the modem.

System asked me to reboot so I did.  Prepared a sample text to fax.

I now get this after  trying twice.....:( 

Print job received on socket
efax-0.9a: 17:05:35 opened /dev/ttyS_PCTEL0
efax-0.9a: 17:05:37 using PCtel HSP56 MicroModem Linux Driver K2.4.7.V92.001 (03/26/2003) in class 1
efax-0.9a: 17:05:37 dialing T223-0576
efax-0.9a: 17:07:37[COLOR="Red"] Error: dial command failed[/COLOR]
efax-0.9a: 17:07:37 failed page /home/anselm/efax-gtk-server/efax-gtk-server-WixOyx.001
efax-0.9a: 17:07:37 finished - unrecoverable error


Print job received on socket
efax-0.9a: 17:08:22 opened /dev/ttyS_PCTEL0
efax-0.9a: 17:08:24 using PCtel HSP56 MicroModem Linux Driver K2.4.7.V92.001 (03/26/2003) in class 1
efax-0.9a: 17:08:24 dialing T2230576
efax-0.9a: 17:10:24 [COLOR="Red"]Error: dial command failed[/COLOR]
efax-0.9a: 17:10:24 failed page /home/anselm/efax-gtk-server/efax-gtk-server-S1C09Z.001
efax-0.9a: 17:10:24 finished - unrecoverable error:mad:

I normally do not give up on things but truly this time I will take a break...   Unless someone can come  to my aid quickly and point out what is wrong.

---

### Post by Bartender on 2007-08-05
Don't know if I can help you out or not.  Have seen very very few posts regarding faxes in Linux.

What happens if you set aside the faxing part?  Can you just get online?

And the phone # you asked your modem to dial...what's with the "T" at the beginning?  All I've ever seen are numbers.  Speaking of which, go back in to wvdial or ppp-config or whatever you used and remove the dash between 223 & 0576.  Lots of people have said leave the dashes out.
I have tried using a comma, the star sign, and a space for call-waiting (*70, 5551212) and was able to connect but dashes are a no-no.

---

### Post by OzzyFrank on 2007-08-05
I would suggest contacting all the companies that make them (or USB ones if you have to resort to that). Even if someone recommended one, I really would contact the company to make sure they support Ubuntu. I've seen too much of companies who tell you after you've bought that "yes, we support Linux, but not Ubuntu".

Otherwise, get a serial modem like I did. Then use **wvdialconf** to detect the modem, edit the **wvial.conf** file it generates to include phone#, username and password, then after that all you do is run **wvdial** for a hassle-free connection each time!!

---

### Post by Chilongola on 2007-08-09
Sorry about late reply!  Bartender and OzzyFrank


Yes I did note that one does not use the "-" in numbers.  Also keep noticing the "t" appearing in error notice. 

For a while yet I do need to fax documents.  I normally use my scanner and e-mail documents but my scanner is a Prima Scan 2400.  Parallel connection.  That will not work in Ubuntu.

I have read so many threads elsewhere in whcih folkjs swear they get their pctel's and agere's to work but no dice here.

OzzyFrank mind letting me know which serial modem u purchased??  Thanks.

Cheers all.

---

### Post by jkdub on 2007-08-09
Hello,

I've never been able to get a pci modem to work. So I use external modems too.

I have two brands that work with every linux I've tried. One is an Actiontec USB/Serial modem, the other is a Trendnet TFM 560X Serial modem. The Actiontec even works hooked to the USB in Ubuntu and Knoppix (the only 2 I've tried USB with).

These are the cheapest external modems I could find but I've had them for a couple years now and both work very well.

---

### Post by OzzyFrank on 2007-08-10
Hey dude, I think you can use ANY serial modem, as they are all "hardware" modems that don't require software to function (like newer ones in Windoze). As jkdub says, you can even get USB/serial ones to work (I gather these are actual serial/hardware modems that allow you to connect via a USB port, in case you don't have a serial port, etc... feel free to correct me if I am wrong, but I think this must be the case, as your usual USB modem is a Wintel/software modem).

As for mine, well it does have a brand name on it, though doesn't show up anywhere: SwannSmart V.90 56k External Voice Modem... i think it is Australian, but have never found actual drivers (in Win of course) or the company online, but in Windows got it to work with generic drivers (took a few goes!) and in Ubuntu JUST WORKED!

I suggest you get a cheap 2nd hand one off eBay! should be able to get one for $30 delivered, or less if you're lucky... I've heard of new ones going well over $100, which seemed absurd in this modern era... till I realised they were targeting desperate Linux users, hehe. But Windows users are getting rid of serial modems for smaller USB ones, just for space, and of course there are the rest who are going broadband.

When you get one, go into** /etc**, double-click **wvdialconf**. I couldn't get any of the other apps people suggested to recognise my modem, and thought this had failed too, till I realised I hadn't plugged it back in properly after checking it repeatedly (so make sure you plug it in properly! hehe). As mentioned earlier, then all you need to do is edit 3 lines in the **wvdial.conf** file that is generated, then run **wvdial** to connect instantly (make a launcher for it on your panel for one-click access).

Cheers

---

### Post by Talon2 on 2007-08-10
I'll post a few links:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16825104004](http://www.newegg.com/Product/Product.aspx?Item=N82E16825104004)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16825104135](http://www.newegg.com/Product/Product.aspx?Item=N82E16825104135)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16825134002](http://www.newegg.com/Product/Product.aspx?Item=N82E16825134002)

Hopefully that will get you going.  There are plenty of modems that work with Ubuntu.  I would definately recommend you stay away from WinModems and USBModems if you want a relaxed pleasant life though.

Good luck.

---

### Post by Chilongola on 2007-08-11
Thanks, buddies.  I do not live in the USA.  I am in Belize, Cen.  America.   All serial modems have "disappeared".  I have a USB UM9100-U  that came with an HP computer.  Ubuntu recognizes it but just cannt get it to work either.  I got farther with the pctel.  Funny thing is that there folks who swear their's work!!!!   Coupled with "dogged" determination I do not want this to beat me.  A relative should be back here in a couple of weeks From Miami.  He promised to get a "good" serial modem. I gave him references jkdub gave above.   In the meantime I go on.  But for now going fishing for the weekend.  Wish you all could join in... Tks again.

---

### Post by davidsrsb on 2007-08-11
I still see Aztech externals around here in malaysia. maybe time to buy a couple???

Internals certainly mean at least compiling kernel modules. Many are now badly supported - I have a couple of pegasys chipset units which use Smlink. This company modem business was sold to Conexant, who refuse to support end users at all.

Many PCs don't have a com port now. if you get a usb-serial cable, make sure that ity uses the supported pl2303 chip. Avoid Hugepine like the plague.

---

### Post by Chilongola on 2007-08-27
Ok Ibought an external modem "cNet"  CN5614Xr.  So I just set it up and it should work.  Or do I need to run something.  In the hardware listing it tells me it is in /dev/TTYS0.

---

### Post by utnubuuser on 2007-08-27
Hello -- I'm trying to find out if anyone is on at the moment who might be able to re-boot from recovery screen? What code do I enter?  (Feisty)

---

### Post by Chilongola on 2007-08-27
Sorry, cannot help u there
Cheers

---

### Post by OzzyFrank on 2007-08-27
If you're trying to get the modem going, I gave directions twice in this post. Cheers

---

### Post by Chilongola on 2007-08-27
Tks for the reminder OzzyFrank.  It dials, now to send a fax....!!!  Later.

---

### Post by Chilongola on 2007-08-29
Fax worked !!!!

Text typed in Open Office then sent to Fax: To an old regular fax machine

Socket running on port 9900
Print job received on socket
efax-0.9a: 23:32:33 opened /dev/ttyS0
efax-0.9a: 23:32:35 using P2109-V90CONEXANTV90 in class 2
efax-0.9a: 23:32:35 dialing T22305XX
efax-0.9a: 23:32:48 The remote ID is  "       50101122XX5XX"
efax-0.9a: 23:32:48 connected
efax-0.9a: 23:32:54 session 196lpi  9600bps 8.5"/215mm  any   1D    -     -  10ms
efax-0.9a: 23:32:54 header:[2007-08-28 23:32    XXXXXX (22X 1XXX) --> 223XXXX      1/1]
efax-0.9a: 23:33:25 sent 20+2292 lines and 9480+20177 bytes, in 31 secs at 7653 bps
efax-0.9a: 23:33:30 sent page /home/xxxxxx/efax-gtk-server/efax-gtk-server-vt7b07.001
efax-0.9a: 23:33:30 finished - success

Do not understand why area code appears before int'l access code"011"!!!!

From Open Office also to my hp all in one at work:

Socket running on port 9900
Print job received on socket
efax-0.9a: 23:44:28 opened /dev/ttyS0
efax-0.9a: 23:44:29 using P2109-V90CONEXANTV90 in class 2
efax-0.9a: 23:44:29 dialing T22xxxxx
efax-0.9a: 23:45:10 The remote ID is  "        501 223 7xxx"
efax-0.9a: 23:45:10 connected
efax-0.9a: 23:45:18 session 196lpi 14.4kbps 8.5"/215mm  any   1D    -     -  0ms
efax-0.9a: 23:45:18 header:[2007-08-28 23:44    ANSELM (2xx 1xxx) --> 22xxxxx      1/1]
efax-0.9a: 23:45:24 sent 20+2292 lines and 9777+0 bytes, in 6 secs at 13036 bps
efax-0.9a: 23:45:29 sent page /home/xxxxxx/efax-gtk-server/efax-gtk-server-024cEp.001
efax-0.9a: 23:45:29 finished - success

Remote ID was different when sent to another number within same area.??

But it worked!!!

Off course it went thru efax-gtx.  I still cannot send anything with GFAX but suffice...

---

