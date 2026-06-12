---
title: "Help with WIne! PLease!"
date: 2007-06-10
forum: General Help
---

### Post by GeekyWill on 2007-06-10
So I just installed Ubuntu Feisty on my machine yesterday, and started looking for ways to play my Windows games and use some of my old apps. I quickly found Wine, followed there installation page, and it installed fine. The tabs in the Accessories bar were there, along with the uninstaller in the Systems Tools bar. The program started and worked fine.
Soon after I wanted to check the status on some debit cards online. The sites required IE to work, so I went looking for a Linux compatible one, and found IE4Linux. I followed the instructions and was soon using IE to check my balances. However, when I went to install some games through Wine, it wasn't in the Accessories tab. Puzzled, I went and completely removed the prgram and then reinstalled the application, to no effect. Finally, I removed IE4Linux, along with the changes it made to my sources.list. Still no Wine. I have checked my file system, and there is no .wine folder, even though Add/Remove Applications and Synaptic Package Manager both say it is installed.
Someone please help me!

Note: I posted this problem much earlier, but only got one answer, and that was useless. Remember, I am a newbie. Don't assume I know anything advanced.

---

### Post by crazy_vyper on 2007-06-13
using (i think) sudo dpkg -install -force all *package name* will reinstall wine regardless of errors, used this when installing cwiid yesterday ^_^ hope this helps

P.S If thats not the command, then it IS something like it.

---

### Post by andymushu on 2007-06-13
i have the exact same problem. the only way i can start wine is through the terminal, which doesn't even work. hope someone figures this out.

---

