---
title: "Dapper: libmcrypto ? Where is it, where can I get it ? (needed for minisip)"
date: 2006-12-23
forum: General Help
---

### Post by scotty64 on 2006-12-23
Does anyone know what (Dapper) package contains the libmcrypto library and the .dev files? 
I only found libcrypto.
I would like to compile the "minisip" softphone ([www.minisip.org](www.minisip.org)) and it complains about that missing library. And just in case Dapper has no "libmcrypto": Where can I download the source for that library - Google only returns links to developer websites, but nothing like a "libmcrypto homepage".

thanks and happy Xmas...

---

### Post by scotty64 on 2006-12-26
Found the problem:
libmcrypto is actually part of the minisip trunk, but the build script provided with minisip seems not to recognize and build it...

---

