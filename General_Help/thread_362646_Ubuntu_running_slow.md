---
title: "Ubuntu running slow"
date: 2007-02-15
forum: General Help
---

### Post by Rabbit_Alex on 2007-02-15
I would like some help speeding up Ubuntu Edgy.  I have noticed since I installed last week that it runs slower than Windows XP during normal use (Firefox, installing software, watching flash videos, etc).  I am running Edgy with GNOME (using XFCE didn't speed it up at all).

For an example of what is running slow, the Flash-style drop down menus in this forum take several seconds to open.  Opening Firefox can take up to a minute and and it renders pages slowly.  Things really slow down when I have several apps open such as Firefox, a terminal and Synaptic.  I do not have this problem (not very much) when running XP.

My laptop is a 2-year old Dell Inspiron 9100.  Here are the specs.
Pentium 4 3.2 Ghz (Prescott core I think)
1 GB RAM
ATI Ratheon 9700 Mobile 128 MB
60 GB HD

Can anyone recommend a way to speed this thing up?

---

### Post by trevdiggy on 2007-02-15
I've been having the same issue.  About a week ago I first noticed it.  Not sure if it was a bad update or what?  Opening a terminal or Nautilus, which usually takes a couple of seconds, now takes like 20 seconds.  Firefox or GnuCash are at least as bad.  I'm attempting to find some core component, like Xorg, Gnome or my ATI drivers, that was recently updated and roll it back.  I'll post if anything works.

It's not a matter of too many programs open.  System Monitor says I'm idle.  The slowness is even apparent (painfully) when the screensaver kicks in.  It jerks around like when I had the wrong ATI drivers installed.
This isn't a slow machine:

Athlon 64 X2 (dual 2.2 GHz)
1 GB DDR2 667
128MB Radeon X800

Ubuntu Edgy 
Gnome 2.16.1
xorg 1:7.1.1ubuntu6.2

Any ideas?

---

### Post by dcstar on 2007-02-15
> **Rabbit_Alex said:**
> I would like some help speeding up Ubuntu Edgy.  I have noticed since I installed last week that it runs slower than Windows XP during normal use (Firefox, installing software, watching flash videos, etc).  I am running Edgy with GNOME (using XFCE didn't speed it up at all).

For an example of what is running slow, the Flash-style drop down menus in this forum take several seconds to open.  Opening Firefox can take up to a minute and and it renders pages slowly.  Things really slow down when I have several apps open such as Firefox, a terminal and Synaptic.  I do not have this problem (not very much) when running XP.

My laptop is a 2-year old Dell Inspiron 9100.  Here are the specs.
Pentium 4 3.2 Ghz (Prescott core I think)
1 GB RAM
ATI Ratheon 9700 Mobile 128 MB
60 GB HD

Can anyone recommend a way to speed this thing up?

Do a forum search for "disable ipv6", the solutions have helped a lot of people.

---

### Post by trevdiggy on 2007-02-15
Thanks, dcstar, but disabling IPv6 (as described [here]("http://ubuntuforums.org/showthread.php?t=187534&highlight=disable+ipv6")) didn't change my system speed.

Bootup isn't noticeably slower than usual, but from the moment I log in Gnome is slow to load and everything thereafter.

Any ideas are appreciated.  

Thanks,

Trevor

---

### Post by Rabbit_Alex on 2007-02-15
I don't think this is a problem with my network speed.  My download speed is fine (I can watch it in the monitor program) but Firefox takes a long time to display the page. Disabling IPV6 didn't help speed up Firefox's rendering speed or general system speed.

Any other ideas?

---

### Post by trevdiggy on 2007-02-15
Just FYI: I downgraded the fglrx ati driver and it did nothing.
Also note, the system has been this slow since before the latest kernel update.

I wish there was a log of updates so I could figure out what changed to slow things down.

---

### Post by Icarus76 on 2007-02-16
Since last edgy's kernel update (-11) my system runs slower too with firefox and another program open in gnome. A fresh install doesn't resolve the problem because, after upgrading, it appears again. I've tried to install flash from repositories and from the adobe installer, but nothing changes. Also tried to install nvidia-glx drivers and nvidia installer, result? the same.
It's a possible kernel bug?

---

### Post by jonty-comp on 2007-02-16
Yes, I've recently reinstalled Ubuntu after a stint with Arch Linux (:shock:) and it's a helluva lot slower.
Normal applications seem to start pretty OK, although they might take a while, and Beryl seems fine, but I used to be able to play 2 720p High-Definition videos at once on different cube faces and watch them both by rotating the cube with no noticeable lag or jerkyness, but with Ubuntu I can hardly play one widescreen DVD, and running glxgears slows the system to a crawl. :|

Specs:
AMD Sempron64 3400+
512Mb RAM
256Mb nVidia GF6200
Latest nVidia-glx drivers with the AddARGBGLXVisuals option on
1280x1024 19" LCD screen

Is this some broken thing somewhere? It's really annoying me, so much that I may well switch back to Arch.  #-o

EDIT: A-ha, I just installed the latest nvidia driver from the nvidia site instead of the one in the ubuntu repos using envy, and now it runs much faster! Still doesn't play the HD video too well, but I'll install VLC and see how that copes with it...

---

### Post by Icarus76 on 2007-02-16
Well, doing a fresh install, upgrading without install the new 17-11 kernel and without flash plugin, and firefox and opera continues crashing or slowing the system. Starting any program what requires administrative rights with another like nautilus causes same effect any times in my system. Before the release of the new kernel, all worked fine. Seems like another new package of these day is causing the problems.

---

### Post by awells527 on 2007-02-17
Run this command to see if your graphic acceleration is working properly.

```
glxgears -printfps
```

Do it when no other programs are running.  If you are getting significantly under 1000 fps, then you have a problem with your video driver.  Also, 'glxinfo' will tell you if glx is loaded.

---

### Post by punkybouy on 2007-02-19
Forget Firefox and install Swiftfox.  I had the same problems and Swiftfox is much faster which probably means there are issues with Firefox.

---

### Post by raziel_tk on 2007-02-19
I've the same problem. No just firefox, but also other applications are very slow. There is one thing: I didn't install the latest kernel because I didn't want to rebuil some other stuff. So it shouldn't be the kernel, maybe something else. I recently installed beryl, but it worket well for one day, the issue started the day after... What can it be??? Bye

---

### Post by The Geoff on 2007-02-19
I've been having much the same problem after upgrading to eft.  I *think* it may be connected to the system that thumbnails image and video files, as it always slows down when I have downloaded an image/vid to desktop, or when I have a window containing said files open.

Anyone know how to turn the feature off?

---

### Post by Rabbit_Alex on 2007-02-19
> **The Geoff said:**
> I've been having much the same problem after upgrading to eft.  I *think* it may be connected to the system that thumbnails image and video files, as it always slows down when I have downloaded an image/vid to desktop, or when I have a window containing said files open.

Anyone know how to turn the feature off?

Can you be more specific?  Do you mean when you are using Firefox?  What application shows you the thumbnails of the files?

---

### Post by crapapelada on 2007-03-05
I am having the same issue since last Friday; I have not installed anything in the last days, but since Friday it takes ages to start almost any application: a terminal window, firefox, file system browser and so on.
It runs normally when launching system tools, like networking tools and the packet manager...strange but true, anything that requires to insert the password for security reasons runs as quick as it did before.
Another strange thing is that if I launch the file browser (from places etc.) it takes about a couple of minutes, if I open the external USB drive using the autocreated desktop icon it opens in a blink of an eye.
Anybody else is experiencing this?

EDIT: all applications once opened run normally, i.e. VERY fast, as before the problem appeared.

EDIT 2: just tried this [http://www.ubuntuforums.org/showthread.php?t=296443](http://www.ubuntuforums.org/showthread.php?t=296443) and everything is OK now.
Solved for me.

---

### Post by depele on 2007-03-17
my ,kubuntu is also very slow. 

Just started from the last upgrade.

any idea how I can fix it. 

ip6, internet settings (network) are all fine.

cpu: 2.8
ram: 512
ati fglrx is working fine

---

### Post by LinuxKing2007 on 2007-03-20
Did you try upgrading your display driver and changing your x config file to use 3d acceleration. Thats what I had to do.:guitar:

---

### Post by Paulusgnome on 2008-03-15
I have both Ubuntu and Windas XP on my PC in dual-boot configuration.

I too have observed that Ububtu is running quite a lot slower after recent updates than it had been. Just loading up Firefox takes a good 10 seconds where is had been taking only a second or so. Booting up is only a little slower however.
I have installed nothing, nor made any system changes, apart from the routine updates, for months, so I don't think it is anything I have done. 
My PC is reasonably speedy - 2 x 3 Ghz Xeons, 1 Gig RAM, spacious HDDs, and still runs Windas XP OK, so  the problem is definitely with Ubuntu I think.
Hopefully the good people at Ubuntu can sort out a fix soon or I will be forced into the drastic step of installing Fedora in its place...:lolflag:

---

### Post by haxx on 2008-03-15
i tried nearly all the same fixes noted here and got NO results.

Today i installed the 7.10 alternate and the difference is nearly of miracle proportions 

give it a try if u dont mind the back up and install times and can bear the OEM's setup method

---

### Post by theophane on 2008-03-28
> **haxx said:**
> i tried nearly all the same fixes noted here and got NO results.

Today i installed the 7.10 alternate and the difference is nearly of miracle proportions 

give it a try if u dont mind the back up and install times and can bear the OEM's setup method

Weird, the alternate setup is the same than the regular one, it is just in text mode, no ?
Correct me if I'm wrong, but I don't really see what kind of benefits you could get from installing Ubuntu through the alternate cd...

---

### Post by Sagia on 2008-06-06
For year I heard that Linux is more stable and faster than windows. but when i try it using it (ubuntu, kubuntu, xubuntu), i so disappointed with is stability and performance. it always crash on my system, and it so slowwwwww. Even my computer can run vista much faster than ubuntu.... and way more stable. Look like I will stick with microsoft.

my spec

AMD Athlon XP-M overclock to 2.83 Ghz
2 GB of DDR 400 Mhz (227)
MSI K7N2 Delta2 nForce2 Ultra
ATI Radeon 9600XT 256 MB

---

