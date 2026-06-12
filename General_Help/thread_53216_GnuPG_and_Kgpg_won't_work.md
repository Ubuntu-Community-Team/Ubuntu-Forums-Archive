---
title: "GnuPG and Kgpg won't work"
date: 2005-07-30
forum: General Help
---

### Post by Psycs on 2005-07-30
Hi, everyone!

I used Synaptic to install Kgpg on Hoary (it downloaded about 20MB worth of files). It appeared installed under the Accessories menu, and initially it did work, once (it even installed Shredder onto my Desktop), but has since stopped working.

I've tried uninstalling and installing both GnuPG and Kgpg several times, but I always end with the same result. Clicking the icon in the menu does absolutely nothing.

Any advise on how to fix this?   

BTW, simply using GnuPG with the terminal is not really an option I'd like to consider.

Edit:   Might Seahorse (the Gnome equivalent) be an OK replacement? I'm particularly interested in the "drag & drop encryption + clipboard en/decryption" features of Kgpg.

---

### Post by Psycs on 2005-07-30
Could there be a problem with the installation? Notice the icon does not show...

---

### Post by ralphdewitt on 2005-08-04
Have you used Ksysgaurd to check if you have another gpg, or Kgpg process running. If so kill them off. Also check the forum searching for Kmail and kgpg there were some threads on the files that need to be install and the config file changes. Also look and see if you have and lock files in your .gnupg directory and sub directories. I had a problem with a dead lock file left over from my file importation.

Hope this helps some.

---

