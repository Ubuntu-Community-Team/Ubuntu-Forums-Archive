---
title: "USB DeLorme Earthmate LT-20 gps problems"
date: 2006-07-22
forum: General Help
---

### Post by anubix on 2006-07-22
I purchased a USB DeLorme Earthmate LT-20 gps before making the switch from winblows... now i can't get it to work.  the bundled software (road and street atlas 2006) wont work with wine "internet explorer 5.0 or later is required to install this product", gpsdrive wont work with the usb LT-20, and i can't get gpsd to recognize the device either, becuase i can't find any information on configuring it.
anyone got any ideas?
pz

---

### Post by ion9 on 2006-07-27
you may whant to look in the the Earthmate userland librayes [http://emul.berlios.de/](http://emul.berlios.de/)  thay have a packed gpsd that supports the lt-20 and earthmate USB.

---

### Post by webdr on 2006-08-08
:D  [FONT="Tahoma"][SIZE="3"][SIZE="6"]**I got it working...**[/SIZE][/SIZE] 
[SIZE="3"]After much gnashing of teeth and trial and error.

So no one else need endure it... Here's how.

I am running 
ubuntu 6.06
gpsd 2.30
and gprsdrive 2.09

I did nothing special aside from using the package manager to install these, so no recompiling, making, etc. Just straight binaries.

Earlier this afternoon, I bought a earthmate gps LT-20 and StreetAtlas package because my beloved magellan meridian has died. Much tears.

I plugged the lt-20 in and could not for the life of me figure out what next... well, here ya go.

1) to make sure your gps is dumping data... 
[INDENT]First, do ls /dev/ttyUSB* at the command prompt[/INDENT]
This is a list of active? USB device files.
[INDENT]Next cat /dev/ttyUSBx ... typically x=0, therefore cat/dev/ttyUSB0[/INDENT]

If you get a string like the one below, breath a sigh of relieve the darn thing IS working.
[INDENT]$GPRMC,035545.000,A,3036.096,N,09619.512,W,0.0,0.0,080806,4.3,E*71
$GPGGA,035545.000,3036.09648,N,09619.51249,W,2,06,1.3,095.99,M,-23.3,M,,*51
$GPVTG,0.0,T,4.3,M,0.0,N,0.0,K*49
[/INDENT]

ctrl+c to stop that last command.

If not, start going through the other ttyUSBx numbers till u find it.

**Next**, start gpsdrive

click preferences
[IMG]http://www.ats.bz/ssgpsdrive.png[/IMG]
Match my GPS settings... 

Then click close
Last click start gpsd
and viola!

I hope this helps others...BTW, I'm running into mucho problems with the touch screen on my toughbook CF-72. :confused: 

