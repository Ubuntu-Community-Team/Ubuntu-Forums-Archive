---
title: "Bigendian?"
date: 2012-11-18
forum: General Help
---

### Post by joerack on 2012-11-18
Hello, I get this error while compiling 

"Checking whether byte ordering is bigendian... yes
configure: error: bigendian is not supported... stopping"

please help

---

### Post by mcduck on 2012-11-18
Endianness is related to processor architecture (usually referring to whether the architecture has the most significant, or least significant, byte ordered first). x86 and x86-64 architectures used by Intel and AMD are little-endian, while PowerPC, ARM and most others are big-endian.

What are you trying to compile, and on what platform? Based on the error it would seem that the code you are trying to compile is not intended for the type of computer you are using.

[http://en.wikipedia.org/wiki/Endianness]("http://en.wikipedia.org/wiki/Endianness")

---

### Post by joerack on 2012-11-18
I'm trying to prepare a mysql database with lua with an i386 architecture

---

### Post by mcduck on 2012-11-18
You shouldn't need to compile anything to do that, both MySQl and Lua (and MySQL libraries for Lua) are available in Ubuntu's repositories.

If you prefer to compile manually anyway, make sure you have downloaded the correct source code.

---

