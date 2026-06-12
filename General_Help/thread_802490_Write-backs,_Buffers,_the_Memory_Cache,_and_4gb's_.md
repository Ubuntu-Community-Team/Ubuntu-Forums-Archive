---
title: "Write-backs, Buffers, the Memory Cache, and 4gb's of scientific data in RAM"
date: 2008-05-21
forum: General Help
---

### Post by mlapaglia on 2008-05-21
Hello,

I am using a Dell E521 with 500gb + 320gb HDD's, 4GB DDR2 800MHz memory, and a AMD Athlon X2 64bit 2.3GHz processor.

I am running a few scientific programs through the computer, and I am noticing the memory reported using "free -m" to be quite low. Some googling taught me that Linux using memory caches, and for the most part all of my memory is being used 100% of the time, either for actual processes or for the cache system. After watching 2 x 1gb files get loaded into memory for processing over the course of an hour, I watched the buffer count go up and down, quite surprised with how efficient Linux is with memory.

I've got a question about data integrity. I have read that if a program doesn't use write-throughs, and the power to the computer is cut, the data can be lost. How can I know if my program is using write-backs or write-throughs?

---

