---
title: "Installing Darwinia"
date: 2008-06-05
forum: General Help
---

### Post by paraplegicpanda on 2008-06-05
I have successfully installed Uplink, Darwinia, and Defcon from Introversion Software, and Uplink and Defcon run great. Unfortunately I cannot get Darwinia to startup. This is the error I get:

```
paraplegicpanda@hacktopix:~/darwinia$ ./darwinia
.
./lib/darwinia.bin.x86: ./lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)

```

I encountered this when I started trying to install Uplink and I used the information [here]("http://whynotwiki.com/GNU/Linux_/_Running_32-bit_applications_on_64-bit_Linux") to get it going. Now I have tried fixing this problem the same way but to no avail. I have tried copying all of the files titled 'libgcc_s.so.1' that I find on the packages page, but none of the have worked. Any ideas?

HP DV6704NR laptop
Ubuntu 8.04 Hardy Heron 64-bit

---

### Post by benpage26 on 2008-06-22
I also have the same problem!
```
/usr/local/games/darwinia/lib/darwinia.bin.x86: /usr/local/games/darwinia/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

```

---

