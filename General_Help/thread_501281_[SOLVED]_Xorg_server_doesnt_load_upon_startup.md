---
title: "[SOLVED] Xorg server doesnt load upon startup"
date: 2007-07-15
forum: General Help
---

### Post by Bob_12 on 2007-07-15
Xorg server doesnt load upon startup and all I get is an error screen asking if I want to diagnose the problem. Then after another screen it brings me to a black text only prompt type thing. It says something about Nvidia not being found so I was wondering what text commands I'd need to know to get back to the basic drivers for xorg and get my GUI back. I dont want to have to reinstall Ubuntu a 5th time....

---

### Post by Beamerboy on 2007-07-15
> **Bob_12 said:**
> Xorg server doesnt load upon startup and all I get is an error screen asking if I want to diagnose the problem. Then after another screen it brings me to a black text only prompt type thing. It says something about Nvidia not being found so I was wondering what text commands I'd need to know to get back to the basic drivers for xorg and get my GUI back. I dont want to have to reinstall Ubuntu a 5th time....

Which NVidia driver have you installed?

The standard repo driver is nvidia-glx
There is also nvidia-glx-new
If you are on an older card you may have installed nvidia-glx-legacy

Finally you may have installed the binary drivers from NVidia's site.

I ask because if you started out with nvidia-glx and then installed nvidia-glx-new and have attempted to revert to a different driver or install the official Nvidia binary, you are probably encountering an API mismatch (where the driver and the kernel module versions don't match).

If you have installed the Nvidia official binary driver from their site or used the Restricted Drivers Manager after installing NVidia-glx-new from the repos, you will find nvidia-glx-new has left something behind.

Can you check in /lib/linux-restricted-modules/ using the following command:

```

ls -al /lib/linux-restricted-modules/

```

If you have a file called ".nvidia_new_installed" then type:

```

sudo rm /lib/linux-restricted-modules/.nvidia_new_installed

```

Only do this if the driver you are currently trying run is NOT nvidia-glx-new

It is a silly bug that should have been resolved by now, it really is poor that the repo drivers are not cleaning themselves up properly when they are uninstalled.

If this doesn't solve your problem get back to me in this thread, I have a long history of dealing with restricted driver b0rkage so I have a few other tricks up my sleeve if this doesn't work.

Paladine

---

### Post by Bob_12 on 2007-07-15
Thank you so much, I onky wish I would have seen your post earlier. I already reloaded 6.06 (its the only disc I have currently burnt) on my computer and now i have another problem. Its stuck in 800x600 resolution and I cant get it to go higher. I'm going crazy! I love Ubuntu but sometimes linux is just so frustrating!

---

