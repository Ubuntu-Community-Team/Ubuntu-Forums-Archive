---
title: "Ubuntu 18.04 will not install on an Intel NUC7I7BNH..."
date: 2018-07-09
forum: General Help
---

### Post by vivicus on 2018-07-09
Hi there,

So I was previously on the 17 release on my NUC and other than Wayland being a trainwreck it's been relatively solid.  I went to do a fresh install of 18.04LTS because, you know, LTS.

When I attempt to load the live USB as non-UEFI, I get "32-bit relocation outside of kernel!".  When I attempt to load it as a UEFI setup in any of the options, I get a black screen with no information.

As far as troubleshooting goes (What little I have been able to do) I pushed the latest BIOS to my NUC and tried again, with similar results.  Am I up a creek, here?  Should I just deal with my dislike of 17 until it goes EOL?

Thanks,

Rusty

---

### Post by vivicus on 2018-07-09
Okay so get this craziness.

I did the following:

1.) Tried to put a new 18.04LTS image on the USB, ran it, nothing.  Same black screen.

2.) Pulled down the 16.04LTS image, flashed it, ran it.  Got an install as I expected, installed it, went fine.

3.) Reflashed 18.04LTS, tried to boot to it, this time the boot worked.  I am currently installing.  If I have any issues I'll open a new thread but I think this can be closed- I'm going to chalk it up to just absolute black magic (Which I hate) but I have no reasonable explanation.

---

### Post by mIk3_08 on 2018-07-09
I think if you already have the Ubuntu 17.04 release in your NUC you can upgrade it to 18.04;

go to terminal and type; 
sudo apt update && sudo apt dist-upgrade

or

there are some tutorials here;
[https://tutorials.ubuntu.com/tutorial/tutorial-upgrading-ubuntu-desktop#3](https://tutorials.ubuntu.com/tutorial/tutorial-upgrading-ubuntu-desktop#3)

But if you want a fresh install just set your bios to boot first in your usb before it can boot to your main hard drive.

---

### Post by vivicus on 2018-07-09
I could have, sure, but I didn't particularly want to keep what was on the NUC to begin with.  I've basically been using it as a testing ground for stuff.  Thanks for the recommendation, in any case.

---

### Post by mIk3_08 on 2018-07-10
Wow! Cool...:cool: Good Luck...

---

