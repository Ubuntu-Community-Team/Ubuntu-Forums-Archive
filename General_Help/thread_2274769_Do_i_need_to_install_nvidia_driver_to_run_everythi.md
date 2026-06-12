---
title: "Do i need to install nvidia driver to run everything smooth on ubuntu"
date: 2015-04-22
forum: General Help
---

### Post by sebastiaan5 on 2015-04-22
pc specs: lenono y50-70 16gb ram intel i7 nvidia gtx860m

I want to reinstall ubuntu and I want to know if I can run everything (no gaming) on ubuntu on the intel card.
Previous ubuntu crahsed several times cause to nvidia driver, eventually I couldnt boot ubuntu any more and lost all my files on it.

The thing I want to do is run Netbeans, visual paradigm, VLC, mozilla, wireshark and some other tools for programming very smoothly and stable without pc crashing.

So my question is do I need to enable gtx860m graphic card?

greetings.

---

### Post by dino99 on 2015-04-22
vivid is ready to be released, and it have the required nvidia 346/349 drivers for your card into the archive. Nouveau is not so powerfull right now (will be when the kernel 4.1 will be released)

---

### Post by mc4man on 2015-04-22
On a Lenovo y510p Intel is absolutely fine, I never use the nvidia chip (GT 755m) as not needed & Optimus chips have fairly significant tearing due to the complete lack of vsync when using nvidia.
I'd go with 14.04.2 over 15.04 unless you want to keep upgrading every 9 months, if that's ok then 15.04 seems ok, certainly better than the 14.10 garbage.

---

### Post by nerdtron on 2015-04-22
You said no gaming. and already have a lot of applications installed. If something broke your display drivers, a newbie can't necessarily fix it immediately (although people here can help you).

As always, I remember this quote:

"If it ain't broke, don't fix it."

---

### Post by sebastiaan5 on 2015-04-22
Well I used to game but I want to quit with it for now and focus on programming and linux.

So I tried to install drivers tried 5 tutorials and tried to do myself eventually I did damage to the kernel and broke ubuntu.

---

### Post by dino99 on 2015-04-22
> **sebastiaan5 said:**
> Well I used to game but I want to quit with it for now and focus on programming and linux.

So I tried to install drivers tried 5 tutorials and tried to do myself eventually I did damage to the kernel and broke ubuntu.

331 is still not fixed( need to reinstall the -uvm package, not a big deal) , but newers are now

---

