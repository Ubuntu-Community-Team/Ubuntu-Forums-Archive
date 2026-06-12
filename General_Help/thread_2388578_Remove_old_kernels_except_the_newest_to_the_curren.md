---
title: "Remove old kernels except the newest to the current one being used."
date: 2018-04-04
forum: General Help
---

### Post by Robert_Gaines on 2018-04-04
I like the idea of removing old kernels to save harddisk space, the current procedure removes all but the current one in use. How can I do the same job but leave the previous kernel to the one in use in place? This would be useful for many reasons for unexplained screw ups, malicious attacks (rare but not impossible), or just your stupid self somehow making the system unbootable. Sure, there are tools in Linux to repair your system, but it is just easier and faster just to boot up in a previous image or simply just do a complete install for the majority of us who simply don't have the time for a nitty-gritty system repair. So, how would you go about doing this? Is there a way all ready built in? Can this be done in a script?

---

### Post by gordintoronto on 2018-04-04
sudo apt autoremove

---

### Post by Robert_Gaines on 2018-04-18
I already use sudo apt autoremove. I take it what I want to do is not possible so I can't leave one of the older images in case of primary image failure.

---

### Post by howefield on 2018-04-18
What do you mean by "current procedure" ?

sudo apt autoremove will remove all older kernels except for the current and next to last ones, in other words it will do what you want.

---

### Post by Impavidus on 2018-04-18
sudo apt autoremove does what you want, although I've noticed that after that feature on kernel updates was introduced (was it on 13.10?) it took a while before it worked reliably. It kept kernels that should have been removed. I'm working on a thread where autoremove doesn't work on 14.04. But even then, it's not very hard to manually select the kernel to remove. It's just four packages or so, and you don't have to do it very often.

---

