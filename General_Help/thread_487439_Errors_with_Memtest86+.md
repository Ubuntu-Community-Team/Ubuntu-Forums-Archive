---
title: "Errors with Memtest86+"
date: 2007-06-29
forum: General Help
---

### Post by datasong on 2007-06-29
I recently installed Ubuntu 7.04 and began to get erratic behavior.  The computer would totally freeze up after brief usage.  This happened with both the 32-bit and 64-bit versions.  I decided to run Memtest86+ to see what would happen.  I got a bunch of errors that I don't understand but I noticed something that seemed strange to me on the screen.  The line that seemed to be indicating the part of memory being tested was different before and after the errors appeared.

Before errors it said:  "Testing:   108K - 3072M  4096M" 

After errors it said:   "Testing:  4096M - 5120M  4096M"

Where did "5120M" come from?  I only have 4096M of RAM.  Can anyone offer any insight?

AMD-64 3500+
4 GB RAM
NVIDIA GeForce FX 5200

---

### Post by orasis on 2007-06-29
> **datasong said:**
> I recently installed Ubuntu 7.04 and began to get erratic behavior.  The computer would totally freeze up after brief usage.  This happened with both the 32-bit and 64-bit versions.  I decided to run Memtest86+ to see what would happen.  I got a bunch of errors that I don't understand but I noticed something that seemed strange to me on the screen.  The line that seemed to be indicating the part of memory being tested was different before and after the errors appeared.

Before errors it said:  "Testing:   108K - 3072M  4096M" 

After errors it said:   "Testing:  4096M - 5120M  4096M"

Where did "5120M" come from?  I only have 4096M of RAM.  Can anyone offer any insight?

AMD-64 3500+
4 GB RAM
NVIDIA GeForce FX 5200


Faulty RAM can report wrong sizes, you have bad RAM - only solution find the bad SIMM's by testing with one stick in your PC at a time until you find the culprit - and replace it.

---

### Post by datasong on 2007-06-29
You confirmed my suspicion.  Thanks.

---

