---
title: "Using 10.04 now?"
date: 2020-09-25
forum: General Help
---

### Post by tpprynn20 on 2020-09-25
I've downloaded Ubuntu 10.04 today, which still feels like peak, optimum Linux to me - the Windows 98 of Linux - until trying to be online. I've gone for this old version to use on a X201 Thinkpad that is almost exclusively going to be used as a word-processor. I think I may have attempted this before and remember still tinkering with Firefox with a view to having a quick look at email or an online newspaper while out and seeing it didn't cope well with today's internet, and that newer versions of Firefox failed due to dependency issues inevitably.

Is anyone else here using 10.04 or earlier on any machines with any success? Are there ways to get a browser working properly with it? I did wonder if an older version of Opera for example might work if a .deb of it is somewhere online.

I know it'd annoy some to hear this said but I'm not bothered about security and have Debian 10 on a newer laptop for long stays online.

Thanks.

---

### Post by guiverc on 2020-09-25
The security aspects are key, you should not use it online.

The base of Ubuntu 10.04 with GNOME was GTK2.

The base of Ubuntu only a year or later  switched to GTK3, so most of the modern software will be incompatible as you're using really old (depreciated) libraries, and some of the GTK2 libs cannot co-exist with GTK3 ones (the GTK3 libs were designed to replace, not co-exist). (*some can co-exist, as LXDE was GTK2 and can use many GTK3 programs, but it will have limits as some GTK2 libs were still updated so `gimp` will still work as it's porting [to GTK3] is still incomplete)*  If you update your libraries for later software, I would expect trouble with your desktop as you'll likely cause API/ABI mismatches thus programs will crash.  I'd expect all these issues to occur in user space, so in theory you should be able to recover, but rebooting will still be quicker.  It wouldn't be fun to use.

