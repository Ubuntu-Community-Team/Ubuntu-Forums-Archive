---
title: "Question about moving from 32-bit OS to a 64-bit"
date: 2015-03-11
forum: General Help
---

### Post by New_buntu_89 on 2015-03-11
I have a question for the Ubuntu computer experts that is mostly for my peace of mind. 

I recently found that I had accidentally installed Ubuntu with the wrong architecture. According to most sources I could find, since I am using a modern laptop with an Intel i7 processor and 6GB of RAM, I should be using the AMD64 version and not the x86. So, I re-installed Ubuntu on the / partition, and left the /home partition untouched. My question is whether or not this was the right choice, as opposed to re-installing everything. It seems to be working right now, but is there anything in the /home partition that is specific to either architecture? If so, should I re-install everything, or change some particular files in the /home folder? Should I expect any kind of weird little problems, glitches, crashes or slow-downs in the future?

---

### Post by ian-weisser on 2015-03-11
> **New_buntu_89 said:**
> My question is whether or not this was the right choice
Yes, it was the right choice.


> **New_buntu_89 said:**
> is there anything in the /home partition that is specific to either architecture?
In typical usage, no. Preserving your /home should be just fine.
When I converted exactly the way you did from 32 to 64, I preserved my /home, too, without any ill effects.

---

