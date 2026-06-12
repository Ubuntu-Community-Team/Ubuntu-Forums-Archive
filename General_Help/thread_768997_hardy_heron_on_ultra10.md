---
title: "hardy heron on ultra10"
date: 2008-04-26
forum: General Help
---

### Post by howlingmadhowie on 2008-04-26
well, i tried to install hardy on an ultra10 today and it's taken most of the day and i'm still not quite finished.

problem:
with elite3d card the live cd wouldn't boot. 
solution:
remove elite3d card and use onboard graphic

problem:
installation fails. silo didn't install
solution:
edit silo.conf by hand and regenerate the initrd image

problem:
services weren't being started
solution:
cp /usr/sbin/start-stop-daemon.REAL to /usr/sbin/start-stop-daemon

problem:
creator3d or elite3d card not being recognised
solution:
download firmware from sun (patch id 112620-10) and install afb.ucode using afbinit


i found a creator3d card lying around, but for some reason, my sun tft monitor doesn't react to it. looks like i'll have to switch the computer off and try the elite3d.

---

### Post by singler on 2008-04-28
May I ask where you have found Hardy Heron for Sparc. I cannot find it anywhere. However, I successfully installed 7.10 on a Sun T5120.

---

### Post by larry80 on 2008-04-29
> **singler said:**
> May I ask where you have found Hardy Heron for Sparc. I cannot find it anywhere. However, I successfully installed 7.10 on a Sun T5120.

I got a old Netra I uppgraded this morning.

I did an apt-get update/upgrade and a new update-manager-core was there :)

---

### Post by howlingmadhowie on 2008-04-29
the sparc port can be found here:
[http://cdimage.ubuntu.com/ports/releases/8.04/release/](http://cdimage.ubuntu.com/ports/releases/8.04/release/)

some of the packages aren't as new as in the i386 or x64 releases (for example firefox is 3b3). maybe this is still a daily build, i dunno.

---

### Post by pacarey on 2008-05-20
I had some difficulty too trying to install hardy on to a sun ultra 10. For me the problem is in the latter stages on the install. The machine almost completes the install but then hangs around the clearing up bit and just goes to a full blue screen. On switching to another console and having a look at the background running tasks it seems to have hanged while doing the silo install and will not go any further.

I tried the install a few times, but was met with this blue screeening around the silo install bit. The only option left was to do a fresh install of gutsy, which installed perfect. Update that, and then run the update-manager to upgrade to hardy. Which worked, even if it was in a roundabout way :)

---

### Post by [Wizard] on 2008-07-06
Hi all

First post so here goes...
I've got an old Ultra 10 kicking around that's dying to get an ubuntu/debian installation on it since the last HD with Solaris died on me...

The only snag is that I've lost the original SUN keyboard and I can't seem to boot the CD...

-"Can't open input device..."

Any workaround on how to boot the CD without keyboard?

---

### Post by D-EJ915 on 2008-07-06
use serial console, hook up your null modem cable from the serial port to your computer then use your favourite software (I use minicom on linux) to connect with it.  There are probably some guides around about how to do it.

---

### Post by coutts99 on 2008-07-08
> **howlingmadhowie said:**
> 
problem:
installation fails. silo didn't install
solution:
edit silo.conf by hand and regenerate the initrd image

problem:
services weren't being started
solution:
cp /usr/sbin/start-stop-daemon.REAL to /usr/sbin/start-stop-daemon


Exact same problems here when I installed on a sunblade 100.

---

### Post by howlingmadhowie on 2008-07-11
you can also get an old sun keyboard and mouse with the right socket (mini-dim 8?) for about 20 EUR on ebay. :)

---

### Post by ryry46d9 on 2008-10-04
you will be looking for a type5 im not sure if the type6 will work on these boxes 

the serial cable works as long as you want it to be head less also using the cable spits out a lot more info for doing diagnostic trouble shooting  so I would invest it one just to say you have one 

if your other computer is windows you can use hyper terminal 

lots of how-to on google even how to make your own cable from parts laing around 


good luck

---

### Post by tm002ly on 2008-10-10
&#23567;&#30333;&#33258;&#20174;&#37027;&#27425;&#8220;&#39321;&#28207;&#20845;&#21512;&#24425;&#8221;&#20107;&#20214;&#21518;&#65292;&#27599;&#22825;&#37117;&#38506;&#30528;&#25105;&#65292;&#32780;&#19988;&#26102;&#38388;&#36234;&#26469;&#36234;&#38271;&#65292;&#19981;&#36807;&#24120;&#24120;&#22312;&#19981;&#33258;&#35273;&#38388;&#23601;&#20250;&#39078;&#30528;&#30473;&#24551;&#37057;&#22320;&#30475;&#30528;&#25105;&#12290;&#25105;&#35828;&#31505;&#35805;&#36887;&#20182;&#20063;&#26410;&#33021;&#20351;&#20182;&#24320;&#24576;&#65292;&#34429;&#26159;&#36731;&#26366;&#36947;&#20154;&#21644;&#30333;&#23567;&#22992;&#30473;&#23431;&#38388;&#30340;&#31070;&#20260;&#65292;&#31505;&#24847;&#20877;&#20063;&#19981;&#33021;&#21040;&#36798;&#30524;&#24213;[&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm203.gz.cn)[&#20845;&#21512;&#24425;](http://www.tm203.sc.cn)[&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm203.gx.cn)[&#20845;&#21512;&#24425;](http://www.tm203.gd.cn)[&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm203.hn.cn)

---

### Post by zeroge on 2008-11-04
This is a great way to show you how to make a cool new [scarf](http://www.scarves-store.com) for the fall. Plus, a review of Sabrina Gschwandtner's new [Pure Wool Scarf](http://www.scarves-store.com/pure-wool-scarves-c-10.html)... I have always found it so easy once I watch someone show me how to make [pure wool shawls](http://www.scarves-store.com/shawls-pure-wool-shawls-c-4_14.html)! I could read the instructions forever even with a picture and never get [scarf](http://www.scarves-store.com) right. This is just great [Pashmina scarf](http://www.scarves-store.com/100pashmina-scarves-c-12.html)!

---

