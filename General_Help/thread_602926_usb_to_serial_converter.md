---
title: "usb to serial converter"
date: 2007-11-04
forum: General Help
---

### Post by dlynch912 on 2007-11-04
I just got a new thinkpad T61 and install Gutsy on it.  

I need to console in to various systems and this laptop doesn't have a serial port. I bought a Radio Shack 26-183 usb-to-serial converter, but when i plug it in, nothing happens.  No /dev/USB0 is created, the output of dmesg is:

[169455.220000] usb 3-2: new full speed USB device using uhci_hcd and address 10
[169455.384000] usb 3-2: configuration #1 chosen from 1 choice


Am I missing something?  Is there a package I need to install that I'm not thinking of?

Thanks in advance for any and all help.


~Dave

---

### Post by dlynch912 on 2007-11-04
bumb

---

### Post by fragos on 2007-11-04
Your problem is identifying the mount point.  Check for something like /dev/ttyUSB0 or something in /dev/usb folder.  You can control what's used with udev rule.  The lsusb command will be helpfull as it will show even unmounted USB devices.

---

### Post by dlynch912 on 2007-11-05
i actually don't think the kernel is recognizing the device at all.  I've searched around online and it seems to work for everyone but me.  how can i get the kernel to recognize the device??

---

### Post by fragos on 2007-11-05
Let's start with the following:

Open a terminal window and run "lsusb" with the serial converter plugged in and removed.  That willl tell us if it's actualy recognized.  I'll need to see that output.

---

### Post by dlynch912 on 2007-11-05
When I type 'lsusb' i get the following for this device:

Bus 004 Device 008: ID 05ad:0fba Y.C. Cable U.S.A., Inc. 


But in dmesg, i get this:

Nov  5 14:37:27 odin kernel: [ 2772.724000] usb 5-2: new full speed USB device using uhci_hcd and address 2
Nov  5 14:37:27 odin kernel: [ 2772.924000] usb 5-2: configuration #1 chosen from 2 choices


shouldn't it attach to something like /dev/ttyUSB0 or something?

---

### Post by cyriss on 2007-12-20
I'm having the exact same problem right now.  When I connect the cable, I get the following from /var/log/messages:

Dec 20 21:22:17 localhost kernel: [  905.228556] usb 5-2: new full speed USB device using uhci_hcd and address 4
Dec 20 21:22:17 localhost kernel: [  905.390627] usb 5-2: configuration #1 chosen from 1 choice

lsusb gives:
Bus 005 Device 004: ID 05ad:0fba Y.C. Cable U.S.A., Inc.

However, there is no device created in /dev (no ttyUSB*) and nothing in /dev/usb.  The only thing new created in /dev is the following:

crw-rw-rw- 1 root   root        5,   2 2007-12-20 21:25 ptmx
crw-rw---- 1 root   root      189, 516 2007-12-20 21:24 5-1
crw-rw---- 1 root   root      254,  18 2007-12-20 21:24 usbdev5.5_ep00
crw-rw---- 1 root   root      254,  20 2007-12-20 21:24 usbdev5.5_ep02
crw-rw---- 1 root   root      254,  19 2007-12-20 21:24 usbdev5.5_ep81
crw-rw---- 1 root   root      254,  21 2007-12-20 21:24 usbdev5.5_ep83

Anyone having this problem or, better yet, have a solution?

If its any help, I'm running Gutsy.

---

### Post by fragos on 2007-12-20
Mount points are created by udev rules.  Look at /etc/udev.  There is a two step process here.  First the hardware is recognized and then udev rules generate a /dev mount point for applications to reference.  Loading of an appropriate driver is separate but I don't think you need one for a USB serial adapter.

---

### Post by dasunst3r on 2007-12-20
See if you have a /dev/ttyS___ somewhere.  If you do, then the device works.

---

### Post by cyriss on 2007-12-21
Well, i do have a /dev/ttyS* node (in fact i have 0-3), but it is not created when I hotplug the cable and, as far as i can tell so far, doesn't work with the cable either.