`lynx` is a browser that may work, eg. [https://packages.ubuntu.com/focal/lynx](https://packages.ubuntu.com/focal/lynx) though I don't recall the version of libc6 etc that came with 10.04, but as it uses lower libraries in the software stack you'll have more luck that a browser using features higher up (like GTK/Qt & like toolkits).

I would suggest using a supported release of Ubuntu, unless you're off-line. Few people will be able to help you, as most of us won't have a *lucid* system handy to query packages, and online tools don't provide support for anything that old.

Also consider Ubuntu-MATE, as the GTK2 libs used by GNOME of that era, where forked, names changes (to avoid clashes with GTK2/GTK3) then it was progressively streamlined (ie. legacy code removed improving efficiency), and updated (to modern ideas & for modern GTK3 compatibility). MATE is no longer GTK2 but fully GTK3, but is still GNOME/GTK2 like. That maybe your best & safest choice.

---

### Post by Frogs Hair on 2020-09-25
You could try Opera 12. 
[https://get.opera.com/ftp/pub/opera/linux/1212/](https://get.opera.com/ftp/pub/opera/linux/1212/)

---

### Post by TygerTung on 2020-09-25
10.04 was the best really, it was so fast and stable. The more modern versions are so much more resource hungry for no more visible utilitie, maybe less as the desktop environment was really easy to customise.
Bring back 10.04!

I used to use it on my P4 3.2 GHz box and it ran great. Not as good with more modern versions. I still have that machine.

---

### Post by Impavidus on 2020-09-26
> **tpprynn20 said:**
> ... but I'm not bothered about security ...But *I* am bothered about *your* security. I don't want *your* computer to turn into a bot that participates in a DoS-attack on *my* favourite website.

> **TygerTung said:**
> 10.04 was the best really, it was so fast and stable. The more modern versions are so much more resource hungry **for no more visible utilitie**, maybe less as the desktop environment was really easy to customise.
Bring back 10.04!

I used to use it on my P4 3.2 GHz box and it ran great. Not as good with more modern versions. I still have that machine.

I agree with that one. Most changes to the desktop environment and window manager are eye candy that I disable. Similarly, modern websites aren't any more usable than those of 20 years ago, despite taking 1000 times more memory and 100 times more bandwidth, but the old ones have been taken off-line.

I must add though that even as the Ubuntu desktop environment isn't very customisable, some other flavours are. I use Xubuntu.

---

### Post by TheFu on 2020-09-26
There must be at least 20 remote root attacks against 10.04 today. These are well-known and scanned constantly on the internet.

Feel free to use any OS you like on a non-networked system or on a network that is 100% controlled by you, with an air gap to the outside.

No way should this OS be connected to the internet.  Trying to support old, end-of-life releases just isn't worth the time for any professionals for 50-1000 reasons. Sorry.

When the system gets hacked, don't be surprised.

I agree that 10.04 was the best OS made. It "felt" like Unix. It was stable. But it had flaws that we didn't know until later. Those flaws were not fixed.  If you prefer the GUI from that time, just pick a GUI that hasn't changed in 20+ yrs, but is still maintained, like fvwm. We get the completely patched, current, OS libraries with newest, most secure (as far as we know), applications, and we don't have to deal with a bloated GUI or re-re-re-relearn stuff because a new DE team decided to make things "simple" for noobs.   We do still have to put up with core OS updates like systemd, netplan, and a few others that most end users never see, but those can be integrated.

BTW, the new Firefox requires pulseaudio, which 10.04 didn't have.  Running an old browser is a huge security risk.

OTOH, all these risks would go for an interesting news article.  "I ran an unpatched OS from 2010 on the internet and was only hacked 85 times in 30 days" is the title I'd start with.  Then you could write 30 sub-articles about each of the successful hacks.  Might make for interesting reading.  Or perhaps the box is behind a router and only gets hacked 3 times.  That would be useful too.

---

### Post by TygerTung on 2020-09-26
Not to mention that 10.04 was designed to boot in 10 seconds! Of course it takes longer as the bio has to boot up and then grub has to select what you're booting, but maybe you can get grub to autoselect to save time.

---

### Post by uninvolved on 2020-09-27
Doesn't that computer have at least 4 GB of RAM and an i5? I just looked it up. It'll run a modern OS just fine and actually be secure.

---

### Post by Frogs Hair on 2020-09-27
If you like Gnome 2 try [Ubuntu Mate]("https://ubuntu-mate.org/features/")

---

### Post by TygerTung on 2020-09-27
I have tried Ubuntu Mate, but it ran so much slower than 10.04

Maybe it would be worth trying 10.04 to see if I really do get hacked. How would I know if I have been, and how would a "hacker" know my computer was there so they could hack it. Why would they bother, if the only thing on it was an OS? Would having one vulnerable machine on my home network be dangerous for other machines on my home network?

---

### Post by Impavidus on 2020-09-28
On my current laptop (from 2011) I originally ran Ubuntu 10.04. It booted in 23 seconds. Now I run Xubuntu 20.04. It boots in 35 seconds. Slower, but acceptable.

Who would a hacker care about your computer? Even if they're not interested in stealing or kidnapping your data, they may be interested in your network connection to send spam or they may want your processing power to mine cryptocurrency using your electricity. I can think of several other applications. So just don't use 10.04. It's dead.

---

### Post by rsteinmetz70112 on 2020-09-28
As far as I could find quickly that machine would have the following specs:

Lenovo ThinkPad X201 Tablet
Hard Drive: 320GB
RAM Memory: 4GB
CPU Processor: Intel i5-520U @ 1.07 GHz
OS: Windows 7 Pro

I have an IBM Thinkpad X31 my wife uses for email and it still works although I replaced the Hard Drive with an SSD. It currently runs Windows but has run Ubuntu up to 16.04 acceptably (faster than Windows). If I looked into it I'm pretty sure one of the 64 bit low resource distributions of Linux would work fine. That will allow you to keep your computer patched well into the future. If your machine doesn't have 4GB you should upgrade it to maximum RAM.

---

### Post by uninvolved on 2020-09-28
Lubuntu 18.04 LTS still has some support time left. It's nice and light, and LXDE is capable of being quite beautiful while staying out of your way.

---

### Post by ActionParsnip on 2020-09-28
Dude I'm running Lubuntu 20.04 on 1 core and 1Gb RAM. Your system can run Windows 7 64bit so can run the latest versions of Ubuntu with no problems. I recommend using 20.04 as it is LTS and supported until April 2025.

---

### Post by TygerTung on 2020-09-30
I'm running Lubuntu 20.04 on my ASUS netbook which only has a 1.6 Ghz Duel Core Atom and 2 GB of ram and it runs ok. I guess we can't go back, even though we might want to.

---

