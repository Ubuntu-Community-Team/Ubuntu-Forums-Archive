---
title: "Kernel puts chars to /dev/random very slowly"
date: 2007-11-14
forum: General Help
---

### Post by Yakov Hrebtov on 2007-11-14
Ubuntu's kernel puts random chars to /dev/random very slowly. 
I use the folowing command in my scripts to generate some key:

cat /dev/random | head -c 45 | uuencode -m - | head -2 | tail -1

I need to wait for ages until this command completes on Ubuntu...
I know that /dev/random generate bytes only if kernel has required randomness in the entropy pool, and I'm ready to have some delays, but not 10+ minutes delay to generate a hundred of random bytes... 

I have compared Ubuntu's and Ferora's /dev/random behavior and see that Fedora's random generator performs much-much quicker.
Value in /proc/sys/kernel/random/entropy_avail on Fedora grows much faster than on Ubuntu.

Current behavior makes almost impossible for me use true random generator and forces me to use /dev/urandom.
How can I tune the random generator to speed it up? 

Thanks in advance.

---

