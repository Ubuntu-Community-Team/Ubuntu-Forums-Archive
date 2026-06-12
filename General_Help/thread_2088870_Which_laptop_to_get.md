---
title: "Which laptop to get"
date: 2012-11-27
forum: General Help
---

### Post by cybergalvez on 2012-11-27
Hi all,
I am thinking of getting my kid a new laptop as her dell broke, I am looking at the Lenovo G580 (Intel i5) 15.6" at 6# vs the Lenovo S405 (AMD A6) at 14" and 4#.

I know that the A6 is probably close to an i3 rather than the i5 but it is a nice given it's so light. 

Any suggestions form the collective wisdom? I will be putting either Ubuntu (gnome-shell) or xubuntu (which is what currently runs on her dell laptop right now) with w8 in a virtalbox, as she occasionally uses windows for school

Thanks for any and all suggestions

---

### Post by TheFu on 2012-11-27
I start with any laptop selection by listing all the things that I need the laptop to do and which physical attributes I need it to have.  Then I prioritize these and sort based on those priorities.

For example, do you need "DisplayPort" or USB3 or eSATA connections?
Does GigE wired networking have any priority at all?
Screen resolution?
Battery life?

There are at least 20 other items in my list.  I learned to do this after being extremely disappointed with a laptop previously.  Seems that I hate low resolution laptops. I know this now after going from 1440p to 800p to 1080p laptops over the years. 1080p is the minimal resolution for me.  That is more important than the CPU in my book.

I know this is a crazy idea, but have you considered providing a lower end laptop/tablet and providing virtual machines on the network for her to connect into?  There's a guy in Europe that did this over a year ago and he's been relatively happy. He uses an iPad with a keyboard as the display into his "remote desktop."  Just a thought.

---

### Post by LuciferRex on 2012-11-27
> **TheFu said:**
> I know this is a crazy idea, but have you considered providing a lower end laptop/tablet and providing virtual machines on the network for her to connect into?  There's a guy in Europe that did this over a year ago and he's been relatively happy. He uses an iPad with a keyboard as the display into his "remote desktop."  Just a thought.
Do you, by chance, have a link to that?

---

### Post by cybergalvez on 2012-11-27
> **TheFu said:**
> I start with any laptop selection by listing all the things that I need the laptop to do and which physical attributes I need it to have.  Then I prioritize these and sort based on those priorities.

For example, do you need "DisplayPort" or USB3 or eSATA connections?
Does GigE wired networking have any priority at all?
Screen resolution?
Battery life?

There are at least 20 other items in my list.  I learned to do this after being extremely disappointed with a laptop previously.  Seems that I hate low resolution laptops. I know this now after going from 1440p to 800p to 1080p laptops over the years. 1080p is the minimal resolution for me.  That is more important than the CPU in my book.

I know this is a crazy idea, but have you considered providing a lower end laptop/tablet and providing virtual machines on the network for her to connect into?  There's a guy in Europe that did this over a year ago and he's been relatively happy. He uses an iPad with a keyboard as the display into his "remote desktop."  Just a thought.

all excelent points. aside from the processors weight and size they are very simliar. as for the remote deskop option, not sure that will work for her as she needs more portablity then I think a networked VM would provide her. but still something to think about.

---

### Post by Bartender on 2012-11-27
> **cybergalvez said:**
> I am thinking of getting my kid a new laptop as her dell broke
 
Is the Dell well & truly broken?  What are its symptoms?  

Might be a likely candidate for Ubuntu-ization...

---

### Post by cybergalvez on 2012-11-27
> **Bartender said:**
> Is the Dell well & truly broken?  What are its symptoms?  

Might be a likely candidate for Ubuntu-ization...

The DC jack plug is broken, so the battary won't charge. Apperenlty this seems to an issue with Dells, and it would cost me $380 to fix it. It still works if its plugged in, but that doesn't help her when when needs to take it to school.

---

