---
title: "Quick Charging in Linux"
date: 2007-02-26
forum: General Help
---

### Post by njkrut on 2007-02-26
Hello All.  I've many times over had the issue of not being able to charge my devices in Linux.  Anything from a Blackberry Phone to an Apple iPod it is just very irritating.

Gone are those days for me.

I bumped into a nice little tool called barry ([http://barry.sourceforge.net/](http://barry.sourceforge.net/)).  It is a pretty neat tool for anyone who uses a Blackberry.

Anyways down to the point.  I decided to change the code around and make it so that it is easy to change the power for any device.  Attached is the source and here is the explanation.  There are a slew of other ideas I had for this but for right now here are the features.  This may already be done but I was unable to find where.

I'm calling it anycharge or acharge (a play off barry's bcharge).  Obviously it is a little buggy since I've been working on it 30 minutes.

---------------------------------------------------------------

./acharge [--help | --list | device codes]

The way it works is this:
  Insert your USB device into your computer.
  From the terminal run: ./acharge list (in many instances you will need to run this as root to get detailed device information.)
  This will give you some output.  Look for your device name.  Above the device you should see some numbers here is an example:

Vendor: **1452** Product: **4613**
   Manufacturer : Apple
   Product : iPod mini
   Serial Number: 0000000000000000
Vendor: **1133** Product: **50437**
   Manufacturer : Logitech
   Product : USB Receiver
   Serial Number: ?

  The bolded items are the important information.
  Next run ./acharge [device id] in my case ./acharge 1452 this will turn the power on that port to 500mA.

This should be the process you need to turn the power to 500mA on any device.  Please let me know if this works for someone, anyone.  =)

---------------------------------------------------------------

Nicholas J. Krut
[email]njkrut@gmail.com[/email]

[Binary]("http://www.nikru.com/acharge/acharge") - Link to precompiled binary.
[Source]("http://www.nikru.com/acharge/acharge.cc") - Link to source.

To compile: 
   **g++ -o acharge acharge.cc -lusb**
Needs usb development package:
   **sudo aptitude install libusb0 libusb-dev**

---

### Post by njkrut on 2007-02-26
I don't think this is the appropriate Forum for this post could someone move it?  Sorry for the mistake!  =/

---

### Post by c.los on 2007-04-27
Doesn't work for me, I get the same results as I did with bCharge.

Before on Ubuntu 6.06 w/ bCharge
After I ran bCharge it would say it updated the device, but I would still have the error message on my Blackberry.

On Ubuntu 7 as soon as I plug my Blackberry in, it displays the little lightning bolt next to the battery like its charging but then disappears all together, after running bCharge and now aCharge, nothing happens - the program returns that it changed the charge settings, but it didn't :-/

---

### Post by c.los on 2007-04-27
Sorry, quick update - when I run aCharge now with the vendor ID (i was doing it with the product id before) it starts charging but then it gets taken away (possibly because of something running in ubuntu?)

---

### Post by Evil Dax on 2007-05-06
Since upgrading to Feisty, my telephone also doesn't charge anymore... Not even with this little tool.
Any more ideas?

---

### Post by tadtoll on 2007-07-17
Thanks for creating this! 

I was able to get it to run (but not work) from the provided binary, which is a lot easier than compiling barry. 

Iif you follow the blackberry and barry forums/ists, you will find that there is something about the feisty packaged kernel that causes barry (bcharge) to not work properly. This also appears to impact acharge, since I could not get it to set my charge to 500 on my 8830. 

[barry mail archivel]("http://www.mail-archive.com/barry-devel@lists.sourceforge.net/msg00145.html")

The solution, so far, whether using acharge or bcharge (barry) is the compile a kernel yourself, or move to gutsy.

---

### Post by fragos on 2007-07-17
% volts appears to be provided on all USB ports on my box.  They even provide power after a software shutdown unless I also turn off my power strip.  Every device that I've seen that would charge on a USB port had a device connector wiring problem.  The USB cables for my Palm E2 and LG VX8300 are both this way.  A different 3rd party cable for the Palm solved that problem.  I've yet to rewire the phone cable to fix the problem there.

---

### Post by arrrghhh on 2007-07-24
i got this working great with my pocket pc 6700!  thanks a bundle!

as a sidenote, i referenced this thread and your software in [this thread](http://ubuntuforums.org/showthread.php?t=498622).  i posted directions on how i got it to work.

i also noticed that this does cause my ppc to stay charging most of the time, but every it still does drop and come back - but it stays a heck of a lot longer than it used to (which was hardly at all) so i am still very appreciative of this software!  great stuff, keep it up!

edit...

i might've spoken too soon... after a few minutes it goes back to the old way of constantly disconnecting and reconnecting... and when i unplug it and plug it back in, i see the device when i do ./acharge --list - but when i do ./acharge [vendor#] it says "already at 500ma" - so it doesn't seemingly do anything for me...

---

### Post by snoozer on 2007-08-06
Hey everyone,

I ran into the same problem.
My BB didn't charge on my Ubuntu-System (even after I compiled my own 2.6.22.1 vanilla kernel from ftp.kernel.org). I'm running feisty on a notebook.
bcharge is a nice tool (if it works) - for me, it didn't.

After looking into some posts in several forums, I got back to my kernel and looked for some module I might have missed.

While searching through the kernel-tree, I found the following:


CONFIG_USB_BERRY_CHARGE:
Say Y here if you want to connect a BlackBerry device to your
computer's USB port and have it automatically switch to "recharge"
mode.

To compile this driver as a module, choose M here: the
module will be called berry_charge.


Just invoke a search for the config-key and activate the module. Everything worked fine for me after that.

Thanks for all the posts, they helped a lot!

Bye,
Jan

---

