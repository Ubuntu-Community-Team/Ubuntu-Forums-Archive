---
title: "Ubuntu slower than Win2k ?"
date: 2005-10-23
forum: General Help
---

### Post by TomG on 2005-10-23
Hi

I try Ubuntu 5.10 for a few days. I'm quite happy with it but I feel some slowness comparing to Win2k. 
For example the display of my web pages and the switch from a window to another is a little bit slower. The problem is more obvious when I'm burning a CD with K3B, it is difficult to work normally at the same time.
I don't have such problem on Win2000.
I have a quite weak configuration (Athlon 1800 + 512Mb of RAM)
SWAP seems not really used but CPU sometimes reaches high values.
Is there something to check and do ?

Cheers
Tom

---

### Post by gruszczy on 2005-10-23
I've got same problem. I use Ubuntu while programming, but I go back to windows while browsing the web, because it's simply faster.

---

### Post by TomG on 2005-10-23
From your point of is there any solution except upgrading the hardware ?
Thanks
Tom

---

### Post by ymmotrojam on 2005-10-23
One of the things that I *cough* like about Windows is that all the effects can be turned off. I'm not saying they can't in Ubuntu, but where would I get a theme that is very minimalistic, without a whole lot of pizazz?

---

### Post by dtfinch on 2005-10-23
Galeon or Epiphany may be faster than Firefox for web browsing, despite all using Gecko. Firefox currently has Linux issues. Having to manually enable DMA has always been a big issue in Ubuntu and most other distros. I have had CD and DVD slowness in the past caused by DMA being disabled. Hard disk performance nowadays is usually near the same with or without DMA, but CPU usage is much higher if DMA is disabled. Enable dma permanently in /etc/hdparm.conf. Also, there's an slocate jon in /etc/cron.daily that can slow your system down from time to time. People who use the "locate" command a lot often can't imagine life without it reindexing their systems daily, while others won't miss it at all.

---

### Post by stack445 on 2005-10-23
I've re-install windows recently for games, and the first thing i did notice, was, that it is actualy a LOT faster then Ubuntu. I've been using linux for about two years now, and at first it was beacause my old machine was not powerful enough to run windows with all the crap.  Now it's eve worst with the last ubuntu.  

Is it just me or Hoary was faster ?

---

### Post by tseliot on 2005-10-23
[QUOTE=stack445]Is it just me or Hoary was faster ?[/QUOTE]

Breezy it's faster for me.

---

### Post by Staesys on 2005-10-23
The new Opera is also very fast. On my system anyway, it's a lot faster than FireFox.

---

### Post by Bitmastro on 2005-10-23
Check out if it's a video problem (maybe it's the composite extension, or some other trouble in xorg.conf). to try something faster install the xubuntu-desktop meta-package with synaptic and in gdm use xfce session. Also try kazehakase as browser, or opera. It should not be so slow.. I use it with an athlon 2600, 512Mb RAM and it's pretty fast, I've even installed it in a k6-450 with 256Mb of Ram and a P3 800 with 128Mb of ram (but in these 2 I was using hoary)

---

### Post by brickbat on 2005-10-23
Hi,

In my experience all linuxes need tweaking to get them pretty fast.  I ran linux for a year on a 500mhz p3 and i really liked it.

The thing about any windows is that it will be really fast when you install it but after a few months............
The whole registry thing is a huge structural flaw.

Also windows has a faster response for things like typing and mouse movements but (assuming you have tweaked it) I think that ubuntu is actually faster when running apps.

I did have one strange thing with firefox linux vs. win.  On some heavy java pages, the load time was incredibly slow in linux.  I never could figure it out.  Now I dual boot and run as many apps as I can in both. One page that did this really badly was that michelin europe route planner.

eg.  I use thunderbird in both and have one fat32 partition with my mailbox with both systems.  Then I just run the one that feels better at the time.

ciao
bb

---

### Post by kurtkraut on 2005-10-23
7If you use Firefox, you may speed up it doing this:

1.Type "about:config" into the address bar and hit return. Scroll down and look for the following entries:

network.http.pipelining
network.http.proxy.pipelining
network.http.pipelining.maxrequests

