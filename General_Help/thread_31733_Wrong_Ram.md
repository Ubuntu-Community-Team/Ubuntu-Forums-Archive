---
title: "Wrong Ram"
date: 2005-05-04
forum: General Help
---

### Post by DutchLau on 2005-05-04
Okay, so I've installed Ubuntu i386 on my AMD64 box (see my signature), I got everything working, but when I go to the system monitor it says I only have 885.4 MB Ram, although I have dual channel DDR 400 Ram installed in the PC. 

What could be causing this problem?

Greets,

DutchLau

---

### Post by bored2k on 2005-05-04
386 Kernel supports a maximum of 900MB of RAM. Install linux-686 OR your AMD64 appropiate kernnel for the correct RAM amount to be used.

---

### Post by DutchLau on 2005-05-04
Wow, I never knew that,

So just how do I install the 686 kernel? I don't want to install Hoary64 yet. I already did, but there just isn't enough support for it. 

Thanks,

DutchLau

---

### Post by bored2k on 2005-05-04
[QUOTE=DutchLau]Wow, I never knew that,

So just how do I install the 686 kernel? I don't want to install Hoary64 yet. I already did, but there just isn't enough support for it. 

Thanks,

DutchLau[/QUOTE]
 ```
echo debian SO rocks this will be done in one EZ step ;) && sudo apt-get install linux-686
``` 

Reboot, then select it from the grub menu.

---

### Post by DutchLau on 2005-05-04
It will keep the same programs & home folder right Bored? 

I'm downloading it now, thanks a million :P

Greets, 

DutchLau

---

### Post by mlmurray on 2005-05-04
I'll answer for bored2k:  Right.  It won't change anything other than the kernel and the modules. It doesn't mess with your home folder or any installed applications.

I can attest that he is right.  I have 1GB of ram and upgrading the kernel (the K7, in my case) fixed the problem.

Have no fear.  It's as simple as he says it is.  :)

---

### Post by DutchLau on 2005-05-04
Wow, amazing, I'm running the i686 kernel already, if anything, it's faster than the i386 kernel. Someday I will get around to installing Hoary 64, but until then, I guess I'm using i686!

Thanks alot!

---

