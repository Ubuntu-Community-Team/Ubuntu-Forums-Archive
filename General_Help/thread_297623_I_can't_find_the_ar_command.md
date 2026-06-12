---
title: "I can't find the ar command"
date: 2006-11-11
forum: General Help
---

### Post by mesh2005 on 2006-11-11
I can't find the ar command. How can I install it? I have installed the Ubuntu 64-bit

---

### Post by lloyd_b on 2006-11-11
I believe that "ar" is part of the package "binutils".

Note: If you're planning on doing development on that machine, just install the "build-essential" package - this should get you "ar" and a lot of other useful tools.

Lloyd B.

---

### Post by mesh2005 on 2006-11-11
I couldn't find the binutils using apt-get!

---

### Post by lloyd_b on 2006-11-11
>  I couldn't find the binutils using apt-get!

Could you be more specific?  Run "apt-get install binutils", then post the output.  "binutils" is a standard package - if you can't retrieve it, then there's something wrong with your apt configuration.

Lloyd B.

---

### Post by mesh2005 on 2006-11-12
Thank you, I fixed it. It was a missing line in the source.list

---

