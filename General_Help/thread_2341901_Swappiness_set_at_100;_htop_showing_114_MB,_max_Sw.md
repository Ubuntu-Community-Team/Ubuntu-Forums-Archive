---
title: "Swappiness set at 100; htop showing 114 MB, max Swap is 7.5 GB; Wanting max"
date: 2016-11-01
forum: General Help
---

### Post by SciGuy1872 on 2016-11-01
Hi.  I set swappinesss at 100 because I wanted the full 7.5 GB to be used, and I read that doing such with the swappiness setting would achieve my goal; however, htop reports that only 114 MB is being used.  
     I read that setting it to a value of 10 would be better--just trying different values right now.  Is there some other way to force the computer to use the full 7.5GB?

Thanks,
     Anthony

---

### Post by oldrocker99 on 2016-11-02
If you want all your RAM to be used before the swapfile is used, swappiness needs to be set to **0**. If you want the swapfile to be used over RAM, swappiness needs to be set to 100.

Here's pretty much all you need to know:[http://askubuntu.com/questions/103915/how-do-i-configure-swappiness](http://askubuntu.com/questions/103915/how-do-i-configure-swappiness).

---

### Post by QIII on 2016-11-02
You do realize that physical memory is at least an order of magnitude faster than swap, don't you?

---

### Post by SciGuy1872 on 2016-11-02
Yes, I do realize that--I am just trying different settings.  Chromium takes 15 seconds to start--I should probably use Lubuntu.  The speed with other programs seem to be fine, maybe Thunderbird is an exception.  I have 4GB of memory, along with a dual-core at 2.3 GHz.
Thanks for the answer,
                  Anthony

---

### Post by mcduck on 2016-11-02
swappiness is not absolute control over swap use. Even with swappiness set to 0, the kernel will use swap if it would otherwise run out of memory. And even with swappiness of 100, kernel will still only swap if it needs to.

It only controls how much the kernel should favour keeping old data cached in RAM versus swapping it to hard drive. If there isn't enough data, then there's nothing to swap. And if the kernel needs more memory than you have RAM, it has to sue swap regardless (since the only other options would be to crash or give up and throw "out of memory" error).

To make it even more complicated, swappiness isn't the only number the kernel considers when deciding if something should be swapped or kept in RAM. The actual logic is bit more complicated than taht.

---

