---
title: "Mini-Note wireless only works in 2.6.24-17?"
date: 2008-06-12
forum: General Help
---

### Post by xjgnsdof on 2008-06-12
I notice that when I use any other kernel, I can't connect to my wireless network. Is anybody else experiencing this? Any workarounds?

---

### Post by earlycj5 on 2008-06-12
I've used it with 2.6.24-16, 17, 18 and a custom compiled 2.6.25.5 vanilla kernel.

I just recompiled NDISWrapper, installed, and modprobed NDISWrapper for each kernel version as I made a change.  If you're using the NDISWrapper from the repositories then it should be updating with the kernel updates I'd think.

---

### Post by xjgnsdof on 2008-06-12
So I should recompile NDiswrapper with each kernel update? I'll give that a shot.

---

### Post by earlycj5 on 2008-06-13
I'm not saying that you *should*.  I'm just saying, that's my method since I'm fiddling with different kernel configurations and is the easiest way for me to enable wireless.  It's easy to compile as far as many of the programs I compile go.

Try it and see if it works.  Don't forget to install checkinstall so you can create a .deb package.

---

### Post by xjgnsdof on 2008-06-13
I followed the instructions at [https://wiki.ubuntu.com/LaptopTestingTeam/HP2133]("https://wiki.ubuntu.com/LaptopTestingTeam/HP2133"), but I still can't connect to my home wireless network to save my life. The laptop next to it, a Compaq that also runs ndiswrapper, connects after two or three attempts and stays on for days at a time, so there's no problem with the network.

After following the instructions and updating Ubuntu, the wireless on my Mini-Note goes to hell. It takes about 20 attempts to connect, and it only stays on for a few hours.

I need concrete advice, here, because I need this computer to access the web at my new job next week. For the record, my Mini-Note is the KX870AT model.

---

### Post by earlycj5 on 2008-06-13
I never can keep the model numbers straight, 7200 RPM HD, Vista Business, 6 Cell, Bluetooth, 2GB RAM?  If so that's the model I have.

In that case I should be able to help with more concrete advice.

I've had issues with using WPA at home with my Mini-Note, I've not looked into it much yet living in a small town and a limestone home.

Here at work I have no problems with WEP though.

I've followed the Wiki to a "T" except I've compiled and installed my own NDISWrapper, version 1.53 as noted above.  The Broadcom driver download it suggests is what I use.

---

### Post by xjgnsdof on 2008-06-13
Yes, that's the right model. I guess I just need to try another wireless network and see what happens.

I recall, however, getting perfect connectivity when I used the -17 kernel. Do you know where I can get a deb for it? I can't find it in Synaptic.

---

### Post by earlycj5 on 2008-06-14
A .deb for which program?

---

### Post by xjgnsdof on 2008-06-14
I need a deb for the -17 kernel, as I don't know how to upgrade to it otherwise.

---

### Post by earlycj5 on 2008-06-14
> **elgilicious said:**
> I need a deb for the -17 kernel, as I don't know how to upgrade to it otherwise.

Guess I wasn't clear enough, you want a .deb for the NDISWrapper for the -17 kernel then?

I don't know, like I said, it should've upgraded with the kernel.

Not in the repositories?  Since I roll my own I don't keep up with what's there for NDISWrapper...

I don't think I have the -17 kernel installed on here but I can and can make a .deb for you to try.

*edit*  I don't even see that kernel in the repositories I have -16 and -18 are all that I see.

In that case I'd upgrade to the latest kernel version -18 and see if it works.  If you're comfortable compiling NDISWrapper yourself then try that...

---

### Post by xjgnsdof on 2008-06-14
I guess I don't know what I want. I too don't see that kernel in the repos, but I know that I upgraded to -17 a few weeks back. I'm thinking about just starting from scratch, because this is really bothering me. If you have any suggestions, let me know.

---

### Post by xjgnsdof on 2008-06-14
I just did a fresh install of Hardy via USB drive. I followed the wiki instructions to the letter and updated everything but the kernel. Before the update, I could connect; after, I can't. This is BS. I'm supposed to run an outdated system?

---

### Post by xjgnsdof on 2008-06-15
I installed Linux Mint 5 and, after updates, couldn't connect after 12 attempts. What the hell is going on? I started from a fresh install!

---

### Post by xjgnsdof on 2008-06-15
For some reason, I connect to the wireless network just fine in my room, after a handful of attempts. When I'm right next to the wireless router, it takes forever to connect.

---

