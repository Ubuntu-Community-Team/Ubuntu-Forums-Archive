---
title: "Dependencies in Patching Ubuntu 6.10"
date: 2007-01-22
forum: General Help
---

### Post by DavidLeitch on 2007-01-22
Hallo from Hobart in Tasmania -- Australia's southern island State.

I am a very happy convert to Ubuntu, having recently installed 6.10 (from the live CD) onto my Windows 98SE PC. I have subsequently applied 2 batches of security patches (the first consisting of 98 packages, and 6 packages in the second batch).

I intend to install Edgy on my friend's PC also. Because the friend's Internet connection is very slow, I have copied my security patch downloads onto CD from /var/cache/apt/archives, keeping the first and second batches separate.

I expect that I should have no trouble if I copy the first batch into my friend's /var/cache/apt/archives directory, install them using Update Manager, delete them using <$sudo apt-get clean> and then repeating the process for the second batch.

However, if I were to copy all 104 packages into /var/cache/apt/archives and try to install them all at once, would the dependencies be resolved properly in all circumstances? Or wuld I be safer if I do it more methodically as described in preceding paragraph?

Thanks in advance...

---

### Post by aysiu on 2007-01-22
I've moved your thread to a more appropriate subforum.

---

