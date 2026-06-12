---
title: "Why does my data transfer speed start fast then taper down?"
date: 2021-07-20
forum: General Help
---

### Post by juntjoo2 on 2021-07-20
Strange thing is copying files from my sd card through my phone plugged directly to my old laptop drive using a Ubuntu live disk goes fast at first like 50MB/s then slows down really slow to as  1MB/s and half the time quits. And it appears disconnecting my phone then reconnecting it resolved this temporary fatigue then I can try again about about a gig at a time. I wonder if this is a symptom of using the external hard drive which sounds like it has to wind into gear everytime I do anything.

---

### Post by GhX6GZMB on 2021-07-20
A detailed description of your hardware might help.

---

### Post by juntjoo2 on 2021-07-20
What specs are you looking for? It's an old 2011 laptop, 1ghz, 4gb ram.

Are you familiar with this "fatigue" symptom? 

Right now I'm getting a steady 550kB/s. Slower than the SD card in the phone, the phone's USB 3.0, and the laptop's USB 2.0. So IDK what else could be the bottleneck in there

---

### Post by GhX6GZMB on 2021-07-20
Well, the interesting information would be your laptop HDD, your external HDD and the interface to it. USB2 can be many things.

---

### Post by him610 on 2021-07-20
I think it has to do with buffers.
When you first start the transfer, buffers are empty so it appears the transfer is fast. After they fill up then transfer speed slows down because the buffers are emptied by the system at a slower speed due to some of the reasons discussed in #3 & #4, and possibly other things too.

Does that make sense, or did I just confuse everyone?

---

### Post by juntjoo2 on 2021-07-20
Oh sorry, not "external hard drive" but external DVD drive. Whatever. It's slow. Buffers? I think I understand.

---

### Post by Tadaen_Sylvermane on 2021-07-21
Another thing to think of. If it's thousands of tiny files it will be much slower than one big massive file. I'm not educated enough to explain the why behind this, just know that it does matter.

---

### Post by GhX6GZMB on 2021-07-21
"External DVD drive"?
Of course it's slow. It needs to burn a DVD, this takes some time. The fast burst you see at the beginning is the RAM buffers filling up, then it's down to DVD write speed.

---

### Post by juntjoo2 on 2021-07-21
I'm not reading or writing from it though. I'm just using it to run the live ubuntu DVD

---

### Post by GhX6GZMB on 2021-07-21
I'm sorry, but you've lost me. Try rephrasing the whole issue so it's understandable.

---

### Post by juntjoo2 on 2021-07-21
I'm just wondering how the write speeds go from really fast to really slow from my phone directly connected to my laptop to the hard drive. It seems if I restart the transfer after it slows down it starts again really fast. Someone else said something about "buffering"

---

