---
title: "Wubi 7.10: fix freezes with hardy kernel"
date: 2007-12-26
forum: General Help
---

### Post by daspooky on 2007-12-26
Hello folks,

I have some good news for those of you who are able to install Gutsy succesfully by using Wubi 7.10 alpha 386, but are experiencing complete freezups of your machines while copying large files.

According to our friend Ago, the freezes are caused by a bug in the Kernel used in Ubuntu Gutsy (2.6.22). The cure to the freezes is to download kernel **2.6.24** from kernel.org, compile and install it in Gutsy. I have tried this, and I can confirm this kernel indeed fixes the freezes. However I was never able to get sound and wifi to work after compiling this kernel.

The ultimate solution is to download and install the Hardy development kernel (also 2.6.24). Fortunately, this is extremely easy to do by using the script **hardy.py** which can be found [here]("http://ubuntuforums.org/showthread.php?t=646755") (**many thanks to walkerk for creating this handy script!**). The beauty about it is that sound and wifi are not broken after installing it!

**So, 2 steps to get a loopmounted Gutsy installation without freezes:**

1. Install Gutsy with wubi 7.10 alpha 386
2. Run the script hardy.py to get the current Hardy kernel

Voila, no freezes anymore!

---

### Post by ago on 2007-12-26
Thanks a lot for the script.

FYI a new version of Wubi 8.04 will appear soon.

I am waiting for 2 things:

1. I have submitted a series of patches that have to be merged upstream
2. Even if the 2.6.24 kernel is available in hardy repositories as a package, hardy still uses the 2.6.22 kernel by default, they will switch soon

For the rest we should be in good shape.

---

### Post by daspooky on 2007-12-28
All credits go to walkerk :)

Thanks for the info Ago. Good to hear new builds are coming soon. From the looks of it, I think all will be fine with wubi 8.04. I still had zero freezes since the few days I'm running kernel 2.6.24.

---

### Post by siddharth.unnikrishnan on 2007-12-29
hey...

im really runnin outta patience for the new Wubi 8.04 to be out and can ya please tell me how long will i probably have to wait?

eagerly waiting for a response....

n keep up the great work....

thankz....

---

### Post by ago on 2007-12-30
As mentioned I have to wait for the new kernel to be used by default and a few patches to be merged upstream, the first part is out of my control, the second part should happen within the first two weeks of the new year. So we might have the first builds by mid january but not necessarily with the new kernel.

---

