---
title: "Pcmcia wifi card for Dell lattitude"
date: 2008-05-02
forum: General Help
---

### Post by BLTicklemonster on 2008-05-02
I have searched but wasn't really sure what I was looking at, being new to laptops, so I'll just come right out and sound noobish and ask here.

I have a Dell Latitude c610 (the bottom of the laptop has a sticker that says c510/c610, but I suspect that it's a c610). It has no wireless capability, but I would like to be able to use it in wifi spots if I'm out and about. Am I right in suspecting that this can be done by using a pcmcia wifi card? Is there even such a thing? Does anyone have a laptop like this, and have done this who can give me an idea what I have to look forward to, as in, what cards work best (cheap card, please, I'm a govt worker) and what does it take to set it up? I will have to be in the wild with it while setting it up, of course, as I use a wired network at the house, so instructions that are simple enough for a (all together now) _*govt employee to follow and thorough enough to get it right the first time*_ so that I can just print and take along with me would be great.

Thank you for your time.

---

### Post by Monicker on 2008-05-02
I used to have a latitude c6xx model at a previous job.  This card should work in it.

[http://www.airlink101.com/products/awlc4030.html]("http://www.airlink101.com/products/awlc4030.html")

I also use it in my Thinkpad.  It works out of the box with Ubuntu 8.04

---

### Post by karuptdata on 2008-05-02
Hello,

Yes you can pick up a pcmcia wireless card for little of nothing now days, if you arent against shopping online may i suggest visiting pricewatch.com. They keep track of the latest sales from several online tech stores. 

You will want to use ndiswrapper to get the wifi card working under Ubuntu but this is actually fairly easy as well. Check out [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) its pretty exhaustive on directions to setup ndiswrapper and your wifi card.

---

### Post by sharpeg on 2008-05-02
I have exactly the same machine as you and **stongly**advise against the PC card route. I have been using a PC card I bought from PC world for around £20 and although it seemed fine, it casued windows to crash dramatically and seems to be at least part of the cause of Hardy crashing, hanging and generally behaving badly. It also acheives fairly low throughput (can only acheive 2Mb/s on a broadband test as opposed to 6.5 on a wired network).

I have just installed a 'propper' Dell internal mini-pci wireless card and that is working perfectly in windows with a higher throughput (around 3.5 Mb/s). I have yet to try it in Hardy as I need to do a fuill re-install as I am one of the people who has been having major lock-ups with it.

The card was around £10 on ebay and took me 2 minutes to fit it and five minutes to download and instal the driver. It also avoids having the lump sticking out of the side of your machine which is easy to knock against things.

HTH

Geoff

---

### Post by BLTicklemonster on 2008-05-02
Oh, okay, so um... tell me more! Like I guess I go to dell.com to purchase it, maybe? Where can I go to find out how to open this "Chinese mystery box" called a laptop? (I have yet to find one that was "undo this, and voila" simple) If I can put something ***inside*** the computer, I'm all for it. 

And unless its gNewSense, I can't get hardy 8.4 to even boot from a live cd anyway, so I'll most likely stick with gutsy for a long time. But reinstalling doesn't bother me. I don't really have anything on the laptop that I can't drop on a thumb drive and store for later use. (my sister gave me the laptop for getting another one going, or I wouldn't even bother to own one, but now that I have it, it's pretty cool to have around, so I'd like to get more use out of it.)

I wonder if I can get a dvd/rw or even a dvd cd/rw for this laptop? That'd be cool.

*edit: just found the service manual.

---

### Post by sharpeg on 2008-05-02
OK. First things first, the fitting. This was one of the simplest things I've done with PC hardware in years.

[LIST]
Shut down the PC and remove the battery
Turn the PC over
There is a large square panel with three screws. 
Unscrew the screws (the two large ones stay attached to the cover, the smaller one comes out altogether.
Gently remove the cover (it should come off easily, if not, you may not have removed the screws enough)
You will now see the the memory (one or two sticks) and a space where the wifi card will go. You will see two wires. These are the aerial.
Take the card and slide it into the socket until the two retaining clips click into place and then press the aeirail leads into the 'sockets' on the board.[/LIST]

As I say, this took me less than 5 minutes, much to my surprise.

Under Win XP, it just worked when I booted it up. Under Hardy, it knew it was there but I had to tell it to install a restricted driver. Took about ten minutes but you need an internet connection to download the files. Hopefully you can connect to your router via the Ethernet socket to do this.

As for where to buy it, I wouldn't go to Dell. I'm sure you can get it from there but it would probably cost several times more than necessary. I got mine from e-bay. This is the one I bought:

[http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&rd=1&item=220227047487&ssPageName=STRK:MEWN:IT&ih=012](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&rd=1&item=220227047487&ssPageName=STRK:MEWN:IT&ih=012)

An example from a US seller is here:

[http://cgi.ebay.co.uk/Dell-Latitude-C610-C640-Wireless-WIFI-Mini-PCI-card-B-G_W0QQitemZ350055406412QQihZ022QQcategoryZ45001QQrdZ1QQssPageNameZWD2VQQcmdZViewItemQQ_trksidZp1638Q2em122](http://cgi.ebay.co.uk/Dell-Latitude-C610-C640-Wireless-WIFI-Mini-PCI-card-B-G_W0QQitemZ350055406412QQihZ022QQcategoryZ45001QQrdZ1QQssPageNameZWD2VQQcmdZViewItemQQ_trksidZp1638Q2em122)

Although if you look around you can probably get a dell branded one.

As for the installation, if you're happy with Gusty I would stick with it for now. I'm trying to get Hardy working just becasue I hate to be beaten! Much like yourself, I don't keep anything important on the laptop. I keep most of my files on a NAS box and use the laptop as a 'terminal' to access my main PC which is kept in a cupboard!

If you are having trouble booting from the disk, have you tried making another one? I actually have to make three copies before I had one that actually worked. Don't know if the problem is with the download or burning process but I have had the same problem before.

Anyway, good luck and if I can be of any further assistance, please let me know.

---

### Post by BLTicklemonster on 2008-05-09
Excellent. I will be ordering one soon, and putting it in. I may never get a chance to use it, but I want it in case I ever do.

I appreciate all your help with this, fellows.


Sharpeg, I'll be hardwired to the internet to download the restricted driver in Gutsy. Once that is done, I will most likely go to some wifi place and see about getting it to work. 

I ain't never done none of this here stuff, therefore, any guidance in this area would be greatly appreciated so that I can perhaps have some printed material with me when I try to get it going.

---

### Post by ugm6hr on 2008-05-09
I don't have the same laptop, but I have a Dell 500m with a mini-PCI slot.

It should take any mini-PCI wifi card, as Dell don't put BIOS restrictions on (unlike HP/Compaq).

So - to ensure maximum compatibility with Ubuntu, I'd suggest an Atheros or probably preferable Intel card.

I suspect the Dell branded ones are Broadcom cards - which are better avoided.

---

### Post by sharpeg on 2008-05-09
Yep, I've got a Dell branded one and it appears to be a Broadcom. When I was looking on ebay there did seem to be some 'genuine dell' ones listed that said they were Intel.

Having said that, mine works perfectly and I am now getting high speeds (measured up to 4.8 Mbps using a Braodband speed test) but slightly lower than using the wired connection (around 6.2Mbps peak) but I suspect that I could improve on that with some tweaks.

Ticklemonster - as for written instructions, to be honest there aren't any. I put it in, installed the driver and it just worked! The only instructions you should need will be the ones you will find at the cybercafe, library, MacDonalds or wherever you are trying to use it and these vary from place to place but are all fairly simple. 

While you're still at home and after you've done all the installs, unplug your wired connection, reboot and you should see that your little network icon (a little picture of a PC) is replaced with an annimated circle as it searches for wireless networks. So long as you see this, you shouldn't have any problems connecting when it does find a wireless network.

Actually, one thing you might have to do is tell the BIOS that the card is there and you want it turned on. This is easy. When you boot up, press F2 while is is loading the BIOS and go in to the BIOS setup. Navigate to the page that shows the Network adapters (use alt-P and I think it's page 3) and make sure that the onboard wireless adapter is enabled.

I know it sound unlikly that it's this easy but honestly, this was all new to me and it really was that simple!

---

### Post by BLTicklemonster on 2008-05-11
So this is what I want?

[http://www.amazon.com/gp/offer-listing/B000BI23V0/ref=dp_olp_2](http://www.amazon.com/gp/offer-listing/B000BI23V0/ref=dp_olp_2)

---

### Post by ugm6hr on 2008-05-11
> **BLTicklemonster said:**
> So this is what I want?

[http://www.amazon.com/gp/offer-listing/B000BI23V0/ref=dp_olp_2](http://www.amazon.com/gp/offer-listing/B000BI23V0/ref=dp_olp_2)

That one is very well supported by Linux.  I had a 2100 card (which I think is the same thing but 802.11b only), which works great with an open source Intel driver.

There is even a report of a C510 user who gives it 5* with Ubuntu 7.10 ([http://www.amazon.com/gp/pdp/profile/AJA20XE1WO09E/ref=cm_cr_pr_pdp](http://www.amazon.com/gp/pdp/profile/AJA20XE1WO09E/ref=cm_cr_pr_pdp))

I know the newer Dell Ubuntu machines use the 3945 (with 802.11n support), but I think the 2200 is probably better supported in Linux.

So I can't see you having any problems with it...  Shuld be a plug in and turn on job.  Of course, there is also a 1* report from someone (who presumably got a dud), so you never can tell.

---

### Post by BLTicklemonster on 2008-05-11
I appreciate it everybody. I'll order that one.

---

### Post by BLTicklemonster on 2008-05-15
Got it today. Booted Ubuntu, and went to network, and it showed wireless connection set to roaming mode, so that's probably there. XP was another beast. Wasn't found automagically. Wasn't on the install cd. Had to google it and got it here:
[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=N&Inst=Yes&ProductID=1637&DwnldID=15800&strOSs=44&OSFullName=Windows*%20XP%20Professional&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=N&Inst=Yes&ProductID=1637&DwnldID=15800&strOSs=44&OSFullName=Windows*%20XP%20Professional&lang=eng)

(for future reference, thank you)

Installed, and it says it can't find a wireless connection, so it's working.

Now to go find a wi-fi spot. Maybe Schroeder's New Deli out in Armuchee...

Thanks for all your help, guys!

---

### Post by BLTicklemonster on 2008-05-15
Lmao, this is cool. I'm in downtown Rome, and I looked at the icon, clicked it, and there's like 8 different wifis listed. I connected to the local govt wifi, and have 3 bars.

Like I said, thanks a ton, guys!!!

---

### Post by ugm6hr on 2008-05-16
Glad it worked :)

---

### Post by sharpeg on 2008-05-16
Gald it all worked so well. See what I mean about it 'just working'!

---

### Post by BLTicklemonster on 2008-05-16
Yes! Just boot Ubuntu and viola. 

Boot XP, and 

a. it can't find drivers from the hard drive or online (wired)
b. can't find drivers from the cd
c. finding the drivers took some serious (well I'm retarded so work with me here) twiddling around with my search terms in google.

So yeah, I'm digging Ubuntu even more now.

---

