---
title: "32 or 64 bit?"
date: 2008-05-12
forum: General Help
---

### Post by elias4444 on 2008-05-12
I'm getting ready to upgrade to Ubuntu 8.04, but was wondering if it's time to finally try 64 bit or not?

I have a few questions though:

1) Is 64 bit Ubuntu really worth running over 32 bit? (i.e., is it faster? More stable?)
2) Does 32 bit software run on 64 bit Ubuntu?
3) Where does 64 bit Ubuntu fall short? Where will I see problems?
4) Should I just stick with 32 bit for now?

For the record: This will be running on Intel Core 2 Duo processor machines, and a x2 Dual Core Intel Xeon machine (a Mac Pro).

Any advice is appreciated! Thank you!

---

### Post by chewearn on 2008-05-13
Check the x86_64 sub-forum; 'tis in the sticky:
[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

---

### Post by jespdj on 2008-05-13
These questions have been asked by many people before you. Please do a search and read the stickies in the x86_64 forum.

> **elias4444 said:**
> 1) Is 64 bit Ubuntu really worth running over 32 bit? (i.e., is it faster? More stable?)
It's faster, but you might not notice a big speed difference in practice. Especially for processor-intensive tasks (for example, audio or video encoding) there might be a noticeable speed difference of up to about 30%. I don't think it is less or more stable than 32-bit.
> **elias4444 said:**
> 2) Does 32 bit software run on 64 bit Ubuntu?
Yes. You might need to install 32-bit libraries yourself for some 32-bit software. For some popular proprietary software packages for which there is no 64-bit native version available (Flash and Skype), there are packages which make installing it no more difficult than installing any other piece of software.
> **elias4444 said:**
> 3) Where does 64 bit Ubuntu fall short? Where will I see problems?
Nowhere, really.
> **elias4444 said:**
> 4) Should I just stick with 32 bit for now?
No, why? If you have a 64-bit capable processor, then why would you limit it to running a 32-bit OS?

I'm running 64-bit Ubuntu 8.04 on my Dell XPS M1530 and it works great.

---

### Post by nirkir on 2008-05-13
I've been using 64 bit version (on AMD) with both Fiesty and Hardy.

The bottom line is that you can get everything working.

It is also worth noting that some application might require another step or two to get then working properly (usually it is quite easy and I believe it is worth the pain).

Most notable are:
   1) application that work in 32-bit and therefore require 32 bit libraries (installable through synaptic)
   2) firefox plugins (you can get them to work using nspluginwrapper)

My opinion is that, having bought a 64-bit capable machine, I should use it.

---

