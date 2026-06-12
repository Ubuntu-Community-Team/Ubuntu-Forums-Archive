---
title: "USB Hub Power Cycling"
date: 2013-03-04
forum: General Help
---

### Post by ndstate on 2013-03-04
Hello,

I recently purchased a USB 3.0 hub and I  am having issues with it power cycling my external hard drive (USB 3.0 only, no power). When the AC power is plugged in to the hub it will turn the hard drive on and off continuously. When power is not plugged in to the hub it seems to work fine for powering the hard drive.  This is the second hub from the manufactuer. The external hard drive works fine if plugged directly into the computer.

How do I go about figuring out if this is a Ubuntu setting or something causing the issue?  

Thanks

---

### Post by tgalati4 on 2013-03-04
It's possible that the power supply has an over-current, resetable fuse that is causing the on/off behavior.  USB3 allows more power than USB2, but the power supply may not be up to specification.

To see what is going on, open a terminal, plug the drive in, plug the power supply in:

```
dmesg | tail -50
```

Wait a few minutes for the on/off behavior then run the command again and compare the results.

---

### Post by ndstate on 2013-03-04
Hello,

Thank you for the tip.

[Here is a link to the results before the power cycle]("http://pastebin.com/kC7kKyNz")

[Here is a link to the results after the power cycle, this is right after the device remounted.]("http://pastebin.com/jgR1ii99")

[3rd Power Cycle, before the device remounted]("http://pastebin.com/Umq9jr0P")

Thank you!

---

### Post by tgalati4 on 2013-03-04
You have buffer I/O errors on /dev/sdb5 which is both bad and probably the disk that your Ubuntu installation is on.  The USB3 shows up fine and shows the disconnect/reconnect with each power cycle.  Sometimes, when there is an overcurrent, you will get an error message--but I don't see any.  So I would look at the specifications printed on the 5VDC power supply.  How many milliAmps does it say?

USB3 is supposed to supply 900 mA (up from 500 mA in USB2) for each port.  If you have multiple ports being used, or if your power supply can't supply 900 mA, then that could be the problem.  Or it could be a faulty hub, or a poor design, or the disk is drawing more than 900 mA.

USB3 specifications:  [http://en.wikipedia.org/wiki/USB_3.0](http://en.wikipedia.org/wiki/USB_3.0)

There's a lot of crappy hardware out there, so you have to do a lot of testing and read reviews to get stuff that works the way it is supposed to.  I had a similar thing happen a few years ago with a portable USB2 drive enclosure.  Some drives would work in it, others would refuse to work, even with the dual USB cable (500mA + 500mA).  Obviously a drive that draws more than 1,000 mA (1 Amp) will not work in that enclosure, so I had to use an external power supply for those drives.

---

### Post by ndstate on 2013-03-04
sdb5 is the hard drive I am plugging in, its a partioned NTFS 1tb HD that was in my comptuer before I replaced it with an SSD.

I am seeing a lot of ```
xhci_hcd 0000:00:14.0: WARN Event TRB for slot 21 ep 0 with no TDs queued?
``` type errors.  I cannot find anything when searching that would explain what this is.  Also, ```
usb 4-3: Set SEL for device-initiated U1 failed
```  -- any ideas on those?

Power output is listed as 2.5A on the power adaptor it came with 

[New Port, With Power, After Power Cycle]("http://pastebin.com/j30sq4WA")
[Power Cycle, Unplugged Hub, Plugged in HD directly to computer]("http://pastebin.com/vdE3PL7A")

Can I see how much power the external disk is drawing?


Thank you for your continued help

---

### Post by tgalati4 on 2013-03-08
I couldn't find any info on those errors either, so I didn't comment.  They could simply be warnings in the kernel, that something is strange in the communication, but not fatal for file disk access.  The kernel has a lot of these warnings, an benign warnings tend to get suppressed in later kernels.

As far as power consumption, I know that Mac OSX will show consumption in "About This Mac" --USB Properties.  I'm not aware of a similar utility in linux to show actual consumption, just warnings that show up when in an overcurrent situation.

So the errors could be a result of underpower.  Perhaps the power supply is not putting out full voltage and current needed to keep the drive spinning properly.  That could account for errors.  I would look for similar errors under Mac and Windows and that would confirm that your hard disk/power supply is real and not linux-related.

---

### Post by ndstate on 2013-03-10
Thanks.  I am sending the hub back.  The HD is also going back as there are tons of corrupt sectors.  Thanks for your help!

---

