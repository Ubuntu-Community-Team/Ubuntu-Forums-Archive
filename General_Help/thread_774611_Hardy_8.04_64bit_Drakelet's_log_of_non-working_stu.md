---
title: "Hardy 8.04 64bit: Drakelet's log of non-working stuff.  Current status: Most things"
date: 2008-04-29
forum: General Help
---

### Post by Drakelet on 2008-04-29
Hi.

I'm having problems.  I am fairly new, but have some experience, and as this is support needed and not questions, I decided to post here, not the newbie board.

I already have two threads on other things, but I'm getting LOTS so decided to put them all in one place.

Firstly, previous threads:
[**[COLOR=#980101][B][ubuntu]**[/COLOR] Intel 536EP, Hardy 64bit - Not working, tried everything I can think of[/B]]("http://ubuntuforums.org/showthread.php?t=772995")
[**     [COLOR=#980101][B][ubuntu]**[/COLOR] Resizing NTFS - claiming I only have 8Mb free, when I have about 40Gb![/B]]("http://ubuntuforums.org/showthread.php?t=772633")
                [**I give up: Which dial-up modems WILL work for Hardy 8.04 (64bit)?**]("http://ubuntuforums.org/showthread.php?t=779213")

I'm running Hardy 64bit, and dual-booting with Windows.  Setup is C2D E6750 @3.00GHz, 2GB RAM, 8800GT.  If you need anything else, ask away.

When I manually unzipped, I couldn't install the modem.
[IMG]http://i268.photobucket.com/albums/jj23/JGibbins92/Ubuntu/make536fail1small.gif[/IMG]

When I tried to use wvdial, I came up with this.
[IMG]http://i268.photobucket.com/albums/jj23/JGibbins92/Ubuntu/wvtest1small.gif[/IMG]

More details on the modem problem, the main one, in the above threads, and below.

Another thing I tried was changing the Visual Effects in Appearance.  It always said "Desktop Effects could not be enabled".

This is maddening.  I want to get rid of Windows damnit!

Thanks in advance.  If you need ANYTHING, please ask.  I want this sorted, and am willing to try anything (within reason of course ;)).

EDIT: From other thread:

I have an Intel 536EP, but I can't get it working whatever I do. I've looked through all the websites, all the guides etc, but nothing seems to get it working. See my other thread on the modem issues.

Does anyone currently have Hardy on modem?  If so, which modem?  If it works, I'll buy it (well, one like it).

EDIT:
If anyone can help, here is my scanModem results:
[http://jgibbins92.googlepages.com/Modem.zip](http://jgibbins92.googlepages.com/Modem.zip)
>                               USB modems not recognized
For candidate card in slot 05:00.0, firmware information and bootup diagnostics are:
 PCI slot    PCI ID        SubsystemID    Name
 ----------    ---------    ---------    --------------
 05:00.0    8086:1040    8086:1000    Communication controller: Intel Corporation 536EP Data Fax Modem

I have actually just found a new, updated driver.  Hopefully that will work.  Wish me luck!!!

EDIT2:

Didn't work.  Tried the 2008 driver from here:
[http://linmodems.technion.ac.il/pack...lippe.Vouters/]("http://linmodems.technion.ac.il/packages/intel/Philippe.Vouters/")
When I did "make 536", it came up with a load of text, then said "Failed to build driver".
This is a screenshot from my previous driver attempt, but I'm pretty sure it's identical, or very similar:
[see image above]

I think some of the problems may be to do with as-yet not installed kernel files or whatever. But I don't know how to install them.

Actually, it would probably be best to keep it to my other thread.
[http://ubuntuforums.org/showthread.php?t=774611](http://ubuntuforums.org/showthread.php?t=774611)

EDIT3:
Did some searching on XMODEM.
According to my Hardware ID from Windows Device Manager, it is an E-Tech PCI56AVP
[http://www.e-tech.nu/producten/faxmodems_pci56avp.htm](http://www.e-tech.nu/producten/faxmodems_pci56avp.htm)
An Intel 536EP (as I said)
[http://xmodem.org/chipsets/intel/intel_536ep.html](http://xmodem.org/chipsets/intel/intel_536ep.html)

FIXED:
A problem I've had from the start: I can't seem to unzip anything from the terminal. I've tried lots of commands following "tar", all with no success.
[image removed - not needed]

This is trying to gunzip scanModem.  I tried a variety of methods.

Also, I heard Tab was supposed to fill in the name.  It never worked.

I've tried changing location and renaming, but neither worked.

---

### Post by Drakelet on 2008-04-30
It's been a day.  Anyone?  Please?

---

### Post by zipperback on 2008-04-30
try this instead:

tar -xvfz intel-536EP.tgz

- zipperback
:popcorn:

---

### Post by wirelessmonkey on 2008-04-30
In all your above examples, your files are on your desktop, but you're running the commands from your home directory. Try this:

~$:tar xvfz ~/Desktop/Intel-536EP.tgz 
for the last example try
~$: gunzip ~/Desktop/scanModem.gz


for each of these, you could just
~$: cd Desktop

then run your commands just like you did in your examples.


Best of Luck

---

### Post by Drakelet on 2008-04-30
OOOOH!!  Thanks.  Because it said "james-desktop", I thought it meant it was the desktop.  Just realised the computer name is "james-desktop".  I feel really stupid now, but hey, I've learnt from my mistakes and won't forget it now!

Will try it in a few mins, will get back to you all then.

---

### Post by Drakelet on 2008-04-30
Right, just tried it.  The whole tar'ing worked fine, can't believe I had the wrong directory!

Still can't install the modem though.  When I type the "make 536" command, I get this:
[see first post for image]

No idea why.  Maybe it's because it's 8.04, and the driver is for 7.04.  But there aren't any newer versions...

When I tried wvdial, it said that I don't have a modem installed.
[see first post for image]

It mentions about setserial.  I have that, but how the hell do I install/run/whatever it?  I read the readme, and it said about putting the rc.serial file in a certain place, but that certain place didn't exist.

Finally, the scanModem.  Again, how exactly do I install/run it?  I did the code and got the Modem folder, but what is everything?  I read most, but still don't fully understand what of it I need.

Thanks, and sorry for my noobyness.  I will learn though, don't worry about that.

---

### Post by Drakelet on 2008-05-01
I have today off so plan to try and get it working today.  But without help I can't. :( I'm completely stumped.  I'm still researching, but can't find anything.

Help!?

Done some research.  Does the Intel 536EP even work on 64bit Hardy!?  Anyone know?

Also, if I wanted to swap from 64bit to 32bit, how would I go about doing it?  Could I just install it over, or would I have to format everything?

Finally, my Windows is on a partition.  Could I format that partition and reinstall Windows, only on that partition, without Windows deleting Hardy?  I know about the bootloader problem, but that is fixable.

---

### Post by Drakelet on 2008-05-01
Still can't get anything working. :(

---

### Post by _duncan_ on 2008-05-04
@Drakelet,

I came by this thread from your other thread entitled "I give up....." because I had some experience with dial-up. But after 3 minutes of loading the huge attachments you posted using my slow dial-up connection, I decided to *give up* (no pun intended).

Users on dial-up are probably the ones who can help you with your modem driver problems. However, I doubt anyone would be willing to wait 30 minutes for the pages to load completely before seeing what the problem is. Maybe you can edit this thread to make it more friendly to dial-up users?

---

### Post by Drakelet on 2008-05-04
Yeah, sorry about that.  Just EVERYONE seems to have broadband now.  But then, taking in mind it's about dial-up... OK, I'm just stupid.  Editing now.

*Slaps self in head*

---

### Post by Drakelet on 2008-05-04
I'm off to bed now.  Bumping for the US crowd. :)

---

### Post by Drakelet on 2008-05-05
_duncan_?  Any chance of some help?

---

### Post by _duncan_ on 2008-05-07
I think the original poster of [_[COLOR="Red"]this[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=471503") thread will be in a better position to help you. In fact they packaged it nicely so users don't even have to compile it. The main complication is you are using 64-bit. I don't know if the driver will work for it. If it doesn't your options are:

1. Install the 32-bit version of hardy and go through the same process.


2. Get yourself a full **_hardware_** modem, preferably those that connect via serial ports (assuming your computer has a serial port). I have yet to see an external hardware modem that doesn't work with linux. Hardware modems don't require drivers to work, so it probably wouldn't matter if you are using 64 or 32 bit Ubuntu.


3. You have 2 options if your computer don't have a serial port:

   3.a Buy a USB-to-serial converter to go with the serial modem.

   3.b Look around for an external USB hardware modem. Search this forum for the exact brand/model to purchase. Just be careful because a lot of external USB modems are not full hardware modems but winmodems.


4. Although possible, I wouldn't recommend replacing your existing winmodem with yet another winmodem, regardless of the chipset it comes with (smartlink, conexant, intel, whatever). You will probably end up with the same problem. Worse, each kernel upgrade will require you to go through the same process of compiling the driver to make the modem work. Add to that the complication of 64-bit.

-----------

The compilation error you are seeing in the 1st post is caused by not having the C compilation libraries installed. The easiest way to do this is to install "build-essential" from the Ubuntu CD. I've seen threads discussing this so I won't replicate the step-by-step here.

-----------

This is as much help as I can give. Most of the info I wrote are available from this forum, waiting to be found. If you haven't done so already, read the "DialUpModemHowTo" wiki (2nd link on my signature). Good luck!

---

### Post by Drakelet on 2008-05-07
Thanks _duncan_.

With the link, which one should I use?  There is no 8.04 one.  In fact, the last few posts say it doesn't work.

I will try 32bit, as soon as I can get it anyway.

Any tips on any specific hardware modems you could recommend?  "Probably", knowing my luck, means wasted money. :P As for serial ports, I don't think I'd have any.  Do the USB converters work fine?

---

### Post by Drakelet on 2008-05-07
Any idea if any of these will work?

[http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&rd=1&item=120258034881&ssPageName=STRK:MEWA:IT&ih=002](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&rd=1&item=120258034881&ssPageName=STRK:MEWA:IT&ih=002)
[http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&rd=1&item=300221329500&ssPageName=STRK:MEWA:IT&ih=020](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&rd=1&item=300221329500&ssPageName=STRK:MEWA:IT&ih=020)
[http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&rd=1&item=280223771941&ssPageName=STRK:MEWA:IT&ih=018](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&rd=1&item=280223771941&ssPageName=STRK:MEWA:IT&ih=018)
[http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&rd=1&item=150243592801&ssPageName=STRK:MEWA:IT&ih=005](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&rd=1&item=150243592801&ssPageName=STRK:MEWA:IT&ih=005)
[http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&rd=1&item=160238232988&ssPageName=STRK:MEWA:IT&ih=006](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&rd=1&item=160238232988&ssPageName=STRK:MEWA:IT&ih=006)
[http://www.aria.co.uk/Products/Peripherals/Modems/56K+External+(Serial)+Modem?productId=6422](http://www.aria.co.uk/Products/Peripherals/Modems/56K+External+(Serial)+Modem?productId=6422)
[http://www.ebuyer.com/product/132962](http://www.ebuyer.com/product/132962)

---

