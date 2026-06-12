---
title: "Linux Machine Refurb"
date: 2016-04-05
forum: General Help
---

### Post by uzzo23 on 2016-04-05
Hello folks! My linux machine died on me a good while back. It was either a MOBO or CPU failure. I found an old box at the garbage dump of all places that still had an old biostar board in it. So I carried it home and took my dead board out and put this one in. To my amazement, it booted up and ran. But it's an old board with a pentium 4 processor. It freezes up when watching videos and other more labor intensive applications. So I decided I was going to get a new MOBO and CPU to try and speed things up a bit. I've been on newegg so long today that I have a headache. It seems that it's much harder now to find a board that will fit a full atx tower. And most of the ones I did look at didn't even have video chipsets in them. And then reading reviews on some that have the UEFI instead of BIOS. A few of the reviews I read said that UEFI didn't play well with linux. So I was just wondering if anyone here could put me on a sub $150.00 upgrade that will play nice with linux.

---

### Post by oldfred on 2016-04-05
I built two new UEFI systems in the last year & half.
One as Asus Z97 and the other Gigabyte Z170.
No issues with 14.04 on Z97 with Intel i5 nor Z170 with new Intel i5 6500 with 16.04.
Both chips include video, so I do not game and Intel video is more than enough for standard use.

UEFI is more complex as it is both new UEFI using gpt partitioning and has a legacy/CSM/BIOS mode for MBR partitioned drives.
I had 5 or 10 settings in UEFI to change.

I figure a bit better CPU saves the video card and justify the cost that way, at least to myself. Not sure it would work on spouse or not.

---

