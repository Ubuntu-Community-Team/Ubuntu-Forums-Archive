---
title: "help putting Ubuntu on a USB Hard drive"
date: 2007-01-01
forum: General Help
---

### Post by lyceum on 2007-01-01
My dad has 2 laptops, on personal, one for work. He just bought a new hard drive for his personal laptop and would like to run Ubuntu on that drive, but he wants to be able to hook the hard drive up with a USB 2 connection. He wants to leave his old hard drive where it is. Here is the thing, I can't see the hard drive on Windows, before I portioned the hard drive or after. Ubuntu picked it up just fine, so I though that was odd. 

I loaded Ubuntu onto the hard drive (without thinking) and now I can't get to my hard drive on my laptop. That is not a big deal, I was testing another disrto and was ready to put Ubuntu back on anyway. Now, my laptop boots up just fine, but I can't boot on any other PC. He wants to be able to plug the thing into any PC that can boot from a USB and just go from there. 

I know where I messed up, I do not know how to set Ubuntu up as a "floater" like DSL on a flash disk. It set Grub up for my machine, not for others. At least, I think that is what I did wrong. Can you even run Ubuntu from a flash disk? (a large enough one anyway)

Its a 100GB Seagate hard drive set to Master in a Mobile Disk external data storage USB 2 box.

And advice? Thanks.

---

### Post by lyceum on 2007-01-02
*Bumping*

---

### Post by laidback on 2007-01-02
The book Ubuntu Hacks by Jonathan Oxer et al, published by O'Reilly  has a way of using a memory stick in conjunction with a live CD, it's called persistent mode. I've tried it and managed to get it working, but I find its use limited as I couldn't work out how to store all my settings between sessions, i.e. Internet connection set up. This meant redefining too many things each time. 

If you're interested please note the following erata to page 8 and 9. 
towards bottom of page 8:-

Line $sudo mkfs.ext3 -b 4096 -L casper-cow /dev/sda1 should be
$sudo mkfs.ext3 -b 4096 -L casper-rw /dev/sda1 (rw not cow)

and on page 9 in the paragraph starting ...When the live CD starts up,.....
press F6 rather than the F key indicated.

Hope this helps.

---

### Post by lyceum on 2007-01-02
> **laidback said:**
> The book Ubuntu Hacks by Jonathan Oxer et al, published by O'Reilly  has a way of using a memory stick in conjunction with a live CD, it's called persistent mode. I've tried it and managed to get it working, but I find its use limited as I couldn't work out how to store all my settings between sessions, i.e. Internet connection set up. This meant redefining too many things each time. 

If you're interested please note the following erata to page 8 and 9. 
towards bottom of page 8:-

Line $sudo mkfs.ext3 -b 4096 -L casper-cow /dev/sda1 should be
$sudo mkfs.ext3 -b 4096 -L casper-rw /dev/sda1 (rw not cow)

and on page 9 in the paragraph starting ...When the live CD starts up,.....
press F6 rather than the F key indicated.

Hope this helps.

Awesome! I'll check it out and post back either way it turns out. Thanks!

---

### Post by bodhi.zazen on 2007-01-02
USB install:
	[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
	[http://doc.gwos.org/index.php/Ubuntuliveusb](http://doc.gwos.org/index.php/Ubuntuliveusb)

USB Live:
	[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by lyceum on 2007-01-03
Just wanted to say thanks to those that posted. In the end I did a normal install of Dapper on the new hard drive plugged in to the USB and slacked off (did nothing). My dad decided to give Ubuntu a shot and when I swapped the hard drives the new one took to the laptop like it was installed there in the first place. :cool: I guess it was the box I had the hard drive in.

---