My understanding of udev (which is admittedly minimal), is that it should create a named node when a device is hotplugged regardless of whether a rule exists in /etc/udev/ specifically for that device.  If this is wrong, is there a particular rule that I should have in place?

thanks.

---

### Post by dasunst3r on 2007-12-26
In your file manager, navigate to /dev, get a detailed view, and have it sort by date modified.  Then, plug in your device.  That device should be "recently modified."

---

### Post by MichaelLehner on 2007-12-29
Could you check if /dev/ttyUSB* is created and a few seconds later disconnected again?

This is my actual problem.
On dmesg i get the following output:
```

//Disconnecting the device.
[ 4250.416000] usb 2-1: USB disconnect, address 11
//Reconnecting it.
[ 4253.612000] usb 2-1: new full speed USB device using uhci_hcd and address 12
[ 4253.808000] usb 2-1: configuration #1 chosen from 1 choice
[ 4253.808000] ftdi_sio 2-1:1.0: FTDI USB Serial Device converter detected
[ 4253.808000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/ftdi_sio.c: Detected FT232BM
[ 4253.808000] usb 2-1: FTDI USB Serial Device converter now attached to ttyUSB0
//Now /dev/ttyUSB0 is available
[ 4258.900000] usb 2-1: usbfs: interface 0 claimed by ftdi_sio while 'brltty' sets config #1
[ 4258.904000] ftdi_sio ttyUSB0: FTDI USB Serial Device converter now disconnected from ttyUSB0
[ 4258.904000] ftdi_sio 2-1:1.0: device disconnected
// /dev/ttyUSB0 disappeared again. I didn't do anything else than waiting.
```

I solved the problem by renaming /etc/udev/rules.d/85-brltty.rule und kill brltty. But I think this is a workaround and no real solution. Can anyone tell me what's really going wrong and how to solve this?

---

### Post by mr_tentacle on 2008-01-10
The problem you are seeing is an artifact of the brltty rules.  Brltty is a braille terminal apparently (man brltty for details), and a bunch of these use common USB-Serial chips.  What is happening is the 85-brltty.rules has an entry that matches the vendor-ID and product for the usb-serial adapter you have.   

Brltty steals the TTY device as soon as it gets created.  This is why deleting the brltty rules fixed the problem.   The "correct" fix is to identify the line in brltty.rules that is causing the conflict and comment it out.

Do this by doing an lsusb before and after attaching the device - the "extra" line after the device is installed is the one you want.  In my case it was:

Bus 005 Device 007: ID 0403:6001 Future Technology Devices International, Ltd 8-bit FIFO

Now find the line in brltty.rules that matches your device. For me it was this one:

SYSFS{idVendor}=="0403", SYSFS{idProduct}=="6001", RUN+="/lib/brltty/brltty.sh -b ht -d usb:"

Comment it out by inserting "#" as the first character,  Kill brltty, if its running, reconnect your devices and your USB-Serial adapter should work fine.

---

### Post by cdcase on 2008-02-21
I've been trying to solve this problem for the last 4 hours, and I figured out the following:
[LIST=1]
[*]Some people are able to get FTDI_SIO to recognize the cable and mount it for a split-second, but then brltty steals the device and it fails to mount properly. To fix that, comment out the line inside brltty that identifies the cable as a braille terminal and it should work.
[*]Others are not so lucky. I discovered that the cable is based on the Prolific chipset, and requires the pl2303 driver inside the Linux kernel. If this is your case:
[LIST=1]
[*]There's a bug in the driver that causes the kernel not to recognize the vendor and product ID of the cable.
[*]The next version of the Linux kernel, 2.6.25, has already patched this error, and when that comes out, the cable should be plug & play, and should automatically mount to /dev/ttyUSB0.
[*]If you're feeling daring, you can compile the latest version of the kernel, 2.6.25-rc2, by yourself, load the modules by "modprobe pl2303" (I think), and your problem should be fixed.
[/LIST]
[/LIST]


That's it!

---

### Post by aggie on 2008-02-21
Hi,

