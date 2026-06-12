---
title: "No sound HP laptop Sunrise Point Ubuntu 18.04 LTS"
date: 2018-04-29
forum: General Help
---

### Post by claven123 on 2018-04-29
I just installed Ubuntu 18.04 LTS dual boot with windows.  I have no sound.  My sound card is Intel Corporation Sunrise Point-LP HD Audio running on HP laptop.


What are my next steps

Thanks

Dennis

---

### Post by Yellow Pasque on 2018-04-30
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by claven123 on 2018-04-30
[http://www.alsa-project.org/db/?f=93375dfee288c2832f5aa3a6e7cd7fc7430ba77b](http://www.alsa-project.org/db/?f=93375dfee288c2832f5aa3a6e7cd7fc7430ba77b)



[COLOR=#333333][FONT=monospace]FYI.  I get sound via headphones.  I've runs some diagnostic stuff, but I'm sure it will be included in the above, drivers sound board etc...


Dennis 




[/FONT][/COLOR]

---

### Post by claven123 on 2018-05-02
Any suggestions on no sound?

Thanks

D

---

### Post by claven123 on 2018-05-07
bump.

D

---

### Post by Yellow Pasque on 2018-05-08
I didn't see anything obviously wrong in your info. I don't claim to be an expert though.
This was the closest thing I found in regards to your model: [https://github.com/torvalds/linux/commit/44be77c590f381bc629815ac789b8b15ecc4ddcf#diff-449948bd155c285a6d8c54bc1211c870](https://github.com/torvalds/linux/commit/44be77c590f381bc629815ac789b8b15ecc4ddcf#diff-449948bd155c285a6d8c54bc1211c870)
But that fix should already be integrated in the kernel you are using (4.15.x).

I'd like to note how hard it is to search by model name for a lot of recent HP Pavilion products. I guess marketers like "brand equity", but the Pavilion name is plastered over everything (and I've owned a few dating back to the last millennium). It seems very few people/reviewers use the detailed model number (cc0xx in your case). They just say Pavilion 15, but that's not very specific.

---

### Post by jszwedko2 on 2018-10-03
I'm having this same issue (Ubuntu 18.04 with  Intel Corporation Sunrise Point-LP HD Audio).

Alsa info: [http://www.alsa-project.org/db/?f=b9832ca6a3207b78257e8e709f4728b2ff4ecc47](http://www.alsa-project.org/db/?f=b9832ca6a3207b78257e8e709f4728b2ff4ecc47)

---

