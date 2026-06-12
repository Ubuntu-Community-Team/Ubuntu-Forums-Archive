---
title: "How much swap space should I assign?"
date: 2013-12-09
forum: General Help
---

### Post by Kymus on 2013-12-09
I've got a 1TB drive that was formerly isolated to a 500gb partition when I last installed linux (for some reason). The old swap space for 500gb was 6gb. I'm reading that a  rule of thumb is that it should be equal to RAM, but that this suggestion is outdated. Should I leave it at 6 or bump it up to 8?

---

### Post by Bucky Ball on 2013-12-09
You don't really need more than 2Gb. But the debate continues ...

---

### Post by Kymus on 2013-12-09
I'll just stick with the old amount then; whatev. Thanks :)

---

### Post by amjjawad on 2013-12-09
Kindly have a read at: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Usually, for newer hardware, I set: SWAP = RAM
Typing this from Core i5 1st generation with 4GB RAM and my SWAP Partition is 4GB.

For older hardware, I need to allocate: SWAP = 2xRAM
I have two machines with 512MB RAM so I set SWAP Partition to 1GB.

But again, have a read at the link I posted :)

---

### Post by r-senior on 2013-12-09
This is what a computer with 8GB of swap looks like when the swap is approaching half full. ;)

[ATTACH=CONFIG]248457[/ATTACH]

---

### Post by cybrsaylr on 2013-12-09
> **amjjawad said:**
> Usually, for newer hardware, I set: SWAP = RAM
Typing this from Core i5 1st generation with 4GB RAM and my SWAP Partition is 4GB.
Also always followed this guideline and had no problems.

---

### Post by CaptainMark on 2013-12-09
I have 10gb ram but only set 2gb for swap and I consider that more than enough, I dont hibernate my computer though, if you do you need to have an equal swap to ram

---

### Post by deadflowr on 2013-12-09
> **CaptainMark said:**
> I have 10gb ram but only set 2gb for swap and I consider that more than enough, I dont hibernate my computer though, if you do you need to have an equal swap to ram

I once had 1gb of ram and when setting the swap paid no attention to the size input and set 20gb, lol.

---

### Post by cybrsaylr on 2013-12-20
It's easy to mess up.
One time I ended up with two swap files and didn't know how that happened.

---

