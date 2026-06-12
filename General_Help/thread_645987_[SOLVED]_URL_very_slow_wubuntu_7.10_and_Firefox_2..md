---
title: "[SOLVED] URL very slow w/ubuntu 7.10 and Firefox 2.0"
date: 2007-12-20
forum: General Help
---

### Post by JackS on 2007-12-20
Windows loads this web page quickly and ubuntu loads it VERY slowly.
Acually, this URL runs so slowly on my ubuntu that it is not useful:
[http://lgb.webtrak-lochard.com/introduction.html](http://lgb.webtrak-lochard.com/introduction.html)

I need speed.  Does anyone have any advice?
What am I missing in my linux configuration?


Here's my hardware and software:
$ uname -a
Linux sunbus-desktop 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux

Here's a little bit about my Firefox 2.0 application:
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.11) Gecko/20071204 Ubuntu/7.10 (gutsy) Firefox/2.0.0.11

I have installed the Adobe SVG plugin, from here:
[http://www.adobe.com/svg/viewer/install/main.html](http://www.adobe.com/svg/viewer/install/main.html)
[http://download.adobe.com/pub/adobe/magic/svgviewer/linux/3.x/3.01x88/en/adobesvg-3.01x88-linux-i386.tar.gz](http://download.adobe.com/pub/adobe/magic/svgviewer/linux/3.x/3.01x88/en/adobesvg-3.01x88-linux-i386.tar.gz)

And it passes this test:
[http://www.adobe.com/svg/viewer/install/svgtest.html](http://www.adobe.com/svg/viewer/install/svgtest.html)


I'd love to learn what I need to fix here.  Don't want to use Windows.
Thanks,

-Jack

---

### Post by jayson.rowe on 2007-12-20
It could be your DNS settings - try this:
1. Open a terminal window and type the following.

$ sudo network-admin

Note: Root access is required for this step.
2. Change to the DNS tab and enter the following two addresses in the top of the first field labeled DNS Servers.

208.67.222.222
208.67.220.220

To avoid having your settings get revoked after reboots, or after periods of inactivity, do this:

$ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
$ sudo gedit /etc/dhcp3/dhclient.conf
# append the following line to the document
prepend domain-name-servers 208.67.222.222,208.67.220.220;
# save and exit
$ sudo ifdown eth0 && sudo ifup eth0

You may be required to change eth0 to your own network device's name if it uses a non-standard name.

---

### Post by JackS on 2007-12-20
Tried the DNS addresses you recommended.
Sadly, that URL is just as impossibly slow as before.

These old DNS addresses too. Slow as molasses in...you know.
151.164.1.8
206.13.28.12

Going back to the original DNS I had been using earlier today.
My ISP recommends
68.94.156.1
68.94.157.1

Thanks for your reply.
-Jack

---

### Post by jayson.rowe on 2007-12-20
Jack,
Sorry that didn't work for you - perhaps someone else can chime in with another suggestion.

---

### Post by JackS on 2007-12-22
Opera installation was dirt simple.  I was up and running in
minutes.  Opera solved the problem.   Opera seems to have
implemented the SVG differently than Mozilla/FFox.
[http://www.opera.com/](http://www.opera.com/)

Thank  you

---

