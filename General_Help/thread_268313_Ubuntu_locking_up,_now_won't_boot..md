---
title: "Ubuntu locking up, now won't boot."
date: 2006-09-29
forum: General Help
---

### Post by rende on 2006-09-29
Hi all, I have been running dapper for about month now, previously ran gentoo for a few years on my current system.  No serious problems up until about a week ago.  My system would lock up for no reason, I was unable to get any response from mouse or keyboard and also was unable to ssh in from another computer, or even ping the system.  Seemed to happen randomally, I tried some of the normal fixes like changing to an older video driver, etc. an still this problem. 

After about the 5th or 6th lockup, I hard booted and the boot process froze at Mounting the root file system...

I suspected possibly a hard drive was failing so I booted with the Live CD and fscked my drives and mounted the root partition and everything seemed to be fine.  I rebooted again and was able to boot from the harddrive into my system where it ran fine for awhile and then promptly locked up again...

I again hardbooted and got the same pause at Mounting the root file system..., So I once again broke out the Live CD to reboot and take a look at the logs and now the Live CD will not boot either, it also freezes at Mounting the root file system...

So now I cannot boot using either my HD or my Live CD.  I thought maybe a mem error, so I ran memtest and it ran through all 10 tests without an error, then I ended the test once it restarted back at test 1 and rebooted but still the same problem...

Anyone have any ideas?

Thanks.

---

### Post by morphodone on 2006-09-30
I always have a few different live cd distro's lying around.

You might download another live distro and see how that goes.

---

### Post by rende on 2006-09-30
Hrm, well I tried knoppix too, thats not working either.  

I'm not sure exactly what it could be ..... Out of 3 more tries to boot the Dapper Drake live CD: I was able to get the Ubuntu LiveCD to boot once, but it froze/locked up on the gnome desktop before I had a chance to do anything.  On another attempt it froze about as soon as the first spalsh screen appears after choosing Run/Install Ubuntu (ie. the screen with the status bard, but it froze before any text was displayed) and on another it froze on this same screen only at a different part.

I also ran memtest once again and didnt get any errors reported.

Any ideas what could be causing it to lock up so randomally?

---

### Post by morphodone on 2006-09-30
Well it's not just the cdrom drive because you can't boot to
the hard drive either.

Hmmm, maybe your motherboard is going bad.  I've had a couple of boards
that had bad capacitors.

All sorts of unexplained things happened at that point though.

Wouldn't think memtest would complete either...

weird

---

### Post by rende on 2006-09-30
Yeah so I have 2 HDs connected to the system and I disconnected them and tried without on both ubuntu LiveCD and Knoppix just to remove the drives from the equation...

I boot with debug on knoppix and i edit the boot options for ubuntu and remove the splash screen.  In both it halts right after it searches for USB ports...I get a message like 3 USB Ports found, and then it freezes.

Take note, *before* the halt, it goes through some probing of the IDE interfaces, so Probing IDE interface ide0... etc, finds my CDROM drive and thats all, but the point is it gets past this part to searching for usb.

So now I retry and add nousb as a boot option, and it halts as its probing the IDE interfaces.

So normal boot, it halts when it detects my USB ports, if I turn off usb support, it halts when it is probing IDE interfaces.

I'm beginning to thing mobo is going bad like was suggested, I have never encountered anything like this so its hard for me to say...But drives aren't the problem, memtest works...so I guess it's time for a new mobo, any other opinions on some tests I can try to verify this?

Thanks!

---

### Post by yopnono on 2006-09-30
Have you tried just to clear/reset your BIOS.

---

### Post by rende on 2006-09-30
Yes, I did a reset to default settings.  I'm starting to think it might be time for a new mobo...:(  It just seems odd how random the lockups appear.  The behavoir I described above happens about 90% of the time, but every now and then it locks up at some other part of the boot process and more rarely it even boots completely and I can login but it locks shortly tehreafter.

Seems the frequency of actually getting it to boot is decreasing the more I mess with it.

---

### Post by yopnono on 2006-09-30
Have you checked the temp/fans of AC/DC unit and cpu.

---

### Post by PriceChild on 2006-09-30
I started getting random errors usually associated with the motherboard, and also only half of my IDE drives working (always those on IDE1)

In the end, i almost forked out for another MB before someone suggested the power supply.

£5 later and all is fixed :D

If i were you i would try and test every single piece of your pc with friend's parts, eliminating pieces if they work fine.

---

### Post by rende on 2006-09-30
Hrm, I don't have an digital thermometer, so I'm not sure if there is anyway I can check my temps during boot process...My BIOS does support some CPU temp warnings tho and it allwos me to set the temp for when the warning will happen so I will take a look at that.

Good idea about the power supply that didn't even occur to me, I can still hear it running when it locks up, but i suppose some fluctuations in the power could make things unstable.

I'll throw in a new power supply that I have from an old copmuter and give that a shot too.

Thanks

---

