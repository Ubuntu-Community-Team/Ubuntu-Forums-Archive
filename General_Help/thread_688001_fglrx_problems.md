---
title: "fglrx problems"
date: 2008-02-04
forum: General Help
---

### Post by JohnnyBoy022 on 2008-02-04
Ok, I have a pretty complicated problem, I will try to explain it the best I can.
I did a clean install of Ubuntu 7.10. My system is a Dell Inspiron E1505 with ATI Mobility Radeon X1400. As soon as I installed Ubuntu a message popped up about restricted drivers. The fglrx driver was one on the list and I clicked install. Everything worked perfectly - compiz worked fine and all.

The only thing that didn't work was suspend. I talked to some people on IRC: they said the fglrx version that is in the Ubuntu restricted drivers repos didn't work with suspend. He said to download the new 8.1 version from the ati website. He said there was no need to uninstall the old one (that Ubuntu installed). So I went to ati's web site and downloaded the installer. It ran just fine, it looked like it had installed just fine. 

When I rebooted nothing worked. I tried fglrxinfo and it have me some weird error. I wasn't using any driver at this point. The only way I can get my system to work is to revert back to the generic vesa driver. I tried removing fglrx via synaptic, and then reinstalling fglrx from the ubuntu restricted drivers source. That didn't work either, I always have to go back and use the vesa driver.

Anyone know how I can completely remove all the junk that the ati installer put on, and get a fresh start? I'm thinking about doing a clean install of Ubuntu because I know that would work, but I would rather not. Thanks in advance for the help.

---

### Post by pointone on 2008-02-05
Not quite sure how you would go about removing everything; depends on exactly how you installed the drivers in the first place. Did you build a package or just run the installer directly?

For future reference: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by JohnnyBoy022 on 2008-02-05
I ran the installer directly. I guess the main problem is I don't know how to remove something that this installer created. How would I go about doing this?

---

