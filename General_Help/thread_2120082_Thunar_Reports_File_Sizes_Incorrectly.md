---
title: "Thunar Reports File Sizes Incorrectly"
date: 2013-02-25
forum: General Help
---

### Post by SillySod on 2013-02-25
I recently upgraded to Thunar 1.6.2 but the downside to this appears to be that it no longer knows that there are 1,024 bytes in a kilobyte or 1,024 kilobytes in a megabyte, it thinks there are 1,000 in each, so all the values in the "size" column are wrong!

Folders are reported as being 4.1kb when they are 4,096 bytes = 4K exactly!

I regularly use files exactly 640K long but Thunar tells me these are 655.4K long!  This is a bit of problem as part of the checking process when generating these 640K files involves verifying the file length!

Is there a fix to this?

---

### Post by Impavidus on 2013-02-25
It's a question of definition. The difficulty is that the words kilobyte, megabyte etc. are slightly ambiguous. To better follow the established (and official) practices of kilometres, megapascals and gigajoules, it has become practice to use the SI prefixes for bytes also in powers of 1000. For the powers of 1024 the term kibibyte, mebibyte, gibibyte (short for kilobinarybyte etc.) have come into use, frequently abbreviated to kiB, MiB, GiB. This is commonly done on Linux, maybe not on other systems. I think many programs have a switch where you can select which practice you prefer.

---

### Post by SillySod on 2013-02-27
Well, in over 30 years of using computers, a kilobyte has always been 1,024 bytes, not a bit more and certainly not a bit less!

I can't see an option in Thunar to change the notation to what it should be, anybody know of a way?

---

