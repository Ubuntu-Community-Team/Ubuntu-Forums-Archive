---
title: "md5 checksum/hash for Ubuntu .iso download?"
date: 2008-06-25
forum: General Help
---

### Post by brons2 on 2008-06-25
Is there somewhere I can view the md5 for the .iso that you download to install?

I downloaded the 64 bit version on my brand new Toshiba laptop but I have tried twice now to burn it in Vista using the Toshiba CD/DVD burn utility and it's made a coaster both times, erroring out about halfway through.  Before I go blaming something with the hardware or the software, I'd like to check the md5 and make sure the download is complete.

I hope it's a problem with the download, this laptop is only 5 days old and I already took back one other laptop that had hardware issues (hardlocks) an AMD TL-60 machine.  This time I got a Core 2 Duo T5250, and I'm a lot happier with the battery life and temps on this one.  But if there's a problem with the DVD drive I'mma take it back since it's only a few days old.

---

### Post by avtolle on 2008-06-25
Here you go: [https://help.ubuntu.com/community/UbuntuHashes#head-be34311205f11c747d4e163c597629c1d4627861](https://help.ubuntu.com/community/UbuntuHashes#head-be34311205f11c747d4e163c597629c1d4627861)

---

### Post by brons2 on 2008-06-25
Awesome, thanks.  I'll check it when I get home.

---

### Post by brons2 on 2008-06-25
well crap the checksums do match.  someting wrong with laptop perhaps.  I will burn on desktop and see.

---

### Post by WeEatVista on 2008-06-25
Try using a different burner instead of using the Toshiba default burner. For different .iso writers and the how to's check this site   [https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

Also check what type of writable CD you are using. CD-RW's didn't work for me, I had to go out and buy buy some CD-R's.  

If all else fails and you really want ubuntu (i know I would) request a free ubuntu CD from here [https://shipit.ubuntu.com/]("https://shipit.ubuntu.com/")

Hope this helps,

We Eat Vista

---

### Post by brons2 on 2008-06-26
I just burned it with one of my desktops instead with CDburnerXP.  

Install of Hardy Heron was flawless, I had done a factory recovery with the CD's since the laptop was a floor model, I didn't know that until after I decided to get it that they only had the floor model left.  The Toshiba factory recovery gives you an option to install the factory Vista OS to a smaller partition, so I did that to leave space for Ubuntu.  The laptop's board has Intel everything:  Core2Duo, 965 chipset, x3100 video, 3965 ABG wireless, wired ethernet, etc.  Seems to be well supported under Linux in general.  Everything worked right out of the box.

So then I decided to try to burn the .iso in Heron using first CD/DVD burner and then Brasero.  No luck, more coasters.  Even when I used Brasero and did a simulation first.

Finally had success when I limited the burn speed to 15x max in Brasero.  My CD's are pretty old, I don't burn that many, so I looked at the spindle and noticed that they were 16x max.  I have probably had this 50 CD spindle for 5 years and only used about half of them.  They're TDK branded, 70min/800MB.  

Oddly, my desktop doesn't seem to care about that, it will burn them at the max speed my burner is capable of, but I guess the laptop drive is more sensitive.  I borrowed a different CD from my roommate, one that is printed on it for up to 40x speeds, we'll see if that makes a difference.  I am also curious to make a DVD to see if I have the same problems. I have a non-copyrighted DVD that I need to rip from the European PAL format and burn in NTSC.  I had no problems burning DVD's with the laptop I took back for lockups, so we'll see what happens.

---

### Post by brons2 on 2008-06-26
Oh by the way, how would one do that in Ubuntu or Linux in general, to convert format from PAL to NTSC?

---

