---
title: "xpdf segfaults"
date: 2007-11-15
forum: General Help
---

### Post by gte258v on 2007-11-15
I'm running 64-bit Feisty.  I just installed xpdf and am having problems with it segfaulting.  After installing it, I used it successfully for a short while.  Then when I tried to reopen xpdf later, from a terminal, it immediately printed a message saying it segfaulted.  Later, I tried again, and it failed without an error message and with $? = 141.  This happens with any PDF file and happens regardless of whether I run xpdf or xpdf.bin. Dmesg shows messages like:

[3698719.083473] xpdf.bin[12440]: segfault at 00002b5a31bd6000 rip 00002b5a34048034 rsp 00007fff78fb3bf8 error 4
[3698737.882497] EDAC e752x: Non-Fatal Error PCI Express B

Evince works fine with the same PDF's.  If I log out and back in, I can use xpdf again, but only for a while before it starts segfaulting again.  Anyone have any ideas?

-Eric

---

