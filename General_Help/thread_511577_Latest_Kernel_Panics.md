---
title: "Latest Kernel Panics"
date: 2007-07-28
forum: General Help
---

### Post by jamestrowbridge on 2007-07-28
I've used 6.06 just fine in the past when it was new, with the exact same hardware I tried out 7.04 and as soon as it was done booting up - the screen would freeze...not even allowing me to turn on the numlock LED.  So I fixed that problem with some grub editting.  Then when I logged in under terminal (restore mode) or GNOME after about 1 or 2 minutes the whole system will freeze and my scroll lock and caps lock LED flash.  This problem has forced me to revert back to 6.06, maybe I'll install 6.10 to try it out, but I'm too frustrated with the newest kernel under 7.04 to use that one.  I'm using an ATI Asus Radeon 9200 series video card, a pentium III 1.13 Ghz, .75 GB mem, and a sony DVD-RW drive.  If any other information is necessary for anyone that wants to give this problem a shot let me know in email.  [email]jamestrowbridge@gmail.com[/email]  thanks.  -Jim

---

### Post by jamestrowbridge on 2007-08-06
Hey everybody, I fixed my problem after about a week of troubleshooting!!  I used the irqpoll kernel option in grub, along with turning off a lot of unused crap from BIOS and now my kernel hasn't panic ed and I even have beryl running, without any FREAKING fglrx dirvers! ha!  I'm using the regular ati driver that was originally detected....I'm happy...it took a while but I fixed it!  good luck with anyone with a similar problem...feel free to email any questions to me.

---

