---
title: "Swap never seems to get used, even for memory intensive tasks"
date: 2007-04-04
forum: General Help
---

### Post by Roobert on 2007-04-04
I'm trying to throw everything I can at Ubuntu to make it use my swap space, as it never seems to get used in my system monitor applet. I'm bzip2'ing a 9.3 GB data archive, at the same time trying to compile some source code with 'make', all the while browsing the web (Firefox), playing music (Amarok), and checking email (Firefox). 

Although CPU goes to 100% (3.2GHz processor), and I've got 3GB RAM, the swap space monitor always shows 0% in use. I've allocated 2.5GB for the swap partition when I installed Feisty. Have I not configured this properly or something? Shouldn't it get used when my disk activity is at a maximum?

---

### Post by ArieT on 2007-04-04
I don't think you need the swap because of your huge ram disk. I've go only 1024mb ram and my pc doesn't use his swap space either.

---

### Post by Qew on 2007-04-04
At most, I'd have made a 512MB swap partition if I had 3GB of RAM. As said above, you could even do without. I also have 1GB of RAM and have a 512MB swap partition, and harldy ever notice swap being used, even on intensive operations. The most I've seen it used was when I noticed about a third of it being consumed.

---

### Post by Roobert on 2007-04-04
Oh, ok. Maybe I was a little to paranoid in installing that much swap. I really don't feel like messing around with my parititions anymore, so I'll leave it as is. Thanks!

---

