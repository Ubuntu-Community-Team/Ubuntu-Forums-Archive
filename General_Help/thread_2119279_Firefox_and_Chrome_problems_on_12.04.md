---
title: "Firefox and Chrome problems on 12.04"
date: 2013-02-23
forum: General Help
---

### Post by freesitebuilder on 2013-02-23
I did a clean install of 12.04 in about August 2012, but Chrome gave me problems - about one in four links gave me the "snap" page.

I switched to Firefox, and it's been crashing several times a day. Finally today it crashed and won't reload - I just get the dialog to send an error report and restart. It's the latest version, which I think is 19.

I suppose this must be a fault on the hardware - I also get random system crashes, mainly "unable to handle kernel null pointer reference" which is bit beyond my experience, although I have googled it etc.

 I know the video card is rubbish - ATI Xpress 200, but could this cause the problem? It's a Celeron D, so I know that's quite old now.

TIA for any advice!

---

### Post by Gyokuro on 2013-02-23
Hi

Sounds like a hardware problem - I would suggest you that you maybe clean your box from dust and check that your memory (RAM) is not faulty. Most errors occur due to dust which let to overheating. Also more information about your hardware would be great: 

dmesg > dmesg.txt

Above command dumps kernel/hardware information in dmesg.txt file and that file/information could help us to try to solve your problem.

---

### Post by freesitebuilder on 2013-02-23
Thanks - I've attached my output as a txt file, let me know if I should include it in the post with CODE tags instead - I always get that confused!

---

### Post by Kow on 2013-02-23
I would highly recommend checking for hardware problems. Check the memory, CPU, hard disk. It will be time consuming, but still something that should be done. I recommend starting with memtest (I believe Ubuntu LiveCDs have this included). Then do some CPU stress tests. Then do a hard disk check (using the livecd). Make sure to run the tests in this order, as bad memory can masks itself as all sorts of problems. Based on your description of random crashes in various programs - especially about the null pointer error, I would guess bad memory or CPU or both. Definitely start with memtest. Let it run for at least 12 hours.

---

