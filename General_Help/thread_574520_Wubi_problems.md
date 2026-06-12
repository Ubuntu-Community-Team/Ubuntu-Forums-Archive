---
title: "Wubi problems"
date: 2007-10-12
forum: General Help
---

### Post by 2gttalon on 2007-10-12
Ok so i downloaded wubi because i wanted to install ubuntu the safe way. I downloaded wubi i and downloaded the ubuntu iso alternate  from the net. Finish the download and goto reboot . I then choose ubuntu from the dual boot menu and it starts the ubuntu text installer which stops and says it can't find the iso. I try to get it to detect my cd-rom version but wont detect that either. I've tried the wubi method twice and every time it goes into the text installer it stalls and tell me it cant find the iso. Whats wrong ?brand new computer is 4 days old

Specs:
Acer travelmate 2480
Win xp

---

### Post by 2gttalon on 2007-10-13
wow 58 views and everyone is clueless?

---

### Post by ago on 2007-10-13
> **2gttalon said:**
> Ok so i downloaded wubi because i wanted to install ubuntu the safe way. I downloaded wubi i and downloaded the ubuntu iso alternate  from the net. Finish the download and goto reboot . I then choose ubuntu from the dual boot menu and it starts the ubuntu text installer which stops and says it can't find the iso. I try to get it to detect my cd-rom version but wont detect that either. I've tried the wubi method twice and every time it goes into the text installer it stalls and tell me it cant find the iso. Whats wrong ?brand new computer is 4 days old

Specs:
Acer travelmate 2480
Win xp
The physiscal cd does not work with 7.04. As for regular ISO you might have been using one for the wrong kernel or wrong version. Check /tmp/lupin.log to see the exact reason.

---

### Post by 2gttalon on 2007-10-14
Well i deleted the dowloaded iso within wubi,so how do i get wubi to download a version other than alternate

---

### Post by Wall86 on 2007-10-14
doanload the .iso you would liek to use and place it in the same folder as the Wubi installer. You should be good to go, if there is an error with the checksum of the downloaded .iso it will then try downloading the alternate .iso

---

### Post by erlyrisa on 2007-11-13
Just to clear things up....

"alternate" actually refers to a ubuntu iso image that has some added abilities...

I presume Wubi would need these added abilities.

Reason I am here, is I have the problem as described above, and really can't be bothered figuring out what is wrong(or for that matter be able to)... other than if I state the obvious -> would Fat32 have anything to do with it? ...I formatted me XP drive old school so that 98 can work beside it. Normally I don't see how the format of the drive has anything to do with the install, unless wubi hasn't been given the ability to mount the drive it's residing on if it's fat32?

PS... sorry to not have been a Linux user for so long (I bought a new laptop, and me desktop now rots) - hopefully wubi will work for me and I can get back in the swing of things.

---

### Post by ago on 2007-11-13
Wubi 7.04 works with the ALTERNATE ISO 7.04
Wubi 7.10 works with the DESKTOP ISO 7.10

You cannot mix and match...
As for 7.10 there are some installation problems with some hardware configurations but if it can be installed, it works well. So I'd start giving a shot to 7.10.

---