Normally the browser will make one request to a web page at a time. When you enable pipelining it will make several at once, which really speeds up page loading.

2. Alter the entries as follows:

Set "network.http.pipelining" to "true"
(Double click to do that)

Set "network.http.proxy.pipelining" to "true"
(Double click to do that)

Set "network.http.pipelining.maxrequests" to some number like 16. This means it will make 16 requests at once.
(Double click and change the value in the form)

3. Lastly right-click anywhere and select New-> Integer. Name it "nglayout.initialpaint.delay" and set its value to "0". This value is the amount of time the browser waits before it acts on information it receives.

---

### Post by !nkubus on 2005-10-23
It must be gmone , because my Kubuntu Breezy is snappyier than ever:cool:

---

### Post by DRF on 2005-10-23
I don't know how much of a perforance increase this gives but I allways change my kernel to the one best suited for the CPU in the computer I install linux on.

In synaptic there should be the following packages:
linux-image-386
linux-image-686
linux-image-k7
(and others for dual processors etc)
The default is the 386 version which works on everything.
If you install the 686/K7 version it will add itself to the grub menu so you can still use the old kernel image if the new one doesn't work.
The 686 image is built for PPro/Celeron/PII/PIII/PIV
The K7 image for the Athlon/Duron AMD processors.

Has anyone actually done a test to find out the actual performace gained by this?

If you know quite a bit about linux you can allways customise your kernel but I personally don't normally have the time so I stay with the pre-built ones.

Daniel

---

### Post by tseliot on 2005-10-23
[QUOTE=TomG]The problem is more obvious when I'm burning a CD with K3B, it is difficult to work normally at the same time.[/QUOTE]

Perhaps your DMA is disabled. Type:
sudo hdparm -d /dev/cdrom

and post the output

---

### Post by jworr on 2005-10-24
I almost hate to say this, but fedora core is much faster that both ubuntu and windows in my experience.  For a computer science class we ran brench marking software and the the same c code was 3 times faster on fedora than win2k on a dual booted machine.  I have also heard other people complain about ubuntu's speed, they suggested going to debian.  But personally I would install fedora even though people say its bloated, it is actually quite fast.  You could also try a different theme or window manager such as clearlooks.  It looks nice and isn't that resource intensive.

---

### Post by TomG on 2005-10-24
Thanks for replies.
I will check the DMA, Firefox settings and try with other browers...
Tom

---

### Post by Pablo_Escobar on 2005-10-24
Ubuntu is much faster for me.
XP when boots - load a lot of crap, which is needed for him to operate normally. (Firewall, Antivirus, Sound configuration), which takes a lot of time.
Ubuntu loads quickly and is snappy whatever I do (amarok, web browsing, Gimp editing, IM all at once). 
It's a good thing tu use BUM, and switch off unneeded services.

---

### Post by wabble on 2005-10-24
[QUOTE=ymmotrojam]One of the things that I *cough* like about Windows is that all the effects can be turned off. I'm not saying they can't in Ubuntu, but where would I get a theme that is very minimalistic, without a whole lot of pizazz?[/QUOTE]

Try [GNOME-Look.org]("http://www.gnome-look.org")

---

### Post by TiMBuS on 2005-10-24
[quote=dtfinch]Hard disk performance nowadays is usually near the same with or without DMA[/quote]
Woah thats not correct. I had a HDD that kept going from DMA to PIO mode, and the  problems were intense. I have a Athlon 3000+ 64 bit CPU and it couldn't even handle opening a folder in windows and playing a song in winamp at the same time.
Also, I find breezy way faster than WinXP

---

