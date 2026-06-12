---
title: "[SOLVED] Problems after first boot up"
date: 2008-05-10
forum: General Help
---

### Post by Megacherv on 2008-05-10
Hi. I've tried installing Ubuntu via Wubi loads of times, and each time it hasn't worked. The installation works 100% perfectly each time I try (I have the ISO saved in C:\ubuntu-backup) but when I boot it up, and do the 10 minute wait, the 'Checking Installation' box comes up. It then freezes at 0%. I've left it for about half an hour (enough time to watch Ben 10 :D) and it didn't change.

I'm guessing that the most likely cause is my RAM amount (222Mb, I did the '--skipmemorycheck' argument in a Command Prompt), but I was wondering if there were any other possible causes. I'm getting my RAM upgraded on Tuesday (he has to order the parts...freakin' old laptop needing nortmal DDR, I won't have enough for 1Gb)

Also, I'm wondering if Ubuntu will automatically work with my wireless card. I can't replace it if not since it's built in and I don't have a card slot on my laptop.

Thanks in advance!

---

### Post by Cookie1456 on 2008-05-10
It should work, I think the minimum RAM needed is 64mb.

What kind of wireless card do you have? Most wireless cards should work right on start.

---

### Post by chorca on 2008-05-12
This same thing happened to me when I tried to install it on an old PII laptop with 160MB of RAM. It got to "Checking Installation" and basically thrashed the disk for about a half hour before I killed the install. It's possible that there's not enough RAM and it's swapping like crazy, though I couldn't say for sure.

---

### Post by ago on 2008-05-14
The minimum required ram is 256MB, below that freezes are likely. That is why we have the memory check... 

A version that will work with less will be probably available in 8.10.

---

### Post by Megacherv on 2008-05-17
I got my laptop's RAM upgraded and it works perfectly fine now. I'm probably not going to use Windows ecept for when I'm using 4oD.

---