I just got a USB to RS232 cable, the problem is there is no company name on it that I can see.
The CD driver that came with it is only for windows.

I do not get the /ttyUSB showing up

This is the information I'm getting when I try lsusb and dmesg

First with the cable attached
[ 2957.021715] usb 1-3: new full speed USB device using ohci_hcd and address 7
[ 2957.231431] usb 1-3: configuration #1 chosen from 1 choice

Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Bus 002 Device 002: ID 041e:4055 Creative Technology, Ltd 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 007: ID 4348:5523  
Bus 001 Device 001: ID 0000:0000 

without the cable attached
[ 2957.231431] usb 1-3: configuration #1 chosen from 1 choice
[ 3320.293452] usb 1-3: USB disconnect, address 7

Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Bus 002 Device 002: ID 041e:4055 Creative Technology, Ltd 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

It seems like it can't recognize the cable.
What can I do?

I need to communicate with my micro controller using usb to serial.
We're not using my computer for the presentation but I wanted to try this out on my computer first before the laptop tomorrow.
I can't open the /dev/ttyUSB file to use for libserial if nothing shows up..

Please help

---

### Post by cdcase on 2008-02-21
You've got a different cable. Ubuntu is detecting the hardware but is not mounting it properly to /dev/ttyUSB*. I don't know what to do specifically for your cable, but I'm guessing the problem appears to be the same.

Your cable has got a different vendor and product ID than the previous two cables that I saw were on this forum. (4348:5523, identified by lsusb). The solutions that I posted were for another cable which probably required another driver (05ad:0fba Y.C. Cable U.S.A., Inc.).

Sorry I couldn't help :(. Perhaps someone else with the same cable as yours can help you solve your problem.

---

### Post by fragos on 2008-02-21
lsusb shows that the cable is seen and responded to the standard command for it's identity.  Vender 4348 and device 5523 were returned but not a discription.  Mounting is a separate operation controlled by udev rules.  As a matter of note it's posible to have multiple mount points for the same device.  Lastly would be the question of a proper diver being installed.

---

### Post by cdcase on 2008-02-21
Here's [another thread on the same issue]("http://ubuntuforums.org/showthread.php?t=91537&page=2").

For those with their cable identifying as vendor 05ad and device 0fba (Radio shack model 26-183), there's no doubt that this is a driver problem, and that [it has already been patched]("http://www.gossamer-threads.com/lists/linux/kernel/879746") in the upcoming release.

Edit: aggie, your problem is also due to the kernel not being able to recognize which driver to use. You're using an HL-340 USB to serial cable, right? I ran through the latest patch for the linux kernel and there also appears to be a patch for your solution. You can try to compile the latest update by yourself, if you're feeling daring :)

---

### Post by aggie on 2008-02-21
The problem is I don't know what the cable is at all. For some weird reason the packaging doesn't have a company name etc.

There is a small cd inside for me to install drivers in windows. When I tried to do that to see what company/driver it's using it didn't work.
It told me to plug in something and failed to detect it and then in the end my installation failed.

I think it was trying to install something called Hornet

I got this at one of the electronic stores near school >_< I guess that's a bad idea

Hum...Is it possible to find a driver using the Vendor ID 4348 and device ID 5523?

---

### Post by aggie on 2008-02-22
Hum...so I did some more digging around and saw that 
USB: add support for 4348:5523 WinChipHead USB->RS 232 adapter
was added in an kernel update

I'm not sure which version this is, but if I update all the way to newest one I guess it should work.

I think I also found the driver too.

If the kernel update didn't work how do I install a driver?

I found it as a text from an email thread

---

### Post by cdcase on 2008-02-22
So, the kernel version I was referring to is 2.6.25-rc2, which is not exactly stable. Both the fix to 05ad:0fba and 4348:5523 are both inside that latest version.

There's no way to "install a driver" I think. The only thing we can do is recompile the latest kernel and pray that it works, since the latest kernel contains all the latest drivers.

