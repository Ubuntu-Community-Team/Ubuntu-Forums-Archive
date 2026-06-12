---
title: "[Ubuntu Gutsy] - Downloads keeps getting corrupted"
date: 2007-11-18
forum: General Help
---

### Post by dennistb on 2007-11-18
Hello I have a odd issue going on and with no luck trying to solve this problem.
Maybe you can please help me :)

My issue is that when i try to download a large file say an iso image, the file will be corrupted, well little bits of it anyway

Even when i tried downloading a torrent file using ktorrent and downloading ubuntu-7.10 from using torrent file located at the ubuntu download page - the download will still be corrupted

ktorrent scans the file for failed chucks and redownloads them
but it keeps getting failed chucks at the vertification process

i do not think this a hardware issue

I even tried ctorrent in the recovery concole  (downloading Ubuntu-7.10)
and still it would be corrupted or not fully downloaded.

Any help on this issue will be greatly appreciated.

ps Maybe i should try downloading a large picture
and see if it looks dissoriented.

---

### Post by leonidas666 on 2007-11-18
Actually, the built in error correction of TCP/IP should prevent that downloads become corrupted. That makes me think that it is in fact a hardware issue. Do you have any specific reason why you think that it is NOT a hardware issue?

My first guess would be that your memory is bad. You could try tunning memtest86, it's on the livecd.

---

### Post by dennistb on 2007-11-18
so It can be a memory problem?
ok i will try it and tell you if anything unsual comes up

what error would i be looking for in the memtest?

---

### Post by leonidas666 on 2007-11-18
> **dennistb said:**
> so It can be a memory problem?
what error would i be looking for in the memtest?

Bad Memory can cause random crashes, random errors when running certain applications, and generally this kind of problems which are a PITA to diagnose. On the other hand, bad memory is fairly easy to diagnose (->memtest), so it's a good starting point. 
when running memtest, in one part of the screen it will display the memory adresses where problems have been found. If this area is empty, your memory is fine. You'll understand it when you run it, it is self-explanatory.

P.S.: Memtest is accessible from the boot-menu of the livecd, you don't need to start the whole ubuntu os from the cd.

---

### Post by traderpats on 2007-11-18
Agree that bad memory will display the symptoms stated.  You could also try removing one of the memory modules and download again.  When I tracked the memory issue down on my system all I had to do was  re-seat the module.  Go figure.

---

### Post by dennistb on 2007-11-18
Thank you guys it was indeed bad memory 
I had two slots of it and i took one out

Now i started ktorrent again, it redownloaded the failed chucks
and now all chucks have been fully comfirmed downloaded.

What a relief, i was spending days trying to fix this issue.

so i should not be having a problem donwloading large files again.
Thanks!

---

### Post by dennistb on 2007-11-18
My other question is why would bad memory problems 
corrupt the downloads?

---

### Post by geirha on 2007-11-18
All the data received from the network is stored in memory before it is written to disk. And if part of the memory is bad, the data received may not be the same as the data written to disk.

---

