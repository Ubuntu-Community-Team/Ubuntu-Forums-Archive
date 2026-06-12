---
title: "Ubuntu Google Drive Chromebook Help"
date: 2016-12-23
forum: General Help
---

### Post by leviwar on 2016-12-23
Hey guys so i got a new chromebook the other day. So i went ahead installed Ubuntu to play World of Warcraft. My problem is my Chromebook memory is only 16gb. I got it all working fine but i had no sound in game. So i installed the drivers for sound and boom ran out of space lol. Could not start ubuntu anymore, My question is i have 100gb+ of google drive space. Is it possible to put Warcraft or Ubuntu on the google drive so my chromebook doesn't run out of space again? 

Any help is very appreciated thankyou.

---

### Post by TheFu on 2016-12-24
Welcome to the forums.

No. That doesn't work.  Get a USB3 flash drive, format it EXT-something and use that for extra stuff. Do not leave it as exFAT or FAT32. Those file systems don't support the needed Unix permission model.
Or
Swap out the current storage in the chromebook. This will void the warranty.  Not all chromebooks allow this. My Acer C720 has a 128G SSD and my Toshiba has 64G SSD. Both of these chromebooks came with 16G of storage in an m2-SSD, but swapping that out for larger storage wasn't hard at all. But ...

When it comes to chromebooks and getting linux help, everything is highly, highly, device dependent.  Things that work on 1 model may be impossible on others. For example, you've assumed that we know how you "loaded ubuntu" onto your chromebook, but didn't actually tell us.  There are multiple different ways, each a little different. Each will have different options to resolve issues or make it impossible to do some things.  For example, running crouton makes supporting NFS next to impossible. For me, that was very important, so I wiped chromeOS and loaded full Ubuntu onto both devices. There are times that I miss chromeOS, but not that often.

Lastly - 16G of memory is probably incorrect. It probably has 16G of storage and 2G of memory. Being accurate with information here helps us to help you better.

---

