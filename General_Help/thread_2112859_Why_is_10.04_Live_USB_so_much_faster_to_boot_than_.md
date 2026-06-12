---
title: "Why is 10.04 Live USB so much faster to boot than 12.04 Live USB?"
date: 2013-02-05
forum: General Help
---

### Post by brucecode on 2013-02-05
Hi,

I have Ubuntu on Live USB and have recently used it to recover some data. Over the last few days I have noticed that my USB with 10.04/Lucid Lynx loads *exceptionally* quickly compared to 12.04/Precise Pangolin.

10.04 loads so quickly that there is barely even time to display the loading dots, whereas 12.04 I can leave the room and get a drink then come back and still wait.

The only three things I can think of as being causes are:

[LIST=1]
[*]10.04 is on a 1G USB but 12.04 is on an 8G USB
[*]12.04 has persistance but I'm pretty sure 10.04 doesn't
[*]I read something on these forums about poor Intel Wireless support for 12.xx but don't know whether that applies to 10.xx - in any case I assume that this is the least reason since wireless isn't (???) required to *load* Ubuntu.
[/LIST]
This isn't really important and is very low priority - it is mostly curiosity...


Thanks,


Bruce

---

### Post by elgordodude on 2013-02-05
My first guess would actually be compiz / unity unless you installed gnome on the persistent file. While it seems worse with 12.10 than 12.04 I can tell you at least anecdotally that I've noticed a significant slowdown on any legacy (e.g. socket 775 or 939 or earlier) hardware.

As for the options, 1 shouldn't matter, USB 3 should be faster than 2, but flash size shouldn't matter. 2. Possibly, how much have you installed, and how much more is it loading at boot as a result? 3. Unlikely, especially since you're not using wireless.

For the record I prefer lubuntu on my live drives, it's about 5% faster, which is negligible, until you're scanning a 1TB drive for viruses...

---

