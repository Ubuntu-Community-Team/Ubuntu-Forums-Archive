---
title: "How do I completely remove Wine?"
date: 2008-03-20
forum: General Help
---

### Post by Hazed on 2008-03-20
Hey all,

I just installed Wine and tried to install Photoshop CS2 on it, which failed.

I then realised there was a new version of Wine out that is capable of installing Photoshop CS2 straight from the cd without any hacking required.

So I tried "sudo apt-get remove --purge wine" and it removed it (or so I thought). I reinstalled the new version of wine, but when i went to install Photoshop, it thought it was still already installed and only asked if i wanted to repair or remove (remove didnt even work!).

So I tried complete removal via Synaptic, then deleted the .wine folder and rebooted...

I reinstalled Wine when ubuntu booted back up, and hey, guess what??? All my Adobe Photoshop files are back!

I have no clue what is going on... I deleted the damn folder, lol... How can it be back???

What I want to do is completely remove Wine and all installed applications under it, and start again...

Any suggestions?

---

### Post by bodhi.zazen on 2008-03-20
sudo apt-get remove --purge wine && rm -rf ~/.wine

---

