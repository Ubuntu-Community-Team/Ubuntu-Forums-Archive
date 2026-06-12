---
title: "lubuntu on aspire one d255"
date: 2018-09-10
forum: General Help
---

### Post by xristosp59 on 2018-09-10
Hello people :D i just installed the 64 bit verison of lubuntu cause it says on intel's website that it has a 64 bit cpu but the netbook only has 1 gb of ram.
Should I install the 32 bit version of lubuntu instead?

---

### Post by Autodave on 2018-09-10
You could considering the amount of RAM that you. It will run marginally faster on the 32 bit install.

---

### Post by Rex Bouwense on 2018-09-10
It depends.  How is the 64 bit version of Lubuntu running?  If it is running fine (and it should be) then no action is required.  As Autodave stated "It will run marginally faster on the 32 bit install".  I am not sure you will be able to notice a difference.  I have the 32 bit installed on one of my computers with 1 GB of RAM and the 64 bit version installed on another.  I cannot tell a difference.

---

### Post by Yellow Pasque on 2018-09-10
If you have $10 to spare, consider moving up to a 2GB stick: [https://www.amazon.com/Memory-Compatible-Aspire-D255-2256-Aod255-2256/dp/B00BXLCTZ4](https://www.amazon.com/Memory-Compatible-Aspire-D255-2256-Aod255-2256/dp/B00BXLCTZ4)

---

### Post by geofftf on 2018-09-11
Your main problem with that machine is the processor, which is an Intel Atom N550 @ 1.5GHz. This processor has a Passmark score of 525. My experience is that you need a processor at least three times as fast for good performance, but you may be more patient than me.

To upgrade the memory on that machine, you have to replace the 1GB module with a 2GB module:

[https://www.memorystock.com/memory/AcerAspireOneD255DDR3.html](https://www.memorystock.com/memory/AcerAspireOneD255DDR3.html)

In general 64 bit programs appear to be bigger but faster than 32 bit programs:

[https://stackoverflow.com/questions/2378399/are-64-bit-programs-bigger-and-faster-than-32-bit-versions](https://stackoverflow.com/questions/2378399/are-64-bit-programs-bigger-and-faster-than-32-bit-versions)

"I typically see a 30% speed improvement for compute-intensive code on x86-64 compared to x86. This is most likely due to the fact that we have 16 x 64 bit general purpose registers and 16 x SSE registers instead of 8 x 32 bit general purpose registers and 8 x SSE registers. This is with the Intel ICC compiler (11.1) on an x86-64 Linux - results with other compilers (e.g. gcc), or with other operating systems (e.g. Windows), may be different of course."

Firefox 64 bit appears to be faster than Firefox 32 bit, but not by much:

[https://www.reddit.com/r/firefox/comments/66k58d/firefox_32_bit_vs_64_bit/](https://www.reddit.com/r/firefox/comments/66k58d/firefox_32_bit_vs_64_bit/)

Firefox 32 bit uses less memory:

[https://www.zdnet.com/article/firefox-54-is-out-faster-but-no-memory-hog-like-chrome-so-is-it-time-to-try-it-again/](https://www.zdnet.com/article/firefox-54-is-out-faster-but-no-memory-hog-like-chrome-so-is-it-time-to-try-it-again/)

Firefox Quantum 64 bit appears to be faster than the 32 bit version:

[https://uk.pcmag.com/news/91993/firefox-quantum-offers-huge-leap-in-speed-usability](https://uk.pcmag.com/news/91993/firefox-quantum-offers-huge-leap-in-speed-usability)

The conclusion that I came to was that 32 bit Lubuntu may be the better choice if you have only 1GB of RAM, but 64 bit Lubuntu is likely to be better with 2GB of RAM.

---

### Post by xristosp59 on 2018-09-20
Thank you for your answers all :D

---

