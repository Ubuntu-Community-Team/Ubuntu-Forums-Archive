---
title: "[SOLVED] Strange Message at Boot up"
date: 2008-01-24
forum: General Help
---

### Post by Odd-rationale on 2008-01-24
Hello! I get a strange error message on boot up:

> 
Starting up ...
PCI: Failed to allocate mem resource #6:20000@c0000000 for 0000:01:00.1
Loading, please wait...

But after that, it seems to boot up normally. I find no glitch/reduction in performance.

Could someone please decipher this message for me?

Is this something I should be worried about?

I get this message every time I boot up a live CD or a ordinary hard drive installation.

Thanks!

---

### Post by AnonCat on 2008-01-24
If everything seems to be working it's probably not worth worrying about.  I get a few messages like that myself but they seem to be largely irrelevant.  Some computers have BIOS bugs that can cause those kinds of errors.

---

### Post by Odd-rationale on 2008-01-24
OK thanks!

Could you at least tell me what it means?

I got into linux to understand more about how my computer works. :)

Thanks!

---

### Post by PeterJS on 2008-01-24
It's usually related to nvida and ATI graphics cards, they don't take kindly to being randomly probed and that's the error message letting you know that the probe was denied. Later on the full drivers load up and can access them properly.

---

