---
title: "Unity doesn't work with latest amd driver?"
date: 2013-01-08
forum: General Help
---

### Post by Skullxbagel on 2013-01-08
Hey everyone,
     I just got Steam, and downloaded a game. It took a while, then told me I need the latest OpenGL software for my driver. So, I went to amd.com, found my driver( for the Radeon HD 6570 ) and, not to mention I couldn't do a non-force install, whenever it finished installing, and I rebooted, Unity was gone. To expand on what I meant whenever I said non-force install, it told me I still had fglrx drivers in my computer and I needed to remove them, or optionally use --force. I did the whole sudo apt-get remove --purge fglrx fglrx-dev* etc.... and it still said I had fglrx drivers, so I just used --force. So if anyone could guide me through a way to get the drivers for my card, and still keep Unity somehow, that would be great, Thanks. 

I have Ubuntu 12.04 if that matters at all.

---

### Post by Calinou on 2013-01-08
Install the driver from the Ubuntu repositories, not from AMD's web site (unless you absolutely want a very recent version of the driver).

Also, Steam is evil.

*AMD and NVIDIA websites: confusing people since 2007.®*

---

### Post by Skullxbagel on 2013-01-08
So I just search Synaptic Package Manager for fglrx?

EDIT: I did that, but this time, it just said I needed to update from the website.

---

