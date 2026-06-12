---
title: "Ubuntu 18.04 Vulkan Problems (AMD HD7900 Graphics Card Tahiti)"
date: 2018-05-24
forum: General Help
---

### Post by jonesyp on 2018-05-24
Hello,

I have installed a fresh copy of Ubuntu 18.04 on my PC with an AMD HD7900 Graphics Card. I believe the code name is 'Tahiti'

First thing I did was install the Oibaf PPA

```
https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers
```

Then I did a ```
sudo apt-get update
``` followed by ```
sudo apt install mesa-vulkan-drivers
```

When I type ```
vulkaninfo
```, I get the following message.


```
===========
VULKAN INFO
===========

Vulkan Instance Version: 1.1.70

/build/vulkan-Kbdbga/vulkan-1.1.70+dfsg1/demos/vulkaninfo.c:2700: failed with VK_ERROR_INITIALIZATION_FAILED
```

I find the Vulkan guidance very confusing so would appreciate any help.  I'm hoping to play the new Tomb Raider game.

Thanks

---

### Post by lryusaki2843 on 2018-06-17
I have the same problem, are you solved?

---

