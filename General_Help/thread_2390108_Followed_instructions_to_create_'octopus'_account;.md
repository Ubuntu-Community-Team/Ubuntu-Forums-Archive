---
title: "Followed instructions to create 'octopus' account; but still cannot encrypt home"
date: 2018-04-25
forum: General Help
---

### Post by random9999 on 2018-04-25
I have no clue what is going on. I recently installed lubuntu 17.10.1. When I attempted to encrypt the home folder during the installation, it wouldn't encrypt it. It kept saying something about 'swap space', I wrote it down and I think it's "An unsafe swap space has been detected". It wouldn't let me encrypt it. 

So I'm attempting to encrypt it after the fact. I'm following the instructions here: [https://websiteforstudents.com/encrypt-home-folder-ubuntu-17-10/](https://websiteforstudents.com/encrypt-home-folder-ubuntu-17-10/)

I managed to create the octopus account and tried to continue with step 3. But it tells me "ERROR:   Cannot proceed".

Where it says sudo ecryptfs-migrate-home -u [COLOR=#ff0000]USER[/COLOR]
in the instructions, I entered octopus instead of USER. It said ERROR Cannot proceed. So I tried it again with my real username. Got the same ERROR message.

I have attempted sudo ecryptfs-migrate-home -u [COLOR=#ff0000]USER[/COLOR] in both accounts.

---

### Post by random9999 on 2018-04-27
bump

---

