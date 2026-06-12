---
title: "&quot;Signal Out of Range&quot; at boot"
date: 2006-11-14
forum: General Help
---

### Post by maniacmusician on 2006-11-14
hey,

since I did a clean install of edgy, I havn't been able to see the graphical boot-up screen (usplash, right?). instead, for those few seconds, it displays a "Signal out of range" message". I originally thought I was missing a package of some sort, because I installed a command line system, and then kde + xorg on top of it. But after reading around, I think it's my resolution that's the problem. 

I used to have it at 1280x1024 in dapper, but I found that this was a wrong aspect ratio for CRT monitors...and this was true. So in edgy, I've changed it to 1400x1050. I have a feeling this is why it doesn't display the usplash...is there any way that I can change the resolution for just the boot time? I don't want to downgrade to 1280x1024. Or if I'm diagnosing the problem wrong, what's another solution?

Thanks

---

### Post by turkenator on 2006-11-14
hey after some digging around found an answer for you
u can change the resolution for grub on the link im giving u it tells u how to do that 
[http://www.8ung.at/spblinux/grub.htm](http://www.8ung.at/spblinux/grub.htm)

Goodluck...
hope it helped

---

### Post by maniacmusician on 2006-11-15
Gah, no sorry it doesn't work.

When I add the vga option, the splash screen does show up. But it's in the bottom right hand corner of the screen, not in the center, where it should be. And with the vga option there, the X server doesn't start up! so I had to remove that and reboot. Now, X starts up...but it screwed with all my fonts and set them back to normal (made things look a lot bigger) so I had to fix that. So that's a no-go. Any other ideas?

---

### Post by turkenator on 2006-11-15
ooops sorry about that :P umm nothing else that comes to my mind

---

### Post by ranpha on 2006-11-16
wondering do you have a ATI graph card. I have the same problem with two machines both having ati card in them

---

### Post by maniacmusician on 2006-11-16
Why yes, in fact I do. but I doubt thats the problem. usplash worked in dapper. I guess it could be a regression.

I think I successfully got the problem nailed down to resolution; but maybe not. 

Just out of curiosity, how did you do your installation? a ____-desktop installation, right off the CD, or did you do a server install +xorg + DE?

---

### Post by ranpha on 2006-11-16
well i installed dapper with the livecd...then they problem was only on one PC. After the upgrade to edgy both computers have the same results.

I tried to remove devoptions= quiet splash. this work and you see the pv boots up (NOTE did this as grub when it boots. I can't seems to edit menu.lst. it refers back to a update and resets everthing). Also i think that the sync rates on my lcd dispay arn't correct so that you don't see anything. For example if i don't switch on my display and boot ubuntu i can't see my login...so i think ATI has some kind of auto sync

---

### Post by maniacmusician on 2006-11-17
I see...then our problems seem to be a little bit different. My setup works for the most part, it's just that 1400x1050 is too high a resolution. So far, I havn't been able to adjust the resolution without screwing up stuff on my computer.

anyone have any ideas?

---

### Post by ranpha on 2006-11-19
don't think our problems are different there related to each other. But i can't try it out on my main computer because it's in a progress of encrypting 1 terabyte then copy it to the back up and then encrypt and copy it back to the normal disk.....very slow progress....

---

