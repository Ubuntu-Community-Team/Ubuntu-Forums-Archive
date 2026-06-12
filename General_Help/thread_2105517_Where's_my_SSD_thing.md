---
title: "Where's my SSD thing?"
date: 2013-01-16
forum: General Help
---

### Post by moteprime on 2013-01-16
Hi there, hope somebody know the answer to this.

I recently bought a Thinkpad e130 (3358) with Win8 on it.
It's supposed to have a hybrid drive with 16Gb SSD. Apparently it's not one of those where the SSD part show up as a single independent drive, but one the probably works through some Windows driver.
The specs state "Hybrid Drive", but if i google the drive, a "Hitachi Travelstar Z7K500", there's nothing about hybrid or SSD there.
  
When i first got it, i partitioned and resized the disk to make room for Ubuntu. Got it installed, everything worked but grub screwed up Win8's boot so i "Recovered" it though the build in Lenovo windows recovery thing. That is the only thing i done to it, but i don't think that it's to blame (if anything is). Recovery didn't work, boot'repair did.

Windows 8 boot in 5 seconds.

So the thing is, where are the SSD?
It's not in the harddrive, and i can't see it anywhere in windows device manager, or disk manager and it's not anywhere to be seen in Ubuntu either.

Anybody know?

---

### Post by oldfred on 2013-01-17
Windows boots fast as it is hibernated.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

    
Is this what you have, an Ultrabook?
        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)

---

### Post by moteprime on 2013-01-18
What happend was. -I opened up the thing, no SSD anywhere. Called the place i bought it at, and after an investigation they concluded that they had posted the wrong specs, (specs come from a large cnet database). 
I'm sorry for not making a new post writing it, but i did mark the thread solved.
But thank you for replying to it anyway.

---

