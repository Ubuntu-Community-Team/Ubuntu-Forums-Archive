---
title: "AIFF/WAV to RAW PCM lossless conversion"
date: 2007-06-05
forum: General Help
---

### Post by tomane on 2007-06-05
Hi,

I tried rezound to convert an AIFF sample to raw PCM 16 bit signed big endian. However after looking carefully at the raw stream I noticed that the conversion had quantization/rounding errors. The original sample is 16 bits, signed, so I don't understand why saving the raw PCM would produce such errors.
So, I'm looking for a tool that can grab a PCM file, usually AIFF or WAV and create a Big Endian 16 bit signed RAW PCM stream. A GUI is not needed and I'd even prefer a CLI based tool.

Cheers,
--to.

---

### Post by tomane on 2007-06-06
Come on, multimedia gurus, show me whatchya got! :D

---

### Post by vanadium on 2007-06-06
Did you try sox? (ps I am not a multimedia guru and I do not know anything about Indian bytes).

---

### Post by tomane on 2007-06-06
Thanks vanadium,

With sox I seem unable to specify the endianness of the raw PCM stream. Any more tools? :confused:

I need to create a raw PCM stream that serves as the input for an embedded audio encoder. The encoder is big endian, whilst the PC is little endian, which is why most programs produce litle endian by default and might not allow to change that. Rezound ouputs big endian Raw PCM if I choose to, but it introduces conversion errors (probably because it does INT->FLOAT->INT).
Are there any tools that can make a RAW PCM stream with the desired endianness or should I just write a small dirty C program?

cheers,
--to

---

