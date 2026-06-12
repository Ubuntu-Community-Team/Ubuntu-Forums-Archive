---
title: "Windows exploded GRUB."
date: 2007-07-15
forum: General Help
---

### Post by Rovdjur on 2007-07-15
So I had my new installation of Ubuntu working flawlessy, and then I installed XP Pro, and everything was working fine (including GRUB), but then I downloaded the preinstalled programs for my laptop off the Lenovo Website (I have a Lenovo Thinkpad T60p), and it installed some Rescue and Recovery thing, and now Grub will not boot.

If I boot from GParted, I can tell it to boot from partition 1, and Windows will boot just fine, but no other partitions will boot (#'s 2-4 with Ubuntu on them). I even tried changing the flags on the partitions but it won't work.

So now I can only force my way into Windows with GParted, and I can not boot Ubuntu at all.

When I turn on my laptop with no CD in there, it just blinks a cursor then says "GRUB" and that's it. I have no option to select or type anything.

Any way to get GRUB working again?

---

### Post by splintercellguy on 2007-07-15
Yep, use Super GRUB to reinstall GRUB.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by Rovdjur on 2007-07-15
> **splintercellguy said:**
> Yep, use Super GRUB to reinstall GRUB.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Well I'll be damned, the web page is not loading. I googled it and the same page came up. I'll give it some time and try again later in case the server is temporarily down or something.

Thank you though!

---

### Post by markusf21 on 2007-07-16
try this page instead [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by bodhi.zazen on 2007-07-16
Yea, the supergrub site is up and down.

But ... you do not need any of that , you can restore grub from the Ubuntu CD :

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