If you know a little bit of coding (or even if you don't), you should be able to recognize the vendor and product ID in the latest version of the kernel that I was talking about at the latest source update. Hopefully, that will be the patch that solves everything.
[http://www.kernel.org/diff/diffview.cgi?file=%2Fpub%2Flinux%2Fkernel%2Fv2.6%2Ftesting%2Fpatch-2.6.25-rc2.bz2;z=5034](http://www.kernel.org/diff/diffview.cgi?file=%2Fpub%2Flinux%2Fkernel%2Fv2.6%2Ftesting%2Fpatch-2.6.25-rc2.bz2;z=5034)

I'm recompiling the latest kernel version right now and I'll tell you how that goes.

I sure hope that 2.6.25 makes it into Hoary; if it does, all of us will have a solution that works out of the box by then.

---

### Post by cdcase on 2008-02-22
So, Gutsy *appears* to run fine on 2.6.25-rc2, but certain strange things are happening. For one, the network configuration tool doesn't work with wireless anymore, even though I made sure to enable my drivers in the kernel. Compiz fusion also went bonkers, as well as my restricted ATI drivers (which is normal, I think).

Xgl had some tiny problems with rendering certain icons, such as Tomboy Notes on my panel, but I think GNOME probably does fine.

That's what I found out with 5 minutes of testing.

In short, don't switch unless you're willing to tackle all those problems just to get your cable working.

---

### Post by aggie on 2008-02-22
yeah I can't recompile the kernel

So what can I do with the ch341.ko driver that will apparently solve my problem?

This is what I found on another thread but I'm not too sure how to use what he did.

or whre to find the ch341.ko driver


> I didn't want to build the whole kernel modules so I did
* make drivers/usb/serial/ch341.ko
* cp drivers/usb/serial/ch341.ko /lib/modules/2.6.22-14-generic/kernel/drivers/usb/serial/
* add "/lib/modules/2.6.22-14-generic/kernel/drivers/usb/serial/ch341.ko: /lib/modules/2.6.22-14-generic/kernel/drivers/usb/serial/usbserial.ko /lib/modules/2.6.22-14-generic/kernel/drivers/usb/core/usbcore.ko" to /lib/modules/2.6.22-14-generic/modules.dep
* Make it load on boot -> echo ch341 >> /etc/modules
* To load it, modprobe ch341

he made a reference to this article
[http://lwn.net/Articles/246334/](http://lwn.net/Articles/246334/)

I think that article is the driver..I just don't know how to take it and use it :(

Sorry that i'm so clueless to this...really new to managing a linux box

---

### Post by cdcase on 2008-02-22
Okay, so I checked up the versions and I found your patch inside 2.6.24, which is a stable version.

You can either do what the guy you quoted did, and I'll help you with that when I get home and can try it out for myself, or you can download the latest kernel image from the Hardy repository and run that to see if it works.

What the guy did was simply compile that (and only that) driver you need, copied it into the kernel that he was running (same as yours and mine - the one that ships with Gutsy), do some very unorthodox things to update the linux-headers package (I think), and tell Linux to load that driver by default.

I'll write up another post when I get home to help you solve your problem :)

---

### Post by aggie on 2008-02-22
I finally got my hands on the laptop we're suppose to make this all work on

He doesn't have the update that fixes this problem. Ubuntu still doesn't recognize it :(

I did a uname -a and it is at 2.6.22-14-generic

>_< I'm not sure how else I'm suppose to find out what version he's on

it would help if I knew where to get the driver lol

I try working on the libserial problem for now since it seems like package manager doesn't install that one :(

---

### Post by aggie on 2008-02-23
@cdcase

We would be very grateful if you could teach us how to get this to work

Looking forward to your reply :KS

---

### Post by cdcase on 2008-02-23
Try the following. The driver is attached with this post.

Navigate to the directory with the driver and do the following
```

// extract and compile driver
tar -xvf ch341.tar.gz
cd ch341
make

// loads a module that might be needed to install our ch341 module
// see: http://ubuntuforums.org/showthread.php?t=692132
sudo modprobe usbserial

// installs this module inside the kernel
sudo insmod ch341.ko
```

To run the driver, do
```
sudo modprobe ch341
```

But I'd recommend adding in some diagnostics to really make sure it's working.
[LIST=1]
[*]do "tail -f /var/log/messages"
[*]hit a few <ENTER>s
[*]Plug in your cable and note whatever prints out
[*]Remove your cable
[*]run "sudo modprobe ch341" in another terminal
[*]Plug in your cable again and see whether something new related to \ttyUSB* comes up
[/LIST]

Finally, I don't know if it is needed, but if after you reboot, the cable fails, add this line and reboot:
```
sudo echo "ch341" >> /etc/modules
```

And that should hopefully fix your problem.

References
[kismat on ch341 patch]("http://ohioloco.ubuntuforums.org/showpost.php?p=4334062&postcount=12")
[insmod ch341 symbol error (contains driver)]("http://ubuntuforums.org/showthread.php?t=692132")

---

### Post by aggie on 2008-02-23
thanks alot!!!
I have to get my partner to try this since he has the cable and it's his laptop.

I hope it works :)

---

### Post by aggie on 2008-02-25
Interesting
He gave me the output of what he did
This is his result
He got an error: FATAL: Module ch341 not found.
But when we look at kernel now, it does attach the cable to /dev/ttyusb

I'm not too sure if it's working properly tho because of the error.

> I did everything it said but . . . 

lawrence@Lawrence-PC:~/Mine/downloads$ tar -xvf ch341.tar.gz ch341/ ch341/Makefile ch341/ch341.c lawrence@Lawrence-PC:~/Mine/downloads$ cd ch341/ lawrence@Lawrence-PC:~/Mine/downloads/ch341$ make make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/lawrence/Mine/downloads/ch341 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/lawrence/Mine/downloads/ch341/ch341.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/lawrence/Mine/downloads/ch341/ch341.mod.o
  LD [M]  /home/lawrence/Mine/downloads/ch341/ch341.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
lawrence@Lawrence-PC:~/Mine/downloads/ch341$ sudo modprobe usbserial [sudo] password for lawrence:
lawrence@Lawrence-PC:~/Mine/downloads/ch341$ sudo insmod ch341.ko lawrence@Lawrence-PC:~/Mine/downloads/ch341$ sudo modprobe ch341
FATAL: Module ch341 not found.


i got that fatal error message at the end when i tried to install the module inside the kernel.  i tailed the log like the guy said and got . . . 

Feb 25 16:13:43 Lawrence-PC kernel: [ 4081.372000] usb 3-1: new full speed USB device using uhci_hcd and address 6
Feb 25 16:13:44 Lawrence-PC kernel: [ 4081.536000] usb 3-1: configuration #1 chosen from 1 choice
Feb 25 16:13:44 Lawrence-PC kernel: [ 4081.540000] ch341 3-1:1.0: ch341-uart converter detected
Feb 25 16:13:44 Lawrence-PC kernel: [ 4081.556000] usb 3-1: ch341-uart converter now attached to ttyUSB0




Feb 25 16:13:46 Lawrence-PC kernel: [ 4084.144000] usb 3-1: USB disconnect, address 6
Feb 25 16:13:46 Lawrence-PC kernel: [ 4084.144000] ch341-uart ttyUSB0: ch341-uart converter now disconnected from ttyUSB0
Feb 25 16:13:46 Lawrence-PC kernel: [ 4084.144000] ch341 3-1:1.0: device disconnected

---

### Post by cdcase on 2008-02-25
Extremely weird! But it appears to be perfectly working. 

If this line is coming up:
> Feb 25 16:13:44 Lawrence-PC kernel: [ 4081.556000] usb 3-1: ch341-uart converter now attached to ttyUSB0

Things should be working. Try plugging in something else to the cable and see whether it works or not :)

---

### Post by aggie on 2008-02-25
yeah for sure we'll have to plug something in to try

cause this is weird too

WITH THE CABLED NOT CONNECTED:

lawrence@Lawrence-PC:~$ lsusb
Bus 006 Device 001: ID 0000:0000
Bus 007 Device 002: ID 1058:1000 Western Digital Technologies, Inc. 
Bus 007 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader Bus 001 Device 001: ID 0000:0000 Bus 003 Device 001: ID 0000:0000 Bus 002 Device 002: ID 046d:c513 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  

WITH THE CABLE CONNECTED:

lawrence@Lawrence-PC:~$ lsusb
Bus 006 Device 001: ID 0000:0000
Bus 007 Device 002: ID 1058:1000 Western Digital Technologies, Inc. 
Bus 007 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader 
Bus 001 Device 001: ID 0000:0000 
Bus 003 Device 009: ID 4348:5523 
Bus 003 Device 001: ID 0000:0000 Bus 002 
Device 002: ID 046d:c513 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  

still empty in lsusb

---

### Post by fragos on 2008-02-25
Bus 003 Device 009: ID 4348:5523 appeared with cable pluged in.  There was no description but it's still there.

---

### Post by Va15a11a on 2008-02-29
Thanks cdcase, the below code worked brill for me, i bought the adapter off of ebay, has blue connectors and only windows drivers.  It does not show a manufacturer in the lsusb output, but this worked great, the last step "sudo modprobe ch341" does not seem to work, but the driver seems to load fine, but i cannot get it to load with the link at startup, i need to run the process everytime.

Thank you for your help.


"Try the following. The driver is attached with this post.

Navigate to the directory with the driver and do the following
Code:

// extract and compile driver
tar -xvf ch341.tar.gz
cd ch341
make

// loads a module that might be needed to install our ch341 module
// see: [http://ubuntuforums.org/showthread.php?t=692132](http://ubuntuforums.org/showthread.php?t=692132)
sudo modprobe usbserial

// installs this module inside the kernel
sudo insmod ch341.ko

To run the driver, do
Code:

sudo modprobe ch341

But I'd recommend adding in some diagnostics to really make sure it's working.

   1. do "tail -f /var/log/messages"
   2. hit a few <ENTER>s
   3. Plug in your cable and note whatever prints out
   4. Remove your cable
   5. run "sudo modprobe ch341" in another terminal
   6. Plug in your cable again and see whether something new related to \ttyUSB* comes up


Finally, I don't know if it is needed, but if after you reboot, the cable fails, add this line and reboot:
Code:

sudo echo "ch341" >> /etc/modules

And that should hopefully fix your problem."

---

### Post by aggie on 2008-03-02
lawrence@Lawrence-PC:~/Mine/downloads/ch341$ sudo modprobe ch341
FATAL: Module ch341 not found.
lawrence@Lawrence-PC:~/Mine/downloads/ch341$ sudo echo "ch341">>/etc/modules
bash: /etc/modules: Permission denied

So he followed the instructions last week and loaded the driver
but today it seemed to be missing
so i re did it and this is the result

Mar  2 14:50:09 Lawrence-PC kernel: [ 1021.492000] usb 3-1: new full speed USB device using uhci_hcd and address 4
Mar  2 14:50:09 Lawrence-PC kernel: [ 1021.712000] usb 3-1: configuration #1 chosen from 1 choice
Mar  2 14:50:09 Lawrence-PC kernel: [ 1021.716000] ch341 3-1:1.0: ch341-uart converter detected
Mar  2 14:50:09 Lawrence-PC kernel: [ 1021.732000] usb 3-1: ch341-uart converter now attached to ttyUSB0
Mar  2 15:13:28 Lawrence-PC -- MARK --

but it still doesn't show up in lsusb
that worries me
It also doesn't seem to work after i reboot.

Will be testing the cable against the micro controller once i get that code working normally

---

### Post by aggie on 2008-03-02
ok i don't think it worked

I opened up a putty session using the /dev/ttyUSB0 with the option of serial

and nothing happened.

I don't have a gender bender to try it against another computer either

---

### Post by aggie on 2008-03-02
we think it might just be the USB cable now
We tried it in windows and it still failed after we got the driver.

Thanks for all the help

We got a new cable...Ubuntu seems to recognize it but we dont' seem to be able to talk to our microcontroller with it

I guess it'll take more time to debug this one

---

### Post by EmilyRose on 2008-03-07
Hey there, I tried doing your instructions in post #27, but when I get to the sudo insmod ch341.ko part it says 'file exists' but when I try to  probe it says no such module!!

I have the one with (05ad:0fba Y.C. Cable U.S.A., Inc.) readouts.  any thoughts??

EDIT: Ok, after some poking about, the error message has now changed to "unknown symbol in module"  But still no luck otherwise :(

---

### Post by amitsabne on 2008-03-24
Hi..these are the errors I get when I try the make command. By the way I have a converter with vendor id 4348 & product id 5523.

[mit@amit-laptop:~/Desktop$ cd ch341/
amit@amit-laptop:~/Desktop/ch341$ make
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/amit/Desktop/ch341 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/amit/Desktop/ch341/ch341.o
/home/amit/Desktop/ch341/ch341.c:316: error: unknown field ‘usb_driver’ specified in initializer
/home/amit/Desktop/ch341/ch341.c:316: warning: initialization makes integer from pointer without a cast
/home/amit/Desktop/ch341/ch341.c:316: error: initializer element is not computable at load time
/home/amit/Desktop/ch341/ch341.c:316: error: (near initialization for ‘ch341_device.num_interrupt_in’)
make[2]: *** [/home/amit/Desktop/ch341/ch341.o] Error 1
make[1]: *** [_module_/home/amit/Desktop/ch341] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [default] Error 2

I am clueless..:(

---

### Post by amitsabne on 2008-03-24
I am not getting it.. These are the errors I am getting. Can  someone help?

amit@amit-laptop:~/Desktop/ch341$ make
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/amit/Desktop/ch341 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/amit/Desktop/ch341/ch341.o
/home/amit/Desktop/ch341/ch341.c:316: error: unknown field ‘usb_driver’ specified in initializer
/home/amit/Desktop/ch341/ch341.c:316: warning: initialization makes integer from pointer without a cast
/home/amit/Desktop/ch341/ch341.c:316: error: initializer element is not computable at load time
/home/amit/Desktop/ch341/ch341.c:316: error: (near initialization for ‘ch341_device.num_interrupt_in’)
make[2]: *** [/home/amit/Desktop/ch341/ch341.o] Error 1
make[1]: *** [_module_/home/amit/Desktop/ch341] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [default] Error 2

---

### Post by k3pp0 on 2008-05-25
did anybody solved the problem?i need the usbserial to connect my ti-89...and of course tried the solution posted below with no result....
lsusb list the 4348:5523 device but there's no communication over cable.....

argh...it doesn't work...
HELP!!!

---

### Post by fragos on 2008-05-25
> **amitsabne said:**
> I am not getting it.. These are the errors I am getting. Can  someone help?

amit@amit-laptop:~/Desktop/ch341$ make
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/amit/Desktop/ch341 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/amit/Desktop/ch341/ch341.o
/home/amit/Desktop/ch341/ch341.c:316: error: unknown field ‘usb_driver’ specified in initializer
/home/amit/Desktop/ch341/ch341.c:316: warning: initialization makes integer from pointer without a cast
/home/amit/Desktop/ch341/ch341.c:316: error: initializer element is not computable at load time
/home/amit/Desktop/ch341/ch341.c:316: error: (near initialization for ‘ch341_device.num_interrupt_in’)
make[2]: *** [/home/amit/Desktop/ch341/ch341.o] Error 1
make[1]: *** [_module_/home/amit/Desktop/ch341] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [default] Error 2

Check out the readme and other text files in the tar ball. There may be a command line parameter you're missing. There may be an email listed for the author.

---

### Post by cdcase on 2008-05-26
My experience with Hardy indicates that it the cable should work automatically without configuration... Hardy has the new kernel by default, which means the new drivers are there and no recompilation is required.

If possible, I'd recommend a switch to Hardy, because that would almost definitely solve all of these problems automatically.

---