### Post by afonic on 2005-10-24
The speed of Gnome (cause we are talking about the window manager's speed and not Ubuntu itself) is much faster when you select a simple theme. Try some more complicated ones and you will see a huge difference.

Also I think that most of you will agree that there is a problem with the Firefox package in Breezy. It is just slow. As a solution I downloaded 1.5 Beta 2 which works just by running the binary (and loads all your settings). It is fast, and stable for a beta, and you also help people at mozilla by reporting bugs and stuff!

---

### Post by Kuolio on 2005-10-24
Ubuntu-Gnome's desktopmanager, Metacity, is just horribly slow :( Change it, and feel the righteous speed of OSS desktopfunctionality.

---

### Post by BIGtrouble77 on 2005-10-24
Like everyone's pretty much made clear so far, it's critical you have things configured properly to get speedy performance.  

The basic windows gui is a little snappier, but it's that way at a huge cost... stability.  As a result, virtually any application can cause a system failure in windows, where in linux you simply need to kill the task and things should still work as normal.

My Breezy laptop is very fast and more stable than any windows install I've ever  done.  Windows does get slower over time, as more applications are installed.  

The critical things to configure after a new ubuntu install are:
Enable DMA
Install  latest (opengl) video drivers
Make sure video overlays are working (xv)
Apply firefox speed hacks (better yet, just use opera)

The only thing I'm still working on getting to run perfectly are 1080i hd videos.  I'm very close to running them perfectly, but I still drop some frames.  I'm not sure, tho, if it's possible to play these videos realtime without a hardware decoder.  (my backup windows machine can't play them back well either)

-BT

---

### Post by sailor420 on 2005-10-24
I just installed the Firefox 1.5 Beta 2, and it has made an *unbelievable* difference in browsing speed. I had heard it was better, but this is incredible.

There's a guide here: [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

### Post by Pigmudgeon on 2005-10-24
That sounds exactly like I've been experiencing, Ubuntu v. Win2k. I run both on an Intel motherboard with a P3 997MHz chip. The Ubuntu stuff is running fine, and printer response time is better than with Win2k, but the mouse action is choppy, and the keyboard is sluggish. 

There are also some screen issues. I have an LCD screen, and it's either in perfect alignment with one system or the other, depending on how I tweak that. Right now I'm running Win2k but the screen is still tweaked for Ubuntu, and there are four vertical zones that are moderately blurry (but still readable). 

Fortunately, I don't run games, but while I'm writing, these problems can be annoying. Is there a FAQ or How-To that addresses tweaking input and the screen?

--p!

---

### Post by speedsix on 2005-10-24
I've just gone from Hoary amd64 to Breezy 32bit and it's so much slower, general graphics speed is poor and so it seems is HD access. Nvidia drivers are installed and I simply copied my xorg.conf over from the Hoary install.

For example when you click shut down and the screen fades it's very slow and a jerky fade. There must be something wrong, how do I check/enable DMA for my sata HD? What about settings for my nvidia card that worked fine on hoary in my xorg file?


Thanks

---

### Post by TomG on 2005-10-24
Regarding slowness while burning, DMA was actually disabled. I set it to ON and I retried my burn. I no longer have problem ! Thanks.
Epiphany browser seems also a little bit better !
Continuing my tests...
Thanks ! :smile:

---

### Post by afonic on 2005-10-24
[QUOTE=Kuolio]Ubuntu-Gnome's desktopmanager, Metacity, is just horribly slow :( Change it, and feel the righteous speed of OSS desktopfunctionality.[/QUOTE]

Care to post some suggestions? ;)

---

### Post by felix.rommel on 2005-10-24
Hello,

I upgraded from Debian Sarge to Breezy and I thought it would be faster than Sarge and Hoary but on my Aspire Notebook the speed is not as fast as I want it to be.

On another partition I installed [OpenSUSE]("http://www.opensuse.org") and I must say that it is FASTER than Breezy. I don't know if it depends on the upgrade from Sarge that Breezy is slower than OpenSUSE!?

But I think about switching to OpenSUSE - good that I have my home dir on a separate partition :)

I stopped some things like startup time and opening OpenOffice which is faster with SUSE. Also the whole Desktop feels snappier, for example the menus pop up faster, switching between windows is also faster etc.

The only thing is that I have a graphics problem with my card with SUSE which is better with Breezy. That's why I compile the xorg-6.9-RC server at the moment and hope that the problem will be solved with this.

So if Breezy isn't fast enough for you I recommend OpenSUSE 10, it's also user friendly and has a good HW detection. You have the choice with Linux.

Have fun.

---

### Post by dakira on 2005-10-24
[QUOTE=BIGtrouble77]Make sure video overlays are working (xv)[/QUOTE]

what exactly do you mean?

---

