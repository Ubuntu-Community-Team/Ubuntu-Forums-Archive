---
title: "Strange behavior of gcc 4.2 (?)"
date: 2008-06-04
forum: General Help
---

### Post by writebear on 2008-06-04
Hi, I'm a newbie here. I will be glad if somebody can help me.

I have a small C program that tests how fast my PC can calculate.

int i, j=0;
clock_t start, stop;
start = clock();
for (i=0; i<INT_MAX; i++) {
 if (i<j) j++; // Only the comparison is actually executed.
}
stop = clock();
printf("time = %ldms\n", (stop-start)*1000/CLOCKS_PER_SEC);

While the binary compiled by gcc-3.3 works fine (it outputs something
like 7460ms), the binary compiled by gcc-4.2 outputs something like
-1769ms that should never happen. I'm quite :confused:... I'm using
Ubuntu 8.04 with the latest updates.

---

