---
title: "Cannot select Ubuntu from dual-boot list - Windows 7 Dual Boot"
date: 2013-04-21
forum: General Help
---

### Post by tehhh1337 on 2013-04-21
Hello all,

So I've actually used Ubuntu on and off for quite sometime. Anyways, recently I tried to install it on my desktop PC. The installation went fine, when I rebooted to finish the installation all was fine, but when I turned off the computer and came back in about an hour, I could not select ubuntu from the OS list on the dual boot screen. This was because every time I pushed a button on my keyboard the entire computer froze. So, what I had to do is wait 10 seconds to get into Windows. Interestingly enough, when I pressed any key on the Windows error recovery it would freeze too (when you force shut down your computer windows pulls up error recovery screen). I ended up just uninstalling Ubuntu, and I'm now able to use the keyboard in the error recovery screen without a freeze. 

Does anyone know why this is happening? It didn't happen with my laptop.

My keyboard is USB, and it has a few "complex" features like touch-sensitive volume controls, etc.

Thanks

---

### Post by tehhh1337 on 2013-04-25
Still waiting for a reply

---

### Post by oldfred on 2013-04-26
Did you have USB keyboard & mouse enabled in BIOS?

I had similar issues and both Windows & Ubuntu would work with their own drivers, but not grub as it relied on the BIOS setting. Perhaps Windows recovery needs BIOS setting also, depending on how you get to it?

---

