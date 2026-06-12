---
title: "Ubuntu on Chromebook?"
date: 2014-12-27
forum: General Help
---

### Post by ron177 on 2014-12-27
[COLOR=#333333]Dear all,[/COLOR]

[COLOR=#333333]I have read a few posts online and watched one or two youtube videos about setting up Ubuntu on Chromebooks. I wanted to inquire about this more thoroughly to see what are the pros and cons of installing Linux in general and Ubuntu in particular on a Chromebook. [/COLOR]

[COLOR=#333333]I have just bought the following HP Chromebook to try it out and have found the Chrome OS software to be extremely limiting. I want to know whether a Linux distro such as Ubuntu on this machine would somehow be slow or ineffective. What I like about Chromebooks pertains to the hardware and not the actual OS. So if I can install a Linux distro on this, I would keep the machine. [/COLOR]

[COLOR=#333333]In addition, I wonder what distro besides Ubuntu do you recommend for a Chromebook? Debian or some version of Ubuntu or something else?[/COLOR]

[COLOR=#333333]Here's the Chromebook in question:

[/COLOR]http://www.bestbuy.com/site/hp-14-chromebook-nvidia-tegra-2gb-memory-16gb-flash-emmc-memory-snow-white-smoke-silver/8827017.p?id=1219371334345&skuId=8827017

[COLOR=#333333]Thanks,[/COLOR]

[COLOR=#333333]R[/COLOR]

---

### Post by TheFu on 2014-12-28
Take it back - quick!

Get an 11inch notebook for $300 somewhere that has:
* a real keyboard
* ethernet port
* labeled function keys / delete / PgUp / PgDn / Home / End keys
* Solid touchpad with kernel support - unlike the chromebooks.
* 4-8G of RAM - that isn't soldered onto the MB
* more than 32G of storage
* VGA output

Trust me - go get a normal, cheap, laptop.  Dell makes one for $280.  I've posted here on other chromebook threads with more details about what sucks.  

I'm tired of rebuilding the kernel drivers for my touchpad after every update.
I'm tired of hitting the power key because it is where the DEL key belongs - this is 9 months after purchasing this crap chromebook.  

Get the dell, dude.  Take it back.

---

### Post by kerry_s on 2014-12-28
lol, i was just reading a article & thought that would make a good cheap ubuntu laptop.
[http://www.engadget.com/2014/11/28/hp-stream-11-review/](http://www.engadget.com/2014/11/28/hp-stream-11-review/)

its on sale $179:
[http://www.microsoftstore.com/store/msusa/en_US/pdp/productID.309174400?srccode=cii_23393768&cpncode=45-19430092-2&WT.mc_id=US_datafeed_Amazon](http://www.microsoftstore.com/store/msusa/en_US/pdp/productID.309174400?srccode=cii_23393768&cpncode=45-19430092-2&WT.mc_id=US_datafeed_Amazon)

---

### Post by TheFu on 2014-12-28
My Acer C720 makes a cheap ubuntu laptop with "issues." Can't say it is good.  All the chromebooks have issues that might not seem important at purchase, but quickly become complete roadblocks.

That HP Stream appears to have the same issues - minus the missing DEL key. I'd still pass.

I've been running 14.04 on my C720 and 13.10 before that since day-1 owning the Chromebook. Booted into ChromeOS for 5 minutes - just long enough to get legacy boot enabled. I can make Linux purrrrr.  The issues aren't with Linux, it is with the limited hardware on all chromebooks and cut-down chromebook-like laptops.

There are small, lite, cheap, long-battery, w/ reasonable CPU, laptops in the $250-$350 price range. Very few people are happy with the $200 chromebooks later. The return rate is higher than any other laptop.  

2G of RAM isn't enough anymore for modern browsers or java-anything, 16G of storage isn't enough either - those are the main issues.  The CPUs are plenty fast for normal desktop use.  My 2G RAM chromebook actually locks up with 10 tabs open and a few other programs. Had to double the swap file size to stop the crashes. Also had to install a larger SSD to have more storage. That voided the warranty. It was completely necessary to make the system useful when stand-alone. The 32G model might be enough - but it isn't $200 either.  Ever wonder why there are so many "refurbished" chromebooks available?

BTW, I'm typing this on entry using the chromebook.  If I were in the market TODAY - I'd get ... let me see ... Dell Inspiron 11 i3147. It was $280 last Xmas, but a recent price - $300 at Staples.

Get the Dell/HP/Toshiba/SONY tiny, cheap laptops and load Ubuntu with a limited GUI like xfce, mint or lxde - dudes.

---

### Post by jhh on 2014-12-28
It depends on how you want to use your chromebook. The battery life is excellent. With very little effort you can put Ubuntu on it with Crouton -- I'm actually running trusty with the XFCE desktop environment, typing on my Toshiba Chromebook 2 right now.

The benefits of the Chromebook is its price, components (I recommend getting an intel one), and ease of use. I am relatively new to Linux, and I am wanting to learn more. I saw this as a unique and inexpensive opportunity to wade into the linux pool.

My plan is to use the Chromebook in its native Chrome OS and Ubuntu. I have it setup to easily run LibreOffice so when I'm in a situation with no internet, it'll run very easily. I am presently working through trying to figure out how to access my DoD email via Firefox.

I heartily recommend it if you are wanting to get an inexpensive but extremely capable portable laptop (with admittedly limited storage).

---

### Post by ron177 on 2014-12-29
Folks, I have tried Ubuntu on a cheap entry level Toshiba and after six months of ownership while I am not completely happy with the purchase I know the pros and cons of having more hard drive, RAM, keyboard features, and so forth. But the attractions of Chromebooks for me are their portability and honestly the hardware. The screen, the keyboard (the comfort of typing -- not the limited features available), the battery life, the trackpad, and the weight of the machine are extremely appealing and in my opinion superior to average entry level laptops out there as far as I can determine.

So if you need a small laptop 3 pounds or less that you can take to office and if you don't want to pay what it takes to get an ultra light laptop, what do you do? I am also wondering if I can add more RAM or hard drive to chromebooks. Is that an option? 

Thanks,

R

---

### Post by TheFu on 2014-12-29
> **ron177 said:**
>  I am also wondering if I can add more RAM or hard drive to chromebooks. Is that an option? 

Different models are different, however .... my C720 with a Celeron(R) 2955U @ 1.40GHz .... 

RAM is usually soldered onto the motherboard - no upgrades without huge trash-the-system risks. Not for me.

The disk storage is SSD - often m.2-ssd which is a tiny format half the size of the mSATA used in most systems.  [https://en.wikipedia.org/wiki/M.2](https://en.wikipedia.org/wiki/M.2)

I had to break the warranty on the chromebook to swap the 16G m.2 SSD for a 128G m.2 SSD. At the time, no larger storage amounts were available.

---

### Post by aysiu on 2014-12-29
I've found Crouton to be the best way to do Ubuntu on a Chromebook:
[http://chrubuntu.blogspot.ca/2013/05/crouton-the-easy-way-to-install-ubuntu-on-chromebook.html](http://chrubuntu.blogspot.ca/2013/05/crouton-the-easy-way-to-install-ubuntu-on-chromebook.html)

Unfortunate, anything involving Development Mode can be a bit fragile (i.e., when you boot up, it'll say "Hit any key to get out of development mode," which will then factory reset your Chromebook, thus deleting your Ubuntu installation).

---

### Post by jhh on 2014-12-29
Ron,

I can completely relate to your post. Those reasons were precisely what led me to investigating the pros/cons of purchasing a chromebook to use as an inexpensive and portable linux laptop. 

I ended up purchasing the Toshiba Chromebook 2 with 16GB SSD and 2GB Ram. It operates exactly like I need and want it to. I am not using it to play games, I was primarily looking for something to easily take with me on the road, input things via a word processor (LibreOffice), and access files I have saved on a thumb drive or other portable drive. I find that the SD drive is all I need to increase the storage (google drive and drop box are great).

While I acknowledge the limited-use of this chromebook for linux, the price was right and the process was simple (via crouton). 

Its construction, portability, and speed make any cons worth it. To be honest, the only thing that I really do not like is that it is 2GB of Ram (I could've and should've gone with 4GB -- but 2GB works fine, I'm just limited in what I can do simultaneously).

---

### Post by andrea48 on 2015-01-01
I have been using that same HP chromebook 14 (4GB) for a couple of months before having this [very bad issue]("http://ubuntuforums.org/showthread.php?t=2257609&highlight=chromebook") (which i think can be solved [as seen here)]("http://jrs-s.net/2014/04/01/restoring-legacy-boot-linux-boot-on-a-chromebook/") and i can tell you it is not the best laptop you can buy, but it is a good compromise: you have some trackpad issue after installation (which can [be solved]("http://ubuntuforums.org/showthread.php?t=2220912")), the keyboard keys are a little small and some are actually missing (as the CANC one); on other and you have a 15hrs battery, good display and flat and light laptop for 150$. Also the speakers are not in the best position... 

You should consider everything The Fu as listed, knowing that you can [buy a 128gb ngff ssd]("http://chromebook-falco.blogspot.com.es/2013/11/here-are-mechanics-of-ngff-ssd-removal.html"), but you will have a lot of working to do.

---

### Post by TheFu on 2015-01-01
> **andrea48 said:**
> you have a 15hrs battery, good display and flat and light laptop for 150$. 

15 hrs?  Really?  The most I've seen on any of these models is 9 hrs - I get a little less than 8 hrs working, but have never allowed it to die completely. BTW - there are issues if you allow that to happen - beware.

Also - the $150 versions are refurbs, not new.  Usually refurbs are $170+ around here.  For $150 the equation is completely different. That's $50 cheaper and definitely worth strong consideration.

BTW - the newer Haskell cheap laptops (not chromebook clones) get 8+ hrs of battery with Cire i3 and Celeron N-whatever CPUs.  This has been enough for a full day working that I don't bring power cables with me anymore.

If you can get a 4G RAM version - buy it.  I see these listed, but never available.  I think it is a conspiracy from vendors and google. They know if there is 4G of RAM then ChromeOS can easily be swapped for other OSes and the low-end laptop market will be gutted.  I looked and never found a 4G RAM that I could actually purchase without paying a $150 premium. At that point the low-end Dell was a much better deal, IMHO.

I've really tried to help folks make an informed decision.  Think I need to put my upgraded Chromebook on Craig's List for sale, since I am so unhappy with it and get the Dell.

---

### Post by andrea48 on 2015-01-01
> **TheFu said:**
>  but have never allowed it to die completely. BTW - there are issues if you allow that to happen - beware.
.

:p:p eheheh it is the first issue i pointed out.
Anyway it reach 15hrs when i leave it downloading the whole night and use for half working day. 

About the price, it's actually my bad i didn't specified: i refer to used ones, actually to the one i get myslef. A _used_ peach 14 HP chromebook 4GB, with box, no waranty but mint condition. You can find for less on ebay if you have little patience. 
The choice has all the issues you pointed out, but here seems th OP want a review of the product, and this is my experience :p.

Anyway what are Haskell laptop? gloogling is not helping :/

---

### Post by libssd on 2015-01-11
@Ron177 : Having run dual-boot installations on a netbook, and Lubuntu via Crouton on a Chromebook, I'll take the latter any day. However, a Chromebook with an ARM processor is not the best environment, as Ubuntu has better support on Intel. Within the past 24 hours, I installed Lubuntu on a 3-year old Samsung S5 Chromebook with an N570 processor, and it runs very well. Considering the limited capabilities of a N570, performance is amazing — everything is very quick, Lubuntu can access, create, and modify files in the Chrome OS Downloads directory, and switching between the two is convenient.

Probably the best source of Crouton information at this time is the Crouton Users group on Google+ : [http://goo.gl/gYxXNC](http://goo.gl/gYxXNC)

---

### Post by nadarockyraccoon on 2015-02-07
I picked my acer c720 up at best buy of all places for $200, and so far I have been happy in that I got what I paid for. I completely did away with chrome and installed ubuntu, that 15gigs isn't enough for dual booting.

I did initially have an issue with the space bar on boot wiping the system(one of my kids did just that) and as result I disabled the power button in ubuntu and I went so far as opening the case to remove the write protection screw and make ubuntu the permanent os, then put the screw back. Some models don't require opening the case to disable write protection. Chances are if you are aware and don't have kids this won't really be an issue.

Thus far my only real issue is that occasionally the touchpad glitches out and I haven't figured out what happens to fix it(rebooting doesn't help but it isn't enough of an issue to occuppy a whole lot of my time). I did have to stop kernel updates so that I wouldn't have to rebuild the touchpad driver all the time. I update the kernel when I am prepared to deal with that. 

Storage isn't much of an issue since it is just general good practice to back things up on external drives anyways. That being said the speed and reliability that the solid state drive offers is a worthy sacrifice to space. Not all chromebooks have solid state drives though, and the ones that don't have ample storage space.

As far as ram is concerned, mine came with two gigs and ran unity just fine. I n the name of efficiency and usability I run gnome-flashback, no fancy stuff like compiz and I'm currently using just over 600 mib of ram, so one gig likely would have been just fine. 

I suppose suspend and and sound are an issue for some people but theses things can be made to work without much effort. I remember the days when a linux distro didn't come with an x interface, it was up to the user to set that up and what is a touchpad? My point is that if you are poor but can spare a couple hours on the interweb to get things working just right then a chromebook is a great route. If you have the money to get some nicer hardware and aren't up to the challenge then get something else, but keep in mind even that something else might have its own problems with lack of full support under ubuntu or any other linux distro. It's a tough thing to support so many different hardware combinations and provide drivers for all that hardware in an os. Windows doesn't do that, it's up to the hardware designers to write drivers for interfacing with there os, Apple does it but they predetermine the hardware. Only linux attempts to make an os with native driver support that works on every computer.

---

### Post by libssd on 2015-02-08
**Rocky** : If you install with crouton, Ubuntu uses the Linux foundation provided by Chrome OS. Ubuntu LXDE, with the full LibreOffice suite and some other utilities on my relatively old Samsung S5 (Atom processor) still has about 7 GB of free disk space. A backup tarball is about 1 Gb. A 32 Gb drive and 4 Gb of RAM would be optimal, but you can do quite a bit with a 16/2 Chromebook.

Crouton info available here: [https://github.com/dnschneid/crouton#readme](https://github.com/dnschneid/crouton#readme) 

Crouton is a very nice solution for Chromebooks, and can be set up to autostart; you enter your Google password, and after a few seconds up pops a full Linux desktop.

---

### Post by nadarockyraccoon on 2015-02-11
**libssd:** I went all out and completely wiped chrome, I even went so far as to change the gbb flags to automatically boot ubuntu. On the internet 15 seconds after pressing power from off, not suspend. I run ubuntu classics, no effects, with all unnecessary unity packages removed. On a clean install this leaves 8.7 GB free, my hd reads as 15.1 GB though. Absolutely, a perfectly capable system for most users. So far I haven't tried to do anything that didn't work from hardware limitations and google is very generous wih it's documentation. Touchpad on the c720 is the only real issue. From what I understand this should be resolved in kernel 3.17(ubuntu15.04), haven't had the chance to test it though.

---