### Post by pqwoerituytrueiwoq on 2016-04-05
video is part of the cpu now days, unless you look at the AM3+ socket
if you are just using it for basic tasks i suggest something like this
it is not worth getting less than 4gb ram, the second stick is practicality 1/2 off
this board does not use all 9 mounting holes, not as wide at a normal ATX board, if you you need wake on LAN in linux look for another board (i know from experience)
there are some $50 refurbished motherboards i saw on newegg, if your case supports micro atx (most ATX cases do) you can save some money
[TABLE]
[TR]
[TH="colspan: 2"]Item[/TH]
[TH]Quantity[/TH]
[TH]Price[/TH]
[/TR]
[TR]
[TD][IMG]https://ssl-images.newegg.com/ProductImageCompressAll/20-226-691-05.jpg[/IMG][/TD]
[TD][Mushkin Enhanced ECO2 8GB (2 x 4GB) 240-Pin DDR3 SDRAM DDR3L 1600 (PC3L 12800) Memory Model 996988E]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820226691")[/TD]
[TD="align: center"]1[/TD]
[TD="align: right"]$31.99
[Add to cart]("http://secure.newegg.com/Shopping/AddToCart.aspx?Submit=ADD&ItemList=N82E16820226691%7C1")[/TD]
[/TR]
[TR]
[TD][IMG]https://ssl-images.newegg.com/ProductImageCompressAll/13-157-501-04.jpg[/IMG][/TD]
[TD][ASRock ASRock Fatal1ty Gaming Fatal1ty Z97 Killer LGA 1150 Intel Z97 HDMI SATA 6Gb/s USB 3.0 ATX Intel Motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813157501R")[/TD]
[TD="align: center"]1[/TD]
[TD="align: right"]$83.00
[Add to cart]("http://secure.newegg.com/Shopping/AddToCart.aspx?Submit=ADD&ItemList=N82E16813157501R%7C1")[/TD]
[/TR]
[TR]
[TD][IMG]https://ssl-images.newegg.com/ProductImageCompressAll/19-117-545-02.jpg[/IMG][/TD]
[TD][Intel G3260 3MB Haswell Dual-Core 3.3 GHz LGA 1150 BX80646G3260 Desktop Processor]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819117545")[/TD]
[TD="align: center"]1[/TD]
[TD="align: right"]$58.49
[Add to cart]("http://secure.newegg.com/Shopping/AddToCart.aspx?Submit=ADD&ItemList=N82E16819117545%7C1")[/TD]
[/TR]
[TR]
[TD="colspan: 3"]Subtotal:[/TD]
[TD="align: right"]$173.48[/TD]
[/TR]
[TR]
[TD="colspan: 3"]Shipping + Tax:[/TD]
[TD="align: right"]$2.99[/TD]
[/TR]
[TR]
[TD="colspan: 3"]Grand Total:[/TD]
[TD="align: right"]$176.47[/TD]
[/TR]
[TR]
[TD="colspan: 4, align: right"][Add all to cart]("http://secure.newegg.com/Shopping/AddToCart.aspx?Submit=ADD&ItemList=N82E16820226691%7C1,N82E16813157501R%7C1,N82E16819117545%7C1")[/TD]
[/TR]
[/TABLE]

---

### Post by uzzo23 on 2016-04-05
> **pqwoerituytrueiwoq said:**
> video is part of the cpu now days, unless you look at the AM3+ socket
if you are just using it for basic tasks i suggest something like this
it is not worth getting less than 4gb ram, the second stick is practicality 1/2 off
this board does not use all 9 mounting holes, not as wide at a normal ATX board, if you you need wake on LAN in linux look for another board (i know from experience)
there are some $50 refurbished motherboards i saw on newegg, if your case supports micro atx (most ATX cases do) you can save some money
[TABLE]
[TR]
[TH="colspan: 2"]Item[/TH]
[TH]Quantity[/TH]
[TH]Price[/TH]
[/TR]
[TR]
[TD][IMG]https://ssl-images.newegg.com/ProductImageCompressAll/20-226-691-05.jpg[/IMG][/TD]
[TD][Mushkin Enhanced ECO2 8GB (2 x 4GB) 240-Pin DDR3 SDRAM DDR3L 1600 (PC3L 12800) Memory Model 996988E]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820226691")[/TD]
[TD="align: center"]1[/TD]
[TD="align: right"]$31.99
[Add to cart]("http://secure.newegg.com/Shopping/AddToCart.aspx?Submit=ADD&ItemList=N82E16820226691%7C1")[/TD]
[/TR]
[TR]
[TD][IMG]https://ssl-images.newegg.com/ProductImageCompressAll/13-157-501-04.jpg[/IMG][/TD]
[TD][ASRock ASRock Fatal1ty Gaming Fatal1ty Z97 Killer LGA 1150 Intel Z97 HDMI SATA 6Gb/s USB 3.0 ATX Intel Motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813157501R")[/TD]
[TD="align: center"]1[/TD]
[TD="align: right"]$83.00
[Add to cart]("http://secure.newegg.com/Shopping/AddToCart.aspx?Submit=ADD&ItemList=N82E16813157501R%7C1")[/TD]
[/TR]
[TR]
[TD][IMG]https://ssl-images.newegg.com/ProductImageCompressAll/19-117-545-02.jpg[/IMG][/TD]
[TD][Intel G3260 3MB Haswell Dual-Core 3.3 GHz LGA 1150 BX80646G3260 Desktop Processor]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819117545")[/TD]
[TD="align: center"]1[/TD]
[TD="align: right"]$58.49
[Add to cart]("http://secure.newegg.com/Shopping/AddToCart.aspx?Submit=ADD&ItemList=N82E16819117545%7C1")[/TD]
[/TR]
[TR]
[TD="colspan: 3"]Subtotal:[/TD]
[TD="align: right"]$173.48[/TD]
[/TR]
[TR]
[TD="colspan: 3"]Shipping + Tax:[/TD]
[TD="align: right"]$2.99[/TD]
[/TR]
[TR]
[TD="colspan: 3"]Grand Total:[/TD]
[TD="align: right"]$176.47[/TD]
[/TR]
[TR]
[TD="colspan: 4, align: right"][Add all to cart]("http://secure.newegg.com/Shopping/AddToCart.aspx?Submit=ADD&ItemList=N82E16820226691%7C1,N82E16813157501R%7C1,N82E16819117545%7C1")[/TD]
[/TR]
[/TABLE]


I was trying to stick with the AMD platform so maybe that's why I had so much trouble. There used to be a member here that had as his avatar the intel logo. But instead of it saying "intel inside" it said "evil inside". I thought it was very humorous and true from some of the things I've read about that company. The boards that I looked at today not only had no video chipset. But there was also no vga input to plug your monitor in. So I guess I'm just behind the times. Where do you plug your monitor in at on one of these boards? Thanks to both of you for the advice.

---

### Post by pqwoerituytrueiwoq on 2016-04-05
for linux systems i don't even suggest AMD systems anymore, due to the GPU driver state it is just not worth it, unless you are planning to use a Nvidia GPU then it does not matter
if you want a cheap AMD system look for a APU system, Intel's GPU linux support is in much better shape, in my exp even if the AMD GPU is actually better due to the driver the intel GPU wins
I consider anything sandy bridge or later on the Intel side perfectly acceptable, excluding there atom CPUs
there are plenty of affordable micro ATX H81 boards available, just add a 1150 socket Pentium class CPU and you are good to go, just check the motherboard's LAN and audio chipsets for linux compatibility

if you still want to go AMD, here are the CPU's with a GPU built in
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007671%20600372025%20600484725%20600166681&IsNodeId=1&bop=And&Order=BESTMATCH&PageSize=30](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007671%20600372025%20600484725%20600166681&IsNodeId=1&bop=And&Order=BESTMATCH&PageSize=30)

---

### Post by mastablasta on 2016-04-06
> **uzzo23 said:**
>  A few of the reviews I read said that UEFI didn't play well with linux. 

no, the Microsoft secure boot might cause issues not UEFI. Linux was one of the first to support UEFI even before windows did.

---

### Post by mastablasta on 2016-04-06
> **pqwoerituytrueiwoq said:**
>  in my exp even if the AMD GPU is actually better due to the driver the intel GPU wins


that doesn't make sense. AMD GPU performance is a lot better than intel's even on APU. if you compare APU with similar price and speed. for example I have E450 which at the time it competed with one of intel atoms (forgot which one). the difference was that atom used less power, but the intel GPU was a lot worse than the chip in AMD which can run 2005/2006 games at descent rates.

I doubt that intel GPU is on par with chip on AMD A series. this shows about the same: [http://www.phoronix.com/scan.php?page=article&item=amd_kaveri_7850k&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_kaveri_7850k&num=1)
CPU is so so and in many cases intel wins and probably also wins on power consumption. but in the GPU segment they are behind AMD.

while new opensource amdgpu driver is already almost on par with fglrx which provided descent experience on Linux (compared to windows) on older AMD chips.

---

### Post by pqwoerituytrueiwoq on 2016-04-06
> **mastablasta said:**
> no, the Microsoft secure boot might cause issues not UEFI. Linux was one of the first to support UEFI even before windows did.

also secure boot is not enabled by default on retail motherboards, if it were there tech support and RMA request would be high for anyone trying install windows 7 or XP (i really hope nobody is still putting that on computers)

@mastablasta that seems odd last a did my own comparison my laptop's Intel Pentium B970 was able to easily beat a desktop class APU (which one was that, i think it was a more budget line one...), i compared it using supertuxkart had tried both opensource and fglrx on the latest kernel which IIRC was 3.2rc* at the time

---

### Post by oldfred on 2016-04-06
I do not follow AMD, much.
But issue seems to be drivers, particularly older ones. And they are making major changes, but support then to get older driver can be an issue.
Nvidia seems to freeze an older driver for older cards, so new features only on new card are in new driver. New features would not work on old card anyway. But older drivers are in repository.
 16.04 Release notes
When upgrading to Ubuntu 16.04 from a previous release, both the fglrx driver and the xorg.conf will be removed, so that the system is set to use either the amdgpu driver or the radeon driver (depending on the available hardware). 
With 15.10 Release notes
AMD's fglrx driver does not work with the current kernel
The fglrx driver is now deprecated in 16.04, use radeon and amdgpu

---

### Post by uzzo23 on 2016-04-06
> **pqwoerituytrueiwoq said:**
>  if it were there tech support and RMA request would be high for anyone trying install windows 7 or XP(i really hope nobody is still putting that on computers)

Hey, I resemble that statement! I had a windows 7 disk that was given to me. So when I built this computer I'm on now. That's what I put on it because there were just a few things that I needed software for that I couldn't do with ubuntu. Although I can't even remember what that was now. I'm just getting sick and tired of the windows 10 icon in my system tray trying to lure me in to upgrade for free it says. It runs in the background all the time now as an executable program. I just don't want to do it. I don't know how any of you guys feel about it. But I find Bill Gates to be a detestable human being and ain't nothing "free" with him and his company's products. That's why I want to get this old linux box running again. I started using it when I built it (my first build) at ubuntu version 8.04. I worked my way up to 11.10 I believe it was and was having audio issues. I submitted a bug report about it that I don't think ever got solved. So I went back to 10.04 and lost everything. So I had to start all over again. That's about when it quit working and the subsequent dump find. It just wouldn't play videos and was constantly freezing up. CPU would be at 100 percent or pretty close to it. Someone here suggested I try either xubuntu or lubuntu and that might improve. I can't really remember which one I installed now. But I haven't used it in quite some time now. So once I get it running again I'll probably be here on a regular basis asking dumb questions like when I first started since I've probably forgotten most of what little I learned in my early days with ubuntu. On a side note. I'd like your opinions on this I found yesterday after hours of exhaustive looking for a MOBO/CPU combo. It's a Dell refurb with a core 2 duo and 2 GB of RAM. An 80GB HD with no OS. I've emailed the company that is selling it to see of I can use my SATA HD with it. It would be a much cheaper alternative to buying the components to fix the one I have.

[http://www.newegg.com/Product/Product.aspx?Item=9SIA8WV3WC6893](http://www.newegg.com/Product/Product.aspx?Item=9SIA8WV3WC6893)

---

### Post by grahammechanical on 2016-04-06
ATX is a specification for motherboards that was designed by Intel many, many years ago. Specifications like this standardize motherboard manufacture. If you have a case that can take ATX style motherboards then any ATX motherboard will fit in that case regardless of who the manufacturer was.

Furthermore, because of specifications like this motherboards that meet other specifications will also fit into an ATX case. The exception to this is AT motherboards which are physically larger than ATX motherboards. Case manufacturers will provide fixing points (holes) for the variety of motherboard sizes that exist from ATX sized motherboards down to the much smaller mini-ITX sized motherboard.

There is an illustration in this wiki page that shows how motherboards smaller than ATX can be fixed into an ATX case.

[https://en.wikipedia.org/wiki/ATX](https://en.wikipedia.org/wiki/ATX)

The placement of the rear connectors is also standardized so that the different board sizes have the connectors grouped together in a similar grouping to the other sized motherboards. The case will have a backplate to accept these connectors. The backplate is removable and there are available inter-changeable backplates to fit standard cases.

Just make sure that you do not get bedazzled by all the different motherboards for sale that you buy a motherboard too large for the case. I did that once. I had decided on a case and motherboard and then changed my mind about the motherboard not noticing that my new choice was a size that did not fit the case I was buying. Thankfully, the shop owner was willing to replace the case for a different one. 

Regards

---

### Post by pqwoerituytrueiwoq on 2016-04-06
it is a core 2 duo those should have SATA HDDs in them, i would expect it to be a sata I link, so 150MBps max,
i would recommend adding a Nvidia GT 610 or GT 520 (they are the same card), especially if you want to run full ubuntu
given it is a full size system you can use 2 HDDs in it, user one for /home and the other for / that should allow for greater I/O activity

---

### Post by uzzo23 on 2016-04-06
> **pqwoerituytrueiwoq said:**
> it is a core 2 duo those should have SATA HDDs in them, i would expect it to be a sata I link, so 150MBps max,
i would recommend adding a Nvidia GT 610 or GT 520 (they are the same card), especially if you want to run full ubuntu
given it is a full size system you can use 2 HDDs in it, user one for /home and the other for / that should allow for greater I/O activity

I didn't get an email response from them so I found a phone number and called them. The guy I talked to did verify that it was a SATA HD and that mine should work fine in that box. So I went ahead and ordered it, it's on the way. I don't know anything about setting up 2 different HD's. Everything is on this 500GB SATA seagate barracuda that's in the box with the bad MOBO. So I'll give it a whirl and if I have any problems getting it set up. I'll post it here, thanks for all of the advice. I really appreciate it!

---

### Post by pqwoerituytrueiwoq on 2016-04-07
it is just like doing multiple partitions on one hdd, just you have 2 drives to use
if you dont use the 80gb and find yourself using swap, put that 80gb drive in and put a swap partition on it, it will be a night and day difference, not as much as more ram, but still

---

### Post by uzzo23 on 2016-09-10
Hi folks, just wanted to update this thread. I got this box running and it's been working fine up until last week. My wife had been using it and had not been shutting it down properly. I don't know if that's what caused it. But it won't connect to the internet now. I'm not having any connectivity problems with my other computers, just the Linux machine. Any advice would be greatly appreciated.

---

### Post by pqwoerituytrueiwoq on 2016-09-10
you should start a new thread and post the specs of the system, eg lsusb and lspci

that said i am going to assume you are using a wired connection
i have had some onboard controllers act up over the years, for example completely disappear from the system
in that even i have managed to get them to reappear by completely powering down the system, and i mean completely (shutdown and cut power for a few seconds)
this is only a temporary fix as it happens again days, weeks, or months later
if you have a issue like that you should get a new PCI or PCIe NIC card (a PCI card can not do full gigabit) used old server NICs are good quality and commonly cheap on ebay

---

### Post by uzzo23 on 2016-09-10
> **pqwoerituytrueiwoq said:**
> you should start a new thread and post the specs of the system, eg lsusb and lspci

that said i am going to assume you are using a wired connection
i have had some onboard controllers act up over the years, for example completely disappear from the system
in that even i have managed to get them to reappear by completely powering down the system, and i mean completely (shutdown and cut power for a few seconds)
this is only a temporary fix as it happens again days, weeks, or months later
if you have a issue like that you should get a new PCI or PCIe NIC card (a PCI card can not do full gigabit) used old server NICs are good quality and commonly cheap on ebay

It is a wired connection my friend. The only problem with starting a new thread and posting the output from those commands is I can't post it from that machine. What would be the best way to do it. Normally I would be able to copy and paste it from that machine. But I don't know how I would do it without being able to connect to the internet.

---

### Post by pqwoerituytrueiwoq on 2016-09-10
There is more than one way to bypass that
     
[LIST]
[*][http://www.newegg.com/USB-Flash-Drives/SubCategory/ID-522](http://www.newegg.com/USB-Flash-Drives/SubCategory/ID-522)
[*][http://www.newegg.com/CD-DVD-Blu-Ray-Media/SubCategory/ID-71](http://www.newegg.com/CD-DVD-Blu-Ray-Media/SubCategory/ID-71)
[*][http://www.newegg.com/Product/Product.aspx?Item=N82E16833315091](http://www.newegg.com/Product/Product.aspx?Item=N82E16833315091)
[*][http://www.newegg.com/Product/Product.aspx?Item=N82E16812315001](http://www.newegg.com/Product/Product.aspx?Item=N82E16812315001)
[*][http://www.ebay.com/itm/201370580455](http://www.ebay.com/itm/201370580455)
[*][http://www.newegg.com/Product/Product.aspx?Item=N82E16833166017](http://www.newegg.com/Product/Product.aspx?Item=N82E16833166017)
[/LIST]
 there is also the frowned upon method of using a cellphone to take a picture of the screen

---

### Post by DuckHook on 2016-09-10
> **pqwoerituytrueiwoq said:**
> …there is also the frowned upon method of using a cellphone to take a picture of the screen[-(

---

### Post by uzzo23 on 2016-09-10
> **pqwoerituytrueiwoq said:**
> There is more than one way to bypass that
     
[LIST]
[*][http://www.newegg.com/USB-Flash-Drives/SubCategory/ID-522](http://www.newegg.com/USB-Flash-Drives/SubCategory/ID-522) 
[*][http://www.newegg.com/CD-DVD-Blu-Ray-Media/SubCategory/ID-71](http://www.newegg.com/CD-DVD-Blu-Ray-Media/SubCategory/ID-71) 
[*][http://www.newegg.com/Product/Product.aspx?Item=N82E16833315091](http://www.newegg.com/Product/Product.aspx?Item=N82E16833315091) 
[*][http://www.newegg.com/Product/Product.aspx?Item=N82E16812315001](http://www.newegg.com/Product/Product.aspx?Item=N82E16812315001) 
[*][http://www.ebay.com/itm/201370580455](http://www.ebay.com/itm/201370580455) 
[*][http://www.newegg.com/Product/Product.aspx?Item=N82E16833166017](http://www.newegg.com/Product/Product.aspx?Item=N82E16833166017) 
[/LIST]
 there is also the frowned upon method of using a cellphone to take a picture of the screen

Thank you so much for the advice my friend. I promise I won't use my cell phone to take a picture of the screen. I do actually have a USB/SD card reader. I wonder if that would work as well to save the output to the SD card and then put it in one of my other computers to post it here. So it kind of sounds like it may be a problem with the Ethernet jack itself. For the price of some of those you posted. I may just as well go ahead and buy one just to see if it would work.

---

### Post by pqwoerituytrueiwoq on 2016-09-10
see if the leds blink on the Ethernet port, wiggle it see if they blink (blinking means working; off mean not working)
maybe that cute new kitten chewed up the wire
if the onboard NIC is not visible in lspci it is either disabled in the bios or is failing/failed, see post 16 for possible temporary fix
networking is enabled in the os right? did you test a live cd?
iv seen mold grow on phone wire contacts make sure that did not happen to your Ethernet port

---

### Post by uzzo23 on 2016-09-10
> **pqwoerituytrueiwoq said:**
> see if the leds blink on the Ethernet port, wiggle it see if they blink (blinking means working; off mean not working)
maybe that cute new kitten chewed up the wire
if the onboard NIC is not visible in lspci it is either disabled in the bios or is failing/failed, see post 16 for possible temporary fix
networking is enabled in the os right? did you test a live cd?
iv seen mold grow on phone wire contacts make sure that did not happen to your Ethernet port

Oh yes, it's blinking away. Has been the whole time. I tried opening the terminal up and running lspci and then saving it to this SD card. But I can't get it to work. Yes, networking is enabled. I haven't tried a live CD yet though.

---

