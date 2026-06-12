---
title: "reinstall latest kernel after bonked module build/install?"
date: 2013-02-09
forum: General Help
---

### Post by Underpants on 2013-02-09
I did something silly with a build/modprobe/make while running on my latest installed kernel. Now that kernel will not boot. I am currently running on a previous kernel.

How can I clean this up? I would like to just get back to the "stock" latest kernel that is in the apt repo.

Edit: I should note.... I was trying to install flashcache ([https://github.com/facebook/flashcache/](https://github.com/facebook/flashcache/))

I tried to do

```
sudo apt-get install --reinstall linux-image-generic linux-image
```
That didn't fix it; so I tried the "recovery mode" option and see a kernel panic around the loading of the flashcache module.... I must need to delete something, somewhere...


[IMG]http://i.imgur.com/ii6JdhF.jpg[/IMG]

---

