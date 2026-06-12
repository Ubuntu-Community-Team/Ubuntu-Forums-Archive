---
title: "emptying trash issue"
date: 2014-09-03
forum: General Help
---

### Post by mattm0691 on 2014-09-03
Hi; linux noob so please break this down retard style for me. I am having a problem emptying my trash can; I have tried to do it through the terminal, I have tried to do it as root, I have tried bleach bit, and probably some other things that I am forgetting. When I try to empty, it gets stuck on a dialogue box that says preparing, and the computer usually just completely freezes up. I have let it sit for about 15 minutes and nothing happens. I have also tried re booting numerous times to see if any change has taken place, and no such luck. There is only one file in the trash, and the size is 0 mb. I also cannot restore this file. Any ideas of thoughts on how to fix this would be very helpful!

---

### Post by slickymaster on 2014-09-03
Hi mattm0691, welcome to the forums.

The trash folder is found at **$HOME/.local/share/Trash**

Open your terminal and try the following command to clear the trash```
rm -rf ~/.local/share/Trash/*
```Be careful using the **rm** command because any misuse may cause deleting sensitive system folders and files .

---

### Post by mattm0691 on 2014-09-03
That seems to have done the trick! Thanks for your reply

---

### Post by slickymaster on 2014-09-04
You're welcome. I'm glad you got it fixed.

Happy *buntuing.

---