webdr [/SIZE]
[/FONT]
[http://www.ats.bz]("http://www.ats.bz")

---

### Post by cssutto on 2006-12-14
I missed one thing.

How did you install the Delorme.  

Somehow you have to get the information in the two CD's on your hard drive.

I do already, but it is installed in the W2K side of my dual boot.

How do I get ubunto to talk to Delorme Street Atlas.

CSSJR

---

### Post by Joshua on 2007-03-23
I tried to follow webdr's post but here's my experience:

Plug in the LT-20
running lsusb shows the device
running lsmod shows the cypress_m8 module is loaded
running dmesg shows the device is on /dev/ttyUSB0
running ls /dev shows that ttyUSB0 is the only usb device

BUT running cat /dev/ttyUSB0 bumps the cursor down to the next line and nothing happens.  Ctrl-C won't get out of it, and finding cat in the monitor programs app shows that it is "uninterruptible" - whatever that means.  It won't let me kill the cat program.

Also, if I restart, plug in the LT-20, run gpsdrive, configure it for /dev/ttyUSB0 and 4800 baud, and then click "start gpsd" it flashes something like "no gps found" and then goes back to simulation mode.

I'm using Edgy for AMD64.

---

### Post by Joshua on 2007-03-23
Even if no one knows what's going on with my description above, does anyone know where I can get more details about how this thing actually works, and tools I can use to figure out what it's doing (like how to load and unload it through the usb port, etc)?  I went to the cypress_m8 and the emul websites but they are a little lacking on detail.

---

### Post by Joshua on 2007-03-27
Does anyone know what the EMUL stuff will provide that the cypress_m8 module that is already in the kernal won't provide?

---

### Post by travtek on 2007-03-30
I have the same problem.  The LT-20 was working fine in Edgy using the 2.6.17-10 kernel.  When I switched to Feisty, it no longer works.  I get "no gps found".  I was also using the LT-20 with Delorme Street Atlas USA 2005 via Wine in Edgy.  It also doesn't recognize the LT-20 after I switched to Feisty.

---

### Post by Joshua on 2007-04-01
travtek,

Well I'm glad someone else can relate to this.  It's driving me nuts!!

I don't know how you got it working in Edgy though.  I'm running Edgy and I've tried with kernel 2.6.17-10 and 2.6.17-11.  Only think I can think that might make me unique is that I'm running AMD64.

SOMEONE PLEASE HELP!

It seems like most people just plug in and it works, but I just can't get it to.

---

### Post by Joshua on 2007-04-02
Ok, I've figured out how to get it to work with my setup.  Still not sure why it does tho.

My setup:
AMD64
Edgy 6.10
Delorme Earthmate LT-20 (USB)
Averatec 2370 Laptop

What I did:
- Remove gpsd and any related programs (other than gpsdrive) with the package manager.  I checked "Mark for COMPLETE removal".
- Download EMUL source and extract it. ([http://developer.berlios.de/project/showfiles.php?group_id=3373](http://developer.berlios.de/project/showfiles.php?group_id=3373))
- cd to the new directory.
- run "./configure", "make clean", "make", and "sudo make install"
- Download the gpsd source from the same site as the EMUL stuff
- cd to the new directory.
- run "./configure", "make clean", "make", and "sudo make install"

Then:
- Restart
- Open terminal and type "gpsd /dev/ttyUSB0"
- Open gpsdrive
- And it should say something about looking for satellites.

GPSDrive doesn't appear to be able to start and stop gpsd properly, so gpsd must be run manually prior to starting gpsdrive.

Anyone know if the gpsd package in ubuntu just doesn't have support for the Earthmate LT-20?

---

### Post by travtek on 2007-04-05
I got the LT-20 working in Edgy by opening a terminal and typing sudo ln -s /dev/USB0 /dev/ttyS0    then the LT-20 shows up as com1.  You may have to use ln -sf /dev/USB0 /dev/ttyS0 if it complains about a link already existing.  

You can then configure Street Atlas USA 2005 to use Delorme tripmate and com1.  It works in Edgy and Dapper but doesn't work in Feisty.  I hope they get this corrected by the final release of Feisty.

You have to install this link every time you reboot.  You can add ln -sf /dev/USB0 /dev/ttyS0 to the /etc/rc.local file and it will just work when you reboot.  Also if you are using serial port 1 for something else like a modem, you can change S0 to S1 in the above examples and the LT-20 shows up on com2

---

### Post by thomasbaker on 2007-04-22
i got my delorme street atlas cd to install with crossover office, but i cant get my lt-20 to start.

i have a dell b130 laptop
feisty 7.04

thanks

---

### Post by travtek on 2007-04-22
Hi thomasbaker
The LT-20 works for me in Edgy but doesn't work in Feisty.  

Feisty Fawn is officially released and the Delorme LT-20 earthmate GPS still doesn't work in Feisty but works in Edgy.  When I plug it in, the same modules load that load in Egdy. 
 
cypress 1-1:1.0: DeLorme Earthmate USB converter detected

[  204.596000] usb 1-1: DeLorme Earthmate USB converter now attached to ttyUSB0

[  204.596000] usbcore: registered new interface driver cypress

[  204.596000] drivers/usb/serial/cypress_m8.c: Cypress USB to Serial Driver v1.09


If I do a cat /dev/ttyUSB0 in Edgy, like webdr suggested, I get streaming data.  If I do the same thing in Feisty, I get  cat  /dev/ttyUSB0: Input/output error

If I check dmesg after doing cat /dev/ttyUSB0 in Feisty I get 
drivers/usb/serial/cypress_m8.c: cypress_serial_control - failed to retrieve serial line settings - -32

[  419.880000] drivers/usb/serial/cypress_m8.c: cypress_m8 suspending failing port 0 - interval might be too short


Any ideas out there on how to fix this?

Thanks,
travtek

---

### Post by undertherift on 2007-04-30
Joshua - do you have other USB devices working?  On my Averatec c3500, the USB drivers are built into the bios or some crap like that, and not recognized by ANY forms of linux.  Don't know if thats the same case here, but if your usb isn't working at all, then you'll have a hard time getting a usb dongle to work. :-?

---

### Post by SqRt7744 on 2007-05-01
I'm having the same problem with the LT-20 in feisty.  Haven't been able to solve it after spending a couple of hours - when I run "cat /dev/ttyUSB0" I don't get an IO error, but nothing gets printed to the screen either.

I found this thread too:
[http://ubuntuforums.org/showthread.php?t=244925](http://ubuntuforums.org/showthread.php?t=244925)
but after reading it several times I still have no idea what the guy is trying to say  :(

ahhh well, hopefully someone can figure this out....

---

### Post by thomasbaker on 2007-05-10
has anyone figured this out yet? Just needing to get my lt-20 to work.

---

### Post by travtek on 2007-05-18
The problem with the LT-20 not working with Feisty is in the cypress_m8 module.  Check out;

[http://www.mail-archive.com/linux-usb-devel@lists.sourceforge.net/msg52237.html](http://www.mail-archive.com/linux-usb-devel@lists.sourceforge.net/msg52237.html)

If you can recompile a module, you can fix it.  My son recompiled my cypress_m8 module for me according to the above link and my Lt-20 works now.

hopefully this will get corrected in the next kernel update

---

### Post by Joshua on 2007-07-01
> **undertherift said:**
> Joshua - do you have other USB devices working?  On my Averatec c3500, the USB drivers are built into the bios or some crap like that, and not recognized by ANY forms of linux.  Don't know if thats the same case here, but if your usb isn't working at all, then you'll have a hard time getting a usb dongle to work. :-?

I know it's been a while... but yes I do have my USB working.  There is an excellent guide at [http://ubuntuforums.org/showthread.php?t=308152](http://ubuntuforums.org/showthread.php?t=308152)

If I remember correctly, it's the part about the RT73 Wireless drivers that gets the USB to work properly.  In my case I'm pretty sure my problems have been with the system recognizing and handling the USB Delorme LT-20.

---

### Post by VernerVonTux on 2007-07-24
Joshua,

Did you get your Earthmate LT-20 working because of the RT73 usb fix under Edgy, or Under Feisty?

Also....

Does anyone know how to apply [the fix]("http://www.mail-archive.com/linux-usb-devel@lists.sourceforge.net/msg52237.html") to the cypress_m8 kernel module proposed by travtek? I suppose I would need help on the following things to do that:

Where to get the source code for the cypress_m8 "2.6.20-16-generic" kernel module.

And how to compile that source code properly, and which directory to compile it in

And would I manually delete the cypress_m8 kernel module ".ko" file that already exists, or let the compilation process do that?

Any help on this issue would be very greatly appreciated :)

---

### Post by stormchas3r on 2007-07-30
I gave up on Feisty on this.  I downgraded to Edgy and the LT-20 work flawlessly.  Although I had to manually start "gpsd /dev/ttyUSB0"   Started gpsdrive and it worked.  So it definitely is a issue with Feisty.

Storm

---

### Post by mikeg113 on 2007-07-30
> **stormchas3r said:**
> I gave up on Feisty on this.  I downgraded to Edgy and the LT-20 work flawlessly.  Although I had to manually start "gpsd /dev/ttyUSB0"   Started gpsdrive and it worked.  So it definitely is a issue with Feisty.

Storm
It's working for me in in Feisty. I have to manually "sudo gpsd /dev/ttyUSB0" as well.
I didn't do anything differently.:confused:

2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

---

### Post by SqRt7744 on 2007-08-02
I have gotten this to work in feisty and gutsy by recompiling the module.  This sounds intimidating but is actually really easy.  I have posted detailed instructions for those happy with the terminal on lauchpad, see:



[https://bugs.launchpad.net/ubuntu/+bug/111694](https://bugs.launchpad.net/ubuntu/+bug/111694)

---

### Post by dunvar on 2007-10-03
SqRt7744, I have done everything up to where you say "run make".  I have tried everything that I can think of, but I still can not get it to work.  What am I doing wrong with make?

---

### Post by ats1080s on 2007-10-04
> **dunvar said:**
> SqRt7744, I have done everything up to where you say "run make".  I have tried everything that I can think of, but I still can not get it to work.  What am I doing wrong with make?

im at the same part.  it always says nothing to do for "default"

:mad:

any seasoned linux users that make their own software have any suggestions?  i know it has something to do with the make file your suppost to create, but i dont know how to use them and google reveals nothing of interest to me.

---

### Post by ats1080s on 2007-10-19
im on ubuntu 7.10 right now and the LT-20 is still not working.  :(  anyone get this stupid thing working in linux yet?

---

### Post by Senathon on 2007-12-20
I got the GPS working on with Feisty and Gusty, and before you  waste your time on it, I got something to explain.

The GPS has very slow tracking rates(takes over 5 mins for a decent lock)
The GPS has no external antenna(I am in the subburb and I barely get a signal).
The GPS is only good maybe for wardriving, do not use it for local directions or imediate turns.

The solution about the Make file with no Default is you have to create the Make fiile with an editor like VI, if you use Gedit, it does not work.  Gedit causes bad file format.


Get a real GPS, do not go with LT-20 Earthmate.

Senathon

---

### Post by marr99 on 2008-07-15
> **travtek said:**
> The problem with the LT-20 not working with Feisty is in the cypress_m8 module.  Check out;

[http://www.mail-archive.com/linux-usb-devel@lists.sourceforge.net/msg52237.html](http://www.mail-archive.com/linux-usb-devel@lists.sourceforge.net/msg52237.html)

If you can recompile a module, you can fix it.  My son recompiled my cypress_m8 module for me according to the above link and my Lt-20 works now.

hopefully this will get corrected in the next kernel update

Good news, everyone! :^)

The DeLorme Earthmate LT-20 (and LT-40) GPS receivers now work again under Linux!  The new 2.6.26 kernel incorporates a series of patches by Mike Isely which fix the problems with the supporting driver.

The full story is a bit more involved, so for anyone interested, please read on....

As near as I've been able to discern, DeLorme has had at least 4 USB-based GPS receivers which all go by the "Earthmate" name.  There is the original USB-based "Earthmate", 2 variants (details below) of the "Earthmate LT-20", and the recent "Earthmate LT-40".  (It appears that there may have even been an older RS-232 "Earthmate" as well, but I'm ignoring any such device here since it is irrelevant to this discussion.

The 'cypress_m8' Linux kernel module initially (until the 2.6.19 kernel came out) worked fine with the original USB Earthmate and the 1st (older) variant of the Earthmate LT-20.

A patch to the 'cypress_m8' driver by Mike Isely went into what became the Linux 2.6.19 kernel.  For me, it caused my previously-working LT-20 to stop working.  I discovered this (way back in Mar 2007) and, after some testing, posted about it, including a "quick 'n' dirty" 1-line fix that made my LT-20 start working again:

   [http://www.mail-archive.com/linux-usb-devel@lists.sourceforge.net/msg52237.html](http://www.mail-archive.com/linux-usb-devel@lists.sourceforge.net/msg52237.html)

Shortly thereafter, I got an email from Mike Isely.  He explained that his patch that got included in creating the Linux 2.6.19 kernel made his original USB Earthmate GPS receiver work more reliably, preventing some situation in which the driver was monopolizing his CPU, sometimes even forcing a reboot.

We began an email exchange/discussion (which eventually drifted off the 'linux-usb-devel' mailing list) about fixing the driver properly, to support both the original Earthmate and the LT-20 version.  At that time, the LT-40 didn't exist.

We both got distracted for several months doing other things.  In that time, Mike had conveniently purchased an Earthmate LT-20 to do some testing.  We finally got around to resuming the discussion and testing.  Up until late January 2008, neither of us realized that there was such a thing as a "new" LT-20 variant.  Mike came up with a patch to the 'cypress_m8' driver that worked with his original Earthmate and with his (new) LT-20.  When I tested it, it didn't work with my (old) LT-20, though.

We quickly realized that DeLorme had put out a newer version of the LT-20 but with the same USB 'Product ID' (PID).

As it turns out, both of the Earthmate LT-20 receivers I own are the older variant.  Mike owns both the old original Earthmate (non-"LT-20") and the newer variant of the LT-20.

Once we realized this and reported our respective LT-20 device capabilities to each other, Mike quickly came up with another patch which worked perfectly on my older LT-20 devices.  Since DeLorme didn't change the PID between the old and new LT-20 receivers, Mike was forced to use the device's report of the 'maximum packet size' (32 bytes on the old LT-20 devices but only 8 bytes on the new LT-20 devices) to discern the proper way to process the datastream.

In fact, for anyone interested in the really gory details, here's the releavant part of the output from 'cat /proc/bus/usb/devices' for every USB-based Earthmate GPS receiver except the LT-40....

The oldest, "original" (non-"LT-20") USB Earthmate:

   T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
   D:  Ver= 1.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
   P:  Vendor=1163 ProdID=0100 Rev= 0.04
   S:  Manufacturer=DeLorme Publishing
   S:  Product=DeLorme USB Earthmate
   C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
   I:* If#= 0 Alt= 0 #EPs= 2 Cls=03(HID  ) Sub=00 Prot=00 Driver=cypress
   E:  Ad=81(I) Atr=03(Int.) MxPS=  32 Ivl=6ms
   E:  Ad=02(O) Atr=03(Int.) MxPS=  32 Ivl=6ms
   
The "older" (32-byte) Earthmate LT-20:

   T:  Bus=04 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
   D:  Ver= 1.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
   P:  Vendor=1163 ProdID=0200 Rev= 0.01
   S:  Manufacturer=DeLorme Publishing
   S:  Product=DeLorme USB Earthmate      
   C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
   I:  If#= 0 Alt= 0 #EPs= 2 Cls=03(HID  ) Sub=00 Prot=00 Driver=cypress
   E:  Ad=81(I) Atr=03(Int.) MxPS=  32 Ivl=6ms
   E:  Ad=02(O) Atr=03(Int.) MxPS=  32 Ivl=6ms

The "newer" (8-byte) Earthmate LT-20:

   T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=1.5 MxCh= 0
   D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
   P:  Vendor=1163 ProdID=0200 Rev= 1.11
   S:  Manufacturer=DeLorme Publishing
   S:  Product=DeLorme USB Earthmate
   C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=400mA
   I:* If#= 0 Alt= 0 #EPs= 2 Cls=03(HID  ) Sub=00 Prot=00 Driver=cypress
   E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
   E:  Ad=02(O) Atr=03(Int.) MxPS=   8 Ivl=10ms
   
The original (non-"LT-20", non-"LT-40") Earthmate has a unique USB PID ("ProdID=0100"), making it easy to distinguish.  As you can see, among other things, the 2 variants of the LT-20 have different values for "Spd" and for "MxPS" on both the Input and Output endpoints.  In USB parlance, the older LT-20 is a "full-speed" device (12 Mbps) and the newer LT-20 is a "low-speed" (1.5 Mbps) device.

Sometime after those tests were made and Mike's repair patches were created, both Mike and I purchased the newer Earthmate LT-40.  It appears to be much more like the old LT-20 than the new LT-20.  Here's the output from 'cat /proc/bus/usb/devices' for the LT-40:

   T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
   D:  Ver= 1.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
   P:  Vendor=1163 ProdID=0200 Rev= 0.01
   S:  Manufacturer=DeLorme Publishing
   S:  Product=DeLorme USB Earthmate      
   C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
   I:  If#= 0 Alt= 0 #EPs= 2 Cls=03(HID  ) Sub=00 Prot=00 Driver=cypress
   E:  Ad=81(I) Atr=03(Int.) MxPS=  32 Ivl=4ms
   E:  Ad=02(O) Atr=03(Int.) MxPS=  32 Ivl=4ms

More importantly, these new LT-40 GPS receivers work perfectly with the new 2.6.26 kernel too.

The bottom line is that the new 2.6.26 kernel properly supports all 4 of these USB-based DeLorme Earthmate GPS receivers.

My sincere thanks to Mike Isely for providing these very useful patches and pushing them upstream for kernel inclusion!  He did all the hard work -- all I did was test and report.

Hopefully this will be useful to all you Linux-loving Earthmate GPS users, like me! :^)

Regards,
Bill Marr

---

