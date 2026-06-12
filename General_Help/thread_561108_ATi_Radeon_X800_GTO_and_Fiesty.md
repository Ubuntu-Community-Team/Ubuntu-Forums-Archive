---
title: "ATi Radeon X800 GTO and Fiesty"
date: 2007-09-27
forum: General Help
---

### Post by riaal on 2007-09-27
I just reinstalled my system (new hdd) and I know xserv is supose to fail and that the live cd is not supose to work (with splash)

So I used the alternate cd and installation works fine but when I boot the system after the "loading" screen the system locks down. Nothing shows on the screen. I know it has something to do with the grapics. The strange thing is that the keyboard don't work either. I ran Fiesty (updated frome Breezy) befor the reinstall.


What to do? Is there a know problem with Fiesty and ATI? Shall I go for 6.06?
I can't accress the terminal at all =/

Thanks!

---

### Post by mali2297 on 2007-09-27
> **riaal said:**
> I just reinstalled my system (new hdd) and I know xserv is supose to fail and that the live cd is not supose to work (with splash)

So I used the alternate cd and installation works fine but when I boot the system after the "loading" screen the system locks down. Nothing shows on the screen. I know it has something to do with the grapics. The strange thing is that the keyboard don't work either. I ran Fiesty (updated frome Breezy) befor the reinstall.


What to do? Is there a know problem with Fiesty and ATI? Shall I go for 6.06?
I can't accress the terminal at all =/

Thanks!

Can't you even boot in recovery mode? 

If you manage to get to a terminal,  run
```

dpkg-reconfigure xserver-xorg

```
and choose the *vesa* driver.

By the way, are you using the  32bit or 64bit version of Ubuntu?

---

### Post by mendo on 2007-09-27
same problem here - i'm running 64 bit feisty, same card.  i boot into recovery mode, and enter these lines:

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial

it says nothings being done after each one, but then i boot (startx) and it works.  i know this isn't a fix, but it's a work around until i find one.

---

### Post by strabes on 2007-09-27
This is a bug with feisty and certain ATI cards. You should upgrade to gutsy as soon as you can. If that is not an option, the fix is as detailed on this page: [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

The information from that page was taken from [here](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b).

You simply need to install the proprietary drivers for your ATI card before the x-server can load (in feisty.) You can do this with the terminal very easily.

---

### Post by riaal on 2007-09-27
So, there is nothing strange with the system locking down? I don't get any error message or something.. I havent actually tryed out recovery mode :S Will do that as soon as I get home! 

Thanks everyone!

---

### Post by mali2297 on 2007-09-27
> **mendo said:**
> same problem here - i'm running 64 bit feisty, same card.  i boot into recovery mode, and enter these lines:

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial

it says nothings being done after each one, but then i boot (startx) and it works.  i know this isn't a fix, but it's a work around until i find one.

This is probably the best idea. You don't need to use *sudo* in recovery mode though.

---

### Post by mendo on 2007-09-27
hey thanks - is gutsy the successor to feisty?  is it stable?  thanks

edit:  i just saw that gutsy beta was released today!  that's cool.  now here's my question - i have kubuntu installed and kubuntu gutsy is only at tribe 4.  if i have kubuntu, i need to stick with kubuntu, right?  i can't install ubuntu gutsy beta from what i have now - kubuntu feisty, right?

---

### Post by SpiritIsReality on 2007-09-27
howdy
my 2 cents worth
if you wanted to try gutsy beta 1 right away, it looks like a fresh install of ubuntu.
you can check around the forum searching for upgrade kubuntu feisty to
kubuntu gutsy.
lwn.net article seems to think kubuntu gutsy beta 1 is out too.
edit : [http://lwn.net/Articles/251882/rss](http://lwn.net/Articles/251882/rss)
I guess check to see when beta 1 kubuntu is out.
other kubuntuans will know better than i do.
maybe search keywords gutsy beta  and see what the hum is.
edit :I didn't follow that article far enough. it's got it nailed.
[http://us.releases.ubuntu.com/kubuntu/7.10/](http://us.releases.ubuntu.com/kubuntu/7.10/)
[https://wiki.kubuntu.org/GutsyGibbon/Beta/Kubuntu](https://wiki.kubuntu.org/GutsyGibbon/Beta/Kubuntu)
[https://help.ubuntu.com/community/GutsyUpgrades#head-3cb12417f0af7f24d4a34f2ae4040bf791c42f52](https://help.ubuntu.com/community/GutsyUpgrades#head-3cb12417f0af7f24d4a34f2ae4040bf791c42f52)
trails

---

