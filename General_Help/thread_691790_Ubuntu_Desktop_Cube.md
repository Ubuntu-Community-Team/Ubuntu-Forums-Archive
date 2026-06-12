---
title: "Ubuntu Desktop Cube"
date: 2008-02-09
forum: General Help
---

### Post by baller_2003 on 2008-02-09
hi,
i am new to the Ubuntu environment. I was trying to enable the 3d cube, but every time i do i get an error message that says "desktop effects could not be enabled." Any suggestions?

---

### Post by anonymousT on 2008-02-09
do you have an ati card?

---

### Post by koldphlame on 2008-02-09
Does Your Graphics Card Support 3d?


:!:

---

### Post by Dev'olution on 2008-02-09
> **baller_2003 said:**
> hi,
i am new to the Ubuntu environment. I was trying to enable the 3d cube, but every time i do i get an error message that says "desktop effects could not be enabled." Any suggestions?
it would seem your graphics card does not have sufficient drivers.

Have you updated them lately?

Can you give us your system specs?

---

### Post by baller_2003 on 2008-02-11
Here's my system specs:

General
MPN: GWS000274

Type: PC

Recommended Use: Small business

Product Form Factor: Desktop

Width: 38.1 cm

Depth: 44.5 cm

Height: 11.9 cm

Processor
Type: Intel Pentium III 600 MHz

Installed Qty: 1

Max Supported Qty: 1

Upgradability: Not upgradeable

Cache memory
Type: L2 Cache - Pipeline Burst

Installed Size: 512 KB (installed) / 512 KB (max)

Mainboard
Chipset Type: Intel 440BX

Data Bus Speed: 100 MHz

Ram
Installed Size: 256 MB / 384 MB (max)

Technology: SDRAM

Memory Speed: 100 MHz

Form Factor: DIMM 168-PIN

Upgrade Rule: Max 128 MB module

Storage controller
Type: 1 x IDE - integrated

Controller Interface Type: IDE / ATA

Channel Qty: 2

Storage
Floppy Drive: 3.5" 1.44 MB floppy

Hard Drive: 1 x 15 GB - standard - IDE/ATA

Hard Drive (2nd): None

Optical storage
Type: CD-ROM - IDE

Read Speed: 48x

Media Load Type: Tray

Monitor
Monitor Type: Display - CRT

Diagonal Size: 17"

Viewable Size: 15.9"

Max Resolution: 1600 x 1200

Compliant Standards: CE

Graphics controller
Type: AGP - plug-in card

Graphics Processor / Vendor: ATI RAGE PRO TURBO

Video Memory: SGRAM

Installed Size: 4 MB

Supported Display Graphics: VGA (640x480), XGA (1024x768), SVGA (800x600), SXGA (1280x1024)

Video Output Supported: RGB

Audio output
Type: Sound card - integrated

Signal Processor: Cirrus Logic CS 4235B

Sound Output Mode: Stereo

Compliant Standards: AC '97

Input device
Type: Mouse, keyboard

Networking: Network adapter - PCI - integrated

Data Link Protocol: Ethernet, Fast Ethernet

Compliant Standards: IEEE 802.3, IEEE 802.3u

Expansion / connectivity
Expansion Bays Total (Free): 

3 ( 2 ) x internal - 3.5" x 1/3H 
1 ( 0 ) x front accessible - 3.5" x 1/3H 
1 ( 0 ) x front accessible - 5.25" x 1/3H 

Expansion Slots Total (Free): 

1 ( 0 ) x processor - Slot 1 
3 ( 2 ) x memory - DIMM 168-PIN 
3 ( 3 ) x PCI - full-length 
1 ( 0 ) x AGP 2x 

Interfaces: 

1 x network - Ethernet 10Base-T/100Base-TX - RJ-45 
2 x USB - 4 PIN USB Type A 
2 x serial - RS-232 - 9 pin D-Sub (DB-9) 
1 x parallel - IEEE 1284 (EPP/ECP) - 25 pin D-Sub (DB-25) 
1 x keyboard - generic - 6 pin mini-DIN (PS/2 style) 
1 x mouse - generic - 6 pin mini-DIN (PS/2 style) 
1 x display / video - VGA - 15 pin HD D-Sub (HD-15) 
1 x audio - line-out - mini-phone stereo 3.5 mm 
1 x microphone - input - mini-phone mono 3.5 mm 
1 x audio - line-In - mini-phone stereo 3.5 mm 

Miscellaneous
Features: Kensington MicroSaver security system

Compliant Standards: Plug and Play

Power
Device Type: Power supply

Installed Qty: 1

Voltage Required: AC 110/220 V ± 10% ( 50/60 Hz )

Power Provided: 145 Watt

Compliant Standards: EPA Energy Star
 
sorry it took me so long to reply. Been bussy today.

---

### Post by baller_2003 on 2008-02-11
By the way the PC is a gateway E-3200

---

### Post by jordanmthomas on 2008-02-11
I don't believe that your graphics card is going to work with compiz.
It was probably a decent card in its day, but its day has come and gone.