### Post by varunendra on 2012-11-28
> **cybergalvez said:**
> Hi all,
I am thinking of getting my kid a new laptop as her dell broke, I am looking at the Lenovo G580 (Intel i5) 15.6" at 6# vs the Lenovo S405 (AMD A6) at 14" and 4#.Which A6 model and what's the price difference?

I'm a huge AMD supporter but a recent test with an A6 based laptop disappointed me.

I bought two Asus laptops about the same time in March-April this year - one with Intel B950 *[COLOR="DarkSlateGray"](which is actually an i3-2310 with hyperthreading disabled and L3 cache reduced)[/COLOR]*, the other with A6 *[COLOR="DarkSlateGray"](don't remember the exact model but perhaps it was 3410MX, because base freq. was 1.6 GHz per core)[/COLOR]*. The AMD one also had a discrete 1GB ATI graphics card. I installed Win7 +apps myself on both the laptops and did some crude tests side-by-side. These were -
[LIST]
[*]7-zip extraction of multiple small files (fonts)
[*]7-zip compression of the same extracted files (using 'Ultra', lzma compression)
[*]Video conversion of a small clip
[*]Game performance on Far-Cry2
[/LIST]
From a consumer's point of view, I was expecting much high performance from the AMD one because I had paid much higher price for it (28k INR against 21k INR for the b950 one). Even from a technician's point of view I was expecting the A6 to perform far better because although the base frequencies were only 1.6 GHz per core, it was a quad core featuring 'Turbo core technology' (which is supposed to 'boost' the frequencies when other cores are not in use) while the B950 didn't have even hyperthreading enabled.

However, it was a huge surprise to me that the performance difference in above tests was not only marginal, but was actually in favour of B950! For example, 1m12 sec. average compression time against 1m24 sec. time for the A6. And against all my expectations with quad core, there was a huge difference in video conversion time in favour of B950 - Don't remember the exact timings, but it was more than 50% longer for A6! And to be extra sure, I had repeated all these tests 3-times on each machine, in the same order, with no significant time-difference. The only better performance from the A6 was in the FarCry2 game, which, to my non-professional eyes, was hardly noticible. And even that difference *[COLOR="DarkSlateGray"](if it was a difference at all, and not my prejudice)[/COLOR]* was, I guess, a contribution of the 1GB graphics card.

I did the tests to decide a laptop for myself (both of the above were for the employer I worked for), and I immediately finalized an i3-2330 based one (Asus X54C-SX261D), and with 2+2GB RAM, it is performing much better than I can ask for.

And mind you, running two VMs (eg. Ubuntu 10.04 + XPSP3) simultaneously on top of my 12.04 64bit host is a common scene here, along with 20+ firefox tabs open and some other tiny apps like ktorrent, nload, thunderbird, etc., and oh, I have some fancy compiz effects enabled too (expo, scale, wobbly windows)! Never experienced a lag when I'm on AC power (obviously, the performance goes way-down on battery power, maybe thanks to some power-saving design).

Sorry for the long post, but couldn't resist when saw A6 against i5 !

.

---

### Post by mastablasta on 2012-11-28
does B950 also have some power savings features missing? i mean what about battery life on the two? i wonder if they really save money (intel) wiht these cheaper CPU or are they just seelling i3 overpriced.
 
also interesting that 1GB GPU didn't increase performance substantially.
 
agree with 1st asnwer. you need to define it's usage, what it needs and then go hunting for compatible ones. might not be as easy as it sounds.

---

### Post by varunendra on 2012-11-28
> **mastablasta said:**
> does B950 also have some power savings features missing? i mean what about battery life on the two? i wonder if they really save money (intel) wiht these cheaper CPU or are they just seelling i3 overpriced.I believe the power consumption is almost same on i3 and their B-series derivatives, with the B-series giving slightly more backup due to disabled hyper-threading.

Practically, I didn't compare side-by-side, but I had once tested the B950 one at full brightness, doing normal browsing on firefox, and it ran about 2Hr40min (Win7, with Aero disabled) before showing "Battery Critical" warning (less than 7min remaining).

At another occasion, I used the A6 based one with projector (both laptop screen + vga out working) at normal brightness for about 2Hrs. and it seemed like it could run for at most 15-20 minutes more before I connected it to AC power.

Although this is not a fair comparison, but I think both are fine in terms of power consumption. I didn't check their battery but I'm sure they used the same battery as I have in my current one, which is 4400mAh, and runs my laptop (i3-2330) for about 3Hr15min (or 20 at most) at lowest brightness (normal gedit typing, or running simple terminal commands). I've used it only a few times like that, and whenever my work included frequent and intensive disk read/writes (like file copying), it would drop to less than 3Hrs, but never less than 2:40.

However, IMHO, the i3s are highly overpriced. If I talk about price in INR (1 US$ = Rs.55 approx.), the cost of i3-2310 model laptop was 24,500 INR, when the B950 model was only 21,000 INR. The only difference was CPU. So basically we were paying Rs.3,500 extra just for hyperthreading and 1MB L3 cache! Which is ridiculous considering the fact that the disabling of hyperthreading doesn't really save production cost. The block that provides that function is there, just laser cut-off in B-series, so we can't use it! A **fill-in-the-blaks** marketing strategy by Intel.

The only reason I went for i3 is that I did need those two extra 'virtual-cores' for my VMs and other performance gains. I was never (and perhaps never will be, because of such marketing strategies) an Intel supporter, but I must admit they have really done something very nice with hyperthreading and overall architecture in Sandy-Bridge. It runs very cool and performance, as I stated earlier, is beyond my expectation. I thought of it as just a slightly better Core2Duo, but what I got is almost a quad core if compared to last C2Ds.

.

---

### Post by TheFu on 2012-11-28
> **LuciferRex said:**
> Do you, by chance, have a link to that?

I learned about it on My Linux Rig's website.  Here's that link.
[http://yieldthought.com/post/31857050698/ipad-linode-1-year-later](http://yieldthought.com/post/31857050698/ipad-linode-1-year-later)

BTW, I was interviewed for that website about a year ago and you can find it there too. [http://www.mylinuxrig.com/post/12414840146/the-linux-setup-thefu-enterprise-architect-writer](http://www.mylinuxrig.com/post/12414840146/the-linux-setup-thefu-enterprise-architect-writer)

I should say that I migrated my main desktop from a virtual machine onto a KVM VM about 3 months ago.  It has been fantastic for me.  I've traveled overseas and didn't have to worry about any security issues at boarders with this method.  It isn't 100% perfect, but it is close.  I'm actually remoted into a VM using NX (NX is like ssh+certs+vnc, but much, much, much more efficient) as I type this now.  The only downside is poor video support, no audio support for my setups and there isn't any NX client for Android available. I would prefer to travel with just an Android tablet, but I've been forced to take at least a netbook instead.  Of course, a laptop or full desktop also can connect using NX clients.  I find it great to use a desktop most of the time, then switch to a laptop when driving or a netbook when flying - all connecting securely to the same virtual desktop running remote.  

I just returned from a trip for Thanksgiving about 3 states away from home. The remote desktop worked perfectly, though I did feel that access from a hotel in Istanbul, Turkey was a little faster.

I cannot say that remote desktops are for everyone. There will always be network issues or networks that block most types of traffic, so having port 443 available for ssh use is really important if you are going to be on a network that blocks any traffic.  From the NX remote desktop, I've used VNC to connect to other internal VMs, including a Windows7 Media Center box.

**Anyway, for many of the folks reading here, a cheap, $200 netbook connected to a remote desktop is an option that should be considered.**

---

### Post by cybergalvez on 2012-12-01
well I ended up getting a Leveno s405. Just now getting xubuntu set up on it. so far it looks good. Thanks all for the advice

---

