---
title: "Intel Phi Pcie coprocessor?"
date: 2022-04-16
forum: General Help
---

### Post by josephchrzempiec on 2022-04-16
Hello, A friend of mine is giving me Two Intil Phi pcie Co-Processor card. He has no clue and I have no clue how to make them work. I only know it needs an Xeon processor to make it work. I not a programmer by any means. But I really need help. Does anyone in the community work with this cards before and if so Can you please help me to get this up and running on ubuntu?


Joseph

---

### Post by DuckHook on 2022-04-16
There's little enough information I could find.

[https://linustechtips.com/topic/1277121-installing-and-configuring-intel-xeon-phi-coprocessor-7120p/](https://linustechtips.com/topic/1277121-installing-and-configuring-intel-xeon-phi-coprocessor-7120p/)
There was no resolution to that thread. The OP couldn't get the driver stack to work.

There's also this:
[https://www.phoronix.com/scan.php?page=news_item&px=No-More-Xeon-Phi-7200-Cards](https://www.phoronix.com/scan.php?page=news_item&px=No-More-Xeon-Phi-7200-Cards)
We don't know what model yours is, but if it's the above, then you are out of luck and Intel doesn't support it anymore even with legacy drivers.

Overall, it looks like you are trying to enable uncommon HW in an exotic usage.

As we warn all such users on these forums: Linux does not play well with oddball HW in edge use&#8209;cases. While it is flexible enough to be shoehorned into just about anything, this requires truly guru&#8209;level knowledge and the willingness to write your own driver modules. Speaking for myself, I have enough trouble figuring out what is *in* the kernel never mind *modifying* it.

Good luck and let us know how it goes.

---

