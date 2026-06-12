---
title: "Ubuntu LiveCD (Hoary) tried to wake up a scsi card and froze!"
date: 2005-09-29
forum: General Help
---

### Post by Valder on 2005-09-29
I can't believe how bad luck is always in love with me!:mad:  So, here's the thing: A month ago I downloaded Live CD 5.04 and started working with that, till I could find time to install Hoary for good on my pc. Now that the time has come, I run into lots of problems! One of them is the following:

Yesterday I was working nice and easy with Live CD. Today I woke up and said "Why dont I try the Live CD again to check some things?" So I did! I put the cd and booted from there. Everything's fine....it says it loads vmlinuz etc etc and then it goes into that nice black screen with lots of info and many Okays at the right.....BUT it gets stuck when it refers to my adaptec scsi 2940 adapter. It says that it is sleeping or something like that and that cd is sending something to it and responded with an error blah blah blah and I dont remember what else. Then it freezes. I press enter, it goes a line below. Well if I wanted it to become a text editor, I would have asked for it!

The thing is that I indeed disabled the card through Windows XP over a month ago because the scsi controller reseted every minute and I couldnt listen to my favorite mp3s without that damn "brrr"! How on Earth did Ubuntu Live CD tried especially today to "wake up" the adapter? 

Is there anyway I can fix this so the loading procedure doesnt get interrupted from the sleepy card? Bios settings or something?

ps: Windows XP still sees it as "disabled" and generally it is where I left it to be!:)  But why this change in ubuntu's act today?

NEW INFO: (I hope I remember them well)

Among many things it says somewhere: 

<<<<<<<Dump card state Ends>>>>>>>>>

aic7xxx_dev_reset *(returned?)* 0x2003 *(and 0x2002 on 3-4 lines below)*

*except dev_reset it also had a simmilar line for abort*

---

