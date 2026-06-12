---
title: "Building A Barebone Ubuntu Box"
date: 2007-04-07
forum: General Help
---

### Post by Iowa Dave on 2007-04-07
I'm not sure of the right category for this so I am putting it here.

Last month I had sweet success building a barebone computer from scratch for a dedicated Ubuntu box. It took about two hours to put together, including installing 6.06 Dapper, all the updates, and one driver. It cost under $400 for a new computer with advanced capabilities.

I had a monitor, keyboard and mouse already. I bought the following components:

Barebone: MSI MBOX K9VGM-V AMD Socket AM2 This combo includes the case, power supply and motherboard. Features on the motherboard include:
&#8226;  	Support for AMD K8 Athlon 64 / 64X2 / Sempron processor
&#8226; 	VIA K9M890 / VT8237R+ chipset
&#8226; 	2 x 533 / 667 / 800 DDR2 up to 2GB
&#8226; 	1 x PCI-E 16X slot
&#8226; 	1 x PCI-E 1X slot
&#8226; 	2 x PCI slots
&#8226; 	2 x ATA 66 / 100 / 133 IDE connector
&#8226; 	8 Ch. audio
&#8226; 	VIAS3 Unichrome 9 graphic controller; onboard VGA memory up to 64MB
&#8226; 	Realtek 10/100 ethernet onboard
&#8226; 	1 x floppy port / 1 x serial port / 8 x USB2.0 ports

Processor: AMD Sempron 64 3000+ Manila 1.6GHz Socket AM2 Processor Model SDA3000CNBOX. This is a low-cost but very capable processor. 18 months ago it rated true "screamer" status. It is just as fast now as it was then. Besides, you don't need Superman for every job. On the daily desktop, Clark Kent is all you need. 

Memory: CORSAIR ValueSelect 1GB 240-Pin DDR2 SDRAM DDR2 667 (PC2 5300) Desktop Memory Model VS1GB667D2. I checked the motherboard manufacturer's website for compatible memory, which many postings on the 'net strongly indicate is important for happy results.

Hard Drive: Seagate Barracuda 7200.10 ST3250620A 250GB 7200 RPM IDE Ultra ATA100 Hard Drive. Big capacity with a reputation for reliability.

DVD: SAMSUNG 18X DVD±R DVD Burner With 12X DVD-RAM Write, LightScribe Technology Black IDE Model SH-S182M/BEBE

Following directions that came in the MSI package, the whole thing went together smoothly and performed a successful Power On Self-Test ("POST"). After that, I put the Ubuntu CD into the DVD drive, rebooted and ran the installer.

Everything seemed fine until I tried scrolling a window in FireFox. The scrolling was very jerky. I also noticed that the sound seemed a little "off". I figured it was probably a driver problem, and went looking for help.

At first all I found were complaints about jerky scrolling in Linux with the VIA chipset. 

But I quickly discovered that VIA are among the good guys who make their drivers available to Linux users. Soon I made my way to an Ubunto help item with the answers I needed: **[https://help.ubuntu.com/community/OpenChrome]("https://help.ubuntu.com/community/OpenChrome")**. The directions there guided me through installing the VIA drivers. After that my video and audio work fine.

Ubuntu seemed to recognize and hook up with everything else just fine.

The computer is entering its second month of daily use, and performing beautifully. I am not "overclocking" or otherwise turning up the "juice" in this computer. It is running cool and quiet.

I have checked in stores, and believe that a commercial product with the same capabilities would cost much more. Most of what I read about homebuilt computers for Windows tells me that the biggest job is installing the hardware drivers. Team Ubuntu gives us a pretty savvy installer when it comes to hardware. One driver is not too many to have to deal with, especially when the instructions are available from Ubuntu Help.

This post is probably too long, but I wanted to share the story. For $cheap I was able to give Ubuntu a desktop machine to work in that is worthy of the work its programmers put into Ubuntu.

Dave

---

### Post by Sugi on 2007-04-07
I built a rig to test Ubuntu too.  I'm quite happy with the results.  
P3 450 Mhz, 384 Mb of ddr1, 64 mb of ram for the video card, cd drive, 3 gigs harddrive and floppy drive.  
(Future Plans: Looking to add a dvd player, another harddrive and better video/sound card)
This is my barebone rig.  It's working out pretty good.  I'm still working on the sound, but expect for that, everything is pretty smooth.  I'm really enjoying ubuntu. ^_,^  
I thought I should share my story, too
And I didn't have to spend a single penny.

---

### Post by ardchoille42 on 2007-04-08
Nice job Iowa Dave! I stopped buying computers off the shelves many years ago when someone showed me how build my own. It's much cheaper and teaches you a lot about hardware. I think the most I paid for a box I built was $700.00 US, but about half of that was the cost of the video card. Computers are amazingly easy to build from scratch and you have the added benefit of picking and choosing your own components.

---

### Post by Iowa Dave on 2007-04-08
Thanks for the kind words. Sugi, I was already sold on Ubuntu from running a dual-boot installation on an older Windows 98 desktop. This project aimed not to test Ubuntu but to run it all by itself on modern, faster hardware. My home network also serves three Mac desktops and two Windows laptops. My goal on this one was to match or slightly exceed the chip speed and hard drive capacity of the others. That having been done, I find the Ubuntu box meets my needs as well or better. It is my primary working computer now. I use it every day.

ardchoille42 reminded me that it helps when someone shows you how to build your first one. If you don't have access to an experienced builder, a book can give pretty good advice. There are several. I bought _Building the Perfect PC_ by Robert Bruce Thompson and Barbara Fritchman Thompson, published by O'Reilly. My project followed the chapter on "Building a Mainstream PC", but with different hardware. The book also gives examples of building servers, game monsters, media centers and small form factor computers.

The "Mainstream" chapter ends in a really cool way. The authors explain all the steps they took to install Windows, the many hardware drivers, and get it all working. Then, "with all of that done, we blew away our Windows installation and installed the operating system we'll really run on this system, Ubuntu."

---

### Post by Cappy on 2007-04-28
I personally got an AM2 3600+ Brisbane. It's only $65 and it overclocks from 1.9GHz to 3GHz. Overclocking doesn't seem to be too popular for linux users, but I still enjoy it.

---