In case you want to scour the net to see if anyone's got it to work, your card is this:
ATI RAGE PRO TURBO with 4 MB of memory.

Sorry to bear bad news.  :(

---

### Post by baller_2003 on 2008-02-11
ok I appreciate the advice what video card would you recommend if I were to install one?

---

### Post by jordanmthomas on 2008-02-11
Heh, I'm not sure.  Compiz really doesn't require too much to run.  If I was to install a different card into that system, I'd just try to stay away from any ATi cards.  Support is on its way, but since I'm assuming you wouldn't be putting a real nice card in, I'd just stay away.

Short answer:  I don't know enough about hardware to suggest a particular card, I just happen to know this one won't work because I tried getting an ATi RAGE PRO to run compiz before and it was a no-go.

You could probably use this though:
[http://desk3d.sourceforge.net/](http://desk3d.sourceforge.net/)

It's in the repositories as a package called 3d-desktop.  It's not as nice or fast as compiz, but it works.

---

### Post by baller_2003 on 2008-02-12
Okay, Thanks for the advice. I think I'll just stick with what I got. Ubuntu is running pretty good on this old machine anyway. right now I have it set up to duel boot. The other partition is windows xp pro. I'm thinking about just doing away with it all together. The more I play with Ubuntu, the more I love it. It seems to be a real durable OS so far, and I can do just about everything in Ubuntu that I can do in windows.

---

### Post by chewit on 2008-02-12
> **anonymousT said:**
> do you have an ati card?

Why does it matter if you have an ATi card.

You telling me a card like the ATiXT2900HD which is a DX10 card won't work with Compiz, but can run crysis on high!

---

### Post by jordanmthomas on 2008-02-12
> **chewit said:**
> Why does it matter if you have an ATi card.

ATi cards are more prone to cause trouble than nvidia or intel ones.  Search the forums for people needing help with compiz and sure enough it's almost always an ATi card.

---

### Post by baller_2003 on 2008-02-12
I do have to agree with this one I did search the Ubuntu forms and quite a few graphics problems dealt with this particular brand of video card. I'm not trying to sound like a know it all. Just going off the threads thats been posted about it

---

### Post by NineseveN on 2008-02-12
> **chewit said:**
> Why does it matter if you have an ATi card.

You telling me a card like the ATiXT2900HD which is a DX10 card won't work with Compiz, but can run crysis on high!

It's not the hardware that's at fault, the hardware is not relevant...the ATi *nix drivers can be garbage for certain things in their current state. As they mature, they'll get better, but as it is, they come with some problems running Compiz and other 3D apps in *nix. For many, if not most of those issues, there's a fix or a workaround...

---

### Post by baller_2003 on 2008-02-12
Yeah thats a good point. like I said to many people before I am new to the Ubuntu environment. So far I really like the way Ubuntu is. The OS seems to be real reliable. I do have to agree with you though, because I can see were you are coming from. Do any of you think that a driver will be written for a Lexmark x3470 printer? I really don't have the money to upgrade to a HP three in one right now.:)

---

### Post by NineseveN on 2008-02-12
> **baller_2003 said:**
> Yeah thats a good point. like I said to many people before I am new to the Ubuntu environment. So far I really like the way Ubuntu is. The OS seems to be real reliable. I do have to agree with you though, because I can see were you are coming from. Do any of you think that a driver will be written for a Lexmark x3470 printer? I really don't have the money to upgrade to a HP three in one right now.:)

I'm new around here as well (been using Ubuntu since late last year), so I still have a lot to learn. At least ATi is making the attempt to get *nix drivers out there, they're new to the OS as well, so I can understand some growing pains (i.e. I don't really fault ATi for anything except being late to the party).

As far as Lexmark, that's really up to them. Open Source driver makers can only do so much reverse engineering, so without the right specs and information and without the effort and aid of the hardware manufacturers, some things are simply a lost cause. 

I've been into computers since 1994 when I was in high school, and I used to hate HP and Nvidia. Some of that was due to typical young fanboi nonsense and some of it was due to real concerns from an end-user standpoint. In the last few years though, I've done a complete 180 on both of those companies (and a few others as well). When I recently upgraded my video card, I bought an Nvidia 7600GS. When I recently needed a new printer/all-in-one, I bought an HP. My thinking on this was that even if I never eventually made the move to *nix (though I did), I wanted to support hardware companies that don't tie users to only the dominant operating system/s...choice is good for everyone, even if everyone doesn't choose to make a choice at all.

---

### Post by baller_2003 on 2008-02-13
Does anyone know what ogg exactly is, and how it works? my Ubuntu book says very little about it:confused:

---

### Post by jordanmthomas on 2008-02-13
It's basically a collection of file formats for media.
Think along the lines of mp3, wav, flac, wmv, mpg, etc.

I believe ogg can be both audio and video;  It's free and open source, and thus is preferred by many in the Linux community.

Does this help or were you looking for something more technical?
You can read up some more here:
[http://www.vorbis.com/faq/](http://www.vorbis.com/faq/)

---

### Post by SunnyRabbiera on 2008-02-13
> **baller_2003 said:**
> Does anyone know what ogg exactly is, and how it works? my Ubuntu book says very little about it:confused:

ogg is normally a sound format, similar in fashion to .mp3 and .wav
.ogg is a open source sound format popular with most linux distributions due to its open source nature.
It normally has a good compression rate like wav files but with the quality of a mp3.
You will encounter two types of ogg files, video ogg and audio ogg

---

### Post by baller_2003 on 2008-02-13
Okay. Thanks, that is actually good to know. I was trying to rip a cd to my computer last night and I wasn't sure which format was the best to rip it in

---

### Post by baller_2003 on 2008-02-13
How easy is it to map a network drive in Ubuntu? I've tried mapping my drive on the osu okmulgee server that holds our H drives. I don't know the name of the server or the IP address for security reasons, but they do give me the path to my H drive. I tried just using the path for it, but every time I try to map it Ubuntu keeps putting a forward slash in front of the two beginning back slashes. The two back slashes doesn't allow the H drive access to leave campus. Any suggestions??:guitar:

---

### Post by jordanmthomas on 2008-02-13
Could you post an example of what the path looks like?  You can change the words within if you want, but I'm not sure what you're getting at.

I will say, though, that instead of typing the \ like they give you, use / instead.

---

### Post by baller_2003 on 2008-02-14
Here is what the H drive path looks like. Every time I enter this path in the connect to server option Ubuntu put a forward / in front of the two back \\. The two \\ have to be in the drive path in order for this path to work. It's some sort of security feature that the school has added to there server.  This is legal and safe by the way.  

\\okmnas01.ad.okstate.edu\myusername$

---

### Post by jordanmthomas on 2008-02-14
You should be able to use this instead:
```
//okmnas01.ad.okstate.edu/myusername$
```
This is what I have to do for mine at least.  My school tells me to use 
```
\\zeus.pclab.tntech.edu\users\myusername
```
but switching the backslashes to forwardslashes works (not that I use that one much, they give you 100 MB of storage...I like my CSC account better, with over a terrabyte).

---

### Post by baller_2003 on 2008-02-15
Sorry, I tried this path and I couldn't get it to map the drive. It looks like I will have to have the name of the server so it is not declared "null". Like I said, our network administrator will not give us that information. I tried to get it, but I can see where he's coming from.

---

### Post by baller_2003 on 2008-02-15
If anyone haves any time to do this for me, I would greatly appreciate it. I need a list of printers that Ubuntu 7.10 has drivers for. Thank you.

---

### Post by NineseveN on 2008-02-15
Ubuntu will run any *nix printer driver. 

For as list of suggested printers:
[http://www.linux-foundation.org/en/OpenPrinting/Database/SuggestedPrinters](http://www.linux-foundation.org/en/OpenPrinting/Database/SuggestedPrinters)

To search for a specific printer:
[http://www.openprinting.org/printer_list.cgi](http://www.openprinting.org/printer_list.cgi)


Linux support by printer vendor:
[http://www.linux-foundation.org/en/OpenPrinting/Database/LinuxSupportByPrinterVendors](http://www.linux-foundation.org/en/OpenPrinting/Database/LinuxSupportByPrinterVendors)

---

### Post by jordanmthomas on 2008-02-15
> **baller_2003 said:**
> Sorry, I tried this path and I couldn't get it to map the drive. It looks like I will have to have the name of the server so it is not declared "null". Like I said, our network administrator will not give us that information. I tried to get it, but I can see where he's coming from.

The name of the server is 
okmnas01.ad.okstate.edu

and the name of the share is
myusername$

---

### Post by baller_2003 on 2008-02-16
Okay, thanks for the info. I will try this when I make it back to campus on Sunday. I will let you know if it works as soon as I can. Thanks.

---

### Post by baller_2003 on 2008-02-16
By the way, do you know the command I can use to run something like a disk cleanup in Ubuntu?

---

### Post by NineseveN on 2008-02-16
> **baller_2003 said:**
> By the way, do you know the command I can use to run something like a disk cleanup in Ubuntu?

Try this thread (might be what you're looking for)...
[http://ubuntuforums.org/showthread.php?t=20001](http://ubuntuforums.org/showthread.php?t=20001)

---

### Post by baller_2003 on 2008-02-16
Thanks for the info. I found what I needed

---

### Post by baller_2003 on 2008-02-17
Does anybody know if Ubuntu has the drivers for the IBM pc webcam? The s/n is 302BB1AX. I would appreciate a reply as soon as possible. Not really a rush though. Thank you

---

### Post by baller_2003 on 2008-02-18
I successfully installed Ubuntu on my grandparent's Dell GX110. This computer has a wamping 384 megs of ram. A WD 13 gig hard drive and a P3 motherboard. Everything works good, but when my grandmother tries to do her shopping at walmart the monitor display turns into dull colored strips and lines, and then the monitor goes into a standby mode. I have to manually restart the machine in order to bring the display back. This is the only website I found that it doesn't like so far. Any suggestions:confused:

---

