---
title: "Compile vanilla kernel in the EXACT ubuntu way?"
date: 2007-10-10
forum: General Help
---

### Post by hua on 2007-10-10
I have 4G RAM on my desktop. Unfortunately, generic 7.10 kernel can only see 3.5G
I want to stay with 32bit kernel.
I have tried 7.10 server kernel, which has PAE enabled. It sees all 4G RAM, but I am struggling to have fglrx driver installed on server kernel without any hassle. Therefore, I am planning to compile the vanilla kernel in the EXACT way how ubuntu developers do, but with PAE enabled(I think it should be enable by default), to achieve max compatibility.
I have read some the topics about compiling vanilla kernel in the ubuntu way and done kernel compiling several times before. However, I am struggling to find the official patch list that ubuntu developer applied on the vanilla kernel source.

Does sush a list exist? or there is something more than just a patch list? Can we ask the developer team publish the info to save us the time to guessing?

Thanks

---

### Post by nick_h on 2007-10-10
Ubuntu kernel developers use a git repository.

Read the [Kernel GIT Guide](https://wiki.ubuntu.com/KernelGitGuide) for information on how to download the latest kernel.

---

