---
title: "API Mismatch, reverting kernal."
date: 2007-02-10
forum: General Help
---

### Post by gridbread on 2007-02-10
I made the mistake of not paying attention to my update manager and upgraded my kernal. 
As a result X has the error "API mismatch" which says the Nvidia kernal has 1.0-8776 (beta drivers for Beryl) and my X module has 1.0-9746.
I can't upgrade using "sudo apt-get install --reinstall linux-restricted-modules '1.0-9746' nvidia-glx" because they don't exist.
I've been able to get X to work by selecting an alternative in grub, but that seems like just a temporary fix, I'd think.
How would I go about downgrading/reverting to a previous compatible kernal?
Thanks!

---

### Post by banditti on 2007-02-11
Does this help?

[http://ubuntuforums.org/showthread.php?t=357757&highlight=API+mismatch+nvidia+beryl](http://ubuntuforums.org/showthread.php?t=357757&highlight=API+mismatch+nvidia+beryl)

---

